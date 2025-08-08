---
title: 적응형 Forms을 위한 Marketo Engage 데이터를 구성하는 방법
description: 적응형 Forms에서 Marketo Engage 스키마를 사용하는 방법에 대해 알아봅니다.
keywords: '적응형 Forms에서 Marketo Engage 데이터 소스 사용, Marketo 인스턴스 데이터 소스를 양식과 연결하는 방법 : 양식을 Marketo에 연결합니다.'
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 4656ec65-f1ad-4e97-8d93-25933cdc7f7b
source-git-commit: 1be7bafc1d93a65a81eeb2f7e86cac33cde7aa35
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 7%

---

# 기존 적응형 양식의 Marketo Engage 데이터 소스 구성

<span class="preview"> 이 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

![워크플로](/help/forms/assets/workflow-marketo-2.png)

Marketo Engage을 기존 AEM Forms과 통합하기 위한 클라우드 서비스 구성을 만든 후 양식에 대한 데이터 소스를 구성할 수 있습니다.

데이터 통합을 구성하면 사용자가 다양한 데이터 소스 또는 스키마에 연결할 수 있습니다. Marketo Engage 데이터 소스와 통합하여 다양한 양식에서 이를 사용하면 해당 데이터에 대한 작업이 용이해집니다. 적응형 양식에 대해 지원되는 기본 데이터 원본을 살펴보려면 [데이터 원본 구성](/help/forms/configure-data-sources.md) 문서를 참조하십시오.

## 양식용 Marketo Engage 데이터 소스 구성을 위한 고려 사항

양식에 대해 Marketo Engage 데이터 소스를 구성하는 동안 고려해야 할 사항은 다음과 같습니다.

* Edge Delivery Services Forms을 Marketo Engage과 연결할 수 없습니다.

## 양식에 Marketo Engage 데이터 소스를 사용하기 위한 사전 요구 사항

양식과 함께 Marketo Engage 데이터 소스를 사용하기 위한 전제 조건:

* [클라우드 서비스 구성을 만들어 Marketo Engage을 양식과 통합](/help/forms/integrate-form-to-marketo-engage.md)합니다.

## Marketo Engage 데이터 소스에 대해 기존 적응형 양식을 구성하는 방법

