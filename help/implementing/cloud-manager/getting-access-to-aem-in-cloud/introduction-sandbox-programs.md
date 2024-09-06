---
title: 샌드박스 프로그램 소개
description: 샌드박스 프로그램이 무엇이며 프로덕션 프로그램과 어떻게 다른지 알아봅니다.
exl-id: 4606590c-6826-4794-9d2e-5548a00aa2fa
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 17306cf0877513d1412ffba311bd5d601edec062
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 32%

---


# 샌드박스 프로그램 소개 {#sandbox-programs}

샌드박스 프로그램이 무엇이며 프로덕션 프로그램과 어떻게 다른지 알아봅니다.

## 소개 {#introduction}

샌드박스 프로그램은 일반적으로 교육, 데모 실행, 지원, POC(Proof Of Concepts) 목적으로 만들어지며 라이브 트래픽을 전달하기 위한 것이 아닙니다.

샌드박스 프로그램은 AEM Cloud Service에서 사용할 수 있는 두 가지 유형의 프로그램 중 하나이며 다른 하나는 [프로덕션 프로그램](introduction-production-programs.md)입니다. 프로그램 유형에 대한 자세한 내용은 [프로그램 및 프로그램 유형 이해](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)를 참조하십시오.

## 자동 생성 {#auto-creation}

샌드박스 프로그램에는 자동 생성 기능이 있습니다. [샌드박스 프로그램을 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)할 때마다 Cloud Manager은 자동으로 다음 작업을 수행합니다.

* AEM Sites, Assets 및 Edge Delivery Services을 프로그램에 기본 솔루션으로 추가합니다.

  ![샌드박스용 솔루션 및 추가 기능 선택](assets/sandbox-solutions-add-ons.png)

* [AEM Project Archetype](https://experienceleague.adobe.com/ko/docs/ experience-manager-core-components/using/developing/archetype/overview)을(를) 기반으로 하는 샘플 프로젝트로 프로젝트 git 저장소를 설정합니다.
* 개발 환경을 만듭니다.
* 개발 환경에 배포하는 비프로덕션 파이프라인을 만듭니다.

샌드박스 프로그램에는 개발 환경이 하나만 있습니다.

## 제한 사항 및 조건 {#limitations}

샌드박스 프로그램은 라이브 트래픽을 위한 것이 아니기 때문에 프로덕션 프로그램과 구별되는 특정 사용 제한 사항 및 조건이 있습니다.

| 제한/조건 | 설명 |
| --- | --- |
| 라이브 트래픽 없음 | 샌드박스 프로그램은 라이브 트래픽을 전달하기 위한 것이 아니므로 [AEM as a Cloud Service 약정](https://www.adobe.com/legal/service-commitments.html)이 적용되지 않습니다. |
| 자동 확장 없음 | 샌드박스 프로그램에서 생성된 환경은 자동 확장을 위해 구성되지 않습니다. 따라서 이러한 환경은 성능 또는 부하 테스트에 적합하지 않습니다. |
| 사용자 정의 도메인 또는 IP 허용 목록 없음 | [사용자 지정 도메인](/help/implementing/cloud-manager/custom-domain-names/introduction.md) 및 [IP 허용 목록](/help/implementing/cloud-manager/ip-allow-lists/introduction.md)은(는) 샌드박스 프로그램에서 사용할 수 없습니다. |
| 추가 게시 영역 없음 | [추가 게시 영역](/help/operations/additional-publish-regions.md)은(는) 샌드박스 프로그램에서 사용할 수 없습니다. |
| No 99.99% SLA | [99.99% SLA](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla)은(는) 샌드박스 프로그램에 적용되지 않습니다. |
| 고급 네트워킹 없음 | [고급 네트워킹 기능](/help/security/configuring-advanced-networking.md)(예: VPN, 비표준 포트, 전용 송신 IP 주소 등의 셀프서비스 프로비저닝)은 샌드박스 프로그램에서 사용할 수 없습니다. |
| 자동 AEM 업데이트 없음 | AEM 업데이트는 샌드박스 프로그램에 자동으로 푸시되지 않지만 샌드박스 프로그램의 환경에 수동으로 적용할 수 있습니다.<br>· 대상 환경에 적절하게 구성된 파이프라인이 있는 경우에만 수동 업데이트를 실행할 수 있습니다.<br>· 프로덕션 또는 스테이징 환경 중 하나를 수동으로 업데이트하면 자동으로 다른 하나도 업데이트됩니다. 프로덕션+스테이징 환경 세트는 동일한 AEM 릴리스에 있어야 합니다.<br>자세한 내용은 [AEM 버전 업데이트](/help/implementing/deploying/aem-version-updates.md)를 참조하세요.<br>환경을 업데이트하는 방법은 [환경 업데이트](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment)를 참조하세요. |
| 기술 지원 없음 | 샌드박스 프로그램은 일반적으로 교육, 데모 실행, 활성화 또는 POC(개념 증명) 목적으로 만들어지므로 샌드박스 프로그램에서 발생하는 문제에 대해서는 기술 지원을 사용할 수 없습니다.<br>샌드박스 프로그램을 만들고 관리하는 데 문제가 있는 경우 이러한 문제는 기술 지원 범위에 포함됩니다. |
| 최대 절전 모드 및 삭제 | 샌드박스 프로그램의 환경은 8시간 동안 비활성 상태인 경우 자동으로 절전 모드로 전환됩니다. 샌드박스 환경은 6개월 연속 절전 모드 후에 삭제됩니다.<br>환경의 최대 절전 모드 해제 및 자동 샌드박스 삭제 방법에 대한 자세한 내용은 [샌드박스 환경의 최대 절전 모드 설정 및 해제](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/hibernating-environments.md)를 참조하십시오. |
