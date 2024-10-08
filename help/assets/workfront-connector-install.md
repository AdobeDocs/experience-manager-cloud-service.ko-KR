---
title: ' [!DNL Workfront for Experience Manager enhanced connector] 설치'
description: ' [!DNL Workfront for Experience Manager enhanced connector] 설치'
role: Admin
feature: Workfront Integrations and Apps
exl-id: 2907a3b2-e28c-4194-afa8-47eadec6e39a
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 2%

---

# [!DNL Workfront for Experience Manager enhanced connector] 설치 {#assets-integration-overview}

| [모범 사례 검색](/help/assets/search-best-practices.md) | [메타데이터 모범 사례](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [OpenAPI 기능이 있는 Dynamic Media](/help/assets/dynamic-media-open-apis-overview.md) | [AEM Assets 개발자 설명서](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-connector-install.html) |
| AEM as a Cloud Service | 이 문서 |

[!DNL Adobe Experience Manager]에서 [!DNL Cloud Service](으)로 관리자 액세스 권한이 있는 사용자가 향상된 커넥터를 설치합니다. 설치하기 전에 플랫폼 지원 및 기타 [커넥터에 대한 필수 구성 요소](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience)를 검토하십시오.

>[!IMPORTANT]
>
>2022년 6월 현재, Adobe은 Workfront과 Adobe Experience Manager Assets as a Cloud Service 기본 통합을 연결하기 위한 새로운 통합을 발표했습니다. 이 통합은 이 두 솔루션을 연결하는 데 필요한 방법이 되었습니다. Workfront과 새 AEM Assetsas a Cloud Service 를 연결하기 위한 향상된 커넥터(1.9.8 및 이후 버전)의 모든 향후 구현이 차단됩니다. 이 통합을 설정하는 방법에 대한 자세한 내용은 [Experience Manager Assets as a Cloud Service 통합 구성](workfront-connector-configure.md)을 참조하십시오.

>[!IMPORTANT]
>
>* Adobe을 사용하려면 인증된 파트너 또는 [!DNL Adobe Professional Services]을(를) 통해서만 [!DNL Adobe Workfront for Experience Manager enhanced connector]을(를) 배포하고 구성해야 합니다. 인증 파트너 또는 [!DNL Adobe Professional Services] 없이 배포 및 구성된 경우 Adobe에서 지원하지 않습니다.
>
>* Adobe은 이 커넥터를 중복 커넥터로 만드는 [!DNL Adobe Workfront] 및 [!DNL Adobe Experience Manager]에 대한 업데이트를 릴리스할 수 있습니다. 이러한 경우 고객은 이 커넥터를 사용하지 않도록 전환해야 할 수 있습니다.
>
>* Adobe은 향상된 커넥터 버전 1.7.4 이상을 지원합니다. 이전 프리릴리스 및 사용자 지정 버전은 지원되지 않습니다. 향상된 커넥터 버전을 확인하려면 [향상된 커넥터 설치 지침](workfront-connector-install.md)의 5단계(a)를 참조하십시오.
>
>* [Workfront for Experience Manager Assets 강화 커넥터에 대한 파트너 인증 시험](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html)을 참조하세요. 시험에 대한 자세한 내용은 [시험 가이드](https://express.adobe.com/page/Tc7Mq6zLbPFy8/)를 참조하세요.

커넥터를 설치하기 전에 다음 사전 설치 단계를 따르십시오.

1. AEM as a Cloud Service 프로그램에서 고급 네트워킹을 구성하고 IP 허용 목록을 활성화한 경우 이벤트 구독 및 다양한 API 호출이 AEM으로 전달되도록 허용하려면 Workfront IP를 이 허용 목록에 추가해야 합니다.

   * [Workfront 클러스터 IP](https://experienceleague.adobe.com/docs/workfront/using/administration-and-setup/get-started-administration/configure-your-firewall.html?lang=en#ip-addresses-to-allow-for-clusters-1-2-3-5-7-8-and-9). [!DNL Workfront]의 IP 클러스터를 확인하려면 **[!UICONTROL 설정]** > **[!UICONTROL 시스템]** > **[!UICONTROL 고객 정보]**&#x200B;로 이동합니다.

   * [Workfront 이벤트 구독 API IP](https://experienceleague.adobe.com/docs/workfront/using/adobe-workfront-api/event-subscriptions/event-subs-api.html)

   >[!IMPORTANT]
   >
   >* 프로그램에 대해 고급 네트워킹이 구성되어 있고 IP 허용 목록을 사용하는 경우 고급 Workfront 커넥터 아키텍처의 제한으로 인해 프로그램 이그레스 IP를 Cloud Manager의 허용 목록에도 추가해야 합니다.
   >
   >* p{PROGRAM_ID}.external.adobeaemcloud.com
   >
   >* 프로그램의 IP를 찾으려면 터미널 창을 열고 다음과 같은 명령을 실행합니다.
   >
   >    ```
   >    dscacheutil -q host -a name p{PROGRAM_ID}.external.adobeaemcloud.com
   >
   >    ```

1. [!DNL Experience Manager] 저장소에 다음 오버레이가 없는지 확인하십시오. 이러한 경로에 기존 오버레이가 있는 경우 오버레이를 제거하거나 둘 사이의 변경 사항 델타를 병합해야 합니다.

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`
   * `/apps/dam/gui/content/assets/jcr:content/actions/secondary/create/items/fileupload`

1. 이 설치를 수행하려면 지식이 있어야 [!DNL Experience Manager]의 Maven 프로젝트를 [!DNL Cloud Service](으)로 설정할 수 있습니다. 다음 리소스를 사용하여 Maven 프로젝트에 서드파티 패키지를 포함하는 방법을 이해합니다.

   * [Maven 프로젝트에 서드파티 패키지를 포함합니다](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#including-third-party).
   * [배포 대상 [!DNL Cloud Manager]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html).

[!DNL Experience Manager]에서 [!DNL Cloud Service](으)로 추가 기능을 설치하려면 다음 단계를 수행하십시오.

1. [Adobe 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip)에서 향상된 커넥터를 다운로드합니다.

1. Cloud Manager에서 [액세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=en)하고 AEM as a Cloud Service 저장소를 복제합니다.

1. 원하는 IDE를 사용하여 복제된 AEM as a Cloud Service 저장소를 엽니다.

1. 1단계에서 다운로드한 향상된 커넥터 zip 파일을 다음 경로에 배치합니다.

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >`resources` 폴더가 없으면 폴더를 만드십시오.


1. `pom.xml` 종속성 추가:

   1. 부모 `pom.xml`에 종속성을 추가하십시오.

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
      >상위 `pom.xml`에 종속성을 복사하기 전에 향상된 커넥터 버전 번호를 업데이트하십시오.

   1. `all module pom.xml`에 종속성을 추가합니다.

      ```XML
         <dependency>
            <groupId>digital.hoodoo</groupId>
            <artifactId>workfront-tools.ui.apps</artifactId>
            <type>zip</type>
            <scope>system</scope>
            <systemPath>${project.basedir}/../ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
         </dependency>
      ```


1. `pom.xml` 임베드를 추가합니다. 모든 하위 프로젝트의 `pom.xml`에 있는 `embeddeds` 섹션에 [!DNL Workfront for Experience Manager enhanced connector] 패키지를 추가합니다. 모든 모듈 `pom.xml`에 포함되어야 합니다.

   ```XML
   <!-- Workfront Tools -->
   <embedded>
      <groupId>digital.hoodoo</groupId>
      <artifactId>workfront-tools.ui.apps</artifactId>
      <type>zip</type>
      <target>/apps/<path-to-project-install-folder>/install</target>
   </embedded>
   ```

   포함된 섹션의 대상이 `/apps/<path-to-project-install-folder>/install`(으)로 설정되어 있습니다. 이 JCR 경로 `/apps/<path-to-project-install-folder>`은(는) `all/src/main/content/META-INF/vault/filter.xml` 파일의 필터 규칙에 포함되어야 합니다. 저장소에 대한 필터 규칙은 일반적으로 프로그램 이름에서 파생됩니다. 폴더 이름을 기존 규칙의 대상으로 사용합니다.

1. 변경 사항을 저장소에 푸시합니다.

1. 파이프라인을 실행하여 [변경 내용을 Cloud Manager에 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html)합니다.

1. 시스템 사용자 구성을 만들려면 [!DNL Experience Manager] 사용자 그룹에 `wf-workfront-users`을(를) 만들고 `/content/dam`에 `jcr:all` 권한을 할당하십시오. 시스템 사용자 `workfront-tools`이(가) 자동으로 만들어지고 필요한 권한이 자동으로 관리됩니다. 향상된 커넥터를 사용하는 [!DNL Workfront]의 모든 사용자가 이 그룹의 일부로 자동으로 추가됩니다.

[!DNL Workfront for Experience Manager enhanced connector]을(를) 이전 버전에서 최신 버전으로 업데이트하려면 [여기](update-workfront-enhanced-connector.md)를 클릭하십시오.

## [!DNL Experience Manager]을(를) [!DNL Cloud Service](으)로 [!DNL Workfront] 간의 연결을 구성하십시오. {#configure-connection}

[!DNL Workfront]과(와)의 연결을 만들려면 다음 단계를 수행하십시오.

1. [!DNL Experience Manager]에서 **[!UICONTROL 도구]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Workfront 도구 구성]**&#x200B;을 선택합니다.

1. 왼쪽 패널에서 `workfront-tools`을(를) 선택하고 페이지의 오른쪽 상단 영역에서 **[!UICONTROL 만들기]** 옵션을 선택합니다.

1. **[!UICONTROL Workfront 연결]** 대화 상자에서 [!DNL Workfront] 배포에 대한 필요한 세부 정보를 입력하고 **[!UICONTROL Workfront에 연결]** 옵션을 선택합니다. 연결되면 [!DNL Workfront] 환경에서 [!DNL Workfront] 문서 사용자 지정 통합이 자동으로 만들어집니다.

   ![[!DNL Experience Manager] 및 [!DNL Workfront]](/help/assets/assets/wf-connection-config.png) 연결

1. **[!UICONTROL 고급]** 탭으로 이동하여 **[!UICONTROL 서버 AEM as a Cloud Service임]** 옵션을 선택합니다.
