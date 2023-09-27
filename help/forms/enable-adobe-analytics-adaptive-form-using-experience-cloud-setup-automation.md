---
title: 적응형 양식용 Adobe Analytics 활성화
description: Experience Cloud 설정 자동화를 통해 Adobe Analytics를 적응형 양식에 연결하여 방문자 상호 작용과 참여에 대한 인사이트를 추적할 수 있습니다.
source-git-commit: 4fc6d29cd008b04ad97ceb17201c1f8d0e72439e
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 60%

---


# Experience Cloud 설정 자동화를 사용하여 적응형 양식용 Adobe Analytics 활성화 {#integrate-adobe-analytics-to-aem-forms-with-experience-cloud-setup-automation}

<span class="preview"> 이는 프리릴리스 기능이고 [프리릴리스 채널](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features)을 통해 액세스할 수 있습니다. </span>

Experience Cloud 설정 자동화를 통해 Adobe Analytics를 Adaptive Forms에 연결하여 양식과의 사용자 상호 작용을 추적 및 분석하고 방문자 상호 작용과 참여에 대한 인사이트를 제공할 수 있습니다. 또한 Experience Cloud 설정 자동화를 통해 완료 시간과 드롭오프 시점과 같은 지표 평가를 포함하는 양식 성능을 모니터링할 수 있습니다. 이 분석을 사용하면 로그인 상태에 따라 사용자 행동(예: 익명 사용자)을 구분하여 일반적인 트렌드와 패턴을 식별하는 동시에 양식을 최적화하여 사용자 경험을 향상시킬 수 있습니다.


## Adobe Analytics와 적응형 양식 통합의 이점 {#advantages-of-integrating-adobe-analytics-with-aem-forms}

* **최종 사용자 행동에 대한 인사이트**: Adobe Analytics를 통해 최종 사용자 행동에 대한 인사이트를 확보하고 사용자 액션, 드롭오프와 완료율을 표시하여 개인이 양식을 이용하는 방법을 보다 깊이 이해할 수 있습니다.
* **비기술적인 비즈니스 사용자가 인사이트를 확보하도록 지원**: 사용하기 쉬운 인터페이스를 통해 기술 전문가가 아닌 사용자도 Adobe Analytics를 사용하여 양식 사용 데이터에 액세스하여 해석할 수 있도록 지원하고 데이터 기반의 의사 결정을 내려 등록 경험을 개선할 수 있습니다.
* **사용량에 따라 데이터 캡처 경험 최적화**: 조직은 데이터 캡처의 문제점을 쉽게 식별하여 양식 유용성을 개선하고 제출을 늘리는 타겟팅 기능을 향상시킬 수 있습니다.

## 적응형 양식 사용 지표의 범위 {#scope-of-adaptive-forms-usage-metrics}

Adobe Analytics는 양식 사용에 대한 중요한 인사이트 확보를 위해 설계된 포괄적인 적응형 양식 성능 지표를 제공합니다. 해당 지표는 다음과 같습니다.

* **양식 렌디션, 양식 제출, 유효성 검사 오류와 고유 방문자 수**&#x200B;를 사용하여 양식의 사용량과 효율성을 평가할 수 있습니다.

* **방문자 인사이트**&#x200B;는 방문 및 제출 빈도, 고유 방문자 수를 포함하여 양식 대상자에 대한 포괄적인 보기를 제공합니다.

* **디바이스 유형** 데이터는 사용자가 양식에 액세스하기 위해 사용하는 디바이스에 대해 알려 줍니다.

* **지리적 분류**&#x200B;에 양식 사용자의 지역적 분포가 표시됩니다.

* **트래픽 소스** 및 **방문 빈도가 높은 양식** 지표는 상위 참조 도메인과 가장 많이 방문한 양식으로 구성되어 트래픽 발생 위치와 가장 방문 빈도가 높은 양식을 이해하는 데 유용합니다.

* **상위 양식의 사용자 활동**&#x200B;을 통해 필드 방문, 양식 렌디션, 유효성 검사 오류, 포기한 양식과 양식 제출에 대한 인사이트를 확보하여 사용자 행동을 분석할 수 있습니다.

* **양식 작성에 사용된 시간의 타임라인**&#x200B;은 사용자가 양식을 이용한 시간을 보여 주는 타임라인 기반 보기를 제공합니다.

* **방문자 도움이 필요한 영역** 지표는 도움말 보기, 유효성 검사 오류 인스턴스, 필드 방문 빈도를 포함하여 사용자가 양식을 작성하는 데 도움이 필요한 영역을 강조 표시합니다.

![Analytics 보고서](assets/analytics-report.png){width="100%"}


