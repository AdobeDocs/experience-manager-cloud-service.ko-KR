---
title: 기초 구성 요소를 기반으로 하는 적응형 양식에 새 로케일에 대한 지원을 추가하려면 어떻게 합니까?
description: 적응형 Forms의 경우 즉시 제공된 언어 외에도 더 많은 언어에 대한 로케일을 추가할 수 있습니다.
feature: Adaptive Forms, Foundation Components
exl-id: 4c7d6caa-1adb-4663-933f-b09129b9baef
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '1220'
ht-degree: 6%

---

# 적응형 Forms 현지화를 위한 새 로케일 지원 {#supporting-new-locales-for-adaptive-forms-localization}

<span class="preview"> [새 적응형 양식 만들기](/help/forms/creating-adaptive-form-core-components.md) 또는 [AEM Sites 페이지에 적응형 양식 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md) 작업을 할 때 현대적이고 확장 가능한 데이터 캡처 [핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)를 사용하는 것이 좋습니다. 이러한 구성 요소는 적응형 양식 만들기 작업이 대폭 개선되어 우수한 사용자 경험을 보장할 수 있게 되었음을 나타냅니다. 이 문서에서는 기초 구성 요소를 사용하여 적응형 양식을 작성하는 이전 접근법에 대해 설명합니다. </span>


| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/manage-administer-aem-forms/supporting-new-language-localization.html) |
| 핵심 구성 요소 | [여기 클릭](supporting-new-language-localization-core-components.md) |
| 기초 구성 요소 | 이 문서 |

AEM Forms은 영어(en), 스페인어(es), 프랑스어(fr), 이탈리아어(it), 독일어(de), 일본어(ja), 포르투갈어-브라질어(pt-BR), 중국어(zh-CN), 중국어-대만(zh-TW) 및 한국어(ko-KR) 로케일을 즉시 지원합니다. 힌디어(hi_IN)와 같은 더 많은 로케일에 대한 지원을 추가할 수도 있습니다.

## 로케일 사전 이해 {#about-locale-dictionaries}

적응형 양식의 현지화는 두 가지 유형의 로케일 사전을 사용합니다.

* **양식별 사전**&#x200B;에 적응형 양식에 사용되는 문자열이 포함되어 있습니다. 예를 들어 레이블, 필드 이름, 오류 메시지, 도움말 설명이 있습니다. 각 로케일에 대한 XLIFF 파일 집합으로 관리되며 `[author-instance]/libs/cq/i18n/gui/translator.html`에서 액세스할 수 있습니다.

* **전역 사전** AEM 클라이언트 라이브러리에 JSON 개체로 관리되는 두 개의 전역 사전이 있습니다. 이러한 사전에는 기본 오류 메시지, 월 이름, 통화 기호, 날짜 및 시간 패턴 등이 포함됩니다. `[author-instance]/libs/fd/xfaforms/clientlibs/I18N`에서 이 사전을 찾을 수 있습니다. 이러한 위치에는 각 로케일에 대해 별도의 폴더가 있습니다. 글로벌 사전은 자주 업데이트되지 않으므로 각 로케일에 대해 별도의 JavaScript 파일을 유지하면 브라우저가 이를 캐시할 수 있고 동일한 서버의 다른 적응형 양식에 액세스할 때 네트워크 대역폭 사용을 줄일 수 있습니다.

## 새 로케일에 대한 지원 추가 {#add-support-for-new-locales}

새 로케일에 대한 지원을 추가하려면 다음 단계를 수행하십시오.

