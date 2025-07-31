---
Title: How to integrate Marketo Engage with AEM Forms using Form wizard?
Description: Learn how to integrate your Marketo Engage instance with AEM Forms using form wizard.
Keywords: How to connect a Marketo instance with form? , Connect a form to Marketo, Integrate a form with Marketo Engage, Integrate an Adaptive Form with a Marketo instance.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
exl-id: 1fcba628-ffd8-416a-a8b5-76b35d4aabd4
source-git-commit: ce4646d8db1870f8ec85faddeb4e0a6a04f4c46e
workflow-type: tm+mt
source-wordcount: '1012'
ht-degree: 7%

---

# Marketo Engage과 적응형 양식 통합

<span class="preview"> 이 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

![워크플로](/help/forms/assets/workflow-marketo-4.png)

Marketo Engage을 AEM Forms과 통합하기 위한 클라우드 서비스 구성을 만든 후 [Adobe Marketo Engage](https://experienceleague.adobe.com/ko/docs/marketo/using/home)과 통합하도록 적응형 양식을 구성할 수 있습니다.

각 단계를 안내하여 구성 프로세스를 단순화하는 양식 마법사를 사용하여 Marketo Engage을 적응형 양식에 연결할 수 있습니다. 여기에는 템플릿, 스타일 및 데이터 필드 선택뿐만 아니라 데이터 매핑 설정을 통해 양식이 만들어지면 Marketo Engage과 통신할 수 있도록 하는 작업도 포함됩니다. 양식 마법사를 사용하여 제출 시 Adobe Marketo Engage에 직접 데이터를 제출하도록 적응형 양식을 구성할 수도 있습니다.

## 양식용 Marketo Engage 데이터 소스 구성을 위한 고려 사항

양식에 대해 Marketo Engage 데이터 소스를 구성하는 동안 고려해야 할 사항은 다음과 같습니다.

* Edge Delivery Services Forms을 Marketo Engage과 연결할 수 없습니다.

## Marketo Engage을 양식과 연결하기 위한 사전 요구 사항

Marketo Engage을 양식과 연결하기 위한 전제 조건:

* [클라우드 서비스 구성을 만들어 Marketo Engage을 양식과 통합](/help/forms/integrate-form-to-marketo-engage.md)합니다.

## Marketo Engage과 통합하도록 새 적응형 양식을 구성하는 방법

>[!VIDEO](https://video.tv.adobe.com/v/3442867/marketo-aem-marketo-engage-engage-aem-forms)

>[!BEGINTABS]

>[!TAB 기초 구성 요소]

Marketo Engage과 통합하도록 기초 구성 요소 기반의 새 적응형 양식을 구성하려면 다음 단계를 수행하십시오.

1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 선택합니다.

   ![Forms 및 문서 선택](/help/forms/assets/select-forms.png)

1. **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 양식]**&#x200B;을 선택합니다. 양식 만들기 마법사가 열립니다.

   ![AF 선택](/help/forms/assets/select-create-forms.png)

1. **[!UICONTROL Source]** 탭에서 템플릿을 선택합니다

   ![템플릿 선택](/help/forms/assets/select-template-af1.png)

1. **[!UICONTROL 스타일]**&#x200B;에서 테마를 선택합니다.

   ![테마 선택](/help/forms/assets/select-form-theme-af1.png)
1. **[!UICONTROL 데이터]** 탭에서 데이터 모델을 **Marketo Engage**(으)로 선택합니다.
1. 화면 오른쪽 창에 나타나는 드롭다운 목록에서 **[!UICONTROL 클라우드 구성]**&#x200B;을(를) 선택합니다.
기본적으로 연관된 구성의 모든 필드가 나타납니다. 마법사를 사용하면 확인란을 사용하여 적응형 양식에 포함할 필드를 선택할 수 있습니다.

   ![데이터 모델 선택](/help/forms/assets/select-marketo-data-af1.png)

1. **[!UICONTROL 제출]** 탭에서 제출 액션을 **[!UICONTROL Marketo에 제출]**(으)로 선택합니다.

   데이터 모델을 **Marketo Engage**(으)로 선택하면 **Marketo에 제출**(으)로 제출 동작이 자동으로 선택됩니다. **[!UICONTROL 제출]** 탭에서 다른 제출 액션을 선택할 수 있습니다. **[!UICONTROL 제출]** 탭에는 사용 가능한 모든 제출 액션이 표시됩니다.

   ![Marketo 참여에 제출](/help/forms/assets/select-marketo-engage.png)

1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다. 적응형 양식을 저장할 제목, 이름 및 위치를 지정합니다.

   ![양식 만들기](/help/forms/assets/create-marketo-form.png)

1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

이제 적응형 양식이 Marketo Engage 인스턴스와 연결하도록 구성되었습니다. 또는 적응형 양식 속성을 편집하여 관련 구성을 변경할 수도 있습니다

>[!TAB 핵심 구성 요소]

Marketo Engage과 통합하도록 핵심 구성 요소를 기반으로 새 적응형 양식을 구성하려면 다음 단계를 수행하십시오.

1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 선택합니다.

   ![Forms 및 문서 선택](/help/forms/assets/select-forms.png)

1. **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 양식]**&#x200B;을 선택합니다. 양식 만들기 마법사가 열립니다.

   ![AF 선택](/help/forms/assets/select-create-forms.png)

1. **[!UICONTROL Source]** 탭에서 템플릿을 선택합니다

   ![템플릿 선택](/help/forms/assets/select-template.png)

