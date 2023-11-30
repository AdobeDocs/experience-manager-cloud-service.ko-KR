---
title: 콘텐츠 전송 도구 시작하기
description: 콘텐츠 전송 도구를 시작하는 방법 알아보기
exl-id: c0cecf65-f419-484b-9d55-3cbd561e8dcd
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '1424'
ht-degree: 21%

---

# 콘텐츠 전송 도구 시작하기 {#getting-started-content-transfer-tool}


## 사용 가능 {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_download"
>title="다운로드"
>abstract="소프트웨어 배포 포털에서 콘텐츠 전송 도구를 zip 파일로 다운로드할 수 있습니다. 패키지 관리자를 통해 소스 AEM(Adobe Experience Manager) 인스턴스에 패키지를 설치할 수 있습니다. 최신 버전을 다운로드하십시오."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=ko-KR" text="릴리스 정보"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="소프트웨어 배포 포털"

소프트웨어 배포 포털에서 콘텐츠 전송 도구를 zip 파일로 다운로드할 수 있습니다. 다음을 통해 패키지를 설치할 수 있습니다. [패키지 관리자](/help/implementing/developing/tools/package-manager.md) 소스 Adobe Experience Manager(AEM) 인스턴스에서 다음을 수행합니다. 최신 버전을 다운로드하십시오. 최신 버전에 대한 자세한 내용은 [릴리스 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=ko-KR).

버전 2.0.0 이상만 지원되며 최신 버전을 사용하는 것이 좋습니다.

>[!NOTE]
>[소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) 포털에서 컨텐츠 전송 도구를 다운로드합니다.

## 소스 환경 연결 {#source-environment-connectivity}

>[!NOTE]
>
>Cloud Acceleration Manager에서 마이그레이션 세트가 삭제된 경우에도 연결 오류가 발생할 수 있습니다.

소스 AEM 인스턴스가 허용 목록에 추가된 특정 호스트에만 도달할 수 있는 방화벽을 통해 실행되고 있을 수 있습니다. 추출을 성공적으로 실행하려면 AEM을 실행 중인 인스턴스에서 다음 끝점에 액세스할 수 있어야 합니다.

* Azure Blob 스토리지 서비스: `casstorageprod.blob.core.windows.net`

>[!NOTE]
>다음 오류로 인해 추출에 실패하는 경우: &quot;javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX 경로 작성 실패: sun.security.provider.certpath.SunCertPathBuilderException: 요청된 대상에 대한 올바른 인증 경로를 찾을 수 없음&quot; 해당 CA 인증서를 가져와 이 문제를 해결할 수 있습니다.

### SSL 로깅 활성화 {#enable-ssl-logging}

SSL/TLS 연결 문제를 이해하는 것은 때때로 어려울 수 있습니다. 추출 프로세스 중 연결 문제를 해결하려면 다음 단계에 따라 소스 AEM 환경의 시스템 콘솔을 통해 SSL 로깅을 활성화할 수 있습니다.

1. 다음 위치로 이동하여 소스 인스턴스의 Adobe Experience Manager 웹 콘솔로 이동합니다. **도구 - 작업 - 웹 콘솔** 또는 을 통해 URL로 바로 이동할 수 있습니다 *https://serveraddress:serverport/system/console/configMgr*
1. 검색 대상 **컨텐츠 전송 도구 추출 서비스 구성**
1. 연필 아이콘 버튼을 사용하여 구성 값을 편집합니다
1. 활성화 **추출을 위해 SSL 로깅 활성화** 설정 후 누르기 **저장**:

   ![이미지](/help/journey-migration/content-transfer-tool/assets/enable_ssl_logging.png)

>[!NOTE]
>이 플래그는 SSL 문제 디버깅에만 사용됩니다. 추출을 실행하기 전에 많은 양의 디스크 공간이 필요할 수 있으므로 플래그가 비활성화되어 있는지 확인하십시오. 이로 인해 드라이브 용량이 채워지고 추출 프로세스가 실패할 수 있습니다.

## 컨텐츠 전송 도구 실행 {#running-tool}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_demo"
>title="콘텐츠 전송 도구 실행"
>abstract="콘텐츠 전송 도구를 사용하여 콘텐츠를 AEM as a Cloud Service(작성자/게시)에 마이그레이션하는 방법을 알아보십시오."
>additional-url="https://video.tv.adobe.com/v/35460/?quality=12&amp;learn=on" text=" 데모 보기"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=ko-KR#migration" text="튜토리얼 - 콘텐츠 전송 도구 사용하기"

다음 섹션은 새 버전의 콘텐츠 전송 도구에 적용됩니다. 이 섹션을 따라 컨텐츠 전송 도구를 사용하여 컨텐츠를 AEM as a Cloud Service으로 마이그레이션하는 방법을 알아보십시오.

