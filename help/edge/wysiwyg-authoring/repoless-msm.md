---
title: 복수 사이트 관리 무시
description: 단일 코드 베이스를 리디렉션 방식으로 활용하여 다국어 사이트를 사용하는 프로젝트를 설정하는 방법에 대한 모범 사례 권장 사항에 대해 알아봅니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: 02957fb8671d953a683ebd6e168979b11ad391c4
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# 복수 사이트 관리 무시 {#repoless-msm}

이 문서에서는 사용자가 이미 `my-aem-site` 프로젝트에 대한 기본 사이트를 만들었으며 AEM의 MSM 기능을 사용하여 이를 현지화하려고 한다고 가정합니다.

리디렉션 사용 사례에 대해 이미 프로젝트를 설정한 경우 루트 페이지 `/content/my-aem-site` 수준에서 클라우드 구성이 할당됩니다. 다국어 사이트의 경우 이 구성 할당을 `/content/my-aem-site/language-master/de`과(와) 같은 언어 루트로 변경해야 합니다.

