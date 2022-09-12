---
title: Adobe AEM Target HTTP 창
description: Adobe AEM Target HTTP 창
source-git-commit: c193b38718622cd2e960a8e8833c2d295822dc33
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 100%

---


# 소개 {#introduction}

이 페이지에서는 Adobe AEM Target HTTP 창에 있는 구성 가능한 매개변수에 대해 설명합니다.

## 매개변수 {#parameters}

![Target HTTP 창](assets/httpwindow.png "Target HTTP 창")

이 창에는 다음과 같은 구성 가능한 매개변수가 포함되어 있습니다.

| 매개변수 | 설명 |
|---|---|
| Adobe Target API URL | Adobe Target API의 URL입니다. |
| 절대 URL 활성화 | URL의 호스트 부분을 사용할지 전체 URL을 사용할지 여부를 결정합니다. 전체(생략되지 않은) URL을 사용하려면 확인란을 활성화하십시오. 이 확인란은 기본적으로 비활성화되어 있습니다. |
| 연결 시간 제한 | 연결이 설정될 때까지의 시간 제한(밀리초)입니다. 기본값은 60,000밀리초입니다. 값이 0이면 무제한으로 해석됩니다. |
| 소켓 시간 제한 | 데이터 대기 시간 또는 두 개의 연속 데이터 패킷 간 최대 비활성화 기간에 대한 제한 시간(밀리초)입니다. 기본값은 30,000밀리초입니다. |
| Adobe Target Recommendations URL 정규 표현식 토큰 바꾸기 | Target Recommandations API URL을 나타내도록 대체해야 하는 Adobe Target 끝점 URL의 토큰을 제어합니다. |
| Adobe Target Recommendations URL 토큰으로 바꾸기 | 위의 매개변수에 기재된 정규 표현식이 대체되므로 최종 URL은 Target Recommandations API를 나타냅니다. |