>[!VIDEO](https://video.tv.adobe.com/v/3442871/marketo-aem-forms-aem-marketo-engage)

<span> 이 비디오는 핵심 구성 요소에만 적용됩니다. UE/Foundation 구성 요소에 대해서는 문서를 참조하십시오.</span>

>[!BEGINTABS]

>[!TAB 기초 구성 요소]

Marketo Engage 데이터 소스를 사용하여 기초 구성 요소 기반의 적응형 양식을 구성하려면 다음 단계를 수행하십시오.

1. [!DNL Experience Manager Forms] 작성자 인스턴스에 로그인합니다.
1. 편집할 적응형 양식을 열고 적응형 양식 컨테이너 속성의 **[!UICONTROL 데이터 모델]** 섹션으로 이동한 후 양식 모델을 **커넥터**(으)로 선택합니다.
1. 드롭다운 목록에서 **[!UICONTROL 커넥터]**&#x200B;를 선택합니다.
1. **[!UICONTROL 커넥터]**&#x200B;를 선택한 후 클라우드 구성을 선택할 수 있습니다.

   ![Marketo 커넥터 선택](/help/forms/assets/select-marketo-connector-af1.png){width=50%, height=50%}

   선택한 Marketo Engage 구성에 따라 양식 요소가 사이드바의 **[!UICONTROL 콘텐츠 브라우저]**&#x200B;에 있는 **[!UICONTROL 데이터 모델 개체]** 탭에 표시됩니다. 이러한 요소를 드래그 앤 드롭하여 적응형 양식을 작성할 수 있습니다.

   ![Marketo 데이터 Source](/help/forms/assets/marketo-engage-data-source-af1.png){width=50%, height=50%}

1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

또는 적응형 양식 속성을 편집하여 관련 구성을 변경할 수도 있습니다.

이제 적응형 양식이 연결된 Marketo Engage 인스턴스의 데이터 소스로 구성되었습니다. 이제 Adobe Marketo Engage으로 데이터를 전송하도록 구성합니다.

>[!TAB 핵심 구성 요소]

Marketo Engage 데이터 소스를 사용하여 핵심 구성 요소 기반의 적응형 양식을 구성하려면 다음 단계를 수행하십시오.

1. [!DNL Experience Manager Forms] 작성자 인스턴스에 로그인합니다.

1. 편집할 적응형 양식을 엽니다.
1. 콘텐츠 트리를 열고 **[!UICONTROL 안내서 컨테이너]**&#x200B;를 선택합니다.
1. 적응형 양식 컨테이너 속성 ![적응형 양식 컨테이너 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 데이터 소스를 구성할 수 있는 적응형 양식 컨테이너 대화 상자가 열립니다.
1. **[!UICONTROL 데이터 모델]** 탭을 열고 양식 모델을 **커넥터**(으)로 선택합니다.
1. 드롭다운 목록에서 **[!UICONTROL 커넥터]**&#x200B;를 선택합니다.

1. **[!UICONTROL 커넥터]**&#x200B;를 선택한 후 클라우드 구성을 선택할 수 있습니다.

   ![Marketo 커넥터 선택](/help/forms/assets/select-marketo-connector.png){width=50%, height=50%}

   선택한 Marketo Engage 구성에 따라 양식 요소가 사이드바의 **[!UICONTROL 콘텐츠 브라우저]**&#x200B;에 있는 **[!UICONTROL 데이터 모델 개체]** 탭에 표시됩니다. 이러한 요소를 드래그 앤 드롭하여 적응형 양식을 작성할 수 있습니다.

   ![Marketo 데이터 Source](/help/forms/assets/marketo-engage-data-source.png){width=50%, height=50%}

1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

또는 적응형 양식 속성을 편집하여 관련 구성을 변경할 수도 있습니다.

이제 적응형 양식이 연결된 Marketo Engage 인스턴스의 데이터 소스로 구성되었습니다. 이제 Adobe Marketo Engage으로 데이터를 전송하도록 구성합니다.

>[!TAB 범용 편집기]

Marketo Engage 데이터 소스를 사용하여 범용 편집기에서 작성된 적응형 양식을 구성하려면 다음 단계를 수행하십시오.

1. 편집할 양식의 속성을 엽니다.
1. **[!UICONTROL 양식 모델]**&#x200B;을(를) 선택하십시오.
1. **양식 모델**&#x200B;에서 **[!UICONTROL 커넥터]**&#x200B;를 선택합니다.
1. **[!UICONTROL 커넥터]**&#x200B;를 선택한 후 클라우드 구성을 선택할 수 있습니다.

   ![Marketo 커넥터 선택](/help/forms/assets/select-marketo-connector-ue.png)

1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭합니다.

선택한 Marketo Engage 구성을 기반으로 양식 요소는 속성 패널에 있는 콘텐츠 브라우저의 **[!UICONTROL 데이터 소스]** 탭에 표시됩니다. 이러한 요소를 드래그 앤 드롭하여 적응형 양식을 작성할 수 있습니다.

![Marketo 데이터 Source](/help/forms/assets/marketo-engage-data-source-ue.png)

이제 양식이 연결된 Marketo Engage 인스턴스의 데이터 소스로 구성되었습니다. 이제 Adobe Marketo Engage으로 데이터를 전송하도록 구성합니다.

>[!ENDTABS]

## 자주 묻는 질문(FAQ)

**Q: 양식의 커넥터를 변경하면 어떻게 됩니까?**\
**A:** 양식의 커넥터를 변경하면 기존 바인딩이 유효하지 않게 됩니다.

**Q: Marketo Engage과 통합된 양식에 대해 규칙 편집기의 호출 서비스에서 사용할 수 있는 세 가지 작업은 무엇입니까?**\
**A:** Marketo Engage과 통합된 양식의 **서비스 호출**&#x200B;에서 사용할 수 있는 기본 작업 세 가지는 다음과 같습니다.
* 동기화 리드
* ID로 리드 가져오기
* 필터 유형별 리드 가져오기

## 다음 단계

이제 적응형 Forms에 대한 Marketo Engage 데이터 소스를 구성했습니다. 그런 다음 [데이터를 Marketo Engage에 보내도록 적응형 양식을 구성](/help/forms/submit-adaptive-form-to-marketo-engage.md)할 수 있습니다.

## 관련 문서

{{af-submit-action}}

## 추가 참조

{{marketo-engage-see-also}}
