---
title: 적응형 양식에 새 로케일 지원 추가
seo-title: Learn to add support for new locales to your adaptive forms
description: AEM Forms을 사용하면 적응형 양식을 현지화하기 위한 새 로케일을 추가할 수 있습니다. 영어(en), 스페인어(es), 프랑스어(fr), 이탈리아어(it), 독일어(de), 일본어(ja), 포르투갈어(브라질), 중국어(zh-CN), 중국어(zh-TW) 및 한국어(ko-KR) 로케일.
seo-description: AEM Forms allows you to add new locales for localizing adaptive forms. We support 10 locales out of the box curently, as  "en","fr","de","ja","pt-br","zh-cn","zh-tw","ko-kr","it","es".
exl-id: 4c7d6caa-1adb-4663-933f-b09129b9baef
source-git-commit: ca0c9f102488c38dbe8c969b54be7404748cbc00
workflow-type: tm+mt
source-wordcount: '1267'
ht-degree: 2%

---

# 적응형 Forms 현지화를 위한 새 로케일 지원 {#supporting-new-locales-for-adaptive-forms-localization}

<span class="preview"> Adobe은 현대적이고 확장 가능한 데이터 캡처를 사용할 것을 권장합니다 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) 대상 [새 적응형 Forms 만들기](/help/forms/creating-adaptive-form-core-components.md) 또는 [AEM Sites 페이지에 적응형 Forms 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). 이러한 구성 요소는 적응형 Forms 작성의 중요한 발전을 나타내어 인상적인 사용자 경험을 보장합니다. 이 문서에서는 기초 구성 요소를 사용하여 적응형 Forms을 작성하는 이전 방법에 대해 설명합니다. </span>


| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기를 클릭하십시오.](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/supporting-new-language-localization.html) |
| AEM as a Cloud Service | 이 문서 |

AEM Forms은 영어(en), 스페인어(es), 프랑스어(fr), 이탈리아어(it), 독일어(de), 일본어(ja), 포르투갈어-브라질어(pt-BR), 중국어(zh-CN), 중국어-대만(zh-TW) 및 한국어(ko-KR) 로케일을 즉시 지원합니다. 힌디어(hi_IN)와 같은 더 많은 로케일에 대한 지원을 추가할 수도 있습니다.

## 로케일 사전 이해 {#about-locale-dictionaries}

적응형 양식의 현지화는 두 가지 유형의 로케일 사전을 사용합니다.

* **양식 특정 사전** 적응형 양식에 사용되는 문자열을 포함합니다. 예를 들어 레이블, 필드 이름, 오류 메시지, 도움말 설명이 있습니다. 각 로케일에 대한 XLIFF 파일 세트로 관리되며 다음 위치에서 액세스할 수 있습니다. `[author-instance]/libs/cq/i18n/gui/translator.html`.

* **글로벌 사전** AEM 클라이언트 라이브러리에는 JSON 개체로 관리되는 두 개의 글로벌 사전이 있습니다. 이러한 사전에는 기본 오류 메시지, 월 이름, 통화 기호, 날짜 및 시간 패턴 등이 포함됩니다. 다음 위치에서 이 사전을 찾을 수 있습니다. `[author-instance]/libs/fd/xfaforms/clientlibs/I18N`. 이러한 위치에는 각 로케일에 대해 별도의 폴더가 있습니다. 글로벌 사전은 자주 업데이트되지 않으므로 각 로케일에 대해 별도의 JavaScript 파일을 유지하면 브라우저가 이를 캐시할 수 있고 동일한 서버의 다른 적응형 양식에 액세스할 때 네트워크 대역폭 사용을 줄일 수 있습니다.

## 새 로케일에 대한 지원 추가 {#add-support-for-new-locales}

새 로케일에 대한 지원을 추가하려면 다음을 수행합니다.

