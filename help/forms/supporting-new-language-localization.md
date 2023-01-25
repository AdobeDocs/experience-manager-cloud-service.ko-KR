---
title: 적응형 양식 현지화를 위한 새 로케일 지원
seo-title: Supporting new locales for adaptive forms localization
description: AEM Forms에서는 적응형 양식을 현지화하기 위해 새 로케일을 추가할 수 있습니다. 영어(en), 스페인어(es), 프랑스어(fr), 이탈리아어(it), 독일어(de), 일본어(ja), 포르투갈어(pt-BR), 중국어(zh-CN), 중국어(zh-TW) 및 한국어(ko-KR) 로케일.
seo-description: AEM Forms allows you to add new locales for localizing adaptive forms. We support 10 locales out of the box curently, as  "en","fr","de","ja","pt-br","zh-cn","zh-tw","ko-kr","it","es".
source-git-commit: f8bbc6605e77cf2858c69dae96e9ab32698d1f16
workflow-type: tm+mt
source-wordcount: '1141'
ht-degree: 0%

---

# 적응형 Forms 지역화를 위한 새 로케일 지원{#supporting-new-locales-for-adaptive-forms-localization}

## 로케일 사전 정보 {#about-locale-dictionaries}

적응형 양식의 현지화는 다음 두 가지 로케일 사전 유형을 사용합니다.

* **양식별 사전** 적응형 양식에 사용된 문자열을 포함합니다. 예를 들어 레이블, 필드 이름, 오류 메시지, 도움말 설명 등이 있습니다. 이 파일은 각 로케일에 대한 XLIFF 파일 세트로 관리되며, 여기에서 액세스할 수 있습니다 `[author-instance]/libs/cq/i18n/gui/translator.html`.

* **글로벌 사전** AEM 클라이언트 라이브러리에는 JSON 개체로 관리되는 두 개의 글로벌 사전이 있습니다. 이러한 사전은 기본 오류 메시지, 월 이름, 통화 기호, 날짜 및 시간 패턴 등을 포함합니다. 이 사전은 `[author-instance]/libs/fd/xfaforms/clientlibs/I18N`. 이러한 위치에는 각 로케일에 대해 별도의 폴더가 있습니다. 글로벌 사전은 자주 업데이트되지 않으므로 각 로케일에 대해 별도의 JavaScript 파일을 유지하면 브라우저에서 캐싱하고 동일한 서버에서 다른 적응형 양식에 액세스할 때 네트워크 대역폭 사용을 줄일 수 있습니다.

AEM Forms에 대한 새로운 지역화를 지원하는 절차:

