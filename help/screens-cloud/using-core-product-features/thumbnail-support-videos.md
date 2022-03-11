---
title: Screens에서 비디오에 대한 축소판 지원 as a Cloud Service
description: 이 페이지에서는 Screens에서 비디오에 대한 축소판 지원을 as a Cloud Service으로 추가하는 방법을 설명합니다.
index: true
exl-id: 7b15d7cc-f089-4008-9039-5f48343a0f20
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 1%

---

# 비디오에 대한 썸네일 지원 {#thumbnail-support-videos}

## 소개 {#introduction}

컨텐츠 작성자는 해당 팀이 실제 비디오를 마무리하는 동안 이미지를 자리 표시자로 사용하고 컨텐츠 재생 및 타깃팅을 적절히 테스트할 수 있도록 비디오의 축소판을 정의할 수 있습니다. 비디오를 재생하지 못할 경우에 이미지를 사용할 수도 있습니다.

비디오 구성 요소에서 축소판 이미지에 대한 지원을 추가하면 고객이 실제 컨텐츠와 함께 채널에 유효한 구성 요소를 제대로 추가하고 비디오가 실제로 전달되기 전에 모든 타깃팅 구성을 수행할 수 있습니다.

>[!NOTE]
>비디오 구성 요소에 설정된 경우 플레이어에서 비디오 재생 오류가 발생하는 경우 축소판 이미지가 재생됩니다. 이렇게 하면 대상자를 완전히 건너뛰는 대신 대상자(컨텐츠 재생)에게 원하는 메시지를 전달할 수 있습니다.

축소판 지원 기능을 사용하면 다음 작업을 수행할 수 있습니다.

* 비디오가 아직 준비되지 않았거나 플레이어에서 대규모 자산 다운로드를 테스트하지 않아도 되는 경우 채널 경험을 준비하십시오

* 장치에서 재생 문제가 발생할 경우 대체 메커니즘을 설정하십시오.

## 비디오에서 축소판 사용 {#using-thumbnails}

>[!IMPORTANT]
>**전제 조건**
>비디오에 축소판을 사용하는 방법을 학습하기 전에 Screens as a Cloud Service 프로젝트에서 채널에 대한 비디오 표현물을 만드는 방법을 배웁니다. 자세한 내용은 [여기](/help/screens-cloud/configuring/creating-screens-video-renditions-cloud-service.md) 자세한 내용

비디오에서 축소판을 사용하려면 아래 절차를 따르십시오.

1. 기존 스크린 채널로 이동하거나 새 채널을 만듭니다.

   >[!NOTE]
   >채널을 만들고 채널에 컨텐츠를 추가하는 방법에 대해 알려면 다음을 참조하십시오 [채널에서 as a Cloud Service 생성 및 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/create-content/creating-channels-screens-cloud.html?lang=en).

1. 채널을 선택하고 을(를) 클릭합니다 **편집** 작업 표시줄에서 편집기를 엽니다.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-1.png)

1. 아래 그림과 같이 기존 비디오 구성 요소를 추가하거나 편집합니다.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-2.png)

1. 비디오를 선택하고 을(를) 클릭합니다. *렌치* 아이콘을 클릭하여 비디오 속성을 엽니다.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-3.png)

1. 다음 **비디오** 대화 상자가 열립니다. **축소판** 드롭 영역.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-4.png)

1. 자산 선택기에서 이미지를 **축소판** 영역을 클릭하고 **완료**.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-5.png)

1. 클릭 **미리 보기**.

1. 비디오가 구성 요소에 설정된 경우 비디오가 재생됩니다. 축소판이 설정되어 있지 않으면 축소판이 재생됩니다. 그렇지 않으면 구성 요소가 구성되지 않은 것으로 간주되어 건너뜁니다.

## 비디오에서 축소판을 사용하는 동안 지원되는 사용 사례 {#understand-use-case}

비디오의 축소판은 다음 사용 사례를 지원합니다.

* 아무 것도 설정되지 않은 비디오 구성 요소는 건너뜁니다.

* 축소판 그림이 설정된 비디오 구성 요소만 축소판 그림을 재생합니다.

* 비디오가 올바르게 표현된 경우 비디오와 축소판 세트가 모두 포함된 비디오 구성 요소는 비디오를 재생합니다.

* 비디오 세트가 있는 비디오 구성 요소는 재생 오류가 발생할 경우 축소판을 재생하거나 축소판이 구성되지 않은 경우 다음 항목으로 건너뜁니다.