### 추출 설정 단계 {#extraction-setup-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction_setup"
>title="추출 설정 단계"
>abstract="마이그레이션 세트를 만들고 관리하는 방법과 추출 키를 복사하는 방법을 알아보십시오."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/migration/content-transfer-tool.html?lang=ko-KR#migration" text="튜토리얼 - 콘텐츠 전송 도구 사용하기"

<!-- Contextualhelp id "aemcloud_ctt_extraction_setup" must be added here -->

1. CAM(Cloud Acceleration Manager)에 로그인한 다음 이전에 만든 CAM 프로젝트를 클릭하여 AEM으로 as a Cloud Service으로 이동할 준비를 평가합니다. CAM 프로젝트를 생성하지 않은 경우 CAM에서 프로젝트 생성 및 관리를 참조하십시오.

1. 다음을 클릭합니다. **컨텐츠 전송** 카드. 이렇게 하면 마이그레이션 세트 목록 보기로 이동합니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam1.png)

1. 다음을 클릭하여 마이그레이션 세트 만들기 **마이그레이션 세트 만들기**.

   >[!NOTE]
   >
   >Cloud Acceleration Manager에서는 프로젝트당 만료된 세트를 포함하여 최대 20개의 마이그레이션 세트를 만들 수 있습니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam2.png)

   다음 대화 상자가 표시됩니다. 오랫동안 사용하지 않으면 마이그레이션 세트가 만료됩니다. 일정 기간 동안 프로젝트 카드 및 마이그레이션 작업 테이블 행에 경고가 표시되면 마이그레이션 세트가 만료되어 해당 데이터를 더 이상 사용할 수 없습니다. 리뷰 [마이그레이션 세트 만료](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md#migration-set-expiry) 을 참조하십시오.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam3.png)

   >[!NOTE]
   >
   >이름은 AEM 노드의 동일한 규칙을 따라야 하므로 다음 문자를 포함할 수 없습니다. . / : [ ] | *

1. 이제 목록 보기에 마이그레이션 목록이 표시됩니다. 세 점 기호(**...**) 드롭다운을 열고 을 선택합니다. **추출 키 복사**. 추출 단계에서 이 키가 필요합니다. 이 추출 키를 복사합니다.

   >[!NOTE]
   >
   >추출 키를 사용하면 소스 AEM 환경을 마이그레이션 세트에 안전하게 연결할 수 있습니다. 이 키를 암호와 동일한 주의로 취급하고 이메일과 같은 보안되지 않은 매체를 통해 공유하지 마십시오.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam4.png)

### 마이그레이션 세트 채우기 {#populating-the-migration-set}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_populate_migrationset"
>title="마이그레이션 세트 채우기"
>abstract="마이그레이션 세트를 만든 후에는 AEM as a Cloud Service 환경으로 이동해야 하는 소스 인스턴스의 콘텐츠로 채워야 합니다. 이를 위해 소스 인스턴스에 콘텐츠 전송 도구를 설치해야 합니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/extracting-content.html?lang=ko-KR" text="콘텐츠 추출하기"

Cloud Acceleration Manager에서 만든 마이그레이션 세트를 채우려면 소스 Adobe Experience Manager(AEM) 인스턴스에 최신 버전의 콘텐츠 전송 도구를 설치해야 합니다. 이 섹션을 통해 마이그레이션 세트를 채우는 방법을 알아보십시오.

1. 소스 Adobe Experience Manager 인스턴스에 최신 버전의 컨텐츠 전송 도구를 설치한 후 로 이동합니다. **작업 - 컨텐츠 마이그레이션**

1. 클릭 **마이그레이션 세트 만들기**

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam5.png)

