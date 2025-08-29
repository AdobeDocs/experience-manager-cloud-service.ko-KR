---
title: 적응형 Forms에 대한 사용자 지정 제출 액션의 502 오류 문제 해결
description: 적응형 Forms(핵심 구성 요소)에서 사용자 지정 제출 액션을 사용할 때 발생하는 502 오류 페이지를 식별하고 해결하는 방법을 알아봅니다. 이 안내서에서는 처리되지 않은 예외와 같은 일반적인 원인을 설명하고 해결 단계를 제공합니다.
feature: Adaptive Forms, Core Components
role: Developer
level: Intermediate
source-git-commit: 03e46bb43e684a6b7057045cf298f40f9f1fe622
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 1%

---


# 문제 해결: 사용자 지정 제출 액션의 502 오류 페이지

적응형 Forms(핵심 구성 요소)로 작업할 때 사용자 지정 제출 액션을 사용하는 양식을 제출한 후 **502 오류 페이지 HTML**&#x200B;이 발생할 수 있습니다.

## 문제

**오류:** 사용자 지정 제출 액션 서비스가 실패하면 502 오류 페이지 HTML이 표시됩니다.

**이유:** 사용자 지정 제출 작업에서 null 포인터, 잘못된 API 응답 또는 런타임 오류와 같은 처리되지 않은 오류가 발생하면 이 오류가 발생합니다.

## 해결 방법

502 오류 페이지를 방지하려면 전송 논리를 try-catch 블록으로 래핑하여 오류를 정상적으로 처리합니다.

자세한 단계는 [적응형 Forms(핵심 구성 요소)에 대한 사용자 지정 제출 액션 만들기](/help/forms/custom-submit-action-for-adaptive-forms-based-on-core-components.md)를 참조하십시오.