각 지표에 대한 자세한 내용은 [AEM Forms Analytics 보고서 보기 및 이해](/help/forms/view-understand-aem-forms-analytics-reports.md)를 참조하십시오.

## 사전 요구 사항 {#prerequisites}

<!--
Analytics, Data Collection (Formerly Adobe Launch), and Experience Manager (experience.adobe.com)
-->

Experience Cloud 설정 자동화를 사용하려면 **Adobe Analytics 라이선스**, **데이터 수집(이전 Adobe 실행)** 추적 스크립트를 관리하려면 **Experience Manager Forms 라이선스** 능률적인 데이터 집계 및 통찰력 생성.

다음에 대한 활성 라이센스가 있는 경우 **Adobe Analytics** 및 **Experience Manager Forms**, 와 통합되었습니다. **데이터 수집(이전 Adobe 실행)**, 개발자 콘솔 내에서 가용성을 확인해야 합니다.

Forms as a Cloud Service 환경에서 앞에서 설명한 것을 사용할 수 있는지 확인하려면 다음을 방문하십시오. [개발자 콘솔](https://developer.adobe.com/console/projects)로 이동하여 프로그램 id가 환경 id인 프로젝트에서 URL이 있는 환경을 검색합니다 `https://author-p45913-e175111-cmstg.adobeaemcloud.com/index.html`, 프로그램 id - 환경 id는 `p45913-e175111`. Experience Cloud 설정 자동화, Adobe Analytics 및 Experience Platform Launch API가 제공되고 있는지 확인합니다. 해당 도구가 제공되면 적응형 양식용 Adobe Analytics를 활성화할 수 있습니다.

![사전 양식 분석 통합](assets/analytics-aem.png){width="100%"}

<!-- 
>[!NOTE]
> If you have an active licenses for Experience Cloud Setup Automation, Adobe Analytics, and Experience Platform Launch API, you should verify their availability within your developer console.
-->

<!-- For more information about your available integrations, see [troubleshooting Adaptive Forms with Analytics Integration](https://experienceleague.adobe.com/docs/experience-manager-65/forms/integrate-aem-forms-with-experience-cloud-solutions/view-understand-aem-forms-analytics-reports.html)
-->

## Adobe Analytics 구성 {#configure-adobe-analytics}

적응형 양식용 Adobe Analytics를 활성화하여 구성하려면 아래 단계를 수행합니다.

* [기초 구성 요소 기반의 적응형 양식용 Adobe Analytics를 사용할 수 있도록 설정](#integrate-adobe-analytics-with-aem-forms-for-foundation-component)
* [코어 구성 요소 기반의 적응형 양식용 Adobe Analytics를 사용할 수 있도록 설정](#integrate-adobe-analytics-with-aem-forms-for-core-components)

>[!VIDEO](https://video.tv.adobe.com/v/3424577/recaptcha-google-adaptive-forms/?quality=12&learn=on)


<!--
>[!NOTE]
>
> This is the demo video for **Foundation Component**. In **Core Component** you are required to perform similar steps but the container is not chosen for forms.
-->

### 기초 구성 요소의 적응형 양식으로 Adobe Analytics를 사용할 수 있도록 설정 {#integrate-adobe-analytics-with-aem-forms-for-foundation-component}

1. 클라우드 서비스의 구성 컨테이너 만들기:
   1. **[!UICONTROL 도구 > 일반 > 구성 브라우저]**&#x200B;로 이동합니다.
   1. 구성 컨테이너를 선택하거나 만들고 **[!UICONTROL 클라우드 구성]** 폴더를 활성화합니다
   1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 탭하여 구성을 저장하고 대화 상자를 종료합니다.
1. AEM 인스턴스에서 **[Forms]** >> **[양식 및 문서]**&#x200B;로 이동합니다.
1. **[!UICONTROL 구성 컨테이너]**&#x200B;에서 **[!UICONTROL 양식]** >> **[!UICONTROL 속성]**&#x200B;을 선택한 다음 1단계의 **[!UICONTROL 구성 브라우저]**&#x200B;에서 만들거나 선택한 구성 컨테이너를 선택합니다.
1. 왼쪽 레일에서 작업 패널을 선택하고 **Analytics 설정** 및 **Adobe Analytics 활성화**&#x200B;를 클릭합니다.
1. 보고서 세트에 원하는 이름을 입력하고 **[!UICONTROL 다음]** 및 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
1. 프로젝트를 저장하고 나면 Adobe Analytics가 적응형 양식과 통합될 때까지 잠시 동안 설정이 실행됩니다. **통합 상태**&#x200B;를 확인할 수도 있습니다.

   >[!NOTE]
   >
   >설정하는 데 15분 이상 걸리면 양식 분석 활성화를 재시도합니다.

1. AEM 인스턴스에서 **[!UICONTROL Forms]** >> **[양식 및 문서]**&#x200B;로 이동하여 **[!UICONTROL 양식]**&#x200B;을 선택하면 아래 이미지에 표시된 대로 Adobe Analytics가 양식에 통합됩니다.
1. 이제 적응형 양식 [Adobe Analytics 보고서](#view-adobe-analytics-report)를 볼 수 있습니다.

![통합된 AEM Analytics](assets/analytics-aem-integrated.png){width="100%"}


### 코어 구성 요소의 적응형 양식으로 Adobe Analytics를 사용할 수 있도록 설정 {#integrate-adobe-analytics-with-aem-forms-for-core-components}

1. AEM 인스턴스에서 **[!UICONTROL Forms]** >> **[!UICONTROL 양식 및 문서]**&#x200B;로 이동하고 **[!UICONTROL 양식]**&#x200B;을 선택합니다.
1. 왼쪽 레일의 작업 패널을 선택하고 **Analytics 설정** 및 **Adobe Analytics 활성화**&#x200B;를 클릭합니다.
1. 보고서 세트에 원하는 이름을 입력하고 **[!UICONTROL 다음]** 및 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
1. 프로젝트를 저장하고 나면 Adobe Analytics가 적응형 양식과 통합될 때까지 잠시 동안 설정이 실행됩니다. **통합 상태**&#x200B;를 확인할 수도 있습니다.

   >[!NOTE]
   >
   >설정하는 데 15분 이상 걸리면 양식 분석 활성화를 재시도합니다.

1. AEM 인스턴스에서 **[!UICONTROL Forms]** >> **[!UICONTROL 양식 및 문서]**&#x200B;으로 이동하여 **[!UICONTROL 양식]** 을 선택하면 Adobe Analytics가 양식에 통합됩니다.
1. 이제 적응형 양식 [Adobe Analytics 보고서](#view-adobe-analytics-report)를 볼 수 있습니다.

## 적응형 양식 Adobe Analytics 보고서 보기 {#view-adobe-analytics-report}

1. AEM 인스턴스에서 **[!UICONTROL Forms]** >> **[!UICONTROL 양식 및 문서]**&#x200B;로 이동합니다.
1. 양식을 선택하면 왼쪽에 표시된 대로 Adobe Analytics가 Adobe Analytics에 활성화된 양식에 통합됩니다.

   ![보고서 보기](assets/activ-aa.png){width="100%"}

1. **Adobe Analytics**&#x200B;를 클릭하여 보고서를 보고 성능 데이터를 분석합니다.

수동으로 적응형 양식을 Adobe Analytics와 연결하려면 [통합: AEM Forms와 Adobe Analytics](/help/forms/integrate-aem-forms-with-adobe-analytics.md)를 참조하십시오.

## Sites에서 적응형 Forms에 Analytics 활성화 {#Connect-Analytics-to-Adaptive-Forms-in-Sites}

AEM Sites에서 적응형 양식에 대한 분석을 구성하면 Sites 페이지의 양식에서 사용자 상호 작용 및 양식 제출을 추적할 수 있습니다. Sites Forms에서 분석을 원활하게 통합함으로써 사용자 행동, 전환율 및 양식의 개선 영역에 대한 중요한 통찰력을 얻을 수 있습니다.

### 사전 요구 사항 {#Prerequisites-to-connect-forms-analytics-to-sites}

AEM Sites용 적응형 Forms에서 analytics를 연결하고 활성화하려면 AEM Sites에 활성 Adobe Analytics이 있는지 확인해야 합니다.

### 사이트에서 적응형 Forms을 연결하여 Analytics 활성화 {#Connect-analytics-to-adaptive-forms}

AEM Sites 페이지에서 적응형 양식에 연결하여 Analytics를 활성화하려면 다음을 포함하십시오. `customfooterlibs` AEM Archetype/Git 저장소 및 배포 파이프라인을 사용하여 AEM Sites 페이지에 클라이언트 라이브러리를 연결합니다.

1. 을(를) 엽니다 [AEM Forms Archetype 또는 복제된 Git 저장소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) 텍스트 편집기의 프로젝트. 예: Visual Studio Code.

1. 적응형 양식이 있는 사이트 페이지로 이동합니다(예: 이 데모 프로젝트에서는 ). `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.

1. 값 복사 `sling:resourceSuperType`. 예를 들어 값은 입니다. `core/wcm/components/page/v3/page`.

   ![Sling 리소스](/help/forms/assets/slingresource.png){width="100%"}

1. 위치에 유사한 구조를 만듭니다. `ui.apps/src/main/content/jcr_root/apps` 과 동일 `core/wcm/components/page/v3/page`.

   ![오버레이 구조](/help/forms/assets/overlaystructure.png){width="100%"}

1. 추가 `customfooterlibs.html` 파일.

       &quot;
       // customheaderlibs.html
       &lt;sly data-sly-use.page=&quot;com.adobe.cq.wcm.core.components.models.Page&quot;>
       &lt;sly data-sly-test=&quot;${page.data &amp;&amp; page.dataLayerClientlibIncluded}&quot; data-sly-call=&quot;${clientlib.js @ categories=&amp;#39;core.forms.components.commons.v1.datalayer&amp;#39;, async=true}&quot;>&lt;/sly>
       &lt;/sly>
       
       &quot;
   
   다음 `customfooterlibs.html` 는 JavaScript에 사용됩니다.

1. [파이프라인 실행](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) 를 눌러 변경 사항을 배포합니다.

### Sites에서 Forms에 양식 분석 규칙 활성화 {#bind-forms-analytics-rules-to-forms-in-sites}

1. 다음 방문: **Adobe Experience Platform 데이터 수집**.
1. 클릭 **태그** 왼쪽에 있습니다.
1. 예를 들어 아래 이미지에 표시된 대로 프로그램 ID로 프로젝트에서 URL이 있는 환경을 검색합니다 `https://author-p45921-e175111-cmstg.adobeaemcloud.com/index.html`, 프로그램 id는 `45921`.

   ![데이터 수집에서 양식 검색](/help/forms/assets/aep-data-collection.png){width="100%"}

1. 다음에 대한 구성 추가 **양식 규칙** 및 **데이터 요소** 아래와 같이:

#### 양식 규칙 추가 {#form-rules}

1. 양식을 선택하고 추가 **새 속성** 오른쪽 위에 있거나 양식을 클릭합니다.
1. 속성 페이지에서 **규칙** 양식에 대한 이벤트를 선택합니다. 아래 예제 이미지에서 **양식 이벤트**.

   ![데이터 수집에서 양식 검색](/help/forms/assets/aep-form-event-properties.png){width="100%"}

1. 양식의 모든 이벤트를 선택하고 **복사** 오른쪽 위 레일에 있습니다.
1. 복사한 후에는 **규칙 복사** 프로젝트 id로 Sites 페이지를 검색하여 양식 규칙을 붙여넣는 위치에 팝업이 나타납니다.

   ![양식 규칙 복사](/help/forms/assets/copy-form-rules.png){width="100%"}

1. 클릭 **복사** 을 눌러 양식 규칙을 사이트 페이지에 붙여넣습니다.

#### 데이터 요소 추가 {#data-elements}

1. 양식을 선택하고 추가 **새 속성** 오른쪽 위에 있거나 양식을 클릭합니다.
1. 속성 페이지에서 **데이터 요소** 양식에 대한 이벤트를 선택합니다.
1. 양식의 모든 이벤트를 선택하고 **복사** 오른쪽 위 레일에 있습니다.
1. 복사한 후에는 **규칙 복사** 프로젝트 id로 Sites 페이지를 검색하여 양식 규칙을 붙여넣는 위치에 팝업이 나타납니다.
1. 클릭 **복사** 을 눌러 양식 규칙을 사이트 페이지에 붙여넣습니다.

   ![양식 데이터 요소](/help/forms/assets/form-data-elements.png){width="100%"}

위의 단계를 통해 양식 및 사이트 규칙을 바인딩하면 다음 단계를 수행하여 Sites 페이지의 적응형 양식에 Analytics를 활성화합니다.

1. 클릭 **게시 플로우** 왼쪽이요
1. 클릭 **라이브러리 추가** 원하는 이름을 입력합니다.
1. 다음에서 **환경** 오른쪽의 드롭다운에서 을(를) 선택합니다. **개발**.
1. 클릭 **변경된 모든 리소스 추가**.
1. 클릭 **개발에 저장 및 구축**.

![게시-개발](/help/forms/assets/publish-to-dev.png){width="100%"}


<!--

## Best Practices

1.	Verify that Adobe Analytics is enabled on all the forms activated for Adobe Analytics.

1.	Check the Adobe Analytics report periodically to gain insights into user behavior and form performance. For instance, you may set the cadence to 15 days or the period you prefer to choose for report analysis. This enables you to improve the forms enrollment experience.

1.	Enable Analytics for all or most of your forms for tracking and analyzing user interaction with your forms and to gain insights into visitor interactions and engagement.

1. Check your forms performance after you update your form fields or components.

1.	Share Analytics report with your peer groups for review, you can schedule your report for a later time.

-->