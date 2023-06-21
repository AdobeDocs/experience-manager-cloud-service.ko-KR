---
title: 화면의 비디오에 대한 썸네일 as a Cloud Service 지원
description: 이 페이지에서는 Screens의 비디오에 대한 썸네일 지원을 as a Cloud Service으로 추가하는 방법에 대해 설명합니다.
index: true
exl-id: 7b15d7cc-f089-4008-9039-5f48343a0f20
source-git-commit: cf1e2717342ca4e00780428d6ccf264bd8eca371
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 1%

---

# 비디오에 대한 썸네일 지원 {#thumbnail-support-videos}

## 소개 {#introduction}

콘텐츠 작성자는 이미지를 자리 표시자로 사용하고 적절한 팀에서 실제 비디오를 마무리하는 동안 콘텐츠 재생 및 타깃팅을 적절하게 테스트할 수 있도록 비디오의 썸네일을 정의할 수 있습니다. 비디오 재생이 실패할 경우 이미지를 사용할 수도 있습니다.

비디오 구성 요소에 썸네일 이미지에 대한 지원을 추가하면 고객은 실제 콘텐츠와 함께 채널에 유효한 구성 요소를 올바르게 추가하고, 비디오가 실제로 배달되기 전에 모든 타깃팅 구성을 수행할 수 있습니다.

>[!NOTE]
>썸네일 이미지는 비디오 구성 요소에 설정된 경우, 플레이어에서 비디오 재생 실패 시 재생됩니다. 이를 통해 원하는 메시지를 완전히 건너뛰지 않고 대상자에게 전달(콘텐츠 재생)할 수 있습니다.

썸네일 지원 기능을 사용하여 다음과 같은 작업을 수행할 수 있습니다.

* 비디오가 아직 준비되지 않았거나 플레이어에서 큰 에셋 다운로드를 테스트하지 않으려는 경우 채널 경험을 준비합니다

* 장치에서 재생 문제가 있을 경우 폴백 메커니즘을 설정합니다.

## 비디오에서 썸네일 사용 {#using-thumbnails}

>[!IMPORTANT]
>**전제 조건**
>비디오에 대한 썸네일을 사용하는 방법을 배우기 전에 Screens as a Cloud Service 프로젝트에서 채널에 대한 비디오 렌디션을 만드는 방법을 알아보십시오. 다음을 참조하십시오 [여기](/help/screens-cloud/configuring/creating-screens-video-renditions-cloud-service.md) 을 참조하십시오.

비디오에서 썸네일을 사용하려면 아래 단계를 따르십시오.

1. 기존 Screens 채널로 이동하거나 새 채널을 만듭니다.

   >[!NOTE]
   >채널을 만들고 채널에 컨텐츠를 추가하는 방법은 을 참조하십시오. [Screens에서 채널 만들기 및 as a Cloud Service 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/create-content/creating-channels-screens-cloud.html?lang=en).

1. 채널을 선택하고 을 클릭합니다. **편집** 작업 표시줄에서 을 클릭하여 편집기를 엽니다.

   ![편집기 열기](/help/screens-cloud/using-core-product-features/assets/thumbnail-1.png)

1. 아래 그림과 같이 기존 비디오 구성 요소를 추가하거나 편집합니다.

   ![구성 요소 편집](/help/screens-cloud/using-core-product-features/assets/thumbnail-2.png)

1. 비디오를 선택하고 *렌치* 아이콘을 클릭하여 비디오 속성을 엽니다.

   ![렌치를 클릭합니다.](/help/screens-cloud/using-core-product-features/assets/thumbnail-3.png)

1. 다음 **비디오** 대화 상자가 열리고 여기서 를 볼 수 있습니다 **축소판** 놓기 영역.

   ![썸네일 보기](/help/screens-cloud/using-core-product-features/assets/thumbnail-4.png)

1. 자산 선택기에서 다음으로 이미지를 끌어다 놓기 **축소판** 놓기 영역 및 클릭 **완료**.

   ![](/help/screens-cloud/using-core-product-features/assets/thumbnail-5.png)

1. 클릭 **미리 보기**.

1. 구성 요소에 비디오가 설정되어 있으면 비디오가 재생됩니다. 썸네일이 설정되어 있지 않으면 썸네일이 재생됩니다. 그렇지 않으면 구성 요소가 구성되지 않은 것으로 간주되고 건너뜁니다.

## 비디오에서 썸네일을 사용하는 동안 지원되는 사용 사례 {#understand-use-case}

비디오의 축소판은 다음과 같은 사용 사례를 지원합니다.

* 아무것도 설정되지 않은 비디오 구성 요소를 건너뜁니다.

* 썸네일 세트만 있는 비디오 구성 요소에서 썸네일을 재생합니다.

* 비디오(비디오에 올바른 렌디션이 있는 경우)와 썸네일 세트가 모두 있는 비디오 구성 요소에서 비디오를 재생합니다.

* 비디오 세트가 있는 비디오 구성 요소는 재생 오류가 발생할 경우 썸네일을 재생하거나 썸네일이 구성되지 않은 경우 다음 항목으로 건너뜁니다.
