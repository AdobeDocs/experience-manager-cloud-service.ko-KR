---
Title: How to configure submit action to Marketo Engage for forms?
Description: Learn how to configure the submit action of Adaptive Form to send data to Marketo Engage.
Keywords: Submit data to Marketo engage, Configure submit action as Submit to Marketo Engage
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
source-git-commit: 681c194f997ab66f93beedad4eea273614e6797d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 7%

---


# Marketo Engage 기존 양식에 대한 제출 액션을 구성합니다.

<span class="preview"> 이 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

![워크플로](/help/forms/assets/workflow-marketo-3.png)

적응형 Forms 편집기는 처리를 위해 적응형 Forms 데이터를 Adobe Marketo Engage으로 보내기 위한 **Marketo Engage에 제출** 제출 액션을 제공합니다. 제출 시 [Adobe Marketo Engage](https://experienceleague.adobe.com/en/docs/marketo/using/home)에 데이터를 제출하도록 기존 적응형 양식을 구성할 수 있습니다.

양식 제출을 처리하기 위한 다양한 기본 제출 액션을 사용할 수 있습니다. [적응형 양식 제출 액션](/help/forms/configure-submit-actions-core-components.md) 문서에서 이러한 옵션에 대해 자세히 알아볼 수 있습니다.

## 양식 Marketo Engage에 제출 액션을 구성하는 동안 고려 사항

* 적응형 양식이 양식 제출 시 Marketo Engage에 데이터를 제출하도록 Marketo Engage 데이터 소스로 구성되어 있는지 확인합니다. 그러나 양식이 Marketo Engage 데이터 스키마로 구성된 경우에도 **OneDrive에 제출** 또는 **SharePoint에 제출**&#x200B;과 같은 대체 항목으로 제출 동작을 변경할 수 있습니다.

## 기존 양식의 Marketo Engage에 제출 액션을 구성하기 위한 전제 조건

제출 액션을 Marketo Engage으로 구성하기 위한 전제 조건:

* 적응형 양식에 대한 [Marketo Engage 데이터 원본](/help/forms/use-marketo-engage-data-source-in-form.md)을(를) 구성하고 양식 요소를 Marketo Engage 필드에 바인딩합니다.

## 기존 양식의 Marketo Engage에 제출 액션을 구성하는 방법

적응형 양식의 제출 액션을 구성하여 Adobe Marketo Engage에 데이터를 제출할 수 있습니다. 제출 액션을 Marketo Engage으로 구성하려면 다음 단계를 수행하십시오.

1. 편집할 적응형 양식을 엽니다.
1. 콘텐츠 트리를 열고 **[!UICONTROL 안내서 컨테이너]**&#x200B;를 선택합니다.
1. 적응형 양식 컨테이너 속성 ![적응형 양식 컨테이너 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 제출 액션을 구성할 수 있는 적응형 양식 컨테이너 대화 상자가 열립니다.
1. **[!UICONTROL 제출]** 탭을 열고 제출 액션을 **Marketo Engage에 제출**(으)로 선택합니다.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

![Marketo 제출 액션](/help/forms/assets/marketo-engage-submit-action.png){width=50%, height=50%}


적응형 양식에 대한 제출 액션을 **Marketo Engage에 제출**(으)로 구성한 후에는 처리를 위해 Adobe Marketo Engage에 데이터를 보낼 수 있습니다. 이 데이터는 마케팅 캠페인을 분석 및 최적화하고, 후속 이메일을 자동화하고, 양식 제출을 기반으로 워크플로우를 트리거하는 데 사용할 수 있습니다.

## 자주 묻는 질문(FAQ)

**Q: Marketo Engage 스키마에 연결하도록 구성된 양식의 제출 액션을 변경할 수 있습니까?**
**A:** 기본적으로 양식이 Marketo Engage 스키마와 연결하도록 구성된 경우 **Marketo에 제출** 작업이 선택됩니다. 그러나 필요한 경우 양식의 제출 액션을 변경할 수 있습니다.

## 다음 단계

[Munchkin 라이브러리](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/setup/munchkin)와(과) 적응형 양식을 연결하여 방문 횟수, 클릭 수, 양식 제출 횟수를 추적할 수도 있습니다.

## 관련 문서

{{af-submit-action}}

## 추가 참조

{{marketo-engage-see-also}}