1. **[!UICONTROL 스타일]**&#x200B;에서 테마를 선택합니다.

   ![테마 선택](/help/forms/assets/select-form-theme.png)


1. **[!UICONTROL 데이터]** 탭에서 데이터 모델을 **Marketo Engage**(으)로 선택합니다.

1. 화면 오른쪽 창에 나타나는 드롭다운 목록에서 **[!UICONTROL 클라우드 구성]**&#x200B;을(를) 선택합니다.
기본적으로 연관된 구성의 모든 필드가 나타납니다. 마법사를 사용하면 확인란을 사용하여 적응형 양식에 포함할 필드를 선택할 수 있습니다.

   ![데이터 모델 선택](/help/forms/assets/select-marketo-data.png)

1. **[!UICONTROL 제출]** 탭에서 제출 액션을 **[!UICONTROL Marketo에 제출]**(으)로 선택합니다.

   데이터 모델을 **Marketo Engage**(으)로 선택하면 **Marketo에 제출**(으)로 제출 동작이 자동으로 선택됩니다. **[!UICONTROL 제출]** 탭에서 다른 제출 액션을 선택할 수 있습니다. **[!UICONTROL 제출]** 탭에는 사용 가능한 모든 제출 액션이 표시됩니다.

   ![Marketo 참여에 제출](/help/forms/assets/select-marketo-engage.png)

1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다. 적응형 양식을 저장할 제목, 이름 및 위치를 지정합니다.

   ![양식 만들기](/help/forms/assets/create-marketo-form.png)

1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

이제 적응형 양식이 Marketo Engage 인스턴스와 연결하도록 구성되었습니다. 또는 적응형 양식 속성을 편집하여 관련 구성을 변경할 수도 있습니다.

>[!TAB 범용 편집기]

Marketo Engage과 통합하도록 범용 편집기에서 작성된 새 적응형 양식을 구성하려면 다음 단계를 수행하십시오.

1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL 양식]** > **[!UICONTROL 양식 및 문서]**&#x200B;를 선택합니다.

   ![Forms 및 문서 선택](/help/forms/assets/select-forms.png)

1. **[!UICONTROL 만들기]** > **[!UICONTROL 적응형 양식]**&#x200B;을 선택합니다. 양식 만들기 마법사가 열립니다.

   ![AF 선택](/help/forms/assets/select-create-forms.png)

1. **[!UICONTROL Source]** 탭에서 템플릿을 선택합니다

   ![템플릿 선택](/help/forms/assets/select-template-ue.png)

1. **[!UICONTROL 데이터]** 탭에서 데이터 모델을 **Marketo Engage**(으)로 선택합니다.

1. 화면 오른쪽 창에 나타나는 드롭다운 목록에서 **[!UICONTROL 클라우드 구성]**&#x200B;을(를) 선택합니다.
기본적으로 연관된 구성의 모든 필드가 나타납니다. 마법사를 사용하면 확인란을 사용하여 적응형 양식에 포함할 필드를 선택할 수 있습니다.

   ![데이터 모델 선택](/help/forms/assets/select-marketo-data-ue.png)

1. **[!UICONTROL 제출]** 탭에서 제출 액션을 **[!UICONTROL Marketo에 제출]**(으)로 선택합니다.

   데이터 모델을 **Marketo Engage**(으)로 선택하면 **Marketo에 제출**(으)로 제출 동작이 자동으로 선택됩니다. **[!UICONTROL 제출]** 탭에서 다른 제출 액션을 선택할 수 있습니다. **[!UICONTROL 제출]** 탭에는 사용 가능한 모든 제출 액션이 표시됩니다.

   ![Marketo 참여에 제출](/help/forms/assets/select-marketo-engage-ue.png)

1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다. 적응형 양식을 저장할 제목, 이름 및 위치를 지정합니다.

   ![양식 만들기](/help/forms/assets/create-marketo-form.png)

1. **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

이제 적응형 양식이 Marketo Engage 인스턴스와 연결하도록 구성되었습니다. 또는 적응형 양식 속성을 편집하여 관련 구성을 변경할 수도 있습니다.

>[!ENDTABS]

## 자주 묻는 질문(FAQ)

**Q: Marketo Engage 스키마에 연결하도록 구성된 양식의 제출 액션을 변경할 수 있습니까?**
**A:** 기본적으로 양식이 Marketo Engage 스키마와 연결하도록 구성된 경우 **Marketo에 제출** 작업이 선택됩니다. 그러나 필요한 경우 양식의 제출 액션을 변경할 수 있습니다.


**Q: 양식의 커넥터를 변경하면 어떻게 됩니까?**\
**A:** 양식의 커넥터를 변경하면 기존 바인딩이 유효하지 않게 됩니다.

**Q: Marketo Engage과 통합된 양식에 대해 규칙 편집기의 호출 서비스에서 사용할 수 있는 세 가지 작업은 무엇입니까?**\
**A:** Marketo Engage과 통합된 양식의 **서비스 호출**&#x200B;에서 사용할 수 있는 기본 작업 세 가지는 다음과 같습니다.

* 동기화 리드
* ID로 리드 가져오기
* 필터 유형별 리드 가져오기

## 다음 단계

[Munchkin 라이브러리](https://experienceleague.adobe.com/ko/docs/marketo/using/product-docs/administration/setup/munchkin)와(과) 적응형 양식을 연결하여 방문 횟수, 클릭 수, 양식 제출 횟수를 추적할 수도 있습니다.

## 관련 문서

{{af-submit-action}}

## 추가 참조

{{marketo-engage-see-also}}
