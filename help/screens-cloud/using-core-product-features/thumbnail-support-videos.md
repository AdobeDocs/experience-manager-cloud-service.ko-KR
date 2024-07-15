---
title: Screensas a Cloud Service 에서 비디오에 대한 썸네일 지원
description: 이 페이지에서는 Screensas a Cloud Service 에서 비디오에 대한 썸네일 지원을 추가하는 방법에 대해 설명합니다.
index: true
exl-id: 7b15d7cc-f089-4008-9039-5f48343a0f20
feature: Developing Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 1%

---

# 비디오에 대한 썸네일 지원 {#thumbnail-support-videos}

## 소개 {#introduction}

콘텐츠 작성자는 이미지를 자리 표시자로 사용하고 적절한 팀에서 실제 비디오를 마무리하는 동안 콘텐츠 재생 및 타깃팅을 적절하게 테스트할 수 있도록 비디오의 썸네일을 정의할 수 있습니다. 비디오 재생이 실패할 경우 이미지를 사용할 수도 있습니다.

비디오 구성 요소에 썸네일 이미지에 대한 지원을 추가하면 고객은 실제 콘텐츠와 함께 채널에 유효한 구성 요소를 올바르게 추가하고, 비디오가 게재되기 전에 모든 타깃팅 구성을 수행할 수 있습니다.

>[!NOTE]
>썸네일 이미지는 비디오 구성 요소에 설정된 경우, 플레이어에서 비디오 재생 오류가 발생하면 재생됩니다. 이 워크플로우를 사용하면 컨텐츠를 완전히 건너뛸 필요 없이 원하는 메시지를 대상자에게 전달(재생)할 수 있습니다.

썸네일 지원 을 통해 다음 작업을 수행할 수 있습니다.

* 비디오가 아직 준비되지 않았거나 플레이어에서 큰 에셋 다운로드를 테스트하지 않으려는 경우 채널 경험을 준비합니다

* 장치에서 재생 문제가 있을 경우 폴백 메커니즘을 설정합니다.

## 비디오에서 썸네일 사용 {#using-thumbnails}

>[!IMPORTANT]
>**전제 조건**
>비디오에 대한 썸네일을 사용하는 방법을 배우기 전에 Screens as a Cloud Service 프로젝트에서 채널에 대한 렌디션을 만드는 방법을 알아보십시오. [Screensas a Cloud Service 에서 비디오 렌디션 만들기](/help/screens-cloud/configuring/creating-screens-video-renditions-cloud-service.md)를 참조하십시오.

비디오에서 썸네일을 사용하려면 아래 단계를 따르십시오.

1. 기존 Screens 채널로 이동하거나 채널을 만듭니다.

   >[!NOTE]
   >채널을 만들고 채널에 콘텐츠를 추가하는 방법은 [Screensas a Cloud Service 에서 채널 만들기 및 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/create-content/creating-channels-screens-cloud.html)를 참조하십시오.

1. 채널을 선택합니다. 작업 표시줄에서 **편집**&#x200B;을 클릭하여 편집기를 엽니다.


   ![작업 표시줄의 편집 단추](/help/screens-cloud/using-core-product-features/assets/thumbnail-1.png).

1. 아래 그림과 같이 기존 비디오 구성 요소를 추가하거나 편집합니다.

   ![비디오 자산의 강조 표시된 이미지](/help/screens-cloud/using-core-product-features/assets/thumbnail-2.png).

1. 아래 그림과 같이 기존 비디오 구성 요소를 추가하거나 편집합니다.

1. 비디오를 선택하고 구성(*렌치*) 아이콘을 클릭하여 비디오 속성을 엽니다.

   ![렌치로 표시된 구성 아이콘을 가리키는 화살표가 있는 선택한 비디오 자산 이미지. 도구 모음](/help/screens-cloud/using-core-product-features/assets/thumbnail-3.png)에서

1. **썸네일** 놓기 영역을 볼 수 있는 **비디오** 대화 상자가 열립니다.

   ![비디오 자산 및 썸네일 드롭박스의 이미지를 보여 주는 비디오 대화 상자](/help/screens-cloud/using-core-product-features/assets/thumbnail-4.png).

1. 자산 선택기에서 **썸네일** 놓기 영역으로 이미지를 끌어다 놓고 **완료**&#x200B;를 클릭합니다.

   ![썸네일 드롭박스에 표시된 이미지 에셋과 함께 비디오 대화 상자 뒤에 표시된 에셋 이미지 선택기](/help/screens-cloud/using-core-product-features/assets/thumbnail-5.png).

1. **미리 보기**&#x200B;를 클릭합니다.

1. 구성 요소에 비디오가 설정되어 있으면 비디오가 재생됩니다. 썸네일이 설정되어 있지 않으면 썸네일이 재생됩니다. 그렇지 않으면 구성 요소가 구성되지 않은 것으로 간주되고 건너뜁니다.

## 비디오에서 썸네일을 사용하는 동안 지원되는 사용 사례 {#understand-use-case}

비디오의 축소판은 다음과 같은 사용 사례를 지원합니다.

* 설정이 없는 비디오 구성 요소를 건너뜁니다.

* 썸네일 세트만 있는 비디오 구성 요소는 썸네일을 재생합니다.

* 비디오(비디오에 올바른 렌디션이 있는 경우)와 썸네일 세트가 모두 있는 비디오 구성 요소가 비디오를 재생합니다.

* 비디오 세트가 있는 비디오 구성 요소는 재생 오류가 있을 경우 썸네일을 재생하고, 썸네일이 구성되지 않은 경우 다음 항목으로 건너뜁니다.
