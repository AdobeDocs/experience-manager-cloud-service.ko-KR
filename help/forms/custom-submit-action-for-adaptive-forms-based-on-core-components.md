---
title: 핵심 구성 요소를 기반으로 적응형 양식에 대한 사용자 지정 제출 액션을 만드는 방법
description: 적응형 Forms에 대한 사용자 지정 제출 액션을 만들어 사용자 지정된 제출 액션을 사용하여 제출하기 전에 데이터를 처리하는 방법에 대해 알아보십시오.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Intermediate
source-git-commit: b703d4c0b0bb25ecc57e5335b672069f7ad2199d
workflow-type: tm+mt
source-wordcount: '1083'
ht-degree: 4%

---


# 적응형 Forms(핵심 구성 요소)에 대한 사용자 지정 제출 액션 만들기

제출 액션을 사용하면 양식에서 캡처한 데이터에 대한 대상을 선택하고 양식 제출 시 실행할 추가 기능을 정의할 수 있습니다. AEM form은 전자 메일을 보내거나 SharePoint 또는 OneDrive에 데이터를 저장하는 것과 같은 여러 [OOTB(기본 제공 작업)](/help/forms/configure-submit-actions-core-components.md)을(를) 지원합니다.

사용자 지정 제출 액션을 만들어 [기본 제공 옵션](/help/forms/configure-submit-actions-core-components.md#select-and-configure-a-submit-action-for-an-adaptive-form-select-and-configure-submit-action)에 포함되지 않은 기능을 추가할 수도 있습니다. 예를 들어 양식 데이터를 타사 애플리케이션과 통합하거나 사용자 입력을 기반으로 개인화된 SMS 알림을 트리거합니다.

<!-- ![Custom Submit Image](/help/forms/assets/custom-submit-action-hero-image.png)
-->

## 전제 조건

적응형 Forms에 대한 첫 번째 사용자 지정 제출 액션을 만들기 전에 다음 사항이 있는지 확인하십시오.

* **IDE(일반 텍스트 편집기)**: 모든 일반 텍스트 편집기가 작동할 수 있지만, Microsoft Visual Studio Code와 같은 IDE(통합 개발 환경)에서는 쉽게 편집할 수 있는 고급 기능을 제공합니다.

* **Git**: 코드 변경 내용을 관리하려면 이 버전 제어 시스템이 필요합니다. 설치되지 않은 경우 https://git-scm.com에서 다운로드하십시오.

## 양식에 대한 첫 번째 사용자 정의 제출 액션 만들기

아래 다이어그램은 적응형 양식에 대한 사용자 지정 제출 액션을 만드는 단계를 보여 줍니다.

![사용자 지정 제출 액션 워크플로우](/help/forms/assets/custom-submit-action-workflow.png){width=50%, height-50%}

### AEM as a Cloud Service Git 저장소를 복제합니다.

1. 명령줄을 열고 AEM as a Cloud Service 저장소를 저장할 디렉터리(예: `/cloud-service-repository/`)를 선택합니다.

1. 아래 명령을 실행하여 저장소를 복제합니다.

   ```
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<app-id>/
   ```
   **이 정보를 찾을 수 있는 위치**

   이러한 세부 정보를 찾는 방법에 대한 단계별 지침은 Adobe Experience League 문서 &quot;[Git 액세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git)&quot;를 참조하십시오.

   **프로젝트가 준비되었습니다!**

   명령이 성공적으로 완료되면 로컬 디렉터리에 새 폴더가 생성됩니다. 이 폴더의 이름은 애플리케이션 이름을 따라 지정합니다(예: app-id). 이 폴더에는 AEM as a Cloud Service Git 저장소에서 다운로드한 모든 파일과 코드가 포함되어 있습니다. `archetype.properties` 파일에서 AEM 프로젝트에 대한 `<appid>`을(를) 찾을 수 있습니다.

   ![Archetype 속성](/help/forms/assets/custom-submit-action-archetype-app-id.png)

   이 안내서에서는 이 폴더를 `[AEMaaCS project directory]`(으)로 지칭합니다.

## 새 제출 액션 추가

1. 편집기에서 저장소 폴더를 엽니다.

   ![복제된 저장소](/help/forms/assets/custom-submit-action-clone-repo.png)

1. `[AEMaaCS project directory]`에서 다음 디렉터리로 이동합니다.

   ```
   /ui.apps/src/main/content/jcr_root/apps/<app-id>/
   ```
   **중요**: `<app-id>`을(를) 실제 응용 프로그램 ID로 바꾸십시오.

1. 사용자 지정 제출 액션에 대한 새 폴더를 만들고 선택한 이름을 지정합니다. 예를 들어 폴더 이름을 `customsubmitaction`(으)로 지정합니다.

   ![사용자 지정 제출 액션 폴더 만들기](/help/forms/assets/custom-submit-action-create-folder.png)

1. 추가된 사용자 정의 제출 액션 디렉토리로 이동합니다.

   `[AEMaaCS project directory]` 내에서 다음 경로로 이동합니다.

   `/ui.apps/src/main/content/jcr_root/apps/<app-id>/customsubmitaction/`

   `Important`: 바꾸기 <app-id> (실제 애플리케이션 ID 포함)

1. 새 구성 파일을 만듭니다.
`customsubmitaction` 폴더 내에서 이름이 `.content.xml`인 새 파일을 만듭니다.

   ![구성 파일 만들기](/help/forms/assets/custom-submit-action-create-config-folder.png)

1. 이 파일을 열고 다음 내용을 붙여 넣어 `[customsubmitaction]`을(를) 제출 액션 이름으로 바꿉니다.

   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
   jcr:description="[customsubmitaction]"
   jcr:primaryType="sling:Folder"
   
   guideComponentType="fd/af/components/guidesubmittype"
   guideDataModel="basic,xfa,xsd"
   submitService="[customsubmitaction]"/>
   ```

   예를 들어 `[customsubmitaction]`을(를) 사용자 지정된 제출 작업 이름으로 `Custom Submit Action`(으)로 바꿉니다.

   ![사용자 지정 제출 액션 구성 파일 만들기](/help/forms/assets/custom-submit-action-config-file.png)

   >[!NOTE]
   >
   > 양식을 작성하는 동안 `Submit action` 드롭다운 목록에 동일한 이름이 표시되므로 [customsubmitaction]의 이름을 기억하십시오.


**새 폴더를`filter.xml`**&#x200B;에 포함

1. [AEMaaCS 프로젝트 디렉터리]에서 `/ui.apps/src/main/content/META-INF/vault/filter.xml` 파일로 이동합니다.

1. 파일을 열고 끝에 다음 줄을 추가합니다.

   ```
   <filter root="/apps/<app-id>/[customsubmitaction-folder]"/>
   ```
   예를 들어 다음 코드 행을 추가하여 `filter.xml` 파일에 `customsubmitaction` 폴더를 추가합니다.

   ```
   <filter root="/apps/wknd/customsubmitaction"/>
   ```

   ![filter.xml에 만든 폴더 추가](/help/forms/assets/custom-submit-action-filter-xml.png)

1. 변경 사항을 저장합니다.

### 추가된 제출 액션에 대한 서비스를 구현합니다.

1. `[AEMaaCS project directory]`에서 다음 디렉터리로 이동합니다.
   `/core/src/main/java/com/<app-id>/core/service/`
   `Important`: 바꾸기 <app-id> (실제 애플리케이션 ID 포함)
1. 새 Java 파일을 만들어 추가된 제출 작업에 대한 서비스를 구현합니다. 예를 들어 새 Java 파일을 `CustomSubmitService.java`(으)로 추가합니다.

   ![사용자 지정 제출 액션 폴더](/help/forms/assets/custom-submit-action-custom-submit-folder.png)

1. 이 파일을 열고 사용자 지정 제출 액션 구현에 대한 코드를 추가합니다.

   예를 들어 아래 Java 코드는 제출된 데이터를 기록하여 양식 제출을 처리하고 상태 `OK`을(를) 반환하는 OSGi 서비스입니다. `CustomSubmitService.java` 파일에 다음 코드를 추가합니다.

   ```
   package com.wknd.core.service;
   
   import com.adobe.aemds.guide.model.FormSubmitInfo;
   import com.adobe.aemds.guide.service.FormSubmitActionService;
   import java.util.HashMap;
   import java.util.Map;
   import org.osgi.service.component.annotations.Component;
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   
       @Component(
       service = FormSubmitActionService.class,
       immediate = true
           )
       public class CustomSubmitService implements FormSubmitActionService {
   
       private static final String serviceName = "Custom Submit Action";
   
       private static Logger log = LoggerFactory.getLogger(CustomSubmitService.class);
   
       @Override
       public String getServiceName() {
       return serviceName;
       }
   
       @Override
       public Map<String, Object> submit(FormSubmitInfo formSubmitInfo) {
       String data = formSubmitInfo.getData();
       log.info("Using custom submit action service, [data] --> " + data);
       Map<String, Object> result = new HashMap<>();
       result.put("status", "OK");
       return result;
        }
       }
   ```

   ![사용자 지정 제출 액션 서비스](/help/forms/assets/custom-submit-action-service.png)

1. 변경 사항을 저장합니다.

### 코드 배포.

**로컬 개발 환경에 대한 코드 배포**

* 로컬 개발 환경에 AEM as a Cloud Service `[AEMaaCS project directory]`을(를) 배포하여 로컬 컴퓨터에서 새 제출 액션을 시도하십시오. 로컬 개발 환경에 배포하려면 다음을 수행하십시오.

   1. 로컬 개발 환경이 실행 중인지 확인합니다. 아직 로컬 개발 환경을 설정하지 않았다면 [AEM Forms의 로컬 개발 환경 설정](/help/forms/setup-local-development-environment.md)에 대한 안내서를 참조하십시오.

   1. 터미널 창이나 명령 프롬프트를 엽니다.

   1. `[AEMaaCS project directory]`(으)로 이동합니다.

   1. 다음 명령을 실행합니다.

      ```
      mvn -PautoInstallPackage clean install
      ```
      ![로컬 배포](/help/forms/assets/custom-submit-action-local-deployment.png)

**Cloud Service 환경에 대한 코드를 배포합니다**

* Cloud Service 환경에 AEM as a Cloud Service `[AEMaaCS project directory]`을(를) 배포합니다. Cloud Service 환경에 배포하려면 다음을 수행하십시오.

   1. 변경 내용 커밋:

      새로운 사용자 정의 제출 액션 구성을 추가한 후 명확한 Git 메시지로 변경 사항을 커밋합니다. (예: &quot;새 사용자 지정 제출 액션을 추가했습니다.)

   1. 업데이트된 코드를 배포합니다.

      [기존 전체 스택 파이프라인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=ko-KR#setup-pipeline)을 통해 코드 배포를 트리거합니다. 새로운 사용자 지정 제출 액션 지원을 통해 업데이트된 코드를 자동으로 빌드하고 배포합니다.

      아직 파이프라인을 설정하지 않았다면 [AEM Formsas a Cloud Service 에 대한 파이프라인 설정 방법](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=ko-KR#setup-pipeline)에 대한 안내서를 참조하십시오.

      ![클라우드 배포](/help/forms/assets/custom-submit-action-cloud-deployment.png)

      **설치를 확인하는 방법**

      프로젝트를 성공적으로 빌드하면 양식을 작성하는 동안 사용자 지정 제출 작업이 `Submit action` 드롭다운 목록에 나타납니다.

      ![사용자 지정 제출 액션 드롭다운 목록](/help/forms/assets/custom-submit-action-drop-down-list.png)

  이제 양식을 작성할 때 추가된 사용자 정의 제출 액션을 사용할 준비가 되었습니다.

### 제출 액션을 새로 추가한 적응형 양식 미리 보기

1. AEM Forms as a Cloud Service 인스턴스에 로그인합니다.
1. **Forms** > **Forms 및 문서**&#x200B;로 이동합니다.

   ![Forms 및 문서](/help/forms/assets/custom-submit-action-fnd.png)

1. 적응형 양식을 선택하고 **편집**&#x200B;을 클릭합니다. 양식이 편집 모드로 열립니다.

   ![양식 편집](/help/forms/assets/custom-submit-action-edit-af.png)

1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. **[!UICONTROL 제출]** 탭을 클릭합니다.
1. **[!UICONTROL 제출 액션]** 드롭다운 목록에서 제출 액션을 선택합니다. 예를 들어 제출 액션을 `Custom Submit Action`(으)로 선택합니다.

   ![사용자 정의 제출 양식](/help/forms/assets/custom-submit-action-select-submit-action.png)

1. 양식을 작성하여 제출하십시오.

   ![양식 제출](/help/forms/assets/custom-submit-action-submit-form.png)

   ![감사 메시지](/help/forms/assets/custom-submit-action-thankyou-msg.png)

   양식이 성공적으로 제출되면 **Adobe Experience Manager 웹 콘솔 구성**&#x200B;을 확인하여 로컬 개발 환경에서 사용자 지정 제출 액션의 동작을 확인할 수 있습니다.
1. `http://<host>:<port>/system/console/configMgr`로 이동합니다.

1. `http://<host>:<port>/system/console/slinglog`의 **Adobe Experience Manager 웹 콘솔 로그 지원**(으)로 이동합니다.

   ![ConfigMgr](/help/forms/assets/custom-submit-action-sling-log.png)

1. `logs/error.log` 옵션을 클릭합니다.
   ![error.log 파일 열기](/help/forms/assets/custom-submit-action-error-log.png)

1. `error.log` 파일을 열어 데이터가 추가되었는지 확인합니다.

   ![error.log 파일](/help/forms/assets/custom-submit-action-form-data-display.png)

   >[!NOTE]
   >
   > AEM as a Cloud Service 환경에서 오류 로그를 보려면 Splunk를 사용할 수 있습니다.

<!--
## Best practices

 * It is recommended to use the OSGi service approach for creating a custom submit action, as it is faster than the AEM servlet approach. 

## Next steps
-->

## 관련 문서

{{af-submit-action}}

<!-- The [Adaptive Forms Core Components](https://github.com/adobe/aem-core-forms-components) repository includes a sample folder, `customsubmission/logsubmit`, to simplify the process of adding new custom submit actions. It also provides the Java service implementation for the `logsubmit` custom submit action, named `CustomAFSubmitService`.java. These resources are available on GitHub. -->