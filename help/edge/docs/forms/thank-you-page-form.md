---
title: 양식 제출 후 사용자 정의 감사 메시지 표시
description: 양식 블록에 대한 감사 페이지와 리디렉션을 구성하여 사용자 경험을 최적화하고 사용자 여정을 간소화하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
exl-id: e6c66b22-dc52-49e3-a920-059adb5be22f
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 100%

---

# 양식 제출 후 사용자 정의 감사 메시지 표시

사용자가 양식을 제출한 후에는 감사 메시지를 통해 원활한 경험을 제공하는 것이 중요합니다. 이로써 양식을 성공적으로 제출할 뿐만 아니라 사용자 만족도를 높이고 더 나은 여정을 안내합니다.

- **감사 메시지**: 감사 메시지는 브랜드 아이덴티티를 강화하는 동시에 안심을 주고 중요한 정보를 제공하는 사용자 경험의 기초입니다. 이는 작업 완성도와 사용자의 만족도를 높이면서 사용자의 작업을 직접적으로 승인합니다.

- **리디렉션**: 리디렉션은 사용자를 관련 대상으로 유도한 다음 사용자 참여도를 최적화하여 최종적으로 전환율을 높이는 데 핵심적인 역할을 합니다. 리디렉션은 사용자에게 고객 여정의 다음 단계를 원활하게 안내함으로써 원활한 탐색 경험을 제공할 수 있습니다. 예를 들어 초기 세부 정보가 수집되면 사용자는 결제 페이지로 리디렉션됩니다.

양식 제출 시 후속 감사 메시지 표시는 적응형 양식 블록의 기본 비헤이비어입니다. 성공적으로 양식이 제출되면 메시지는 양식 상단에 표시됩니다.

![기본 감사 메시지](/help/edge/assets/thank-you-message.png)

단, 특정 요구 사항에 따라 이 환경을 유연하게 조정할 수 있습니다. 옵션은 다음과 같습니다.

- 양식 제출 후 사용자 정의 감사 메시지 표시
- 추가 작업을 위해 양식 제출 후 사용자를 다른 페이지로 리디렉션

>[!NOTE]
>
> 요구 사항에 따라 감사 메시지를 사용자 정의하려면 다음 [문의 스프레드시트](/help/edge/docs/forms/assets/enquiry.xlsx)를 참조하십시오.

## 사용자 정의 감사 메시지 구성

성공적인 양식 제출 시 맞춤형 감사 메시지를 표시하려면 스프레드시트를 구성하여 해당 메시지를 표시할 수 있습니다.

적응형 양식 블록에 대한 사용자 정의 감사 메시지를 구성하려면 아래 단계를 따릅니다.

1. Microsoft SharePoint 또는 Google Workspace의 Edge Delivery 프로젝트 폴더로 이동하여 스프레드시트를 엽니다.
1. 스프레드시트의 `submit` 필드 유형 `value` 열에 맞춤형 감사 메시지를 추가합니다.

   ![맞춤형 감사 메시지](/help/edge/docs/forms/assets/thankyou-custommessage.png)

   예를 들어 `submit` 필드 유형의 `value` 열에서 `Submission Successful!` 메시지를 추가합니다.

1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 시트를 미리 보고 게시합니다.

   ![맞춤형 감사 메시지](/help/edge/docs/forms/assets/customized-thank-you-message.png)

## 양식 제출 후 사용자를 다른 페이지로 리디렉션

양식 제출 후 사용자를 다른 페이지로 리디렉션하면 관련 정보를 제공하고, 작업을 확인하고, 사용자가 원하는 결과를 얻도록 유도함으로써 사용자 경험을 향상시킬 수 있습니다. 예:

- 사용자가 구매 양식을 작성하면 사용자는 결제 페이지로 리디렉션되어 거래를 안전하게 완료할 수 있습니다.
- 이벤트나 웨비나용 등록 양식 제출 시 사용자는 날짜, 시간, 위치 등 이벤트 세부 정보를 표시하는 확인 페이지로 리디렉션됩니다.

아래 단계에 따라 사용자를 다른 페이지로 리디렉션합니다.

1. Microsoft SharePoint 또는 Google Workspace의 Edge Delivery 프로젝트 폴더로 이동하여 스프레드시트를 엽니다.
1. 성공적인 양식 제출 시 사용자를 리디렉션하려면 스프레드시트의 `submit` 필드 유형 `value` 열에 URL을 붙여넣습니다.
페이지를 다른 페이지로 리디렉션하려면 [Edge Delivery 문서](https://www.aem.live/docs/) 페이지 URL을 사용합니다.

   ![감사 리디렉션 URL](/help/edge/docs/forms/assets/thankyou-redirecturl.png)

1. [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content)을 사용하여 시트를 미리 보고 게시합니다.

   ![감사 메시지 리디렉션](/help/edge/docs/forms/assets/thankyou-redirectpage.gif)

새 문서 파일을 만들고 `submit` 필드 유형의 `value` 열에서 미리보기 URL을 추가할 수도 있습니다.

사용자가 양식을 제출한 후에는 분명한 감사 메시지를 제공하는 것이 중요합니다. 이러면 양식이 성공적으로 제출되었는지 확인하고 사용자 만족도를 높일 수 있습니다.

