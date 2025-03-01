---
title: 추가 게시 지역
description: AEM as a Cloud Service가 추가 게시 지역을 지원하여 가용성을 높이고 지연 시간을 줄이는 방법에 대해 알아봅니다.
exl-id: b9ac3c6a-eb8b-461d-8f1d-a0356046a3f9
feature: Operations
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 71%

---


# 추가 게시 지역 {#additional-publish-regions}

AEM Sites로 설정된 프로그램에서 추가 게시 지역에 라이선스를 부여하고 해당 지역을 활성화할 수 있습니다. 구성되면 스테이지 및 프로덕션 환경의 트래픽을 여러 게시 팜으로 라우팅하여 다음과 같은 이점을 얻을 수 있습니다.

* 지연 시간 단축 - CDN에서 AEM 게시 인스턴스로 라우팅되는 요청을 가장 가까운 게시 지역으로 리디렉션하므로 사용자는 여러 지역에서 웹 사이트와 애플리케이션을 방문하는 것이 유리합니다.
* 높은 가용성 - 지역을 사용할 수 없는 경우 CDN은 트래픽을 디렉션하여 사용 가능한 다른 지역으로 보냅니다.

조직은 최대 세 개의 추가 게시 지역에 라이선스를 부여할 수 있습니다.

>[!NOTE]
>
>* 이 기능은 Sites 및 Forms 솔루션에 사용할 수 있습니다.
>* 이 기능은 [샌드박스 프로그램](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md)에 적용할 수 없습니다.
>* 이 기능을 사용하려면 프로그램을 AEM 릴리스 버전 12142 이상으로 업데이트해야 합니다.

## 사용 사례 {#use-cases}

다음은 추가 게시 지역 라이선싱을 통해 조직이 활용할 수 있는 몇 가지 사용 사례입니다.

1. 조직이 기본 지역과 멀리 떨어져 있는 사용자로부터 비즈니스에 중요한 트래픽을 수신하는 경우 추가 게시 지역은 해당 방문자가 경험하는 지연 시간을 단축할 수 있습니다.
1. 조직이 사이트 부재로 금전적인 손해가 발생하거나 평판에 손상을 입을 경우 추가 게시 지역을 사용하면 AEM 게시 계층은 지역 오류에 대해 보다 탄력적으로 대응할 수 있습니다.
1. 조직의 콘텐츠 작성자가 다수의 게시 계층 방문자와 멀리 떨어진 지역에 있는 경우 기본 지역은 콘텐츠 작성자 위치 근처에서 선택할 수 있지만, 추가 게시 지역은 두 대상자가 최적화된 경험을 활용하도록 게시 측 트래픽 근처에서 구성할 수 있습니다.

## 활성화 및 구성 {#enabling-and-configuring}

추가 게시 지역에 라이선스가 부여되면 Cloud Manager를 사용하여 지역을 구성합니다. 세부 지침은 [Cloud Manager 설명서](/help/implementing/cloud-manager/manage-environments.md#multiple-regions)를 참조하십시오.

추가 게시 지역은 스테이지 및 프로덕션 환경에만 적용되지만 RDE 또는 개발 환경에는 적용되지 않습니다.

지역을 사용할 수 없는 경우 Adobe CDN에서 관리하므로 고객이 사용 가능한 지역으로의 트래픽 라우팅을 관리할 필요가 없습니다.

아래 고급 네트워킹 고려 사항 섹션에 설명된 대로, 지역을 사용할 수 없게 될 경우 가용성을 유지하기 위해 고급 네트워킹을 사용하는 고객은 추가 게시 지역별로 이를 구성하는 것이 좋습니다.


## 고급 네트워킹 고려 사항 {#advanced-networking-considerations}

추가 게시 지역이 고급 네트워킹이 이미 구성된 환경에서 활성화되면 고급 네트워킹 규칙과 일치하는 추가 게시 지역의 트래픽이 기본 지역을 통해 기본적으로 라우팅합니다. 높은 가용성을 활용하려면 추가 지역에서 고급 네트워킹을 활성화하는 것이 좋습니다.

연결 손실을 발생시키지 않고도 추가 지역에 고급 네트워킹 구성을 추가하는 방법 등에 대한 자세한 내용은 고급 네트워킹 설명서의 [추가 게시 지역에 대한 고급 네트워킹 구성](/help/security/configuring-advanced-networking.md#advanced-networking-configuration-for-additional-publish-regions) 섹션을 참조하십시오.

## 로깅 {#logging}

추가 게시 영역이 활성화되면 Cloud Manager을 통해 각 영역에 대한 별도의 로그를 사용할 수 있습니다. 자세한 내용은 [로그 액세스 및 관리](/help/implementing/cloud-manager/manage-logs.md) 및 [추가 Publish 지역에 대한 로그](/help/implementing/developing/introduction/logging.md#logs-for-additional-publish-regions)를 참조하십시오.

## 제한 사항 {#limitations}

추가 게시 지역 사용 고려 시 해당 제한 사항을 고려하십시오.

* 추가 게시 영역은 AEM Sites 또는 AEM Forms에만 추가할 수 있습니다.
   * 추가 게시 영역은 동일한 프로그램에 배포된 다른 AEM 솔루션 또는 관련 기능(예: AEM Assets 또는 Adobe Learning Manager)으로 확장되지 않습니다.
   * 그러나 하나 이상의 사이트 또는 Forms 솔루션이 적용되는 한 이러한 솔루션을 프로그램에 추가할 수 있습니다.
* 추가 지역은 관련 권한이 테넌트에 사용되지 않는 경우에만 추가할 수 있습니다.
* 최대 세 개의 추가 게시 지역을 개별 환경에 추가할 수 있습니다.
* 추가 지역은 프로덕션 프로그램에서만 사용할 수 있습니다. 샌드박스 프로그램에서는 기능을 사용할 수 없습니다.
* 추가 게시 지역은 스테이지 및 프로덕션 환경에만 적용되고 RDE 또는 개발 환경에는 적용되지 않습니다.
* 추가 게시 지역에서는 프로그램을 AEM 릴리스 버전 12142 이상으로 업데이트해야 합니다.
