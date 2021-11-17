---
title: ' 설치  [!DNL Workfront for Experience Manager enhanced connector]'
description: ' 설치  [!DNL Workfront for Experience Manager enhanced connector]'
role: Admin
feature: Integrations
source-git-commit: d75d9ac16f64b6770fcf35d58474c47c52b1585b
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---


#  설치 [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

에 관리자 액세스 권한이 있는 사용자 [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] 향상된 커넥터를 설치합니다. 설치하기 전에 플랫폼 지원 및 기타 를 검토하십시오 [커넥터를 위한 사전 요구 사항](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>Adobe을 사용하려면 [!DNL Adobe Workfront for Experience Manager enhanced connector] 인증된 파트너를 통해 [!DNL Adobe Professional Services]. 인증된 파트너 또는 [!DNL Adobe Professional Services]Adobe에서 지원하지 않습니다.
>
>Adobe은 [!DNL Adobe Workfront] 및 [!DNL Adobe Experience Manager] 이 커넥터를 이중화합니다. 이러한 경우 고객은 이 커넥터를 사용하는 상태에서 전환해야 할 수 있습니다.

커넥터를 설치하기 전에 다음 사전 설치 단계를 수행하십시오.

1. [방화벽 구성](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&amp;topicId=Content%2FAdministration_and_Setup%2FGet_started-WF_administration%2Fconfigure-your-firewall.html). 의 IP 클러스터를 확인하려면 [!DNL Workfront], 다음 위치로 이동합니다. [!UICONTROL 설정] > [!UICONTROL 시스템] > [!UICONTROL 고객 정보].

1. 디스패처에서 이름이 인 HTTP 헤더를 허용합니다. `authorization`, `username`, 및 `apikey`. 허용 `GET`, `POST`, 및 `PUT` 요청 `/bin/workfront-tools`.

1. 다음 경로가 [!DNL Experience Manager] 저장소:

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`

1. 이 설치에서 Maven 프로젝트를 설정하는 데 필요한 지식이 필요합니다. [!DNL Experience Manager] 로서의 [!DNL Cloud Service]. Maven 프로젝트에 타사 패키지를 포함하는 방법을 이해하려면 다음 리소스를 사용하십시오.

   * [Maven 프로젝트에 타사 패키지 포함](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#including-third-party).
   * [배포 [!DNL Cloud Manager]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html).

추가 기능을 설치하려면 다음을 수행하십시오 [!DNL Experience Manager] 로서의 [!DNL Cloud Service]다음 단계를 수행합니다.

1. 추가 `pom.xml` 종속성:

   1. 상위에 종속성 추가 `pom.xml`.

      ```XML
      <dependency>
         <groupId>digital.hoodoo</groupId>
         <artifactId>workfront-tools.ui.apps</artifactId>
         <type>zip</type>
         <version>1.7.4</version>
      </dependency>
      ```

   1. 모든 모듈에 종속성 추가 [!DNL pom.xml].

      ```XML
         <dependency>
            <groupId>digital.hoodoo</groupId>
            <artifactId>workfront-tools.ui.apps</artifactId>
            <type>zip</type>
         </dependency>
      ```

1. 추가 `pom.xml` 인증.

   1. adobe-public profile 내의 pom.xml에 아래 저장소 구성을 포함하므로, 커넥터 종속성(위의)은 빌드 시(로컬에서 그리고 Cloud Manager에 의해 모두) 해결될 수 있습니다. 라이센스 구입 시 저장소 액세스를 위한 자격 증명이 제공됩니다. 자격 증명을 서버 섹션의 settings.xml 파일에 추가해야 합니다.

      ```XML
      <repository>
         <id>hoodoo-maven</id>
         <name>Hoodoo Repository</name>
         <url>https://gitlab.com/api/v4/projects/12715200/packages/maven</url>
      </repository>
      ```

   1. 이름이 인 파일 만들기 `./cloudmanager/maven/settings.xml` 를 클릭합니다. 암호로 보호된 Maven 저장소를 지원하려면 다음을 참조하십시오 [프로젝트를 설정하는 방법](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md). 또한, `settings.xml` 참조할 파일입니다. 마지막으로 로컬 업데이트 `settings.xml` 를 컴파일합니다.

      ```XML
         <server>
            <id>hoodoo-maven</id>
            <configuration>
               <httpHeaders>
                     <property>
                        <name>Deploy-Token</name>
                        <value>xxxxxxxxxxxxxxxx</value>
                     </property>
               </httpHeaders>
            </configuration>
         </server>
      ```

1. 추가 `pom.xml` 침대. 추가 [!DNL Workfront for Experience Manager enhanced connector] 패키지 `embeddeds` 섹션 `pom.xml` 모든 하위 프로젝트 모든 모듈에 포함 필요 `pom.xml`.

   ```XML
   <!-- Workfront Tools -->
   <embedded>
      <groupId>digital.hoodoo</groupId>
      <artifactId>workfront-tools.ui.apps</artifactId>
      <type>zip</type>
      <target>/apps/<path-to-project-install-folder>/install</target>
   </embedded>
   ```

1. 시스템 사용자 구성을 만들려면 `wf-workfront-users` in [!DNL Experience Manager] 사용자 그룹 및 권한 할당 `jcr:all` to `/content/dam`. 시스템 사용자 `workfront-tools` 는 자동으로 만들어지며 필요한 권한은 자동으로 관리됩니다. 의 모든 사용자 [!DNL Workfront] 향상된 커넥터를 사용하는 사용자는 자동으로 이 그룹의 일부로 추가됩니다.

## 다음 사이의 연결 구성 [!DNL Experience Manager] 로서의 [!DNL Cloud Service] 및 [!DNL Workfront] {#configure-connection}

연결을 만들려면 [!DNL Workfront]다음 단계를 수행합니다.

1. in [!DNL Experience Manager], 선택 **[!UICONTROL 도구]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Workfront 도구 구성]**.

1. 선택 `workfront-tools` 왼쪽 패널에서 을(를) 선택하고 을(를) 선택합니다. **[!UICONTROL 만들기]** 옵션 을 클릭합니다.

1. 에서 **[!UICONTROL Workfront 연결]** 대화 상자에서 필요한 세부 정보를 제공합니다 [!DNL Workfront] 배포 후 **[!UICONTROL Workfront에 연결]** 선택 사항입니다. 연결되면 [!DNL Workfront] 문서 사용자 지정 통합은 [!DNL Workfront] 환경.

   ![Connect [!DNL Experience Manager] 및 [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. 로 이동합니다 **[!UICONTROL 고급]** 탭을 선택하고 옵션을 선택합니다 **[!UICONTROL 서버 AEM as a Cloud Service]**.
