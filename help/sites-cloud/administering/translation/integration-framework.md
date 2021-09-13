---
title: 번역 통합 프레임워크 구성
description: 타사 번역 서비스와 통합하도록 번역 통합 프레임워크를 구성하는 방법을 알아봅니다.
feature: Language Copy
role: Admin
exl-id: 6e74cdee-7965-4087-a733-e9d81c4aa7c2
source-git-commit: 04054e04d24b5dde093ed3f14ca5987aa11f5b0e
workflow-type: tm+mt
source-wordcount: '1419'
ht-degree: 1%

---

# 번역 통합 프레임워크 구성 {#configuring-the-translation-integration-framework}

번역 통합 프레임워크는 타사 번역 서비스와 통합하여 AEM 컨텐츠 번역을 오케스트레이션합니다. 그것은 세 가지 기본적인 단계를 포함한다.

1. [번역 서비스 공급자에 연결합니다.](#connecting-to-a-translation-service-provider)
1. [번역 통합 프레임워크 구성을 만듭니다.](#creating-a-translation-integration-configuration)
1. [클라우드 구성을 페이지와 연결합니다.](#configuring-pages-for-translation)

AEM의 컨텐츠 번역 기능에 대한 개요를 알려면 [다국어 사이트에 대한 컨텐츠 번역](overview.md)을 참조하십시오.

>[!TIP]
>
>컨텐츠를 번역할 때 새로운 사용자에게 AEM의 강력한 번역 도구를 사용하여 AEM Sites 컨텐츠를 번역할 수 있는 안내식 경로인 [사이트 번역 여정](/help/journey-sites/translation/overview.md)을 참조하여 AEM 또는 번역 경험이 없는 사용자에게 이상적입니다.

## 번역 서비스 공급자에 연결 {#connecting-to-a-translation-service-provider}

AEM을 번역 서비스 공급자에 연결하는 클라우드 구성을 만듭니다. AEM에는 기본적으로 [Microsoft Translator](connect-ms-translator.md)에 연결하는 기능이 포함되어 있습니다.

다음 번역 공급업체는 번역 프로젝트에 대한 AEM API의 구현을 제공합니다.

* [Microsoft Translator](connect-ms-translator.md)
* [Translation.com](https://exchange.adobe.com/experiencecloud.details.90104.globallink-connect-plus-for-aem.html) (Adobe Exchange 프리미어 파트너)
* [클레이 태블릿 기술](https://exchange.adobe.com/experiencecloud.details.90064.clay-tablet-translation-for-experience-manager.html)
* [Lionbridge](https://exchange.adobe.com/experiencecloud.details.100064.lionbridge-connector-for-experience-manager-63.html)
* [Memsource](https://exchange.adobe.com/experiencecloud.details.103166.memsource-connector-for-adobe-experience-manager.html)
* [Cloudwords](https://exchange.adobe.com/experiencecloud.details.90019.html)
* [CrossLang NV](https://exchange.adobe.com/experiencecloud.details.90049.crosslang-xtm-for-adobe-experience-manager.html)
* [린고텍](https://exchange.adobe.com/experiencecloud.details.90088.lingotek-collaborative-translation-platform.html)
* [Smartling](https://exchange.adobe.com/experiencecloud.details.90101.smartling-connector-for-adobe-experience-manager.html)
* [SDL](https://exchange.adobe.com/experiencecloud.details.100110.sdl-translation-management.html)
* [시스트란](https://exchange.adobe.com/experiencecloud.details.90233.systran-for-adobe-experience-manager.html)

커넥터 패키지를 설치한 후 커넥터에 대한 클라우드 구성을 만들 수 있습니다. 일반적으로 번역 서비스를 사용하여 인증하기 위해 자격 증명을 제공해야 합니다. Microsoft Translator 커넥터에 대한 클라우드 구성 추가에 대한 자세한 내용은 [Microsoft Translator와 통합](connect-ms-translator.md)을 참조하십시오.

필요한 경우 동일한 커넥터에 대한 여러 클라우드 구성을 만들 수 있습니다. 예를 들어, 동일한 공급업체와 함께 있는 각 계정 또는 프로젝트에 대해 하나의 구성을 만듭니다.

연결을 구성한 후 연결을 사용하는 번역 통합 프레임워크 구성을 만들 수 있습니다.

## 번역 통합 구성 만들기 {#creating-a-translation-integration-configuration}

번역 통합 프레임워크 구성을 만들어 콘텐츠를 번역하는 방법을 지정합니다. 구성에는 다음 정보가 포함됩니다.

* 사용할 번역 서비스 공급자
* 인간 또는 기계 번역을 수행할지 여부
* 페이지나 자산과 관련된 다른 컨텐츠(예: 태그)를 번역할지 여부

프레임워크 구성을 만들면 클라우드 구성을 구성에 따라 번역할 페이지와 연결합니다. 번역 프로세스가 시작되면 연관된 프레임워크 구성에 따라 번역 워크플로우가 진행됩니다.

웹 사이트의 여러 섹션에 다양한 번역 요구 사항이 있는 경우 그에 따라 여러 프레임워크 구성을 만드십시오. 예를 들어 다국어 웹 사이트에는 영어, 스페인어 및 일본어 복사본이 포함될 수 있습니다. 사이트 소유자는 스페인어 및 일본어 번역에 두 개의 서로 다른 번역 서비스 공급자를 사용합니다. 따라서 프레임워크의 두 가지 구성이 구성됩니다. 각 구성에서는 다른 번역 서비스 공급자를 사용합니다.

번역 통합 프레임워크를 구성한 후에는 [을 사용하는 페이지](preparation.md)와 연결할 수 있습니다.

>[!TIP]
>
>AEM의 컨텐츠 번역 기능에 대한 개요를 알려면 [다국어 사이트에 대한 컨텐츠 번역](overview.md)을 참조하십시오.

프레임워크의 단일 구성은 페이지 컨텐츠와 자산을 변환하는 방법을 제어합니다.

![번역 구성](../assets/translation-configuration.png)

새 번역 구성을 만들려면 다음을 수행하십시오.

1. [전역 탐색 메뉴에서 ](/help/sites-cloud/authoring/getting-started/basic-handling.md#global-navigation) **도구 -> Cloud Services - 및 번역 Cloud Services**&#x200B;을 클릭하거나 탭합니다.
1. 컨텐츠 구조에서 구성을 만들 위치로 이동합니다. 이는 종종 특정 사이트를 기반으로 하거나 전역적일 수 있습니다.
1. 필드에 다음 정보를 제공한 다음 **만들기**&#x200B;를 클릭하거나 탭합니다.
   1. 드롭다운에서 **구성 유형**&#x200B;을 선택합니다.
   1. 구성에 대해 **제목**&#x200B;을 입력합니다. **제목**&#x200B;은 페이지 속성 드롭다운 목록뿐만 아니라 **Cloud Services** 콘솔에서 구성을 식별합니다.
   1. 구성을 저장하는 저장소 노드에 사용할 **이름**&#x200B;을 입력합니다(선택 사항).
1. **구성 편집** 창에서 **사이트** 및 **자산** 탭에서 속성을 구성한 다음 **저장 및 닫기**&#x200B;를 클릭하거나 탭합니다.

### 사이트 구성 속성 {#sites-configuration-properties}

**Sites** 탭은 페이지 컨텐츠의 번역을 수행하는 방식을 제어합니다.

| 속성 | 설명 |
|---|---|
| 번역 워크플로 | 이 속성은 프레임워크가 사이트 컨텐츠에 대해 수행하는 번역 방법을 정의합니다.<br>- 기계 번역: 번역 제공자는 기계 번역을 실시간으로 이용하여 번역을 수행한다.<br>- 인간 번역: 번역자가 번역하기 위해 콘텐츠가 번역 공급자에게 전송됩니다.<br>- 번역하지 않음: 컨텐츠를 번역하도록 전송되지 않습니다. 이는 번역되지 않지만 최신 콘텐츠로 업데이트할 수 있는 특정 콘텐츠 분기를 건너리기 위한 것입니다. |
| 번역 공급자 | 이 속성은 번역을 수행할 번역 공급자를 정의합니다. 해당 커넥터가 설치되면 공급자가 목록에 나타납니다. |
| 컨텐츠 카테고리 | (기계 번역만 해당) 이 속성은 번역하는 컨텐츠를 설명하는 카테고리입니다. 카테고리는 컨텐츠를 번역할 때 용어 및 표현식의 선택에 영향을 줄 수 있습니다. |
| 태그 번역 | 이 옵션을 사용하면 페이지와 연결된 태그를 번역할 수 있습니다. |
| 페이지 자산 번역 | 이 속성은 파일 시스템에서 구성 요소에 추가되거나 자산에서 참조되는 자산을 변환하는 방법을 정의합니다.<br>- 번역하지 마십시오: 페이지 자산은 번역되지 않습니다.<br>- 사이트 번역 워크플로우 사용: 자산은 Sitestab의 구성 속성에 따라  **** 처리됩니다.<br>- 자산 번역 워크플로우 사용: 자산은 자산 탭에 구성된 속성에 따라  **** 처리됩니다. |
| 번역 자동 실행 | 번역 프로젝트를 만든 후 번역 작업을 자동으로 실행하려면 이 속성을 활성화합니다. 이 옵션을 선택하면 번역 작업을 검토하고 범위를 지정할 수 없습니다. |

### 자산 구성 속성 {#assets-configuration-properties}

자산 속성은 자산을 구성하는 방법을 제어합니다. 자산 번역에 대한 자세한 내용은 [Assets](/help/assets/translate-assets.md)에 대한 언어 사본 만들기를 참조하십시오.

| 속성 | 설명 |
|---|---|
| 번역 워크플로 | 이 속성은 프레임워크가 자산에 대해 수행하는 번역 유형을 선택합니다.<br>- 기계 번역: 번역 공급자는 기계 번역을 사용하여 즉시 번역을 수행합니다.<br>- 인간 번역: 컨텐츠를 수동으로 번역하려면 번역 공급자에게 자동으로 전송됩니다.<br>-번역하지 않음: 자산은 번역을 위해 전송되지 않습니다. |
| 번역 공급자 | 이 속성은 번역을 수행할 번역 공급자를 정의합니다. 해당 커넥터가 설치되면 공급자가 목록에 나타납니다. |
| 컨텐츠 카테고리 | (기계 번역만 해당) 이 속성은 번역하는 컨텐츠를 설명합니다. 카테고리는 컨텐츠를 번역할 때 용어 및 표현식의 선택에 영향을 줄 수 있습니다. |
| 자산 번역 | 번역 프로젝트에 자산을 포함하려면 이 속성을 활성화합니다. |
| 메타데이터 번역 | 이 속성을 활성화하여 자산 메타데이터를 변환합니다. |
| 태그 번역 | 이 속성을 활성화하여 자산과 연결된 태그를 변환합니다. |
| 번역 자동 실행 | 번역 프로젝트를 만든 후 번역 작업을 자동으로 실행하려면 이 속성을 선택합니다. 이 옵션을 선택하면 번역 작업을 검토하거나 범위를 지정할 수 없습니다. |

## 번역 페이지 구성 {#configuring-pages-for-translation}

소스 페이지의 번역을 다른 언어로 구성하려면 페이지를 다음 클라우드 구성과 연결합니다.

* AEM을 번역 공급자에 연결하는 클라우드 구성입니다.
* 번역의 세부 사항을 구성하는 번역 통합 프레임워크입니다.

번역 통합 프레임워크 클라우드 구성은 서비스 공급자에 연결하는 데 사용할 클라우드 구성을 식별합니다. 소스 페이지를 프레임워크 클라우드 구성과 연결할 때 이 페이지는 프레임워크 클라우드 구성에서 사용하는 서비스 제공자 클라우드 구성과 연결되어 있어야 합니다.

페이지를 클라우드 구성과 연결할 때 페이지의 하위 항목은 연결을 상속합니다. 예를 들어 `/content/wknd/language-masters/en/magazine` 페이지를 번역 통합 프레임워크와 연결하는 경우, 그 아래의 `magazine` 페이지 및 하위 페이지가 프레임워크에 따라 번역됩니다.

필요한 경우 하위 페이지에서 연결을 재정의할 수 있습니다. 예를 들어, 웹 사이트의 컨텐츠는 대부분 여행 및 라이프스타일에 관한 것입니다. 하지만, 페이지의 한 분기에서 회사를 설명합니다. 이러한 경우 사이트의 루트 페이지는 라이프스타일 카테고리를 사용하여 기계 번역을 지정하는 번역 통합 프레임워크와 연결되고 회사를 설명하는 분기는 일반 카테고리를 사용하여 기계 번역을 수행하는 프레임워크를 사용할 수 있습니다.

### 페이지를 번역 공급자와 연결 {#associating-a-page-with-a-translation-provider}

페이지 및 하위 페이지를 번역하는 데 사용하는 번역 공급자와 페이지를 연결합니다.

1. 사이트 콘솔에서 구성할 페이지를 선택하고 **속성 보기**&#x200B;를 클릭하거나 탭합니다.
1. **Cloud Services** 탭을 클릭하거나 탭합니다.
1. **구성 추가** 드롭다운에서 구성을 선택합니다.
1. **저장 및 닫기**&#x200B;를 클릭하거나 탭합니다.

### 페이지를 번역 통합 프레임워크와 연결 {#associating-pages-with-a-translation-integration-framework}

페이지 및 하위 페이지를 번역하는 방법을 정의하는 번역 통합 프레임워크와 페이지를 연결합니다.

1. 사이트 콘솔에서 구성할 페이지를 선택하고 **속성 보기**&#x200B;를 클릭하거나 탭합니다.
1. **Cloud Services** 탭을 클릭하거나 탭합니다.
1. **구성 추가** 드롭다운에서 구성을 선택합니다.
1. **저장 및 닫기**&#x200B;를 클릭하거나 탭합니다.
