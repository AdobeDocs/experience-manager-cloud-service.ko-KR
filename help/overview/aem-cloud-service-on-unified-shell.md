---
title: 통합 셸의 AEM as a Cloud Service
description: Unified Shell에서 AEM as a Cloud Service의 이점에 대해 알아봅니다.
exl-id: ea739307-dc99-4621-a239-dbe60ab6b52e
source-git-commit: 8c73805b6ed1b7a03c65b4d21a4252c1412a5742
workflow-type: ht
source-wordcount: '399'
ht-degree: 100%

---

# 통합 셸의 AEM as a Cloud Service {#aem-as-a-cloud-service-on-unified-shell}

## 개요 {#overview}

AEM as a Cloud Service(작성자 서비스)가 통합 셸과 통합되어 사용자 경험을 개선하고 다른 모든 Experience Cloud 애플리케이션과 통합합니다. 이 통합의 영향은 아래와 같이 애플리케이션의 상단 헤더에서 볼 수 있습니다.

![이미지](/help/overview/assets/unifiedshell_header.png)

이에 대한 이점은 다음과 같습니다.

* 모든 Experience Cloud 애플리케이션 간 SSO(Single Sign-On)
* 간편한 조직 간 전환 또는 다른 애플리케이션으로의 전환
* 제품 도움말 개선
* 문제를 보고하거나 Adobe와 아이디어를 공유할 수 있는 간편한 제품 내 피드백 버튼
* AEM as a Cloud Service 관련 알림과 더불어 글로벌 제품 공지 및 알림에 대한 액세스 권한

## 통합 셸 비활성화 {#disabling-unified-shell}

기본적으로 AEM as a Cloud Service에서는 통합 셸이 활성화되어 있습니다. 그러나 최상위 헤더를 맞춤화한 경우 맞춤화와 관련된 문제를 방지하기 위해 통합 셸을 비활성화하는 것이 좋습니다. 통합 셸을 비활성화하려면 아래 단계를 따르십시오.

>[!NOTE]
>관리 권한이 있는 계정에서만 통합 셸을 비활성화할 수 있습니다.

1. **도구 > 클라우드 서비스**&#x200B;를 클릭합니다.

   관리 사용자는 아래와 같이 통합 셸 구성 카드를 볼 수 있습니다.

   ![이미지](/help/overview/assets/unifiedshell2.png)

1. **통합 셸 구성**&#x200B;을 클릭합니다. 그런 다음 아래 표시된 확인란을 선택 해제하여 통합 셸을 비활성화합니다.

   ![이미지](/help/overview/assets/unifiedshell3.png)

## 어두운 테마로 변경 {#changing-to-dark-theme}

어두운 테마로 변경하려면 프로필 아이콘을 클릭합니다. 이 작업은 아래와 같이 팝오버를 표시합니다. 토글을 사용하여 통합 셸의 어두운 테마로 전환할 수 있습니다.

>[!INFO]
>
>어두운 테마는 통합 셸(상단 막대)에만 적용됩니다.

![이미지](/help/overview/assets/unifiedshell4.png)

## AEM as a Cloud Service 환경 식별 {#identify-aemaacs-environment}

AEM as a Cloud Service는 프로덕션, 스테이징 및 개발의 세 가지 유형의 환경을 제공합니다. 자세한 내용은 [환경 유형](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments.html?lang=ko)을 참조하십시오. 통합 셸과의 통합을 통해 사용자가 Author 서비스에 로그인한 환경 유형이 아래와 같이 레이블을 통해 상단 헤더에 표시됩니다.

![이미지](/help/overview/assets/unifiedshell_header_label.png)

## AEM 받은 편지함 액세스 {#accessing-the-aem-inbox}

AEM 받은 편지함은 통합 셸에서 벨 아이콘을 클릭하여 액세스할 수 있습니다.

>[!INFO]
>
> 벨 아이콘에 표시된 숫자는 해당 IMS 조직 내의 모든 솔루션에서 읽지 않은 알림과 AEM 받은 편지함에 나열된 작업을 포함합니다.

![이미지](/help/overview/assets/unifiedshell5.png)

팝오버에서 [받은 편지함] 버튼을 클릭하여 AEM 받은 편지함으로 이동합니다.

![이미지](/help/overview/assets/unifiedshell6.png)
