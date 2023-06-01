---
title: AEM Sites 페이지에 적응형 양식 만들기 또는 추가
description: 적응형 양식을 간편하게 만들거나 AEM Sites 페이지에 원활하게 추가하는 방법에 대해 알아보십시오. 다이내믹하고 사용자 정의 가능한 양식을 웹 사이트에 통합하고 디지털 경험을 최적화하여 최대의 영향을 주기 위한 단계별 기술과 모범 사례에 대해 알아보십시오.
feature: Adaptive Forms
hide: true
hidefromtoc: true
source-git-commit: 7dc36220c1f12177037aaa79d864c1ec2209a301
workflow-type: tm+mt
source-wordcount: '1230'
ht-degree: 0%

---


# AEM Sites 페이지에 적응형 양식 만들기 또는 추가 {#create-or-add-an-adaptive-form-to-aem-sites-page}

AEM Forms을 사용하면 적응형 양식을 웹 페이지에 원활하게 통합할 수 있습니다. 이렇게 하면 방문자가 현재 페이지에서 나가지 않고 편리하게 양식을 작성하여 제출할 수 있습니다. 이렇게 함으로써, 그들은 형태와 능동적으로 상호 작용하면서 웹 사이트의 다른 요소와 쉽게 참여할 수 있습니다.

다음 옵션을 활용하여 이 기능을 최대한 활용할 수 있습니다.

* **사용자 정의 양식 추가:** 요구 사항 및 디자인 환경 설정에 맞게 맞춤화하여 처음부터 새로운 양식을 제작하십시오.

* **경험 조각 향상:** 양식을 AEM Experience Fragments에 추가하여 도달 범위를 확장함으로써 여러 페이지 또는 사이트에서 원활하게 재사용할 수 있습니다.

* **승인된 템플릿 활용:** 사전 승인된 템플릿을 활용하여 조직의 브랜딩 지침 및 디자인 표준에 맞는 양식을 신속하게 만들 수 있습니다.

* **기존 양식 추가:** 이미 만든 양식을 웹 사이트에 쉽게 통합하여 방문자가 직접 상호 작용할 수 있도록 합니다.

* **여러 양식 추가:**  페이지에 여러 양식을 추가하여 사용자의 환경 설정 및 요구 사항에 따라 다양한 선택 사항을 제공할 수 있습니다. 처음부터 새로 만든 양식과 기존 양식을 조합할 수 있습니다.

AEM Sites 편집기를 사용하여 여러 양식을 신속하게 만들고 AEM Sites 페이지에 추가할 수 있습니다. AEM Sites 편집기를 사용하면 콘텐츠 작성자가 동적 동작, 유효성 검사, 데이터 통합, 기록 문서 생성 및 비즈니스 프로세스 자동화를 비롯한 적응형 양식 구성 요소를 사용하여 Sites 페이지 내에서 매끄러운 데이터 캡처 경험을 만들 수 있습니다. 또한 버전 관리, 타겟팅, 번역 및 다중 사이트 관리자와 같은 AEM Sites 페이지의 다양한 기능을 사용할 수 있습니다.

## 목표

* AEM Sites 편집기 및 경험 조각을 사용하여 적응형 양식을 만드는 방법에 대해 알아봅니다
* AEM Sites 페이지에 추가된 적응형 양식의 레이아웃 및 테마를 설정하는 방법
* AEM Sites 편집기 및 경험 조각을 사용하여 적응형 양식 만들기


## 고려 사항 {#consideration}

AEM Forms은 적응형 양식 컨테이너 및 적응형 Forms - 임베드 구성 요소를 제공합니다. 적응형 양식 컨테이너를 사용하여 경험 조각 또는 AEM Sites 페이지에서 새 양식을 만들고 추가할 수 있으며, 적응형 Forms - 임베드 구성 요소를 사용하여 기존 적응형 양식을 추가하거나 적응형 Forms 편집기를 사용하여 새 양식을 만들 수 있습니다.

