---
title: Cloud Manager에서의 Edge Delivery Services 소개
description: Edge Delivery Services를 사용하여 Cloud Manager 프로젝트를 게재하는 방법을 알아보십시오.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: ac918008c3f99d74e01be59c9841083abf3604aa
workflow-type: ht
source-wordcount: '819'
ht-degree: 100%

---


# Cloud Manager에서의 Edge Delivery Services 소개 {#edge-delivery-services}

Edge Delivery Services는 웹 사이트에서 콘텐츠를 작성하는 방법을 보다 유연하게 제공하는 구성 가능한 서비스 세트입니다. 이 기능을 사용하면 다음과 같은 작업을 수행할 수 있습니다.

* 완벽한 Lighthouse 점수로 빠른 사이트를 만듭니다.
* 운영 원격 측정을 통해 성능을 지속적으로 모니터링합니다.
* 콘텐츠 소스를 분리하여 작성 효율성을 높입니다.

범용 편집기를 사용하는 AEM 콘텐츠 관리 및 WYSIWYG 작성과 문서 기반 작성을 모두 사용할 수 있습니다.

AEM as a Cloud Service의 Cloud Manager를 사용하면 프로젝트에 Edge Delivery Service를 활성화할 수 있습니다.

>[!TIP]
>
>Edge Delivery Services에 대한 자세한 내용과 AEM에서 사용할 수 있는 방법은 [Edge Delivery Services 개요](/help/edge/overview.md)를 참조하십시오.

## Cloud Manager에서의 Edge Delivery Services 정보 {#edge-in-cloud-manager}

Adobe Experience Manager Sites의 일부로 Edge Delivery Services에 라이선스를 부여한 경우, Cloud Manager에서 Edge Delivery Services를 통해 사이트를 직접 온보딩하고 [안내식 셀프서비스 경험을 사용하여](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) 라이브로 전환할 수 있습니다.

또한 모든 AEM 속성을 관리하는 동시에 주요 워크플로 간에 일관성을 보장하는 통합 환경에 액세스할 수 있습니다. 이 워크플로에는 도메인 이름 관리, SSL 인증서 관리 및 CDN 매핑이 포함됩니다.

## Edge Delivery Services에 대한 Adobe 권장 경로 사용의 이점 {#recommended-path-eds}

Cloud Manager를 통해 Edge Delivery Services 라이선스에 액세스하고 이를 활용하여 Adobe의 이점을 최대한 누릴 수 있습니다. 이를 통해 몇 가지 주요 이점을 활용할 수 있습니다.