1. 이전에 CAM에서 복사한 추출 키를 의 추출 키 입력 필드에 붙여넣습니다. **마이그레이션 세트 만들기** 양식. 이렇게 하면 마이그레이션 세트 이름 및 CAM(Cloud Acceleration Manager) 프로젝트 이름 필드가 자동으로 채워집니다. 이 이름은 CAM의 마이그레이션 세트 이름 및 생성한 CAM 프로젝트 이름과 일치해야 합니다. 이제 콘텐츠 경로를 추가할 수 있습니다. 콘텐츠 경로를 추가한 후 마이그레이션 세트를 저장합니다. 포함 또는 제외된 버전으로 추출을 실행할 수 있습니다.

   >[!NOTE]
   >
   >추출 키가 유효하고 만료에 가깝지 않은지 확인하십시오. 다음 위치에서 이 정보를 가져올 수 있습니다. **마이그레이션 세트 만들기** 추출 키를 붙여넣은 후 대화 상자를 표시합니다. 연결 오류가 발생하는 경우 다음을 참조하십시오. [소스 환경 연결](#source-environment-connectivity) 추가 정보.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam6.png)

1. 그런 다음, 다음 매개 변수를 선택하여 마이그레이션 세트를 만듭니다.

   1. **버전 포함**: 필요에 따라 선택합니다. 버전이 포함된 경우 경로 `/var/audit` 감사 이벤트를 마이그레이션할 때 자동으로 포함됩니다.

      ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam7.png)

      >[!NOTE]
      >버전을 마이그레이션 세트의 일부로 포함하려는 경우 다음을 사용하여 추가 작업을 수행합니다 `wipe=false`, 콘텐츠 전송 도구의 현재 제한으로 인해 버전 지우기를 비활성화해야 합니다. 버전 삭제를 활성화하고 마이그레이션 세트에 대해 추가 작업을 수행하는 경우 수집 작업을 다음과 같이 수행해야 합니다. `wipe=true`.


   1. **포함할 경로**: 경로 브라우저를 사용하여 마이그레이션해야 하는 경로를 선택합니다. 경로 선택기는 입력하거나 선택하여 입력을 허용합니다.

      >[!IMPORTANT]
      >마이그레이션 세트를 만드는 동안 다음 경로가 제한됩니다.
      >* `/apps`
      >* `/libs`
      >* `/home`
      >* `/etc` (일부 `/etc` CTT에서 경로를 선택할 수 있음)

1. 클릭 **저장** 의 모든 필드를 채운 후 **마이그레이션 세트 만들기** 세부 정보 화면입니다.

<!-- 1. You will view your migration set in the **Content Transfer** wizard, as shown in the figure below.

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt07.png)

   All the existing migration sets are displayed on the **Content Transfer** wizard with their current status and status information. You may see some of these icons described below.

   * A *red cloud* indicates that you cannot complete the extraction process.
   * A *green cloud* indicates that you can complete the extraction process.
   * A *yellow icon* indicates that you did not create the existing migration set and the specific one is created by some other user in the same instance.

1. Select a migration set and click **Properties** to view or edit the migration set properties. While editing properties, it is not possible to change the **Migration Set name** or the **Service URL**. 

   ![image](/help/journey-migration/content-transfer-tool/assets-ctt/ctt06.png) -->

### 마이그레이션 세트 크기 확인 중 {#migration-set-size}

마이그레이션 세트를 만든 후 추출 프로세스를 시작하기 전에 마이그레이션 세트에 대해 크기 검사를 실행하는 것이 좋습니다.
마이그레이션 세트에서 크기 검사를 실행하면 다음과 같은 작업을 수행할 수 있습니다.

* 에 디스크 공간이 충분한지 확인 `crx-quickstart` 추출을 완료할 하위 디렉터리입니다.
* 마이그레이션 세트 크기가 지원되는 제품 제한 내에 속하는지 확인하고 실패한 콘텐츠 수집을 방지합니다.

크기 검사를 실행하려면 아래 단계를 따르십시오.

1. 마이그레이션 세트를 선택하고 **크기 확인**.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam8.png)

1. 이렇게 하면 **크기 확인** 대화 상자.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam9.png)

1. 클릭 **크기 확인** 프로세스를 시작합니다. 그런 다음 마이그레이션 세트 목록 보기로 돌아오면 다음을 나타내는 메시지가 표시됩니다. **크기 확인** 이(가) 실행 중입니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam10.png)

1. 다음 이후 **크기 확인** 프로세스가 완료되었습니다. 상태가 다음으로 변경됩니다. **완료됨**. 동일한 마이그레이션 세트를 선택하고 **크기 확인** 결과를 봅니다. 다음은 의 예입니다. **크기 확인** 경고가 없는 결과입니다.

   ![이미지](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam11.png)

1. 다음과 같은 경우 **크기 확인** 결과에 따르면 디스크 공간이 부족하거나 마이그레이션 세트가 제품 제한을 초과하거나 둘 다 **경고** 상태가 표시됩니다.

<!--   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image6.png)
   
   Below is an example of **Check Size** results with warnings.
 
   ![image](/help/journey-migration/content-transfer-tool/assets/CTT_CheckSize_image7.png) -->


## 다음 단계 {#whats-next}

마이그레이션 세트를 만드는 방법을 배웠다면 이제 콘텐츠 전송 도구의 추출 및 수집 프로세스에 대해 알아볼 수 있습니다. 이러한 프로세스를 학습하기 전에 다음을 검토해야 합니다 [대형 콘텐츠 저장소 처리](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) 컨텐츠 전송 활동의 추출 및 수집 단계 속도를 크게 향상시켜 컨텐츠를 AEM으로 as a Cloud Service 이동합니다.
