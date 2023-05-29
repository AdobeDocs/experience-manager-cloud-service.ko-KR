---
title: 설치  [!DNL Workfront for Experience Manager enhanced connector]
description: 설치  [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Integrations
exl-id: 2907a3b2-e28c-4194-afa8-47eadec6e39a
source-git-commit: 5da4be3ec9af6a00cce8d80b8eea7f7520754a1d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

#  설치 [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기를 클릭하십시오.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-connector-install.html) |
| AEM as a Cloud Service | 이 문서 |

에서 관리자 액세스 권한이 있는 사용자 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 향상된 커넥터를 설치합니다. 설치하기 전에 플랫폼 지원 및 기타 를 검토하십시오 [커넥터 사전 요구 사항](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>* Adobe을 사용하려면 [!DNL Adobe Workfront for Experience Manager enhanced connector] 인증된 파트너를 통해서만 또는 [!DNL Adobe Professional Services]. 공인 파트너 없이 구축 및 구성된 경우 또는 [!DNL Adobe Professional Services], Adobe에서 지원되지 않습니다.
>
>* Adobe은 다음에 대한 업데이트를 릴리스할 수 있습니다. [!DNL Adobe Workfront] 및 [!DNL Adobe Experience Manager] 따라서 이 커넥터가 이중화됩니다. 이 경우 고객은 이 커넥터를 사용하지 않도록 전환해야 할 수 있습니다.
>
>* Adobe은 향상된 커넥터 버전 1.7.4 이상을 지원합니다. 이전 프리릴리스 및 사용자 지정 버전은 지원되지 않습니다. 향상된 커넥터 버전을 확인하려면 의 5단계 (a)를 참조하십시오. [향상된 커넥터 설치 지침](workfront-connector-install.md).
>
>* 다음을 참조하십시오 [Workfront for Experience Manager Assets 강화 커넥터에 대한 파트너 인증 시험](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). 시험에 대한 자세한 내용은 [시험 안내서](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).


커넥터를 설치하기 전에 다음 사전 설치 단계를 따르십시오.

1. [방화벽 구성](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FAdministration_and_Setup%2FGet_started-WF_administration%2Fconfigure-your-firewall.html). 의 IP 클러스터를 알기 위해 [!DNL Workfront], 다음으로 이동 [!UICONTROL 설정] > [!UICONTROL 시스템] > [!UICONTROL 고객 정보].

1. Dispatcher에서 다음 HTTP 헤더를 허용합니다. `authorization`, `username`, 및 `apikey`. 허용 `GET`, `POST`, 및 `PUT` 에 대한 요청 `/bin/workfront-tools`.

1. 다음 경로가에 없는지 확인합니다. [!DNL Experience Manager] 저장소:

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`
   * `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`

1. 이 설치는에서 Maven 프로젝트를 설정하는 데 지식이 필요합니다. [!DNL Experience Manager] as a [!DNL Cloud Service]. 다음 리소스를 사용하여 Maven 프로젝트에 서드파티 패키지를 포함하는 방법을 이해합니다.

   * [Maven 프로젝트에 서드파티 패키지 포함](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#including-third-party).
   * [배포 방법 [!DNL Cloud Manager]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html).

에 추가 기능을 설치하려면 [!DNL Experience Manager] as a [!DNL Cloud Service], 다음 단계를 수행합니다.

1. 에서 향상된 커넥터 다운로드 [Adobe 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip).

1. [액세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=en) Cloud Manager에서 AEM as a Cloud Service 저장소를 복제합니다.

1. 원하는 IDE를 사용하여 복제된 AEM as a Cloud Service 저장소를 엽니다.

1. 1단계에서 다운로드한 향상된 커넥터 zip 파일을 다음 경로에 배치합니다.

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >다음과 같은 경우 `resources` 폴더가 없습니다. 폴더를 만드십시오.


1. 추가 `pom.xml` 종속성:

   1. 상위에 종속성 추가 `pom.xml`.

      ```XML
      <dependency>
         <groupId>digital.hoodoo</groupId>
         <artifactId>workfront-tools.ui.apps</artifactId>
         <type>zip</type>
         <version>enhanced connector version number</version>
         <scope>system</scope>
         <systemPath>${project.basedir}/ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
      </dependency>
      ```

      >[!NOTE]
      >
      >종속성을 상위에 복사하기 전에 향상된 커넥터 버전 번호를 업데이트하십시오. `pom.xml`.

   1. 다음에 종속성 추가 `all module pom.xml`.

      ```XML
         <dependency>
            <groupId>digital.hoodoo</groupId>
            <artifactId>workfront-tools.ui.apps</artifactId>
            <type>zip</type>
            <scope>system</scope>
            <systemPath>${project.basedir}/../ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
         </dependency>
      ```


1. 추가 `pom.xml` 임베드. 추가 [!DNL Workfront for Experience Manager enhanced connector] 패키지 대상 `embeddeds` 의 섹션 `pom.xml` 을 참조하십시오. 모든 모듈에 포함되어야 함 `pom.xml`.

   ```XML
   <!-- Workfront Tools -->
   <embedded>
      <groupId>digital.hoodoo</groupId>
      <artifactId>workfront-tools.ui.apps</artifactId>
      <type>zip</type>
      <target>/apps/<path-to-project-install-folder>/install</target>
   </embedded>
   ```

   포함된 섹션의 대상이 다음으로 설정됩니다. `/apps/<path-to-project-install-folder>/install`. 이 JCR 경로 `/apps/<path-to-project-install-folder>` 의 필터 규칙에 포함되어야 합니다. `all/src/main/content/META-INF/vault/filter.xml` 파일. 저장소에 대한 필터 규칙은 일반적으로 프로그램 이름에서 파생됩니다. 폴더 이름을 기존 규칙의 대상으로 사용합니다.

1. 변경 사항을 저장소에 푸시합니다.

1. 파이프라인 실행 대상 [cloud Manager에 변경 사항 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html).

1. 시스템 사용자 구성을 만들려면 `wf-workfront-users` 위치: [!DNL Experience Manager] 사용자 그룹 및 권한 할당 `jcr:all` 끝 `/content/dam`. 시스템 사용자 `workfront-tools` 은 자동으로 만들어지며 필요한 권한은 자동으로 관리됩니다. 의 모든 사용자 [!DNL Workfront] 강화된 커넥터를 사용하는 사용자는 이 그룹의 일부로 자동으로 추가됩니다.

업데이트 정보 [!DNL Workfront for Experience Manager enhanced connector] 이전 버전에서 최신 버전으로 [여기](update-workfront-enhanced-connector.md).

## 간의 연결 구성 [!DNL Experience Manager] as a [!DNL Cloud Service] 및 [!DNL Workfront] {#configure-connection}

을 사용하여 연결을 만들려면 [!DNL Workfront], 다음 단계를 수행합니다.

1. 위치 [!DNL Experience Manager], 선택 **[!UICONTROL 도구]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Workfront 도구 구성]**.

1. 선택 `workfront-tools` 왼쪽 패널에서 을(를) 선택하고 **[!UICONTROL 만들기]** 페이지의 오른쪽 위 영역에 있는 옵션입니다.

1. 다음에서 **[!UICONTROL Workfront 연결]** 대화 상자에서 다음에 대한 필수 세부 정보를 제공합니다. [!DNL Workfront] 배포 및 선택 **[!UICONTROL Workfront에 연결]** 옵션을 선택합니다. 성공적으로 연결되면 [!DNL Workfront] 문서 사용자 정의 통합이 [!DNL Workfront] 환경.

   ![연결 [!DNL Experience Manager] 및 [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. 다음 위치로 이동 **[!UICONTROL 고급]** 탭을 클릭하고 옵션을 선택합니다. **[!UICONTROL 서버 AEM은 as a Cloud Service입니까]**.
