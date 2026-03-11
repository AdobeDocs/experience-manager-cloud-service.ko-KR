---
Title: How to Connect AEM Adaptive Forms with Azure SQL Storage
Description: Learn how to configure an Azure SQL Database connection in AEM Forms and integrate it with your Adaptive Forms to store or retrieve data efficiently using JDBC.
Keywords: Azure SQL integration with AEM Forms, Connecting Adaptive Forms to Azure SQL Database, JDBC connection for Azure SQL in AEM Forms, Storing Adaptive Form data in Azure SQL
feature: Adaptive Forms, Core Components
role: User, Developer
badgeSaas: label="AEM Forms" type="Positive" tooltip="AEM Forms에 적용됩니다)."
exl-id: 111accf7-bf34-499c-832e-c001ea68f6d3
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 2%

---

# 적응형 양식을 Azure SQL 스토리지에 연결

Adobe Experience Manager(AEM)의 적응형 Forms은 외부 데이터베이스와 통합하여 데이터를 저장하거나 검색할 수 있습니다.
이 문서에서는 AEM as a Cloud Service을 통해 JDBC를 사용하여 적응형 양식을 Azure SQL 데이터베이스에 연결하는 방법에 대해 설명합니다.

>
> 
> 이 안내서는 고급 네트워킹이 활성화된 샌드박스가 아닌 AEM as a Cloud Service 환경에 적용됩니다.

## 장점

Azure SQL과 적응형 Forms을 통합하면 다음과 같은 몇 가지 이점이 있습니다.

* **실시간 데이터 상호 작용:** 양식과 Azure 데이터베이스 간에 데이터를 실시간으로 읽고 쓸 수 있습니다.
* **확장성:** Azure SQL은 엔터프라이즈 수준 애플리케이션에 적합한 확장 가능한 데이터베이스 성능을 제공합니다.
* **중앙 데이터 저장소:** 양식 제출 및 검색된 데이터를 중앙 위치에 안전하게 저장합니다.
* **보안 규정 준수:** Azure의 기본 제공 네트워크, 방화벽 및 암호화 옵션을 활용하여 보안 통신을 보장합니다.
* **클라우드 기반 통합:** AEM as a Cloud Service을 사용하는 최신 클라우드 기반 아키텍처에 이상적입니다.

## 사전 요구 사항

