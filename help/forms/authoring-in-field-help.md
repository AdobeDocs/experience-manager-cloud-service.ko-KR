---
title: AEM 적응형 Forms 필드에 대한 도움말 텍스트를 추가하는 방법
description: AEM Forms을 사용하면 상황에 맞는 도움말을 적응형 양식 필드 및 패널에 텍스트나 비디오를 비롯한 리치 미디어로 추가할 수 있습니다.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
feature: Adaptive Forms, Foundation Components
role: User
hide: true
hidefromtoc: true
source-git-commit: d661f869f1264e4a2317692ab6fd22263c89e072
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---


# 양식 필드에 대한 컨텍스트 내 도움말 작성{#authoring-in-context-help-for-form-fields}

## 소개 {#introduction}

양식을 작성하는 최종 사용자가 특정 양식 필드에 세부 정보를 작성하는 방법을 잘 모르는 경우가 있습니다. 이러한 문제를 해결하기 위해 적응형 Forms은 양식 필드에 텍스트 또는 풍부한 컨텍스트 내 도움말을 추가할 수 있는 지원을 제공합니다. 양식 채우기 경험을 개선하는 데 도움이 되며 최종 사용자의 모호성을 방지합니다.

이 문서에서는 양식 작성자가 적응형 Forms을 작성하는 동안 컨텍스트 내 도움말을 추가하는 방법에 대해 설명합니다.

## 상황에 맞는 도움말 추가 {#add-in-context-help}

사이드바의 속성 탭에 있는 도움말 콘텐츠 섹션에서 다음 옵션을 사용하여 상황별 도움말을 지정할 수 있습니다.

* [간단한 설명](authoring-in-field-help.md#p-short-description-p)
* [긴 설명](authoring-in-field-help.md#p-long-description-p)

![양식 필드에 대한 상황별 도움말](assets/descriptions.png)

>[!NOTE]
>
>긴 설명은 짧은 설명을 무시합니다. 둘 다 지정한 경우 긴 설명만 나타납니다.

### 간단한 설명 {#short-description}

간단한 설명 필드는 양식 필드 채우기에 대한 빠르고 짧은 힌트를 제공하기 위한 것입니다. 짧은 설명 필드에 지정된 텍스트는 마우스를 필드 위로 가져가면 도구 설명으로 표시됩니다.

![양식 필드에 대한 상황별 도움말을 추가하는 방법에 대한 간단한 설명](assets/tooltip.png)

>[!NOTE]
>
>필드 아래에 도움말 텍스트를 영구적으로 표시하려면 **항상 간단한 설명 표시**&#x200B;를 선택하십시오.

![필드 아래의 컨텍스트에 맞는 도움말에 영구적 추가](assets/short1.png)

### 긴 설명 {#long-description}

긴 설명 필드를 사용하여 긴 텍스트를 지정하거나 비디오 등 리치 미디어 콘텐츠를 컨텍스트 내 도움말로 포함할 수 있습니다. 예를 들어 다음 이미지는 컨텍스트 내 도움말로서 비디오를 포함할 수 있는 방법을 보여 줍니다.

![양식 필드에 대한 컨텍스트 내 도움말로 리치 미디어 추가](assets/long-descriptions.png)

긴 설명을 추가하면 **이(가) 표시됩니까?필드 옆의** 아이콘. 아이콘을 클릭하면 긴 설명 섹션에 추가된 콘텐츠가 표시됩니다.

![상황에 맞는 리치 미디어 도움말의 예](assets/photoshop.png)

### 패널 수준 도움말 {#panel-level-help}

양식 필드에 대한 컨텍스트 내 도움말 외에도 패널 편집 대화 상자의 도움말 콘텐츠 탭에서 패널 수준에서 도움말을 지정할 수 있습니다.

![양식 패널에 대한 상황에 맞는 도움말 추가](assets/panel-level-help.png)

패널에 대한 도움말을 추가하면 **이(가) 표시됩니까?패널 설명 옆의** 아이콘. 아이콘을 클릭하면 패널 편집 대화 상자의 도움말 콘텐츠 섹션에 추가된 콘텐츠가 표시됩니다.

![양식 패널 수준의 상황에 맞는 도움말 예제](assets/photoshop-1.png)