1. [지원되지 않는 로케일에 대한 지역화 지원 추가](#add-localization-support-for-non-supported-locales-add-localization-support-for-non-supported-locales)
1. [적응형 Forms에서 추가된 로케일 사용](#use-added-locale-in-adaptive-forms-use-added-locale-in-af)

## 지원되지 않는 로케일에 대한 지역화 지원 추가 {#add-localization-support-for-non-supported-locales}

AEM Forms은 현재 영어(en), 스페인어(es), 프랑스어(fr), 이탈리아어(it), 독일어(de), 일본어(ja), 포르투갈어(pt-BR), 중국어(zh-CN), 중국어(zh-TW) 및 한국어(ko-KR) 로케일로 적응형 Forms 컨텐츠의 지역화를 지원합니다.

적응형 Forms 런타임 시 새 로케일에 대한 지원을 추가하려면 다음을 수행합니다.

1. [리포지토리 복제](#1-clone-the-repository-clone-the-repository)
1. [GuideLocalizationService 서비스에 로케일 추가](#1-add-a-locale-to-the-guide-localization-service-add-a-locale-to-the-guide-localization-service-br)
1. [로케일 이름 특정 폴더 추가](#3-add-locale-name-specific-folder-add-locale-name-specific-folder)
1. [로케일에 대한 XFA 클라이언트 라이브러리 추가](#3-add-xfa-client-library-for-a-locale)
1. [로케일에 대한 적응형 양식 클라이언트 라이브러리 추가](#4-add-adaptive-form-client-library-for-a-locale-add-adaptive-form-client-library-for-a-locale-br)
1. [사전에 대한 로케일 지원 추가](#5-add-locale-support-for-the-dictionary-add-locale-support-for-the-dictionary-br)
1. [리포지토리에서 변경 사항을 커밋하고 파이프라인을 배포합니다.](#7-commit-the-changes-in-the-repository-and-deploy-the-pipeline-commit-changes-in-repo-deploy-pipeline)

### 1. 리포지토리 복제 {#clone-the-repository}

1. 명령줄에서 Forms Cloud Service 리포지토리를 복제할 위치로 이동합니다.
1. 원하는 명령을 실행합니다 [cloud Manager에서 검색됨.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) 비슷해요 `git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/`.
1. Git 사용자 이름 및 암호를 사용하여 리포지토리를 복제합니다.
1. 복제된 Forms Cloud Service 저장소 폴더를 기본 편집기에서 엽니다.

### 2. Guide Localization 서비스에 로케일을 추가합니다. {#add-a-locale-to-the-guide-localization-service-br}

1. 을(를) 찾습니다 `Guide Localization Service.cfg.json` 파일을 추가하고 지원되는 로케일 목록에 추가할 로케일을 추가합니다.

   >[!NOTE]
   >
   >* 이름이 인 파일을 만듭니다. `Guide Localization Service.cfg.json` 파일(아직 없음)


### 3. 로케일 이름 특정 폴더 클라이언트 라이브러리 추가 {#add-locale-name-specific-folder}

1. UI.content 폴더에서 `etc/clientlibs` 폴더를 입력합니다.
1. 또한 `locale-name` 아래에 `etc/clientlibs` xfa 및 af clientlibs용 컨테이너로 사용할 수 있습니다.

#### 3.1 locale-name 폴더의 로케일에 대한 XFA 클라이언트 라이브러리 추가

1. 이름이 인 노드 만들기 `[locale-name]_xfa` 을(를) 다음과 같이 입력합니다. `cq:ClientLibraryFolder` 아래에 `etc/clientlibs/locale_name`, 카테고리 포함 `xfaforms.I18N.<locale>`를 누르고 다음 파일을 추가합니다.
* **I18N.js** 정의 `xfalib.locale.Strings` 대상 `<locale>` 에 정의된 대로 `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.
* **js.txt** 다음 포함:
   */libs/fd/xfaforms/clientlibs/I18N/Namespace.js I18N.js /etc/clientlibs/fd/xfaforms/I18N/LogMessages.js*

#### 3.2. locale-name 폴더에 대한 적응형 양식 클라이언트 라이브러리 추가 {#add-adaptive-form-client-library-for-a-locale-br}

1. 이름이 인 노드 만들기 `[locale-name]_af` 을(를) 다음과 같이 입력합니다. `cq:ClientLibraryFolder` 아래에 `etc/clientlibs/locale_name`, 카테고리를 로 사용 `guides.I18N.<locale>` 및 종속 항목을 `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` 및 `guide.common`.
1. 이름이 인 폴더를 만듭니다. `javascript` 및 다음 파일을 추가합니다.

   * **i18n.js** 정의 `guidelib.i18n`, &quot;calendarSymbol&quot; 패턴이 있는 경우 `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` 대상 `<locale>` 에 설명된 대로 [로케일 집합 사양](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf).
   * **LogMessages.js** 정의 `guidelib.i18n.strings` 및 `guidelib.i18n.LogMessages` 대상 `<locale>` 에 정의된 대로 `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`.

1. 추가 **js.txt** 다음 포함:

   ```text
     i18n.js
       LogMessages.js
   ```

### 4. 사전에 대한 로케일 지원 추가 {#add-locale-support-for-the-dictionary-br}

다음 경우에만 이 단계를 수행합니다. `<locale>` 을(를) 추가할 때 `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. 폴더 만들기 `languages` 아래에 `etc`: 아직 없는 경우.

1. 여러 값을 갖는 문자열 속성 추가 `languages` 아직 없는 경우 노드에 추가합니다.
1. 추가 `<locale-name>` 기본 로케일 값 `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`: 아직 없는 경우.

1. 추가 `<locale>` 의 값으로 `languages` 속성 `/etc/languages`.


```text
Add the newly created folders in the `filter.xml` under etc/META-INF/[folder hierarchy] as:
<filter root="/etc/clientlibs/[locale-name]"/>
<filter root="/etc/languages"/>
```

변경 사항을 AEM Git 리포지토리에 커밋하기 전에 [Git 리포지토리 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git).

### 5. 리포지토리에서 변경 사항을 커밋하고 파이프라인을 배포합니다. {#commit-chnages-in-repo-deploy-pipeline}

새 로케일 지원을 추가한 후 변경 사항을 GIT 리포지토리에 커밋합니다. 전체 스택 파이프라인을 사용하여 코드를 배포합니다. 학습 [파이프라인을 설정하는 방법](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#setup-pipeline) 새 로케일 지원을 추가하려면

파이프라인이 완료되면 새로 추가된 로케일이 AEM 환경에 나타납니다.

### 응용 Forms에서 추가된 로케일 사용 {#use-added-locale-in-af}

새로 추가된 로케일을 사용하여 적응형 양식을 사용하고 렌더링하는 절차:

1. AEM 작성자 인스턴스에 로그인합니다.
1. 이동 **Forms** >  **Forms 및 문서**.
1. 적응형 양식을 선택하고 **사전 추가** 및 **번역 프로젝트에 사전 추가** 마법사가 나타납니다.
1. 을(를) 지정합니다. **프로젝트 제목** 을(를) 선택하고 을(를) 선택합니다. **Target 언어** 아래의 드롭다운 메뉴에서 **번역 프로젝트에 사전 추가** 마법사
1. 클릭 **완료** 생성된 번역 프로젝트를 실행합니다.
1. 적응형 양식을 선택하고 **HTML으로 미리 보기**.
1. 추가 `&afAcceptLang=<locale-name>` 적응형 양식의 URL에서 을 참조하십시오.
1. 페이지를 새로 고치면 적응형 양식이 지정된 로케일에 렌더링됩니다.

적응형 양식의 로케일을 식별하는 방법에는 두 가지가 있습니다. 적응형 양식을 렌더링할 때 는 로 요청된 로케일을 식별합니다.

* 보고 `[local]` 선택기를 추가합니다. URL의 형식은 다음과 같습니다 `http://host:[port]/content/forms/af/[afName].[locale].html?wcmmode=disabled`. 사용 `[local]` 선택기를 사용하면 적응형 양식을 캐싱할 수 있습니다.

* 지정된 순서로 다음 매개 변수를 봅니다.

   * 요청 매개 변수 `afAcceptLang`
사용자의 브라우저 로케일을 재정의하려면 
`afAcceptLang` 요청 매개 변수를 사용하여 로케일을 강제 적용합니다. 예를 들어 다음 URL에서는 캐나다-프랑스어 로케일로 양식을 렌더링합니다.
      `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ca-fr`

   * 사용자에 대해 설정된 브라우저 로케일입니다. 이 로켈은 `Accept-Language` 헤더.

요청된 로캘에 대한 클라이언트 라이브러리가 없는 경우 클라이언트 라이브러리에서 로케일에 있는 언어 코드를 확인합니다. 예를 들어, 요청된 로케일이 `en_ZA` (남아프리카 영어) 및 클라이언트 라이브러리 `en_ZA` 은 존재하지 않으며 적응형 양식은 용 클라이언트 라이브러리를 사용합니다 `en` (영어) 언어입니다. 그러나 이들 중 어느 것도 존재하지 않는 경우에는 적응형 양식에 사전을 사용합니다 `en` 로케일.


로케일이 식별되면 적응형 양식에서 양식 특정 사전을 선택합니다. 요청된 로캘의 양식 특정 사전을 찾을 수 없으면 적응형 양식이 작성된 언어에 사전을 사용합니다.

로케일 정보가 없으면 적응형 양식이 양식의 원래 언어로 전달됩니다. 원래 언어는 적응형 양식을 개발하는 동안 사용되는 언어입니다.

Get [샘플 클라이언트 라이브러리](/help/forms/assets/locale-support-sample.zip) 새 로케일에 대한 지원을 추가하려면 필요한 로케일에서 폴더 내용을 변경해야 합니다.

### 새로운 지역화를 지원하는 우수 사례 {#best-practices}

* Adobe은 적응형 양식을 만든 후 번역 프로젝트를 만들 것을 권장합니다.

* 기존 적응형 양식에 새 필드가 추가되면:
   * **기계 번역용**: 사전을 다시 만들고 번역 프로젝트를 실행합니다. 번역 프로젝트를 만든 후 적응형 양식에 추가된 필드는 번역되지 않은 상태로 유지됩니다.
   * **인간 번역**: 사전을 다음 방법으로 내보냅니다 `[server:port]/libs/cq/i18n/gui/translator.html`. 새로 추가된 필드에 대한 사전을 업데이트하고 업로드합니다.