1. [지원되지 않는 로케일에 대한 현지화 지원 추가](#add-localization-support-for-non-supported-locales)
1. [적응형 Forms에서 추가된 로케일 사용](#use-added-locale-in-af)

### 지원되지 않는 로케일에 대한 현지화 지원 추가 {#add-localization-support-for-non-supported-locales}

AEM Forms은 현재 영어(en), 스페인어(es), 프랑스어(fr), 이탈리아어(it), 독일어(de), 일본어(ja), 포르투갈어(pt-BR), 중국어(zh-CN), 중국어-대만(zh-TW) 및 한국어(ko-KR) 로케일로 된 적응형 Forms 콘텐츠의 현지화를 지원합니다.

적응형 Forms 런타임 시 새 로케일에 대한 지원을 추가하려면 다음 작업을 수행하십시오.

1. [저장소 복제](#clone-the-repository)
1. [GuideLocalizationService 서비스에 로케일 추가](#add-a-locale-to-the-guide-localization-service)
1. [로케일 이름별 폴더 추가](#add-locale-name-specific-folder)
1. [사전에 대한 로케일 지원 추가](#add-locale-support-for-the-dictionary)
1. [저장소에서 변경 사항을 커밋하고 파이프라인을 배포합니다.](#commit-changes-in-repo-deploy-pipeline)

#### 1. 저장소 복제 {#clone-the-repository}

1. 명령줄에서 Forms Cloud Service 저장소를 복제하려는 위치로 이동합니다.
1. Cloud Manager에서 [검색한 명령을 실행합니다.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) `git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/`과(와) 비슷합니다.
1. git 사용자 이름 및 암호를 사용하여 저장소를 복제합니다.
1. 원하는 편집기에서 복제된 Forms Cloud Service 저장소 폴더를 엽니다.

#### 2. 가이드 현지화 서비스에 로케일 추가 {#add-a-locale-to-the-guide-localization-service}

1. `Guide Localization Service.cfg.json` 파일을 찾은 다음 추가할 로케일을 지원되는 로케일 목록에 추가하십시오.

   >[!NOTE]
   >
   > 이름이 `Guide Localization Service.cfg.json` 파일인 파일을 만듭니다(아직 없는 경우).

#### 3. 로케일 이름별 폴더 클라이언트 라이브러리 추가 {#add-locale-name-specific-folder}

1. UI.content 폴더에서 `etc/clientlibs` 폴더를 만듭니다.
1. `etc/clientlibs` 아래에 `locale-name`(이)라는 폴더를 추가로 만들어 xfa 및 af clientlib의 컨테이너 역할을 합니다.

##### 3.1 locale-name 폴더에 로케일에 대한 XFA 클라이언트 라이브러리 추가

`etc/clientlibs/locale_name` 아래에 `[locale-name]_xfa`(으)로 명명된 노드를 만들고 `xfaforms.I18N.<locale>` 범주로 `cq:ClientLibraryFolder`(으)로 입력한 후 다음 파일을 추가하십시오.

* `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`에 정의된 대로 `<locale>`에 대해 `xfalib.locale.Strings`을(를) 정의하는 **I18N.js**.
* 다음을 포함하는 **js.txt**:
  */libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js*

##### 3.2. locale-name 폴더에 대한 적응형 양식 클라이언트 라이브러리 추가

1. `etc/clientlibs/locale_name`에서 이름이 `[locale-name]_af`이고 유형이 `cq:ClientLibraryFolder`인 노드를 만드십시오. 카테고리는 `guides.I18N.<locale>`이고 종속성은 `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` 및 `guide.common`입니다.
1. 이름이 `javascript`인 폴더를 만들고 다음 파일을 추가합니다.

   * [로케일 집합 지정](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf)에 설명된 XFA 사양에 따라 `<locale>`에 대해 &quot;calendarSymbols&quot;, `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` 패턴을 가진 `guidelib.i18n`을(를) 정의하는 **i18n.js**.
   * `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`에 정의된 대로 `<locale>`에 대해 `guidelib.i18n.strings` 및 `guidelib.i18n.LogMessages`을(를) 정의하는 **LogMessages.js**.

1. 다음을 포함하는 **js.txt** 추가:

   ```
     i18n.js
     LogMessages.js
   ```

#### 4. 사전에 대한 로케일 지원 추가 {#add-locale-support-for-the-dictionary}

추가하려는 `<locale>`이(가) `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`에 없는 경우에만 이 단계를 수행하십시오.

1. `etc`에 `languages` 폴더를 만듭니다. 아직 만들지 않았습니다.

1. 다중 값 문자열 속성 `languages`이(가) 아직 없는 경우 노드에 추가하십시오.
1. `<locale-name>` 기본 로케일 값 `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`을(를) 추가합니다(아직 없는 경우).

1. `/etc/languages`의 `languages` 속성 값에 `<locale>`을(를) 추가합니다.
1. 다음과 같이 etc/META-INF/[폴더 계층 구조]의 `filter.xml`에 생성된 폴더를 추가합니다.

   ```
   <filter root="/etc/clientlibs/[locale-name]"/>
   <filter root="/etc/languages"/>
   ```

변경 내용을 AEM Git 저장소에 커밋하기 전에 [Git 저장소 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=ko-KR#accessing-git)에 액세스해야 합니다.

#### 5. 저장소의 변경 사항을 커밋하고 파이프라인을 배포합니다 {#commit-changes-in-repo-deploy-pipeline}

로케일 지원을 추가한 후 GIT 저장소에 변경 사항을 커밋합니다. 전체 스택 파이프라인을 사용하여 코드를 배포합니다. 새 로케일 지원을 추가하려면 [파이프라인을 설정하는 방법](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=ko-KR#setup-pipeline)을 알아보세요.
파이프라인이 완료되면 새로 추가된 로케일이 AEM 환경에 나타납니다.

### 적응형 Forms에서 추가된 로케일 사용 {#use-added-locale-in-af}

새로 추가된 로케일을 사용하여 적응형 양식을 사용하고 렌더링하려면 다음 단계를 수행하십시오.

1. AEM 작성자 인스턴스에 로그인합니다.
1. **Forms** > **Forms 및 문서**&#x200B;로 이동합니다.
1. 적응형 양식을 선택하고 **사전 추가**&#x200B;를 클릭하면 **번역 프로젝트에 사전 추가** 마법사가 나타납니다.
1. **프로젝트 제목**&#x200B;을 지정하고 **번역 프로젝트에 사전 추가** 마법사의 드롭다운 메뉴에서 **타겟 언어**&#x200B;를 선택합니다.
1. **완료**&#x200B;를 클릭하고 만든 번역 프로젝트를 실행하십시오.
1. 적응형 양식을 선택하고 **HTML으로 미리 보기**&#x200B;를 클릭합니다.
1. 적응형 양식의 URL에 `&afAcceptLang=<locale-name>`을(를) 추가합니다.
1. 페이지를 새로 고치면 적응형 양식이 지정된 로케일로 렌더링됩니다.

적응형 양식의 로케일을 식별하는 방법에는 두 가지가 있습니다. 적응형 양식이 렌더링되면 다음 방법으로 요청된 로케일을 식별합니다.

* 적응형 양식 URL에서 `[local]` 선택기를 검색하는 중입니다. URL 형식은 `http://host:[port]/content/forms/af/[afName].[locale].html?wcmmode=disabled`입니다. `[local]` 선택기를 사용하면 적응형 양식을 캐싱할 수 있습니다.

* 나열된 순서로 다음 매개 변수를 검색합니다.

   * 요청 매개 변수 `afAcceptLang`
사용자의 브라우저 로캘을 재정의하려면 `afAcceptLang` 요청 매개 변수를 전달하여 로캘을 강제 적용할 수 있습니다. 예를 들어 다음 URL은 캐나다-프랑스어 로케일로 양식을 렌더링하도록 강제합니다.
     `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ca-fr`

   * `Accept-Language` 헤더를 사용하여 요청에 지정된 사용자에 대한 브라우저 로케일 집합입니다.

요청한 로케일에 대한 클라이언트 라이브러리가 없으면 로케일에 있는 언어 코드에 대한 클라이언트 라이브러리를 확인합니다. 예를 들어 요청된 로케일이 `en_ZA`(남아프리카 영어)이고 `en_ZA`에 대한 클라이언트 라이브러리가 없는 경우 적응형 양식은 `en`(영어) 언어에 대한 클라이언트 라이브러리를 사용합니다(있는 경우). 단, 존재하지 않는 경우 적응형 양식은 `en` 로케일에 대한 사전을 사용합니다.


로케일이 식별되면 적응형 양식에서 양식별 사전을 선택합니다. 요청된 로케일에 대한 양식 특정 사전을 찾을 수 없는 경우 적응형 양식이 작성된 언어로 사전을 사용합니다.

로케일 정보가 없으면 적응형 양식이 양식의 원래 언어로 전달됩니다. 원래 언어는 적응형 양식을 개발하는 동안 사용되는 언어입니다.

새 로케일에 대한 지원을 추가하려면 [샘플 클라이언트 라이브러리](/help/forms/assets/locale-support-sample.zip)를 가져오세요. 필요한 로케일에서 폴더 콘텐츠를 변경해야 합니다.

## 새로운 현지화 기능 지원을 위한 모범 사례 {#best-practices}

* Adobe은 적응형 양식을 만든 후 번역 프로젝트를 만들 것을 권장합니다.

* 기존 적응형 양식에 새 필드를 추가하는 경우:
   * **기계 번역의 경우**: 사전을 다시 만들고 번역 프로젝트를 실행합니다. 번역 프로젝트를 만든 후 적응형 양식에 추가된 필드는 번역되지 않은 상태로 유지됩니다.
   * **사람 번역의 경우**: `[server:port]/libs/cq/i18n/gui/translator.html`을(를) 통해 사전을 내보냅니다. 새로 추가된 필드의 사전을 업데이트하고 업로드합니다.


## 추가 참조 {#see-also}

{{see-also}}