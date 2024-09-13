---
title: Cloud Manager의 Edge Delivery Services 소개
description: Edge Delivery Services을 사용하여 Cloud Manager 프로젝트를 제공하는 방법을 알아봅니다.
exl-id: f33bd6f0-62fc-4ecc-b8d2-65d1f1c44d82
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b222b4384b1c2a21ecbb244d149ce7e51cc7990f
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 6%

---

# Cloud Manager의 Edge Delivery Services 소개 {#edge-delivery-services}

Edge Delivery Services는 웹 사이트에서 콘텐츠를 작성하는 방법을 보다 유연하게 제공하는 구성 가능한 서비스 세트입니다. 이 기능을 사용하면 다음 작업을 수행할 수 있습니다.

* 완벽한 등대 점수로 빠른 사이트를 만들 수 있습니다.
* RUM(Real Use Monitoring)을 통해 지속적으로 성능을 모니터링합니다.
* 콘텐츠 소스를 분리하여 작성 효율성을 높입니다.

범용 편집기를 사용한 AEM 컨텐츠 관리 및 WYSIWYG 작성과 문서 기반 작성을 모두 사용할 수 있습니다.

AEM as a Cloud Service의 Cloud Manager을 사용하면 프로젝트에 Edge Delivery 서비스를 활성화할 수 있습니다.

>[!TIP]
>
>Edge Delivery Services 및 AEM에서 사용할 수 있는 방법에 대한 자세한 내용은 [Edge Delivery Services 개요](/help/edge/overview.md)를 참조하십시오.

