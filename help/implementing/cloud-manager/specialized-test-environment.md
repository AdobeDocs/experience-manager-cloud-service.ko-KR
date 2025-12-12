---
title: 특수 테스트 환경 추가
description: Cloud Manager의 전문 테스트 환경이 스트레스 테스트 및 고급 배포 전 검사에 이상적인, 프로덕션에 가까운 조건에서 기능을 확인할 수 있는 전용 공간을 제공하는 방법에 대해 알아봅니다.
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 815fb5c3-a171-4531-8727-b79183d85f06
source-git-commit: 837f1d0eb0bd0f8cf8c0e283db823255f4e53ae1
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 12%

---

# 특수 테스트 환경 추가{#add-special-test-enviro}

<!-- badge: label="Private beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
-->

>[!NOTE]
>
>이제 전문 테스트 환경을 구입할 수 있습니다. 주문하려면 Adobe 담당자에게 문의하십시오.


전문 테스트 환경은 만들 수 있는 새로운 유형의 Cloud Manager 환경입니다. UAT(사용자 승인 테스트) 및 성능 유효성 검사와 같은 고급 사용 사례를 지원하도록 설계되었습니다. 기존 개발, 신속한 개발 또는 스테이징 환경과 달리 전문 테스트 환경은 프로덕션 배포 파이프라인 외부에서 작동합니다. 따라서 프로덕션 워크플로에 대한 간섭을 방지하기 위해 엄격한 격리를 유지하면서 보다 큰 유연성을 제공합니다.

특수 테스트 환경은 일반적인 스테이징 환경의 크기, 확장성 및 구성을 미러링하도록 구축됩니다. 이 접근 방식을 사용하면 전문 테스트 환경에서 수행된 테스트를 통해 코드와 컨텐츠가 프로덕션과 유사한 조건에서 수행되는 방식에 대한 현실적인 통찰력을 얻을 수 있습니다. 또한 프로덕션 또는 스테이지에서 직접 콘텐츠 복사를 지원합니다. 또한 배포 워크플로, 액세스 제어 및 네트워크 구성 측면에서 개발 환경과의 동등성을 유지합니다.

## 전문 테스트 환경의 주요 기능 및 구성 {#key-features}

| 범주 | 비헤이비어 |
| --- | --- |
| 목적 | UAT 및 성능 테스트. |
| 파이프라인 유형 | 프로덕션 파이프라인에는 없습니다. |
| 환경 크기 | 스테이지 환경과 일치합니다. |
| 격리 | 다른 환경에서 완전히 격리됩니다. |
| 코드 파이프라인 | 개발 환경(유효성 검사, 빌드, 배포)과 동일합니다. |
| 콘텐츠 복사 | 프로덕션, 스테이징 또는 특수 테스트 환경에서 허용됩니다. |
| 콘텐츠 복원 | 개발 환경과 동일합니다. |
| 액세스 로그 | 개발 환경과 동일합니다. |
| Developer Console | 개발 환경과 동일합니다. |
| `IP Allow List` | 개발 환경과 동일합니다. |
| 네트워킹 | 개발 환경(서비스, 도메인 이름, SSL 인증서, 고급 네트워크)과 동일합니다. |

[환경 관리](/help/implementing/cloud-manager/manage-environments.md)도 참조하세요.

## 특수 테스트 환경 추가 {#add-specialized-testing-environment}

환경을 추가하거나 편집하려면 사용자가 **비즈니스 소유자** 역할의 멤버여야 합니다.

**특수 테스트 환경을 추가하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 환경을 추가할 프로그램을 클릭합니다.

1. 다음 중 하나를 수행하십시오.

   * **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔의 **환경** 카드에서 **환경 추가**&#x200B;를 클릭합니다.
**환경 추가** 옵션이 흐리게 표시(사용 안 함)되면 사용 권한이 없거나 사용 허가된 리소스에 종속되어 있을 수 있습니다.

     ![환경 카드](assets/no-environments.png)

   * 왼쪽 패널에서 ![데이터 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **환경**&#x200B;을 클릭한 다음 오른쪽 상단 모서리의 환경 페이지에서 **환경 추가**&#x200B;를 클릭합니다.

     ![환경 탭](assets/environments-tab.png)

1. **환경 추가** 대화 상자에서 다음 작업을 수행합니다.

   * **특수 테스트 환경**&#x200B;을 클릭합니다.
   * **이름** 환경을 제공하십시오. 환경이 생성된 후에는 환경 이름을 변경할 수 없습니다.
   * (선택 사항) 환경에 대해 **설명**&#x200B;을 제공합니다.
   * 드롭다운 목록에서 **기본 영역**&#x200B;을(를) 선택하십시오. 특수화된 테스트 환경의 기본 영역(예: *영국(남부)*)이 잠겨 있으므로 변경할 수 없습니다.

     ![전문화된 테스트 환경 라디오 버튼이 선택된 환경 추가 대화 상자](assets/specialized-test-environment.png)

1. **저장**&#x200B;을 클릭합니다.

   이제 **개요** 페이지에 **환경** 카드에 새 환경이 표시됩니다. 이제 새 환경에 대한 파이프라인을 설정할 수 있습니다.

## 추가 리소스 {#additional-resources}

* 비디오: [AEM Cloud Manager의 환경 유형 이해](https://experienceleague.adobe.com/en/perspectives/cloud-manager-environment-types)
* [환경 관리](/help/implementing/cloud-manager/manage-environments.md)

