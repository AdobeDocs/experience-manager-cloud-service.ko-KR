---
title: Adobe AEM Target HTTP 창
description: 'Adobe AEM Target HTTP 창 '
translation-type: tm+mt
source-git-commit: c193b38718622cd2e960a8e8833c2d295822dc33
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 3%

---


# 소개 {#introduction}

이 페이지에서는 Adobe AEM Target HTTP 창에 있는 구성 가능한 매개 변수에 대해 설명합니다.

## 매개 변수 {#parameters}

![Target HTTP ](assets/httpwindow.png "WindowTarget HTTP 창")

창에는 다음과 같은 구성 가능한 매개 변수가 포함되어 있습니다.

| 매개 변수 | 설명 |
|---|---|
| Adobe Target API URL | Adobe Target API의 URL. |
| 절대 URL 활성화 | URL의 호스트 부분 또는 전체 URL이 사용되는지 확인합니다. 전체(요약되지 않은) URL을 사용하려면 확인란을 선택합니다. 기본적으로 이 확인란은 비활성화됩니다. |
| 연결 시간 초과 | 연결이 설정될 때까지 시간 초과(밀리초)입니다. 기본값은 60,000밀리초입니다. 값 0은 무한 시간 초과로 해석됩니다. |
| 소켓 시간 초과 | 데이터를 기다릴 시간 초과(밀리초)나 두 개의 연속 데이터 패킷 간 최대 비활성화 기간. 기본값은 30,000밀리초입니다. |
| Adobe Target Recommendations URL regex 토큰 대체 | Target 명령 API URL을 가리키도록 교체해야 하는 Adobe Target 끝점 URL의 토큰을 제어합니다. |
| Adobe Target Recommendations URL을 토큰으로 대체 | 위의 매개 변수에 설명된 regex를 대체하므로 결과 URL이 Target 명령 API를 가리키게 됩니다. |
