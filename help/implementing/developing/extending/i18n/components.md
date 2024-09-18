---
title: 구성 요소 다국어화
description: 구성 요소 및 대화 상자의 UI 문자열이 다른 언어로 표시될 수 있도록 다국어화
topic-tags: components
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: b55f7260628f759de2718290624cdc82da7a2961
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# 구성 요소 다국어화{#internationalizing-components}

구성 요소 및 대화 상자의 UI 문자열을 다른 언어로 표시할 수 있도록 국제화합니다. 국제화를 위해 설계된 구성 요소를 사용하면 UI 문자열을 외부화하고, 번역한 다음 저장소로 가져올 수 있습니다. 런타임 시 사용자의 언어 환경 설정 또는 페이지 로케일에 따라 UI에 표시되는 언어가 결정됩니다.

![i18n-components-1.png](/help/implementing/developing/extending/assets/i18n-comp1.png)

다음 프로세스를 사용하여 구성 요소를 국제화하고 UI를 다양한 언어로 제공합니다.

1. [문자열을 국제화하는 코드를 사용하여 구성 요소를 구현합니다.](/help/implementing/developing/extending/i18n/dev.md) 코드가 번역할 문자열을 식별하고 런타임 시 표시할 언어를 선택합니다.
1. 사전을 만들고 번역할 영어 문자열을 추가합니다.
1. 사전을 XLIFF 형식으로 내보내고 문자열을 번역한 다음 XLIFF 파일을 다시 AEM으로 가져옵니다.
1. 사전을 애플리케이션의 릴리스 관리 프로세스에 통합합니다.

>[!NOTE]
>
>여기에 설명된 구성 요소 다국어화 방법은 정적 문자열을 번역하기 위한 것입니다. 구성 요소 문자열이 변경될 것으로 예상되는 경우 기존 번역 워크플로를 사용해야 합니다. 예를 들어 작성자가 구성 요소의 편집 대화 상자에 있는 속성을 사용하여 UI 문자열을 편집할 수 있는 경우 언어 사전을 사용하여 문자열을 국제화해서는 안 됩니다.

## 언어 사전 {#language-dictionaries}

AEM 국제화 프레임워크는 저장소의 사전을 사용하여 영어 문자열 및 번역본을 다른 언어로 저장합니다. 프레임워크는 영어를 기본 언어로 사용합니다. 문자열은 영어 버전을 사용하여 식별됩니다. 일반적으로 국제화 프레임워크는 UI 문자열에 영숫자 ID를 사용합니다. 영어 버전의 문자열을 ID로 사용하면 다음과 같은 몇 가지 이점이 있습니다.

* 코드는 읽기 쉽습니다.
* 기본 언어는 항상 사용할 수 있습니다.

번역 변경 사항은 AEM as a cloud service의 [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)을 통해 Git에서 가져와야 합니다.

![i18n-components-2](/help/implementing/developing/extending/assets/i18n-comp2.png)


### 시스템 사전의 문자열 오버레이 {#overlaying-strings-in-system-dictionaries}

구성 요소가 AEM 시스템 사전에 포함된 문자열을 사용하는 경우 자체 사전에 있는 문자열을 복제하십시오. 모든 구성 요소는 사전의 문자열을 사용합니다.

`/apps` 노드 아래에 있는 사전에서 문자열이 복제되는 경우 사용할 번역을 예측할 수 없습니다.
