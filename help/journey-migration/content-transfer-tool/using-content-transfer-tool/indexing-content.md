---
title: 콘텐츠 마이그레이션 후 색인화
description: 마이그레이션 프로세스에서 대상 Cloud Service 인스턴스에 수집된 콘텐츠를 색인화하는 방법을 알아봅니다.
exl-id: a13d5df4-b351-410a-9336-1b34a8af21b6
source-git-commit: 0109cea1be85e647fb6c04dde4714b162bdc75a5
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 10%

---

# 콘텐츠 마이그레이션 후 색인화 {#Indexing-content}

## 색인 생성 {#aem-indexing-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_indexing"
>title="콘텐츠 색인화"
>abstract="AEM 색인화는 Cloud Service 인스턴스로 콘텐츠를 마이그레이션한 후 콘텐츠를 색인화하는 것을 의미합니다. 해당 인스턴스의 콘텐츠 검색을 지원하기 위해서는 색인화가 필요합니다."

Cloud Acceleration Manager가 Cloud Service 인스턴스로의 콘텐츠 수집을 완료했으면 사용할 준비가 되었습니다. 처음에는 콘텐츠가 색인화되지 않아 검색 가능한 콘텐츠 및 성능 저하와 같은 문제가 예상되는 불안정한 환경이 발생할 수 있습니다.
인스턴스에서 최적의 성능을 위해 마이그레이션 프로세스가 콘텐츠 인덱싱을 자동으로 시작합니다. 인덱싱 진행 상황을 모니터링하는 것 외에는 수행할 작업이 없습니다.

> 수집을 시작하는 방법에 대한 자세한 내용은 [Cloud Service에 컨텐츠 수집](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md).

다음 단계는 색인화 중에 UI에서 볼 수 있는 일반적인 흐름을 보여 줍니다. 일부 레이블은 도구 설명에 유용한 컨텍스트를 제공하므로 현재 색인화 상태에 대해 자세히 알아보려면 항목 위로 마우스를 가져갑니다.

시작하려면 Cloud Acceleration Manager 로 이동합니다. 프로젝트 카드를 클릭한 다음 컨텐츠 전송 카드를 클릭합니다. 다음으로 이동 **수집 작업**
나열된 작업을 확인하십시오.

>[!NOTE]
>수집 작업의 작업, ... 드롭다운을 사용하여 인덱싱 로그를 보거나 다운로드할 수 있습니다. 로그는 다음에서 사용할 수 있습니다.
> 인덱싱 작업이 완료된 후 &#39;인덱싱 로그&#39; 작업 섹션

### 보류 중

이는 색인 지정 작업이 시작되기 전에 수집이 실행될 때 수집 작업의 행이 표시되는 방식입니다. 사용자에게 필요한 작업이 없습니다. 어떤 이유로든 수집에 실패하면 인덱스 작업의 큐가 취소되고 시작되지 않습니다.

![이미지](/help/journey-migration/content-transfer-tool/assets-indexing/pending.png)

### 실행 중

수집이 성공하면 인덱싱 작업이 자동으로 시작됩니다. 수집 작업 행에는 AEM 색인화 상태에 대한 진행 아이콘이 표시됩니다. 기간 대화 상자를 열어 작업의 진행 상황을 확인할 수 있습니다.

![이미지](/help/journey-migration/content-transfer-tool/assets-indexing/running.png)

### 완료

인덱싱 작업이 성공하면 인스턴스를 최적의 성능으로 사용할 준비가 되었습니다. 이 시점에서 색인 지정 작업 로그를 검사하기 위해 보거나 다운로드할 수 있습니다.

![이미지](/help/journey-migration/content-transfer-tool/assets-indexing/complete.png)

### 오류수

대상 Cloud Service 인스턴스의 인덱싱이 성공할 가능성이 높습니다. 경우에 따라 실패할 수 있으며 수집 작업 행이 다음과 같이 표시됩니다. 모든 경우에 장애 상태를 마우스로 가리키면 일부 장애에 대한 세부 정보를 확인할 수 있으며, 다음 단계를 결정하는 데 도움이 되는 추가 정보를 제공할 수 있습니다. 이 시점에서 실패의 원인을 찾는 데 도움이 되도록 인덱싱 작업 로그를 보거나 다운로드할 수 있습니다. 다음 단계가 명확하지 않은 경우 Adobe 지원 센터에 문의하여 수집 및 인덱싱 로그에 대한 세부 사항을 확인하십시오.

![이미지](/help/journey-migration/content-transfer-tool/assets-indexing/failed.png)

## 다음 단계 {#whats-next}

대상 클라우드 서비스 인스턴스가 인덱싱되면 인덱싱 작업의 로그를 보고 세부 정보 및 오류를 찾을 수 있습니다.

마이그레이션이 완료되었습니다. 대상 클라우드 서비스 인스턴스의 테스트 및 유효성 검사를 시작할 수 있습니다.
