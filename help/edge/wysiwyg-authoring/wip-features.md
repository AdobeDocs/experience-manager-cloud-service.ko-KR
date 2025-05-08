---
title: Edge Delivery Services를 위해 진행 중인 Sites 기능
description: 진행 중인 AEM Sites의 기능 및 사용 사례를 알아보고 Edge Delivery Services를 사용할 때 대체 솔루션을 알아봅니다.
solution: Experience Manager Sites
feature: Edge Delivery Services
role: User
exl-id: 21745f53-a7ef-4eec-9170-b267c2f4314e
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: ht
source-wordcount: '473'
ht-degree: 100%

---

# Edge Delivery Services를 위해 진행 중인 Sites 기능 {#wip-sites-features}

진행 중인 AEM Sites의 기능 및 사용 사례를 알아보고 Edge Delivery Services를 사용할 때 대체 솔루션을 알아봅니다.

>[!TIP]
>
>진행 중이라고 해서 모든 것이 끝나는 것은 아닙니다. 이 문서에서 진행 중인 작업으로 나열된 기능 또는 사용 사례가 필요한 경우 Adobe 담당자에게 문의하십시오. Adobe와 협력하여 특정 요구 사항을 이해하고 대체 솔루션을 찾을 수 있습니다.

## 진행 중인 기능 {#wip-features}

AEM Sites가 포함된 Edge Delivery Services를 사용하는 경우 대부분의 Sites 기능을 사용할 수 있습니다. 예를 들어 [Sites 콘솔](/help/sites-cloud/authoring/sites-console/introduction.md)에서 사용할 수 있는 거의 모든 작업은 Edge Delivery Services에 적용됩니다.

하지만 일부 기능은 아직 진행 중(WIP)입니다. WIP 기능은 AEM Sites가 포함된 Edge Delivery Services에서 아직 사용할 수 없거나 부분적으로만 사용할 수 있는 Sites 콘솔의 기능입니다. 이러한 이유로 WIP 기능은 Sites와 다르게 제공되거나 사용 사례에 대한 대체 솔루션이 있을 수 있습니다.

다음 목록은 이러한 WIP 기능과 대체 솔루션을 제시합니다. 프로젝트에 WIP 기능이 필요한 경우 아래에 제안된 대안을 검토하고 Adobe에 문의하여 사용 사례를 이해하기 위해 협력해 주십시오.

| Sites 기능 | Edge 상태 | 메모 | Edge 설명서 |
|---|---|---|---|
| [페이지 상속](/help/sites-cloud/administering/msm-and-translation.md) | 사용 가능 |  | [범용 편집기에서의 콘텐츠 상속](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [구성 요소 상속](/help/sites-cloud/administering/msm-and-translation.md) | 부분적으로 사용 가능 | 구성 요소는 콘텐츠를 상속하지만 상속은 페이지 수준에서만 되돌릴 수 있습니다. | [범용 편집기에서의 콘텐츠 상속](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [언어 복제](/help/sites-cloud/administering/translation/overview.md) | 부분적으로 사용 가능 | 구성 요소는 콘텐츠를 상속하지만 상속은 페이지 수준에서만 되돌릴 수 있습니다. | [범용 편집기에서의 콘텐츠 상속](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [다중 사이트 관리](/help/sites-cloud/administering/msm/overview.md) | 부분적으로 사용 가능 | 구성 요소는 콘텐츠를 상속하지만 상속은 페이지 수준에서만 되돌릴 수 있습니다. | [범용 편집기에서의 콘텐츠 상속](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [론치](/help/sites-cloud/authoring/launches/overview.md) | 부분적으로 사용 가능 | 구성 요소는 콘텐츠를 상속하지만 상속은 페이지 수준에서만 되돌릴 수 있습니다. | [범용 편집기에서의 콘텐츠 상속](/help/sites-cloud/authoring/universal-editor/inheritance.md) |
| [페이지 템플릿](/help/sites-cloud/authoring/page-editor/templates.md) | 부분적으로 사용 가능 | 템플릿에서 생성된 페이지는 원본 템플릿의 독립적인 사본입니다. | [범용 편집기로 페이지 템플릿 사용](/help/sites-cloud/authoring/universal-editor/templates.md) |
| [컨텍스트 허브 및 타기팅](/help/sites-cloud/authoring/personalization/overview.md) | 사용할 수 없음 |  |  |
| [타임워프](/help/sites-cloud/authoring/launches/preview.md) | 사용할 수 없음 |  |  |
| [관련 콘텐츠](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#associated-content-browser) | 사용할 수 없음 |  |  |
| [경험 조각](/help/sites-cloud/authoring/fragments/experience-fragments.md) | 대안 | 페이지 만들기 및 조각 구성 요소 사용 |  |

## 진행 중인 작업 사용 사례 {#wip-use-cases}

Edge Delivery Services는 완전히 새롭고 최신 기술 스택을 기반으로 구축되었기 때문에 다음 AEM Sites의 사용 사례는 아직 완전히 다루지 않았으며 현재 진행 중입니다. 프로젝트에 WIP 사용 사례가 필요한 경우 Adobe에 문의하여 협력하고 프로젝트의 요구 사항을 파악하시기 바랍니다.

| Sites 사용 사례 | 세부 사항 |
|---|---|
| 페이지 렌더링을 위한 서버측 로직 | AEM의 런타임을 앱 서버로 사용 |
| 동적 페이지 | SSI 또는 모든 동적에 기술 포함 |
| 사용자 관리 | AEM을 IdP로 사용 |
| 인증 | 보안 콘텐츠에 AEM 사용 |
| 콘텐츠 권한 | 보안 엑스트라넷으로서의 AEM |
