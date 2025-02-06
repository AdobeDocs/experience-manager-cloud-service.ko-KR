---
title: UI 문자열 국제화
description: AEM은 구성 요소 UI에 사용된 텍스트의 다양한 번역을 관리하는 콘솔을 제공합니다.
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 14a6516872f842d099b902b9f633b1d6f984266d
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 0%

---


# 번역기를 사용하여 사전 관리{#using-translator-to-manage-dictionaries}

AEM은 구성 요소 UI에 사용된 텍스트의 다양한 번역을 관리하는 콘솔을 제공합니다. 이 콘솔은 다음 위치에서 사용할 수 있습니다.

`https://<hostname>:<port-number>/libs/cq/i18n/gui/translator.html`

Translator 도구를 사용하여 영어 문자열 및 번역을 관리합니다. 사전이 리포지토리에 만들어집니다(예: `/apps/myproject/i18n`).

Translator 도구와 관리하는 사전은 구성 요소 UI를 다양한 언어로 제공하기 위한 것입니다. 페이지를 번역하려면 [다국어 사이트를 위한 콘텐츠 번역](/help/sites-cloud/administering/translation/overview.md)을 참조하세요.

## 사전 만들기 {#creating-a-dictionary}

개발자는 AEM에서 i18n 사전을 만들어 현지화된 구성 요소 문자열을 관리할 수 있습니다. 사전은 일반적으로 `/apps`에 있는 구성 요소 코드의 일부입니다. 다음은 모든 WKND 구성 요소에서 사용되는 하나의 키/값 쌍이 있는 AEM WKND 코드의 예입니다.

```
{
  "&copy; {0} WKND Site Site. All rights reserved." : "&copy; {0} WKND Site Site. Tous droits réservés."
}
```

개발자는 구성 요소 문자열의 언어 정의를 저장할 새 사전의 루트 노드(`sling:Folder`)를 추가하여 추가 사전을 만들 수 있습니다.

```shell
/apps/myProject/i18n [sling:Folder]
    - de.json [nt:file] [mix:language]
        + jcr:language = de
    - fr.json [nt:file] [mix:language]
        + jcr:language = fr
```

>[!NOTE]
>
>[Sling i18n 모듈](https://sling.apache.org/site/internationalization-support.html)의 구조입니다.

AEM GitHub 리포지토리에서 사전을 만들면 AEM [CI/CD 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)을 통해 사전을 배포할 수 있습니다.

## 사전 위치 {#dictionary-locations}

개발자는 `/apps` 또는 `/content/cq:i18n`에서 자유롭게 소스 언어 사전을 만들 수 있습니다. AEM Archetype 샘플 코드로 시작하면 일반적으로 초기 사전이 `/apps` 경로에 있습니다. 해당 사전 언어 사본을 `/apps`에도 저장하는 것이 목표라면, 해당 언어 사본은 개발자가 구성 요소 코드에서 수동으로 만들고 유지 관리해야 합니다.

또는 소스 사전이 `/apps` 또는 `/content`에 저장되어 있는지 여부에 관계없이 i18n 사전을 위한 새 AEM 런타임 번역 프로세스에서 `/content/cq:i18n/<projectName>`에 번역된 사전을 만듭니다.

i18n 사전, 소스 및 언어 사본을 찾을 위치는 다음 기준을 사용하여 결정해야 합니다.

* `/apps`
   * AEM Archetype 및 WKND 샘플 코드에 따라 구성 요소 문자열 변환이 있는 사전의 기본 위치
   * 가장 높은 렌더링 순서, Sling당([리소스 번들 검색 계층](https://sling.apache.org/documentation/bundles/internationalization-support-i18n.html#resourcebundle-hierarchies))
   * 그러나 AEM as a Cloud Service 환경에서는 `/apps`을(를) 변경할 수 없으므로 사전의 런타임 편집 또는 번역을 수행할 수 없습니다.

* `/content/cq:i18n`
   * 다음과 같은 경우 i18n 사전의 대체 위치
      * 사전의 런타임 번역이 필요합니다.
      * 런타임 시 사전을 편집할 수 있는 권한이 필요합니다.
   * 런타임 사전 번역이 언어 사본을 만드는 기본 위치입니다.

`/apps`은(는) Sling 렌더링 순서에서 항상 `/content`을(를) 대체하므로, `/content/cq:i18n`의 사전이 렌더링에 사용되지 않으므로 키/값 쌍이 동일한 사전이 `/apps`과(와) `/content/cq:i18n`에 동시에 존재하지 않아야 합니다. 사전 언어 사본(즉, 번역 대상)이 `/apps`에 이미 있고 AEM as a Cloud Service의 런타임 시 번역할 수 있도록 하는 것이 목표라면, `/apps`의 원본 사전 언어 사본을 `/content/cq:i18n`(으)로 이동하거나 `/apps`에서 삭제하고 소스 사전을 번역하여 `/content/cq:i18n`에서 자동으로 다시 만들어야 합니다. 이 번역 프로세스는 `/content/cq:i18n`에서 언어 사본을 자동으로 만듭니다.

## 자동 사전 만들기 {#automatic-creation}

AEM 핵심 구성 요소가 포함된 AEM 페이지 및 경험 조각의 경우 새 사전 번역 프로세스는 해당 페이지 또는 경험 조각에서 번역해야 하는 구성 요소 및 구성 요소 문자열도 스캔합니다. 그러면 시스템에서 `/content/cq:i18n`에 해당하는 새 사전 언어 사본을 자동으로 만듭니다. 이는 AEM 핵심 구성 요소를 사용하지 않는 순수 구조화된 컨텐츠이므로 컨텐츠 조각에는 적용되지 않습니다.

## 사전 내보내기 {#exporting-a-dictionary}

`/apps` 또는 `/libs` 위치에 있는 i18n 사전을 런타임 번역할 수 없지만 해당 위치는 변경할 수 없으므로 AEM as a Cloud Service에서 이러한 사전을 런타임 시 AEM 외부의 비동기 번역을 위해 내보낼 수 있습니다.

사전의 소스 언어 문자열을 XLIFF 파일로 내보내려면 다음을 수행합니다.

1. 번역 도구 `http://<host>:<port>/libs/cq/i18n/gui/translator.html` 열기

   >[!NOTE]
   >
   >이 도구는 이 URL을 통해서만 사용할 수 있으며 AEM 제품 UI에서 액세스할 수 없습니다.

1. 사전 드롭다운 메뉴를 사용하여 내보낼 사전을 선택합니다.
1. XLIFF 번역 내보내기 를 클릭한 다음 전체 `<locale>` xliff 내보내기 를 클릭합니다.

## 사전 가져오기 {#importing-a-dictionary}

XLIFF 파일을 사전에 가져와서 사전 콘텐츠를 채우려면 다음과 같이 하십시오.

1. 번역 도구 `http://<host>:<port>/libs/cq/i18n/gui/translator.html` 열기
1. 가져오기, XLIFF 번역 순으로 클릭합니다.
1. 가져올 파일을 선택하고 [확인]을 클릭합니다.
