---
title: 업데이트 [!DNL Workfront for Experience Manager enhanced connector]
description: 업데이트 [!DNL Workfront for Experience Manager enhanced connector]
source-git-commit: 34f3cf925a3ea58de176521be459a61f4317eec3
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 1%

---

# 업데이트 [!DNL Workfront for Experience Manager enhanced connector] {#update-enhanced-connector-for-workfront}

[!UICONTROL Experience Manager Assets as a Cloud Service] 을 통해 다음을 업데이트할 수 있습니다. [!DNL Workfront for Experience Manager enhanced connector] 이전 버전에서 최신 버전으로 마이그레이션 하는 것이 좋습니다.

>[!TIP]
>
>을 찾고 있습니까? [!DNL Workfront for Experience Manager enhanced connector] AEM 6.5에 대한 설명서 업데이트 클릭 [여기](https://experienceleague.adobe.com/docs/experience-manager-65/assets/integrations/workfront-connector-install.html?lang=en##update-enhanced-connector-for-workfront).


를 업데이트하려면 [!DNL Workfront for Experience Manager enhanced connector] 최신 버전으로 마이그레이션:

1. 향상된 커넥터의 최신 버전을 다운로드하십시오. [Adobe 소프트웨어 배포](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/workfront-tools.ui.apps.zip).

1. [액세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/accessing-repos.html?lang=en) Cloud Manager에서 AEM as a Cloud Service 저장소를 복제하고

1. 선택한 IDE를 사용하여 복제된 Experience Manager as a Cloud Service 저장소를 엽니다.

1. 1단계에서 다운로드한 향상된 커넥터 zip 파일을 다음 경로에 배치합니다.

   ```TXT
      /ui.apps/src/main/resources/<zip file>
   ```

   >[!NOTE]
   >
   >만약 `resources` 폴더가 없으므로 폴더를 만듭니다.

1. 상위 버전의 향상된 커넥터 버전을 업데이트합니다 `pom.xml`.

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

1. 의 종속성을 업데이트합니다. `all module pom.xml`.

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
   >다음을 추가했는지 확인합니다. `<scope>` 및 `<systemPath>` 를 단계 5 및 6의 종속성에 추가합니다.

1. 업데이트 `pom.xml` 침대. 추가 [!DNL Workfront for Experience Manager enhanced connector] 패키지 `embeddeds` 섹션 `pom.xml` 모든 하위 프로젝트 모든 모듈에 업데이트 통합 `pom.xml`.

   ```XML
   <!-- Workfront Tools -->
   <embedded>
      <groupId>digital.hoodoo</groupId>
      <artifactId>workfront-tools.ui.apps</artifactId>
      <type>zip</type>
      <target>/apps/<path-to-project-install-folder>/install</target>
   </embedded>
   ```

   포함된 섹션의 대상이 `/apps/<path-to-project-install-folder>/install`. 이 JCR 경로 `/apps/<path-to-project-install-folder>` 는 `all/src/main/content/META-INF/vault/filter.xml` 파일. 저장소의 필터 규칙은 일반적으로 프로그램 이름에서 파생됩니다. 기존 규칙의 대상으로 폴더 이름을 사용합니다.

1. [Hoodo 배포 지점에 대한 종속성을 제거합니다.](remove-external-dependencies.md), 있을 경우.

1. 변경 사항을 저장소에 푸시합니다.

1. 다음 대상 파이프라인 실행 [cloud Manager에 변경 사항 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/deploy-code.html).
