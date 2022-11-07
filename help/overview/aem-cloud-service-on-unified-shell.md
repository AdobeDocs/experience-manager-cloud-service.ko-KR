---
title: 통합 쉘의 AEM as a Cloud Service
description: 통합 쉘의 AEM as a Cloud Service
exl-id: ea739307-dc99-4621-a239-dbe60ab6b52e
source-git-commit: 5d9acdd9b6a377a7509e0638984cb40983fa6652
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 84%

---

# 통합 쉘의 AEM as a Cloud Service {#aem-as-a-cloud-service-on-unified-shell}

>[!NOTE]
>이 기능은 2022년 7월 프리릴리스 채널에 있습니다.
>
>이는 2022년 8월 릴리스에서 일반적으로 사용할 수 있는 새로운 기능을 소개하기 위한 것입니다.
>
>환경에 맞는 기능을 활성화하는 방법에 대한 자세한 내용은 [프리릴리스 채널 설명서](/help/release-notes/prerelease.md#enable-prerelease)를 참조하십시오.

## 개요 {#overview}

AEM as a Cloud Service(작성자 서비스)는 사용자 경험을 향상하고 다른 모든 Experience Cloud 애플리케이션과 통합할 수 있도록 통합 셸과 통합됩니다. 이 통합의 영향은 아래와 같이 애플리케이션의 상단 헤더에서 볼 수 있습니다.

![이미지](/help/overview/assets/unifiedshell_header.png)

이에 대한 이점은 다음과 같습니다.

* 모든 Experience Cloud 애플리케이션 간 SSO(Single Sign-On)
* 간편한 조직 간 전환 또는 다른 애플리케이션으로의 전환
* 제품 도움말 개선
* 문제를 보고하거나 Adobe와 아이디어를 공유할 수 있는 간편한 제품 내 피드백 버튼
* AEM as a Cloud Service에 대한 알림뿐 아니라 글로벌 제품 공지 및 알림에 액세스할 수 있습니다

## 통합 쉘 비활성화 {#disabling-unified-shell}

기본적으로 AEM as a Cloud Service에서는 통합 쉘이 활성화되어 있습니다. 그러나 최상위 헤더를 맞춤화한 경우 맞춤화와 관련된 문제를 방지하기 위해 통합 쉘을 비활성화하는 것이 좋습니다. 통합 쉘을 비활성화하려면 아래 단계를 따르십시오.

>[!NOTE]
>관리 권한이 있는 계정으로만 통합 셸을 비활성화할 수 있습니다.

1. **도구 - 클라우드 서비스**&#x200B;로 이동합니다.

   관리자는 아래와 같이 통합 쉘 구성 카드를 볼 수 있습니다.

   ![이미지](/help/overview/assets/unifiedshell2.png)

1. **통합 쉘 구성**&#x200B;을 클릭합니다. 그런 다음 아래 표시된 확인란을 선택 해제하여 통합 쉘을 비활성화합니다.

   ![이미지](/help/overview/assets/unifiedshell3.png)

## 어두운 테마로 변경 {#changing-to-dark-theme}

어두운 테마로 변경하려면 프로필 아이콘을 클릭합니다. 아래와 같이 팝업이 표시됩니다. 토글을 사용하여 통합 쉘의 어두운 테마로 전환할 수 있습니다.

>[!INFO]
>
>어두운 테마는 통합 쉘(상단 막대)에만 적용됩니다.

![이미지](/help/overview/assets/unifiedshell4.png)


## AEM 받은 편지함 액세스 {#accessing-the-aem-inbox}

AEM 받은 편지함은 통합 쉘에서 벨 아이콘을 클릭하여 액세스할 수 있습니다.

>[!INFO]
>
> 벨 아이콘에 표시된 숫자는 해당 IMS 조직 내의 모든 솔루션에서 읽지 않은 알림과 AEM 받은 편지함에 나열된 작업을 포함합니다.

![이미지](/help/overview/assets/unifiedshell5.png)

팝업에서 [받은 편지함] 버튼을 클릭하여 AEM 받은 편지함으로 이동합니다.

![이미지](/help/overview/assets/unifiedshell6.png)