1. [지원되지 않는 로케일에 대한 현지화 지원 추가](#add-localization-support-for-non-supported-locales)
1. [적응형 Forms에서 추가된 로케일 사용](#use-added-locale-in-af)

### 지원되지 않는 로케일에 대한 현지화 지원 추가 {#add-localization-support-for-non-supported-locales}

AEM Forms은 현재 영어(en), 스페인어(es), 프랑스어(fr), 이탈리아어(it), 독일어(de), 일본어(ja), 포르투갈어(pt-BR), 중국어(zh-CN), 중국어-대만(zh-TW) 및 한국어(ko-KR) 로케일로 된 적응형 Forms 콘텐츠의 현지화를 지원합니다.

적응형 Forms 런타임에 새 로케일에 대한 지원을 추가하려면:

1. [저장소 복제](#clone-the-repository)
1. [GuideLocalizationService 서비스에 로케일 추가](#add-a-locale-to-the-guide-localization-service)
1. [로케일 이름별 폴더 추가](#add-locale-name-specific-folder)
1. [사전에 대한 로케일 지원 추가](#add-locale-support-for-the-dictionary)
1. [저장소에서 변경 사항을 커밋하고 파이프라인을 배포합니다.](#commit-changes-in-repo-deploy-pipeline)

#### 1. 저장소 복제 {#clone-the-repository}

1. 명령줄에서 Forms Cloud Service 저장소를 복제하려는 위치로 이동합니다.
1. 다음 명령을 실행합니다. [Cloud Manager에서 검색되었습니다.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) 와 유사합니다. `git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/`.
1. git 사용자 이름 및 암호를 사용하여 저장소를 복제합니다.
1. 원하는 편집기에서 복제된 Forms Cloud Service 저장소 폴더를 엽니다.

#### 2. 가이드 현지화 서비스에 로케일 추가 {#add-a-locale-to-the-guide-localization-service}

1. 를 찾습니다. `Guide Localization Service.cfg.json` 파일을 추가하고 지원되는 로케일 목록에 추가할 로케일을 추가합니다.

   >[!NOTE]
   >
   > 이라는 이름의 파일을 만듭니다. `Guide Localization Service.cfg.json` 파일(아직 없는 경우)

#### 3. 로케일 이름별 폴더 클라이언트 라이브러리 추가 {#add-locale-name-specific-folder}

1. UI.content 폴더에서 `etc/clientlibs` 폴더를 삭제합니다.
1. 다음 이름의 폴더 추가 생성: `locale-name` 아래에 `etc/clientlibs` 를 xfa 및 af clientlibs의 컨테이너 역할을 합니다.

##### 3.1 locale-name 폴더의 로케일에 대한 XFA 클라이언트 라이브러리 추가

라는 노드를 만듭니다. `[locale-name]_xfa` 및 다음으로 입력 `cq:ClientLibraryFolder` 아래에 `etc/clientlibs/locale_name`, 범주 포함 `xfaforms.I18N.<locale>`을 클릭하고 다음 파일을 추가합니다.

* **I18N.js** 정의 `xfalib.locale.Strings` 대상: `<locale>` 에서 정의된대로 `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.
* **js.txt** 다음을 포함:
  */libs/fd/xfaforms/clientlibs/I18N/Namespace.js I18N.js /etc/clientlibs/fd/xfaforms/I18N/LogMessages.js*

##### 3.2. locale-name 폴더에 대한 적응형 양식 클라이언트 라이브러리 추가

1. 라는 노드를 만듭니다. `[locale-name]_af` 및 다음으로 입력 `cq:ClientLibraryFolder` 아래에 `etc/clientlibs/locale_name`, 범주 포함 `guides.I18N.<locale>` 및 종속성 `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` 및 `guide.common`.
1. 다음 이름의 폴더 만들기 `javascript` 다음 파일을 추가합니다.

   * **i18n.js** 정의 `guidelib.i18n`, &quot;calendarSymbols&quot; 패턴 포함, `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` 대상: `<locale>` 에 설명된 XFA 사양에 따라 [로케일 집합 사양](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf).
   * **LogMessages.js** 정의 `guidelib.i18n.strings` 및 `guidelib.i18n.LogMessages` 대상: `<locale>` 에서 정의된대로 `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`.

1. 추가 **js.txt** 다음을 포함:

   ```
     i18n.js
     LogMessages.js
   ```

#### 4. 사전에 대한 로케일 지원 추가 {#add-locale-support-for-the-dictionary}

다음 경우에만 이 단계를 수행하십시오. `<locale>` 을(를) 추가하고 있는 이(가) 다음에 없습니다. `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. 폴더 만들기 `languages` 아래에 `etc`, 아직 존재하지 않는 경우.

1. 다중 값 문자열 속성 추가 `languages` 노드(아직 없는 경우)에 추가합니다.
1. 추가 `<locale-name>` 기본 로케일 값 `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`, 아직 존재하지 않는 경우.

1. 추가 `<locale>` 의 값에 `languages` 다음의 속성 `/etc/languages`.
1. 새로 만든 폴더를 `filter.xml` etc/META-INF/[폴더 계층] 다음으로:

   ```
   <filter root="/etc/clientlibs/[locale-name]"/>
   <filter root="/etc/languages"/>
   ```

변경 사항을 AEM Git 저장소에 커밋하기 전에 [Git 저장소 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git).

#### 5. 저장소의 변경 사항을 커밋하고 파이프라인을 배포합니다 {#commit-changes-in-repo-deploy-pipeline}

새 로케일 지원을 추가한 후 GIT 저장소에 변경 사항을 커밋합니다. 전체 스택 파이프라인을 사용하여 코드를 배포합니다. 학습 [파이프라인 설정 방법](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#setup-pipeline) 새 로케일 지원을 추가합니다.
파이프라인이 완료되면 새로 추가된 로케일이 AEM 환경에 나타납니다.

### 적응형 Forms에서 추가된 로케일 사용 {#use-added-locale-in-af}

새로 추가된 로케일을 사용하여 적응형 양식을 사용하고 렌더링하려면 다음 단계를 수행하십시오.

1. AEM 작성자 인스턴스에 로그인합니다.
1. 다음으로 이동 **Forms** >  **Forms 및 문서**.
1. 적응형 양식을 선택하고 **사전 추가** 및 **사전을 번역 프로젝트에 추가** 마법사가 나타납니다.
1. 다음을 지정합니다. **프로젝트 제목** 및 선택 **Target 언어** 드롭다운 메뉴 아래의 **사전을 번역 프로젝트에 추가** 마법사.
1. 클릭 **완료** 생성된 번역 프로젝트를 실행합니다.
1. 적응형 양식을 선택하고 **HTML으로 미리 보기**.
1. 추가 `&afAcceptLang=<locale-name>` 를 입력합니다.
1. 페이지를 새로 고치면 적응형 양식이 지정된 로케일로 렌더링됩니다.

적응형 양식의 로케일을 식별하는 방법에는 두 가지가 있습니다. 적응형 양식이 렌더링되면 다음 방법으로 요청된 로케일을 식별합니다.

* 검색 중 `[local]` 적응형 양식 URL의 선택기. URL 형식은 다음과 같습니다. `http://host:[port]/content/forms/af/[afName].[locale].html?wcmmode=disabled`. 사용 `[local]` 선택기를 사용하여 적응형 양식을 캐싱할 수 있습니다.

* 나열된 순서로 다음 매개 변수를 검색합니다.

   * 요청 매개 변수 `afAcceptLang`
사용자의 브라우저 로케일을 재정의하려면 `afAcceptLang` 로케일을 강제 적용하기 위한 매개 변수를 요청합니다. 예를 들어 다음 URL은 캐나다-프랑스어 로케일로 양식을 렌더링하도록 강제합니다.
     `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ca-fr`

   * 을 사용하여 요청에 지정된 사용자에 대한 브라우저 로케일 집합입니다. `Accept-Language` 머리글입니다.

요청한 로케일에 대한 클라이언트 라이브러리가 없으면 로케일에 있는 언어 코드에 대한 클라이언트 라이브러리를 확인합니다. 예를 들어 요청된 로케일이 `en_ZA` (남아프리카 영어) 및 클라이언트 라이브러리 `en_ZA` 이(가) 존재하지 않습니다. 적응형 양식은 클라이언트 라이브러리를 사용합니다. `en` (영어) 언어(있는 경우). 단, 존재하지 않는 경우 적응형 양식은 다음 용도로 사전을 사용합니다 `en` 로케일.


로케일이 식별되면 적응형 양식에서 양식별 사전을 선택합니다. 요청된 로케일에 대한 양식 특정 사전을 찾을 수 없으면 적응형 양식이 작성된 언어용 사전을 사용합니다.

로케일 정보가 없으면 적응형 양식이 양식의 원래 언어로 전달됩니다. 원래 언어는 적응형 양식을 개발하는 동안 사용되는 언어입니다.

Get [샘플 클라이언트 라이브러리](/help/forms/assets/locale-support-sample.zip) 새 로케일에 대한 지원을 추가합니다. 필요한 로케일에서 폴더 콘텐츠를 변경해야 합니다.

## 새로운 현지화 기능 지원을 위한 모범 사례 {#best-practices}

* Adobe은 적응형 양식을 만든 후 번역 프로젝트를 만들 것을 권장합니다.

* 기존 적응형 양식에 새 필드를 추가하는 경우:
   * **기계 번역용**: 사전을 다시 만들고 번역 프로젝트를 실행합니다. 번역 프로젝트를 만든 후 적응형 양식에 추가된 필드는 번역되지 않은 상태로 유지됩니다.
   * **사람 번역용**: 다음을 통해 사전 내보내기 `[server:port]/libs/cq/i18n/gui/translator.html`. 새로 추가된 필드의 사전을 업데이트하고 업로드합니다.