* [Azure SQL 데이터베이스](https://learn.microsoft.com/en-us/azure/azure-sql/database/single-database-create-quickstart?view=azuresql&tabs=azure-portal)를 만들고 **프록시 연결**&#x200B;이 활성화되어 있는지 확인하십시오.

  >[!NOTE]
  >
  > `Azure Portal → SQL Server → Security → Networking → Connectivity`프록시 연결&#x200B;**을 사용하려면**(으)로 이동합니다.

  ![Azure Db 만들기](/help/forms/assets/create-azure-db.png)

* 만든 Azure 데이터베이스에 대해 전용 이그레스 IP를 사용하여 구성된 [고급 네트워킹](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/networking/dedicated-egress-ip-address)을 사용하도록 설정합니다.

  >[!NOTE]
  >
  >    전용 이그레스 IP를 활성화한 후. `Azure Portal → SQL Server → Security → Networking → Public Access`(으)로 이동하여 이그레스 IP를 방화벽 규칙에 추가합니다.

  ![이그레스 IP](/help/forms/assets/cretae-azure-db-egress-ip.png)

* 다음을 사용하여 클라우드 환경에서 포트 전달 설정:
   * **portOrigin**: `30000–30999` 사이
   * **portDest**: `1433`(Azure SQL의 기본 포트)
예: `portOrigin: 30433 → portDest: 1433`

     >
     > 
     > Adobe Cloud Manager 지원 센터에 문의하여 포트 전달을 구성할 수 있습니다.


## Azure SQL에 적응형 Forms을 연결하는 단계

**1단계: AEM as a Cloud Service Git 리포지토리 복제**

1. 명령줄을 열고 AEM as a Cloud Service 저장소를 저장할 디렉터리(예: `/cloud-service-repository/`)를 선택합니다.

1. 아래 명령을 실행하여 저장소를 복제합니다.

   ```
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<app-id>/
   ```

   **이 정보를 찾을 수 있는 위치**

   이러한 세부 정보를 찾는 방법에 대한 단계별 지침은 Adobe Experience League 문서 &quot;[Git 액세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git)&quot;를 참조하십시오.

   명령이 성공적으로 완료되면 로컬 디렉터리에 새 폴더가 생성됩니다. 이 폴더의 이름은 응용 프로그램의 이름을 따릅니다.

1. 편집기에서 저장소 폴더를 엽니다.

**2단계: 필요한 JAR 추가**

[ 패키지를 통해 AEM 프로젝트에 대한 ](https://central.sonatype.com/artifact/com.microsoft.sqlserver/mssql-jdbc/12.8.0.jre11?smo=true)SQL 드라이버 종속성`all`을(를) 포함합니다.:

>[!NOTE]
>
> 프로젝트에 SQL 종속성을 포함하려면 [SQL 드라이버 종속성](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool#mysql-driver-dependencies) 섹션을 참조하십시오.

**3단계: JDBC 구성 추가**

1. JDBC 풀에 대한 OSGi 구성을 배치해야 하는 `<application folder>` 내의 다음 디렉터리로 이동합니다.

   ```bash
   cd ui.config/src/jcr_root/apps/<application folder>/osgiconfig/config/
   ```

**4단계: Azure SQL 연결 구성 파일 만들기**

1. 파일을 만듭니다.

   ```bash
   com.day.commons.datasource.jdbcpool.JdbcPoolService~<application folder>-sql.cfg.json
   ```

1. 아래 코드 행을 추가합니다.

   ```json
   {
   "datasource.name": "azuredbshr",
   "jdbc.driver.class": "com.microsoft.sqlserver.jdbc.SQLServerDriver",
   "jdbc.username": "<azureuser>",
   "jdbc.connection.uri": "jdbc:sqlserver://$[env:AEM_PROXY_HOST;default=proxy.tunnel]:30433;database=testdb;user=<azureuser>;password=<azurepassword>;encrypt=true;trustServerCertificate=false;hostNameInCertificate=*.database.windows.net;loginTimeout=30;",
   "jdbc.password": "******",
   "jdbc.validation.query": "SELECT 1"
       }
   ```

   >
   >
   > `jdbc.username`을(를) 실제 Azure 사용자 이름으로 바꾸고 `jdbc.password`을(를) 실제 보안 암호로 바꿉니다.

**5단계: 변경 내용을 커밋하고 푸시합니다**

터미널을 열고 다음 명령을 실행합니다.

```bash
git add .
git commit -m "<commit message>"
git push 
```

**6단계: Cloud Manager 파이프라인을 통해 변경 내용 배포**

1. **AEM Cloud Manager**&#x200B;에 로그인합니다.
1. 프로젝트로 이동하고 파이프라인을 실행하여 변경 사항을 배포합니다.

**7단계: 양식 데이터 모델(FDM) 만들기**

AEM 및 Azure 설정이 완료되고 코드 변경 사항이 배포되면:

1. AEM 작성자 인스턴스로 이동합니다.
1. **도구** > **Forms** > **데이터 통합**&#x200B;으로 이동합니다.
1. 새 **양식 데이터 모델**&#x200B;을(를) 만듭니다.
1. **데이터 원본** 탭에서 만든 JDBC 구성을 선택합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 클릭하고 연결을 확인합니다.

![양식 데이터 모델 만들기](/help/forms/assets/create-azure-sql-fdm.png)

**8단계: 적응형 양식에서 만든 FDM 사용**

1. 편집 모드에서 적응형 양식을 엽니다.
1. 이전 단계에서 생성된 FDM을 데이터 모델로 선택합니다.
1. [데이터 바인딩을 사용하여 양식 필드를 Azure SQL 데이터 원본](/help/forms/work-with-form-data-model.md#add-data-model-objects-and-services)에 연결하고 제출 액션을 구성하십시오.

## 모범 사례

* 구성 파일에서 암호를 하드코딩하지 않도록 하려면 **암호 관리**&#x200B;를 사용하십시오.
* 데이터베이스 자격 증명을 정기적으로 회전하고 구성을 안전하게 업데이트합니다.
* JDBC 연결 로그에서 오류 및 지연을 모니터링합니다.
* SQL 데이터베이스 및 방화벽 구성의 보안을 유지하기 위한 Azure 모범 사례를 따르십시오.
* 권한이 높은 데이터베이스 계정을 양식 액세스에 사용하지 마십시오.

## 관련 문서

{{af-submit-action}}
