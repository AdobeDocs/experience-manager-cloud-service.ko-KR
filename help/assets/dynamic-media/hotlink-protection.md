---
title: Dynamic Media에서 핫링크 보호 활성화
description: Dynamic Media에서 핫링크 보호를 활성화하는 방법을 알아봅니다.
feature: 자산 관리
role: User
exl-id: 0198b3a3-173e-46ca-a845-3f58f8eab769
source-git-commit: 6933f053e11320d8201922723879983084c52209
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 0%

---

# Dynamic Media에서 핫링크 보호 활성화 {#activating-hotlink-protection-in-dynamic-media}

핫 링크는 타사 웹 사이트에서 HTML 코드를 사용하여 웹 사이트의 이미지를 표시하는 경우입니다. 방문자의 브라우저가 사용자의 서버에서 직접 그림을 액세스하고 있으므로 사진이 요청될 때마다 대역폭을 사용합니다. Hotlink *보호*&#x200B;는 다른 웹 사이트가 웹 페이지에서 사진, CSS 또는 JavaScript™에 직접 연결하지 않도록 하는 방법입니다. 이러한 종류의 차드는 Dynamic Media 계정에서 불필요한 대역폭 사용을 줄이는 데 도움이 됩니다.

[Adobe 고객 ](https://helpx.adobe.com/support.html) 지원 센터는 CDN 수준에서 레퍼러 필터를 구성할 수 있습니다. 이렇게 하면 도메인에 대해 허용되는 웹 사이트 목록의 웹 사이트에만 Dynamic Media 컨텐츠가 제공됩니다.

>[!NOTE]
>
>이 기능을 사용하려면 Adobe Experience Manager Dynamic Media과 함께 번들로 제공되는 기본 CDN을 사용해야 합니다. 다른 모든 사용자 지정 CDN은 이 기능에서 지원되지 않습니다. 핫링크 보호를 활성화하려면 관리자가 Dynamic Media 계정에 대한 구성 변경을 요청하려면 지원 티켓을 만들어야 합니다. 핫 링크 보호 활성화를 위한 추가 비용은 없습니다.