* [선택한 프로그램에서 라이선스를 사용하거나](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md) [다른 프로그램을 업데이트하거나](/help/implementing/cloud-manager/edge-delivery/manage-edge-delivery-sites.md), 두 가지 모두를 수행할 수 있습니다.
* CRUD(만들기, 읽기, 업데이트, 삭제) 작업을 수행할 때 [API 우선](https://developer.adobe.com/experience-cloud/experience-manager-apis/)의 이점을 활용할 수 있습니다.
* [SLA 보고서 액세스](/help/implementing/cloud-manager/reports/report-sla.md)
* 등록된 프로덕션 프로그램에 대한 [Adobe 지원에 액세스합니다.](/help/edge/overview.md#support-ticket)

Edge Delivery Services (EDS) 라이선스가 있는 경우 Edge Delivery 사이트에 대해 [Adobe 관리형 CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn)을 사용할 수 있습니다. 이렇게 하면 인증서를 삭제하지 않는 한 3개월마다 자동으로 갱신되는 셀프서비스 CDN 관리 및 DV 인증서가 활성화됩니다.

또는 Edge Delivery Services 라이선스와 관계없이 CDN(즉, Adobe에서 관리하지 않는 CDN)을 사용하려는 경우, `aem.live` 플랫폼에서 이를 구성해야 합니다. [BYO CDN 설정](https://www.aem.live/docs/byo-cdn-setup)을 참조하십시오.


## 프로덕션 프로그램 또는 샌드박스 프로그램에 Edge Delivery Services 추가에 대한 정보

Edge Delivery Services는 프로젝트를 시작한 방식 또는 사이트를 만들고자 하는 시기에 따라 다양한 방식으로 추가할 수 있습니다.

| 사용 사례 | 설명 |
| --- | --- |
| 새 프로덕션 프로그램에 Edge Delivery Services를 추가하려고 합니다. | [프로덕션 프로그램 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)를 참조하십시오.<br>마법사의 **솔루션 및 추가 기능** 탭에서 **Edge Delivery Services**&#x200B;를 선택합니다. |
| 기존 프로덕션 프로그램에 Edge Delivery Services를 추가하려고 합니다. | [프로그램 편집](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md)을 참조하십시오.<br>**프로그램 편집** 대화 상자의 **솔루션 및 추가 기능** 탭 아래에서 **Edge Delivery Services**&#x200B;를 선택합니다. |
| Cloud Manager에 Edge Delivery 사이트를 추가하려고 합니다. | [Edge Delivery 사이트 추가](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md)를 참조하십시오. |
| 지금 Edge Delivery 사이트를 만들려고 합니다. | [버튼 클릭만으로 Cloud Manager에서 Edge Delivery 사이트를 빠르게 만들기](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md)를 참조하십시오. |
| 새 샌드박스 프로그램이나 기존 샌드박스 프로그램에 Edge Delivery Services를 추가하려고 합니다. | [샌드박스 프로그램 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)를 참조하십시오.<br>샌드박스 프로그램을 만들면 Edge Delivery Services가 기본적으로 프로그램에 추가되므로 선택할 필요가 없습니다.<br>Edge Delivery가 일반적으로 제공되기 전의 기존 샌드박스 프로그램은 Edge Delivery Services를 자동으로 상속합니다. |

>[!NOTE]
>
>* 프로그램을 추가하거나 편집하려면 **비즈니스 소유자** 역할의 멤버이거나 권한이 부여되어야 합니다.
>* 조직에서 사용하지 않는 Edge Delivery Services 라이선스가 있어야 프로덕션 프로그램에 적용할 수 있습니다.
>* Edge Delivery Services 라이선스가 프로그램에 적용되거나 프로그램에서 제거되면 파이프라인을 실행할 필요 없이 변경 사항이 즉시 적용됩니다.


## Cloud Manager에서의 Edge Delivery 할 일 목록 정보 {#ed-todo-list}

<!-- &#x2460; for "1" inside circle -->

**Cloud Manager에서의 Edge Delivery 할 일 목록**&#x200B;은 온보딩 작업 체크리스트로, Edge Delivery 사이트를 [Go-Live](/help/journey-onboarding/go-live-checklist.md)까지 온보딩하고 관리할 수 있도록 안내합니다.

![Cloud Manager의 Edge Delivery 사이트에서 할 일 목록.](/help/implementing/cloud-manager/assets/cm-eds-todo-list.png)

|   | 작업 | 설명 |
| --- | --- | --- |
| 1 | 제품 공동 작업 채널 가입 | **요청 제출하기**&#x200B;를 클릭하면 Adobe에 귀사를 위한 채널을 만들기 위한 요청이 제출됩니다. 채널이 이미 존재하는 경우 귀사 채널로 연결됩니다. |
| 2 | 사전 요구 사항 완료 | [시작하기 튜토리얼 보기](https://www.aem.live/developer/tutorial)를 참조하십시오. |
| 3 | Edge Delivery 사이트 추가 또는 <br>지금 사이트 만들기 | [Edge Delivery 사이트 추가](#eds-add-site)를 참조하십시오.<br>[Cloud Manager에서 Edge Delivery 사이트 만들기](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md)를 참조하십시오. |
| 4 | 외부 Git 저장소를 사용하도록 Edge Delivery 사이트 구성 | [외부 Git 저장소를 사용하도록 Edge Delivery 사이트 구성](/help/implementing/cloud-manager/edge-delivery/config-edge-delivery-site-with-byog.md)을 참조하십시오. |
| 5 | 도메인 추가 | [사용자 정의 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하십시오. |
| 6 | SSL 인증서 추가 | [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)를 참조하십시오. |
| 7 | Edge Delivery 사이트의 CDN 구성 | [도메인 매핑 추가](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md)를 참조하십시오. |
| 8 | 푸시 유효성 검사 설정 | [Edge Delivery 사이트에 대한 푸시 유효성 검사 설정](/help/implementing/cloud-manager/edge-delivery/cdn-setup-push-invalidation.md)을 참조하십시오. |
| 9 | 실행 | [실행 체크리스트](https://www.aem.live/docs/go-live-checklist)를 참조하십시오. |

>[!VIDEO](https://video.tv.adobe.com/v/3441568?learn=on&captions=kor)

## 지원 티켓 로그 {#eds-support-ticket}

{{support-ticket}}



