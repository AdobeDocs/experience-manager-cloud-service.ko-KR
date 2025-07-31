---
Title: How to configure submit action to Marketo Engage for forms?
Description: Learn how to configure the submit action of Adaptive Form to send data to Marketo Engage.
Keywords: Submit data to Marketo engage, Configure submit action as Submit to Marketo Engage
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
exl-id: 0683564b-1ac4-42b4-bc08-101c4fdef286
source-git-commit: ce4646d8db1870f8ec85faddeb4e0a6a04f4c46e
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 8%

---

# 기존 양식의 Marketo Engage에 대한 제출 액션 구성

<span class="preview"> 이 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

![워크플로](/help/forms/assets/workflow-marketo-3.png)

적응형 Forms 편집기는 처리를 위해 적응형 Forms 데이터를 Adobe Marketo Engage으로 보내기 위한 **Marketo Engage에 제출** 제출 액션을 제공합니다. 제출 시 [Adobe Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home)에 데이터를 제출하도록 기존 적응형 양식을 구성할 수 있습니다.

양식 제출을 처리하기 위한 다양한 기본 제출 액션을 사용할 수 있습니다. [적응형 양식 제출 액션](/help/forms/configure-submit-actions-core-components.md) 문서에서 이러한 옵션에 대해 자세히 알아볼 수 있습니다.

## 양식에 대해 Marketo Engage에 제출 액션을 구성하는 동안 고려 사항

* 양식 제출 시 Marketo Engage에 데이터를 제출하도록 적응형 양식이 Marketo Engage 데이터 소스로 구성되어 있는지 확인합니다. 그러나 양식이 Marketo Engage 데이터 스키마로 구성된 경우에도 **OneDrive에 제출** 또는 **SharePoint에 제출**&#x200B;과 같은 대체 항목으로 제출 동작을 변경할 수 있습니다.

## 기존 양식에 대해 Marketo Engage에 제출 액션을 구성하기 위한 전제 조건

Marketo Engage에 제출 액션을 구성하기 위한 전제 조건:

* 적응형 양식에 대해 [Marketo Engage 데이터 원본](/help/forms/use-marketo-engage-data-source-in-form.md)을(를) 구성하고 양식 요소를 Marketo Engage 필드에 바인딩합니다.

## 기존 양식에 대해 Marketo Engage에 제출 액션을 구성하는 방법

>[!VIDEO](https://video.tv.adobe.com/v/3442866/submit-action-marketo-engage-marketo-aem-aem-forms-engage)

>[!BEGINTABS]

>[!TAB 기초 구성 요소]

기초 구성 요소를 기반으로 적응형 양식의 제출 액션을 구성하여 Adobe Marketo Engage에 데이터를 제출할 수 있습니다. Marketo Engage에 제출 액션을 구성하려면 다음 단계를 수행하십시오.

1. [!DNL Experience Manager Forms] 작성자 인스턴스에 로그인합니다.
1. 편집할 적응형 양식을 열고 적응형 양식 컨테이너 속성의 **[!UICONTROL 제출]** 섹션으로 이동한 후 제출 액션을 **Marketo Engage에 제출**(으)로 선택합니다.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

![Marketo 제출 액션](/help/forms/assets/marketo-engage-submit-action-af.png){width=50%, height=50%}

적응형 양식에 대한 제출 액션을 **Marketo Engage에 제출**(으)로 구성한 후에는 처리를 위해 Adobe Marketo Engage에 데이터를 보낼 수 있습니다. 이 데이터는 마케팅 캠페인을 분석 및 최적화하고, 후속 이메일을 자동화하고, 양식 제출을 기반으로 워크플로우를 트리거하는 데 사용할 수 있습니다.

>[!TAB 핵심 구성 요소]

Adobe Marketo Engage에 데이터를 제출하도록 핵심 구성 요소 기반 적응형 양식의 제출 액션을 구성할 수 있습니다. Marketo Engage에 제출 액션을 구성하려면 다음 단계를 수행하십시오.

1. 편집할 적응형 양식을 엽니다.
1. 콘텐츠 트리를 열고 **[!UICONTROL 안내서 컨테이너]**&#x200B;를 선택합니다.
1. 적응형 양식 컨테이너 속성 ![적응형 양식 컨테이너 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 제출 액션을 구성할 수 있는 적응형 양식 컨테이너 대화 상자가 열립니다.
1. **[!UICONTROL 제출]** 탭을 열고 제출 액션을 **Marketo Engage에 제출**(으)로 선택합니다.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

![Marketo 제출 액션](/help/forms/assets/marketo-engage-submit-action.png){width=50%, height=50%}

적응형 양식에 대한 제출 액션을 **Marketo Engage에 제출**(으)로 구성한 후에는 처리를 위해 Adobe Marketo Engage에 데이터를 보낼 수 있습니다. 이 데이터는 마케팅 캠페인을 분석 및 최적화하고, 후속 이메일을 자동화하고, 양식 제출을 기반으로 워크플로우를 트리거하는 데 사용할 수 있습니다.

>[!TAB 범용 편집기]

범용 편집기에서 작성된 적응형 양식의 제출 액션을 구성하여 Adobe Marketo Engage에 데이터를 제출할 수 있습니다. Marketo Engage에 제출 액션을 구성하려면 다음 단계를 수행하십시오.

1. 편집할 적응형 양식을 엽니다.
1. 편집기에서 **양식 속성 편집** 확장을 클릭합니다.
**양식 속성** 대화 상자가 나타납니다.

   >[!NOTE]
   >
   > * 범용 편집기 인터페이스에 **양식 속성 편집** 아이콘이 보이지 않는 경우 Extension Manager에서 **양식 속성 편집** 확장을 사용하도록 설정하십시오.
   > * 범용 편집기에서 확장을 활성화하거나 비활성화하는 방법에 대해 알아보려면 [Extension Manager 기능 하이라이트](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) 문서를 참조하십시오.

1. **제출** 탭을 클릭하고 **[!UICONTROL Marketo Engage에 제출]** 제출 액션을 선택합니다.

   ![Marketo 제출 액션](/help/forms/assets/marketo-engage-submit-action-ue.png)

1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭합니다.

적응형 양식에 대한 제출 액션을 **Marketo Engage에 제출**(으)로 구성한 후에는 처리를 위해 Adobe Marketo Engage에 데이터를 보낼 수 있습니다. 이 데이터는 마케팅 캠페인을 분석 및 최적화하고, 후속 이메일을 자동화하고, 양식 제출을 기반으로 워크플로우를 트리거하는 데 사용할 수 있습니다.

>[!ENDTABS]

## 자주 묻는 질문(FAQ)

**Q: Marketo Engage 스키마에 연결하도록 구성된 양식의 제출 액션을 변경할 수 있습니까?**
**A:** 기본적으로 양식이 Marketo Engage 스키마와 연결하도록 구성된 경우 **Marketo에 제출** 작업이 선택됩니다. 그러나 필요한 경우 양식의 제출 액션을 변경할 수 있습니다.

## 다음 단계

[Munchkin 라이브러리](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/setup/munchkin)와(과) 적응형 양식을 연결하여 방문 횟수, 클릭 수, 양식 제출 횟수를 추적할 수도 있습니다.

## 관련 문서

{{af-submit-action}}

## 추가 참조

{{marketo-engage-see-also}}
