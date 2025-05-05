---
title: ' [!DNL Workfront for Experience Manager enhanced connector]업데이트'
description: ' [!DNL Workfront for Experience Manager enhanced connector]업데이트'
exl-id: 09276b4d-a7c8-4927-8c0a-40eda48e55a7
feature: Workfront Integrations and Apps
role: Admin
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 7%

---

# [!DNL Workfront for Experience Manager enhanced connector] 업데이트 {#update-enhanced-connector-for-workfront}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime 및 Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Edge Delivery Services과 AEM Assets 통합</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>UI 확장성</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Dynamic Media Prime 및 Ultimate 사용</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>모범 사례 검색</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>메타데이터 모범 사례</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>OpenAPI 기능이 포함된 Dynamic Media</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>AEM Assets 개발자 설명서</b></a>
        </td>
    </tr>
</table>

[!UICONTROL Experience Manager Assets as a Cloud Service]을(를) 사용하면 [!DNL Workfront for Experience Manager enhanced connector]을(를) 이전 버전에서 최신 버전으로 업데이트할 수 있습니다.

>[!TIP]
>
>AEM 6.5에 대한 [!DNL Workfront for Experience Manager enhanced connector] 업데이트 설명서를 검색하고 있습니까? [여기](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-connector-install.html?lang=ko##update-enhanced-connector-for-workfront)를 클릭하세요.


[!DNL Workfront for Experience Manager enhanced connector]을(를) 최신 버전으로 업데이트하려면:

1. [Adobe 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/workfront-tools.ui.apps.zip)에서 향상된 커넥터의 최신 버전을 다운로드하십시오.

1. Cloud Manager에서 [액세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=ko)하고 AEM as a Cloud Service 저장소를 복제합니다.

1. 원하는 IDE를 사용하여 복제된 Experience Manager as a Cloud Service 저장소를 엽니다.

1. 1단계에서 다운로드한 향상된 커넥터 zip 파일을 다음 경로에 배치합니다.

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >`resources` 폴더가 없으면 폴더를 만드십시오.

1. 상위 `pom.xml`에서 향상된 커넥터 버전을 업데이트하십시오.

   ```XML
      <dependency>
         <groupId>digital.hoodoo</groupId>
         <artifactId>workfront-tools.ui.apps</artifactId>
         <type>zip</type>
         <version> updated enhanced connector version number</version>
         <scope>system</scope>
         <systemPath>${project.basedir}/ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
      </dependency>
   ```

1. `all module pom.xml`에서 종속성을 업데이트합니다.

   ```XML
      <dependency>
         <groupId>digital.hoodoo</groupId>
         <artifactId>workfront-tools.ui.apps</artifactId>
         <type>zip</type>
         <scope>system</scope>
         <systemPath>${project.basedir}/../ui.apps/src/main/resources/workfront-tools.ui.apps.zip</systemPath>
      </dependency>
   ```

   >[!NOTE]
   >
   >5단계와 6단계의 종속성에 `<scope>` 및 `<systemPath>`을(를) 추가해야 합니다.

1. `pom.xml` 임베드를 업데이트합니다. 모든 하위 프로젝트의 `pom.xml`에 있는 `embeddeds` 섹션에 [!DNL Workfront for Experience Manager enhanced connector] 패키지를 추가합니다. 모든 모듈 `pom.xml`에 업데이트를 통합합니다.

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

1. [Hoodoo 배포 지점의 종속성을 제거합니다](remove-external-dependencies.md)(있는 경우).

1. 변경 사항을 저장소에 푸시합니다.

1. 파이프라인을 실행하여 [변경 내용을 Cloud Manager에 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html?lang=ko)합니다.
