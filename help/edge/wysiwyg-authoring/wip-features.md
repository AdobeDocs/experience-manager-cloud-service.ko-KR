---
title: Edge Delivery Services을 위한 진행 중인 사이트 기능
description: 진행 중인 AEM Sites 기능 및 사용 사례를 알아보고 Edge Delivery Services 사용 시 대체 솔루션을 알아봅니다.
solution: Experience Manager Sites
feature: Edge Delivery Services
role: User
source-git-commit: 50421f55444f61d64cd2ecd046bd7bc5f1f859e3
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 4%

---


# Edge Delivery Services을 위한 진행 중인 사이트 기능 {#wip-sites-features}

진행 중인 AEM Sites 기능 및 사용 사례를 알아보고 Edge Delivery Services 사용 시 대체 솔루션을 알아봅니다.

>[!TIP]
>
>진행 중인 작업이 도로의 끝을 의미하지는 않습니다. 이 문서에서 작업 진행 중으로 나열된 기능이나 사용 사례가 필요한 경우 Adobe 담당자에게 문의하십시오. 여러분과 Adobe은 함께 특정 요구 사항을 이해하고 대체 솔루션을 찾을 수 있습니다.

## 진행 중인 작업 기능 {#wip-features}

AEM Sites에서 Edge Delivery Services을 사용할 때 대부분의 Sites 기능을 사용할 수 있습니다. 예를 들어 [사이트 콘솔](/help/sites-cloud/authoring/sites-console/introduction.md)에서 사용할 수 있는 거의 모든 작업을 Edge Delivery Services에 적용할 수 있습니다.

그러나 일부 기능은 WIP(Work-in-Progress)입니다. WIP 기능은 AEM Sites을 사용하는 Edge Delivery Services에게 아직 제공되지 않거나 일부만 사용할 수 있는 사이트 콘솔의 기능입니다. 이러한 이유로 WIP 기능은 Sites와 다르게 제공되거나 사용 사례에 대한 대체 솔루션이 있을 수 있습니다.

다음 목록에는 이러한 WIP 기능과 대체 솔루션이 나와 있습니다. 프로젝트에 WIP 기능이 필요한 경우 아래 제안된 대안을 검토하고 Adobe에 연락하여 사용 사례를 파악하십시오.

| 사이트 기능 | Edge 상태 | 메모 | Edge 설명서 |
|---|---|---|---|
| [페이지 상속](/help/sites-cloud/administering/msm-and-translation.md) | 사용 가능 |  | [유니버설 편집기의 콘텐츠 상속](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [구성 요소 상속](/help/sites-cloud/administering/msm-and-translation.md) | 부분적으로 사용 가능하 | 구성 요소는 콘텐츠를 상속하지만 상속은 페이지 수준에서만 되돌릴 수 있습니다. | [유니버설 편집기의 콘텐츠 상속](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [언어 사본](/help/sites-cloud/administering/translation/overview.md) | 부분적으로 사용 가능하 | 구성 요소는 콘텐츠를 상속하지만 상속은 페이지 수준에서만 되돌릴 수 있습니다. | [유니버설 편집기의 콘텐츠 상속](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [다중 사이트 관리](/help/sites-cloud/administering/msm/overview.md) | 부분적으로 사용 가능하 | 구성 요소는 콘텐츠를 상속하지만 상속은 페이지 수준에서만 되돌릴 수 있습니다. | [유니버설 편집기의 콘텐츠 상속](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [론치](/help/sites-cloud/authoring/launches/overview.md) | 부분적으로 사용 가능하 | 구성 요소는 콘텐츠를 상속하지만 상속은 페이지 수준에서만 되돌릴 수 있습니다. | [Universal Editor에서 컨텐츠 상속](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [페이지 템플릿](/help/sites-cloud/authoring/page-editor/templates.md) | 개봉박두! | 템플릿에서 만든 페이지는 원본 템플릿의 독립적인 복사본입니다. | [범용 편집기에서 페이지 템플릿 사용](/help/edge/wysiwyg-authoring/templates.md) |
| [Context Hub 및 타깃팅](/help/sites-cloud/authoring/personalization/overview.md) | 사용할 수 없음 |  |  |
| [타임워프](/help/sites-cloud/authoring/launches/preview.md) | 사용할 수 없음 |  |  |
| [관련 콘텐츠](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#associated-content-browser) | 사용할 수 없음 |  |  |
| [경험 조각](/help/sites-cloud/authoring/fragments/experience-fragments.md) | 대체 | 페이지 만들기 및 조각 구성 요소 사용 |  |

## 진행 중인 작업 사용 사례 {#wip-use-cases}

Edge Delivery Services은 완전히 새로운 최신 기술 스택을 기반으로 구축되었기 때문에 AEM Sites의 다음 사용 사례는 아직 완전히 다루어지지 않았으며 진행 중인 작업입니다. 프로젝트에 WIP 사용 사례가 필요한 경우 Adobe에게 연락하여 함께 작업하고 프로젝트의 요구 사항을 파악하십시오.

| 사이트 사용 사례 | 세부 사항 |
|---|---|
| 페이지를 렌더링할 서버측 논리 | AEM의 런타임을 앱 서버로 사용 |
| 동적 페이지 | SSI 또는 모든 동적 포함 기법 |
| 사용자 관리 | AEM을 IdP로 사용 |
| 인증 | 보안 콘텐츠에 AEM 사용 |
| 콘텐츠 권한 | 보안 엑스트라넷으로서의 AEM |