적응형 양식 컨테이너를 사용하여 양식을 만들거나 추가하면 양식은 AEM Sites 번역 플로우를 통해 번역 및 현지화 과정을 거칩니다. 각 언어에 대해 사이트 페이지 및 해당 양식의 개별 사본(언어 사본)이 생성되며 콘텐츠 작성자가 상위 페이지에서 양식의 규칙을 수정할 때 양식의 모든 언어 사본에서 동일한 변경 사항을 적용해야 합니다. 또한 적응형 양식 컨테이너를 사용하여 버전 관리, 타기팅, 번역 및 다중 사이트 관리자와 같은 AEM Sites 페이지의 다양한 기능을 사용할 수 있습니다.

적응형 양식 임베드 구성 요소를 사용하여 양식을 만들거나 추가하면 양식은 AEM Forms 번역 플로우를 사용하여 번역 및 현지화 과정을 거칩니다. 이 경우 Sites 페이지의 모든 언어 사본에서 단일 양식이 유지 관리되고 참조됩니다. 적응형 양식 포함 구성 요소는 버전 관리, 타기팅, 번역 및 다중 사이트 관리자와 같은 AEM Sites 페이지의 다양한 기능에 대한 액세스를 제공하지 않습니다.


## 시작하기 전 {#before-you-start}

+++  환경에 맞는 적응형 Forms 핵심 구성 요소 활성화

다음을 확인합니다. [적응형 Forms 핵심 구성 요소는 AEM Forms as a Cloud Service 환경에서 활성화됩니다](enable-adaptive-forms-core-components.md).

+++

+++ ** 사용[!UICONTROL 적응형 Forms 컨테이너]

활성화하려면 [!UICONTROL 적응형 Forms 컨테이너] 템플릿 정책의 구성 요소에서 다음 단계를 수행합니다.

1. 편집할 AEM Sites 페이지를 엽니다. 편집할 페이지를 열려면 페이지를 선택한 다음 [편집]을 클릭합니다.
1. 사이트 페이지의 템플릿을 엽니다. 템플릿을 열려면 [!UICONTROL 페이지 정보] ![페이지 정보](/help/forms/assets/Smock_Properties_18_N.svg) > [!UICONTROL 템플릿 편집]. 템플릿 편집기에서 해당 템플릿을 엽니다.
1. 구조 보기에서 **[!UICONTROL 정책]** ![정책](/help/forms/assets/Smock_FeedManagement_18_N.svg) 아이콘 을 클릭하여 제품에서 사용할 수 있습니다. 다음에서 **[!UICONTROL 허용된 구성 요소]** 목록 및 선택 **[!UICONTROL 적응형 Forms 컨테이너]**  확인란 **[AEM Archetype 프로젝트 이름] - 적응형 양식**.
1. 클릭 **[!UICONTROL 완료]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++


+++  AEM Sites 페이지에 적응형 Forms 클라이언트 라이브러리 추가

적응형 Forms 컨테이너 구성 요소의 전체 기능을 활성화하려면 배포 파이프라인을 사용하여 Customheaderlibs 및 Customfooterlibs 클라이언트 라이브러리를 AEM Sites 페이지에 추가하십시오. 라이브러리를 추가하려면 다음을 수행하십시오.

1. 액세스 및 복제 [AEM Cloud Service Git 저장소](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html).
1. 계획 텍스트 편집기에서 AEM Cloud Service Git 저장소 폴더를 엽니다. (예: Microsoft Visual Code)
1. 를 엽니다. `ui.apps/src/main/content/jcr_root/apps/[your-project]/components/page/.content.xml` 편집할 파일 및 값 설명 `sling:resourceSuperType`. 예를 들어 값 아래에 를 기록합니다 `core/wcm/components/page/v3/page`.


   ![sling 리소스](/help/forms/assets/slingresource.png)

