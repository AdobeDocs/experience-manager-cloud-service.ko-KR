---
title: '샌드박스 프로그램 소개 '
description: 샌드박스 프로그램은 프로덕션 프로그램과 어떻게 다른지 알아봅니다.
exl-id: 4606590c-6826-4794-9d2e-5548a00aa2fa
source-git-commit: b74a0dbb1c9fdb74941f7b71bed9215853b63666
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---


# 샌드박스 프로그램 소개 {#sandbox-programs}

샌드박스 프로그램은 프로덕션 프로그램과 어떻게 다른지 알아봅니다.

## 소개 {#introduction}

샌드박스 프로그램은 일반적으로 교육, 데모 실행, 지원 또는 개념 증명(POC)의 목적을 위해 만들어지므로 라이브 트래픽을 전달하지 않습니다.

샌드박스 프로그램은 AEM Cloud Service에서 사용할 수 있는 두 가지 프로그램 중 하나이며 다른 프로그램은 [프로덕션 프로그램.](introduction-production-programs.md) 문서를 참조하십시오 [프로그램 및 프로그램 유형 이해](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) 프로그램 유형에 대해 자세히 알아보십시오.

## 자동 만들기 {#auto-creation}

샌드박스 프로그램 기능은 자동 생성 기능을 제공합니다. 새 샌드박스 프로그램을 생성할 때마다 Cloud Manager는 자동으로 다음을 수행합니다.

* 프로그램에서 솔루션으로 AEM Sites 및 AEM Assets을 추가합니다.
* 을 기반으로 샘플 프로젝트를 사용하여 프로젝트 git 리포지토리 설정 [AEM 프로젝트 원형.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)
* 개발 환경을 만듭니다.
* 개발 환경에 배포되는 비프로덕션 파이프라인을 만듭니다.

샌드박스 프로그램에는 하나의 개발 환경만 있습니다.

## 제한 사항 및 조건 {#limitations}

라이브 트래픽에 전용되지 않으므로 샌드박스 프로그램에는 프로덕션 프로그램과 구별되는 사용에 대한 특정 제한 사항과 조건이 있습니다.

### 라이브 트래픽 없음 {#live-traffic}

샌드박스 프로그램은 라이브 트래픽을 전달하기 위한 것이 아니므로 [AEM as a Cloud Service 약정.](https://www.adobe.com/legal/service-commitments.html)

### 자동 크기 조절 없음 {#auto-scaling}

샌드박스 프로그램에서 만든 환경은 자동 크기 조절을 위해 구성되지 않습니다. 따라서 이러한 환경은 성능 또는 로드 테스트에 적합하지 않습니다.

### 사용자 지정 도메인 또는 IP 허용 목록 없음 {#ip-allow}

사용자 지정 도메인 및 IP 허용 목록은 샌드박스 프로그램에서 사용할 수 없습니다.

### 수동 AEM 업데이트 {#updates}

AEM 업데이트는 자동으로 샌드박스 프로그램에 푸시되지 않지만 샌드박스 프로그램의 환경에 수동으로 적용할 수 있습니다.

* 타깃팅된 환경에 올바르게 구성된 파이프라인이 있는 경우에만 수동 업데이트를 실행할 수 있습니다.
* 프로덕션 또는 스테이징 환경에 대한 수동 업데이트는 다른 프로덕션 환경을 자동으로 업데이트합니다. 프로덕션+스테이지 환경 세트는 동일한 AEM 릴리스에 있어야 합니다.

문서를 참조하십시오 [AEM 버전 업데이트](/help/implementing/deploying/aem-version-updates.md) 자세한 내용

문서를 참조하십시오 [환경 업데이트](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment) 환경 업데이트 방법을 알아봅니다.

### 최대 절전 모드 및 삭제 {#hibernation}

샌드박스 프로그램의 환경은 8시간 동안 활동이 없으면 자동으로 최대 절전 모드로 전환됩니다. 최대 절전 모드까지 제공되면, 수동면까지 해제될 수 있습니다.

샌드박스 프로그램은 연속 최대 절전 모드 6개월 후 삭제되며 그 후 다시 생성할 수 있습니다.

자세한 내용은 [최대 절전 모드 및 최대 절전 모드 해제 샌드박스 환경](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/hibernating-environments.md) 자세한 내용
