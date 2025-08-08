---
title: 리디렉션 페이지 또는 감사 메시지를 구성하는 방법
description: 양식을 만드는 동안 양식 작성자가 구성할 수 있는 감사 메시지를 표시하거나 웹 페이지로 리디렉션하는 방법에 대해 알아봅니다.
feature: Adaptive Forms, Edge Delivery Services
role: User
level: Intermediate
source-git-commit: 62134c5b67d610f801c407e696e761ed05e02c87
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# 리디렉션 또는 감사 메시지 구성

범용 편집기를 사용하여 만든 양식에서 양식 작성자는 사용자가 양식을 제출한 후 수행되는 작업을 구성할 수 있습니다. 양식 속성 편집 확장의 제출 탭을 사용하여 감사 메시지를 표시하거나 사용자를 특정 웹 페이지로 리디렉션할 수 있습니다.

**AEM 양식 속성** 확장의 **제출** 탭을 사용하여 유니버설 편집기에서 만든 양식에 대해 감사 메시지를 구성하거나 URL을 리디렉션할 수 있습니다.

## 사전 요구 사항

**양식 속성 편집** 확장의 **제출** 탭을 사용하여 유니버설 편집기에서 만든 양식에 대해 제출 액션을 구성할 수 있습니다.

![양식 속성 아이콘](/help/forms/assets/ue-form-properties-icon.png)

![유니버설 편집기 양식 속성](/help/forms/assets/ue-form-properties.png)

>[!NOTE]
>
>* 범용 편집기 인터페이스에 **양식 속성** 아이콘이 보이지 않는 경우 Extension Manager에서 **양식 속성 편집** 확장을 사용하도록 설정하십시오.
>* 범용 편집기에서 확장을 활성화하거나 비활성화하는 방법에 대해 알아보려면 [Extension Manager 기능 하이라이트](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) 문서를 참조하십시오.

## 리디렉션 또는 감사 메시지를 구성하는 방법

양식 제출 시 사용자를 다른 웹 페이지로 리디렉션하거나 메시지를 표시할 수 있습니다.

리디렉션 페이지 또는 감사 메시지를 구성하려면:

1. 편집할 적응형 양식을 엽니다.
1. 콘텐츠 트리를 열고 **[!UICONTROL 안내서 컨테이너]**&#x200B;를 선택합니다.
1. 적응형 양식 컨테이너 속성 ![적응형 양식 컨테이너 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 데이터 모델을 구성하는 적응형 양식 컨테이너 대화 상자가 열립니다.
1. **[!UICONTROL 제출]** 탭을 엽니다. 리디렉션 페이지 또는 메시지를 구성하는 옵션이 표시됩니다.

   리디렉션 페이지 또는 메시지를 구성하기 위한 가이드 컨테이너의 ![제출 대화 상자](/help/forms/assets/adaptive-forms-core-components-redirect-page-or-thank-you-message.png)

**리디렉션 URL 구성**

* 리디렉션 URL을 구성하려면 [전송] 옵션에서 **[!UICONTROL URL로 리디렉션 옵션]**&#x200B;을 선택하고 절대 주소 또는 AEM Sites 페이지의 리디렉션 URL 또는 상대 경로를 제공합니다.

![리디렉션](/help/edge/docs/forms/universal-editor/assets/redirect-ue.png)

**감사 메시지 구성**

* 사용자 지정 또는 감사 메시지를 구성하려면 **[!UICONTROL 메시지 표시]** 옵션을 선택하고 [메시지] 콘텐트 상자에 메시지를 제공합니다. 서식 있는 텍스트 상자입니다. 전체 화면 옵션을 사용하여 사용 가능한 모든 서식 있는 텍스트 항목을 볼 수 있습니다.

![감사합니다](/help/edge/docs/forms/universal-editor/assets/thankyou-ue.png)

양식 작성자는 양식을 제출한 후 양식 사용자가 리디렉션되는 각 양식에 대한 페이지를 구성할 수 있습니다.