1. 다음으로 이동 `  ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\` `ui.apps/src/main/content/jcr_root/apps` 이전 단계에서 기록한 값과 동일한 폴더 구조를 만듭니다. 예를 들어 이전 단계의 예와 값이 비슷하면 최종 노드 구조는 입니다. `ui.apps/src/main/content/jcr_root/apps/core/wcm/components/page/v3/page`

   ![오버레이 구조](/help/forms/assets/overlaystructure.png)

1. 만들기 `customheaderlibs.html` 및 `customfooterlibs.html` 이전 단계에서 만든 노드 구조의 파일을 편집하고 파일에 다음 내용을 추가합니다.

   ```
        //Customheaderlibs.html
        <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
        <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
        </sly> 
   
        //customfooterlibs.html
        <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
        <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
        </sly> 
   ```

1. [배포 파이프라인 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) 클라이언트 라이브러리를 AEM as a Cloud Service 환경에 배포합니다.

+++

## 적응형 양식 만들기 {#create-an-adaptive-form-in-sites-editor-or-experience-fragment}

AEM sites 페이지 또는 경험 조각에서 직접 요구 사항 및 디자인 환경 설정에 맞게 맞춤화하여 처음부터 새로운 양식을 만들 수 있습니다. 일회성 양식의 경우 AEM 사이트 페이지로 직접 작성하는 것이 좋지만 경험 조각은 웹 사이트의 여러 페이지에서 재사용해야 하는 양식에 이상적입니다.

* [AEM Sites 페이지에서 양식 만들기](#create-an-adaptive-form-in-sites-editor)
* [경험 조각에서 양식 만들기](#create-an-adaptive-form-in-experience-fragment)

### AEM Sites 페이지에서 양식 만들기 {#create-an-adaptive-form-in-sites-editor}

AEM Sites 편집기에서 적응형 양식 컨테이너 구성 요소를 사용하여 사용자 정의 양식을 만들 수 있습니다. 구성 요소를 사용하여 양식 구성 요소를 드래그 앤 드롭하여 양식을 만들 수 있습니다. 양식 구성 요소는 핵심 구성 요소를 기반으로 합니다. 조직의 요구 사항에 따라 이러한 매개 변수를 쉽게 사용자 지정할 수 있습니다.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

Sites 페이지에서 적응형 양식을 만들려면 다음 작업을 수행하십시오.

1. 편집 모드로 AEM Sites 페이지를 엽니다.
1. 을(를) 드래그 앤 드롭합니다 **[!UICONTROL 적응형 Forms 컨테이너]** 구성 요소 브라우저의 구성 요소를 사이트 페이지로 복사합니다. 페이지에 폼에 대한 공백이 만들어집니다. 레이아웃 모드를 사용하여 컨테이너 공간의 크기를 변경할 수 있습니다.
1. 적응형 양식 핵심 구성 요소를 컨테이너 공간으로 드래그 앤 드롭하여 양식을 만듭니다.
1. 제출 단추를 추가합니다.

그런 다음 제출 작업과 고급 속성을 설정합니다.

### 경험 조각에서 양식 만들기 {#create-an-adaptive-form-in-experience-fragment}

AEM Experience Fragments에 양식을 추가하여 도달 범위를 확장함으로써 여러 페이지 또는 사이트에서 원활하게 재사용할 수 있습니다. 예를 들어 경험 조각 내에 뉴스레터 등록 양식을 포함할 수 있습니다. 이렇게 하면 웹 사이트의 여러 페이지에서 조각을 편리하게 재사용할 수 있으므로 양식을 반복적으로 다시 만들 필요가 없습니다. 경험 조각 내에서 뉴스레터 등록 양식에 대해 수행된 모든 업데이트 또는 수정 사항은 활용된 모든 페이지에 자동으로 전파됩니다. 이를 통해 프로세스를 간소화하고 원활한 사용자 경험을 보장하는 동시에 웹 사이트의 양식 관리를 간소화할 수 있습니다.

경험 조각에 적응형 양식을 만들려면 다음 작업을 수행하십시오.

## 적응형 양식의 레이아웃 변경 {#change-layout-of-an-adaptive-form}

AEM Sites 페이지에서 [레이아웃 모드](/help/sites-cloud/authoring/features/responsive-layout.md) AEM Sites 페이지에 추가된 적응형 양식 컨테이너 구성 요소 크기를 조정합니다.