<!-- RELEASED TO GA SEPTEMBER 5, 2024
>[!NOTE]
>
>This feature is only available to [the early adopter program](/help/implementing/cloud-manager/release-notes/current.md#early-adoption). -->


## Cloud Manager Edge Delivery Services 정보 {#edge-in-cloud-manager}

Adobe Experience Manager Sites의 일부로 Edge Delivery Services 라이선스가 부여된 경우 Cloud Manager에서 직접 Edge Delivery Services을 사용하여 사이트를 온보딩하고 [가이드 셀프 서비스 환경을 사용하여](/help/implementing/cloud-manager/managing-code/private-repositories.md) 라이브로 전환할 수 있습니다.

또한 주요 워크플로 전반에서 일관성을 유지하면서 모든 AEM 속성을 관리할 수 있는 통합된 환경에 액세스할 수 있습니다. 여기에는 도메인 이름 관리, SSL 인증서 관리 및 CDN 매핑이 포함됩니다.

## 프로덕션 프로그램 또는 샌드박스 프로그램에 Edge Delivery Services 추가

프로그램을 추가하거나 편집하려면 **비즈니스 소유자** 역할의 멤버이거나 권한을 부여 받아야 합니다.

프로덕션 프로그램에 적용하려면 조직에 사용되지 않은 Edge Delivery Services 라이선스가 있어야 합니다.

>[!NOTE]
>
>Edge Delivery Services 라이센스가 프로그램에 적용되거나 프로그램에서 제거되면 파이프라인을 실행할 필요 없이 변경 사항이 즉시 적용됩니다. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

사용 사례에 따라 다음 중 하나를 수행합니다.

| 사용 사례 | 설명 |
| --- | --- |
| 새 프로덕션 프로그램에 Edge Delivery Services을 추가하고 싶습니다. | [프로덕션 프로그램 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)를 참조하십시오.<br>마법사의 **솔루션 및 추가 기능** 탭에서 **Edge Delivery Services**&#x200B;을(를) 선택합니다. |
| 기존 프로덕션 프로그램에 Edge Delivery Services을 추가하고 싶습니다. | [프로그램 편집](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md)을 참조하세요.<br>**프로그램 편집** 대화 상자의 **솔루션 및 추가 기능** 탭에서 **Edge Delivery Services**&#x200B;을(를) 선택합니다. |
| Cloud Manager에 Edge Delivery 사이트를 추가하고 싶습니다. | [Edge Delivery 사이트 추가](/help/implementing/cloud-manager/edge-delivery/add-edge-delivery-site.md)를 참조하십시오. |
| 신규 또는 기존 샌드박스 프로그램에 Edge Delivery Services을 추가하려고 합니다. | [샌드박스 프로그램 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)를 참조하십시오.<br>샌드박스 프로그램을 만들면 기본적으로 Edge Delivery Services이 프로그램에 추가됩니다. 선택할 필요가 없습니다.<br>Edge Delivery의 일반 공급 전에 기존 샌드박스 프로그램에서 Edge Delivery Services을 자동으로 상속합니다. |

## 계약된 고객에 대한 Adobe 권장 경로 {#recommended-path-eds}

계약 고객은 Cloud Manager을 통해 Edge Delivery Services 라이선스에 액세스하고 사용함으로써 Adobe의 이점을 극대화하십시오. 이 접근 방식을 사용하면 [Adobe 관리 CDN](/help/implementing/dispatcher/cdn.md#aem-managed-cdn)을 사용하고 DV 인증서 구성 및 추가를 포함한 셀프서비스 CDN 관리와 같은 주요 이점을 활용할 수 있습니다. 또한 DV 인증서가 만들어지면 Adobe은 삭제하지 않는 한 3개월마다 자동으로 갱신합니다. Adobe이 있는 Edge Delivery Services 라이선스가 없고 이러한 이점을 무시하기로 결정한 경우 고객 관리 CDN만 사용할 수 있습니다. 이 설정은 `aem.live` 플랫폼에 있어야 합니다.

AEM as a Cloud Service Sites Edge Delivery Services 라이선스와 계약을 체결한 경우 Cloud Manager에 로그인하여 다음을 수행할 수 있도록 합니다.

* 선택한 프로그램에서 라이선스를 사용합니다.
* CRUD(만들기, 읽기, 업데이트, 삭제) 작업을 수행하기 위해 [API 우선](https://developer.adobe.com/experience-cloud/experience-manager-apis/) 혜택을 활용하십시오.
<!-- REMOVED AS PER https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+Self-service+access+to+Edge+Delivery+Services+and+Adobe+Managed+CDN * Access to license dashboard and reporting -->
* SLA 보고에 액세스(*곧 제공*) <!-- ADD LINK TO IT WHEN FINALLY ADDED -->
* Adobe 지원을 받습니다. Adobe의 적절한 인식 및 지원을 위해 Cloud Manager의 프로덕션 프로그램을 통해 Edge Delivery Services 사이트가 등록되었는지 확인하십시오.


## Edge Delivery 할 일 목록 {#ed-todo-list}

**Edge Delivery 할 일 목록**&#x200B;은(는) [Go-Live](/help/journey-onboarding/go-live-checklist.md)까지 온보딩, Edge Delivery 사이트 관리 과정을 안내하는 온보딩 작업 확인 목록입니다.

![Edge Delivery 사이트 할 일 목록](/help/implementing/cloud-manager/assets/cm-eds-todo-list.png)

|  | 작업 | 설명 |
| --- | --- | --- |
| 1 | 제품 공동 작업 채널 가입 | **지금 요청 제출**&#x200B;을 클릭하면 회사에 대한 채널을 만들기 위한 Adobe 요청을 제출합니다. 채널이 이미 존재하는 경우 회사의 채널로 전달됩니다. |
| 2 | 사전 요구 사항 완료 | **시작 자습서 보기**&#x200B;를 클릭하면 [시작 - 개발자 자습서](https://www.aem.live/developer/tutorial)(으)로 이동합니다. |
| 3 | Edge Delivery 사이트 추가 | [Edge Delivery 사이트 추가](#eds-add-site)를 참조하십시오. |
| 4 | 도메인 추가 | [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하십시오. |
| 5 | SSL 인증서 추가 | [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)를 참조하십시오. |
| 6 | Edge Delivery 사이트의 CDN 구성 | [CDN 구성 추가](#add-cdn)를 참조하십시오. |

>[!VIDEO](https://video.tv.adobe.com/v/3428020?learn=on)

<!--
Edge Delivery Services can be enabled when adding a new production program or editing an existing one.

![Add production program with Edge Delivery Services](assets/add-production-program-with-edge.png)

For more information about adding programs, see the following:

* [Create Production programs](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
* [Create Sandbox programs](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) -->
