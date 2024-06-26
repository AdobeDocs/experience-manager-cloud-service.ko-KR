---
title: 핵심 구성 요소를 기반으로 하는 적응형 양식에 새 로케일에 대한 지원을 추가하려면 어떻게 합니까?
description: 적응형 양식에 대한 새 로케일을 추가하는 방법을 알아봅니다.
feature: Adaptive Forms, Core Components
Role: Developer, Author
exl-id: bc06542b-84c8-4c6a-a305-effbd16d5630
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '2068'
ht-degree: 3%

---

# 핵심 구성 요소 기반 적응형 양식의 로케일 추가 {#supporting-new-locales-for-adaptive-forms-localization}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| 기초 구성 요소 | [여기 클릭](supporting-new-language-localization.md) |
| 핵심 구성 요소 | 이 문서 |

<span class="preview"> 오른쪽에서 왼쪽 쓰기 언어 지원 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

AEM Forms은 영어(en), 스페인어(es), 프랑스어(fr), 이탈리아어(it), 독일어(de), 일본어(ja), 포르투갈어-브라질어(pt-BR), 중국어(zh-CN), 중국어-대만(zh-TW) 및 한국어(ko-KR) 로케일을 즉시 지원합니다. 힌디어(hi_IN)와 같은 더 많은 로케일에 대한 지원을 추가할 수도 있습니다. 이러한 로케일을 추가하여 적응형 Forms을 아랍어, 페르시아어, 우르두어 등과 같은 RTL(오른쪽에서 왼쪽으로 쓰기) 언어로 표시할 수도 있습니다.

## AEM Forms은 적응형 양식에 대한 로케일을 어떻게 결정합니까?

AEM Forms에서 적응형 양식을 렌더링할 로케일을 선택하는 방법을 이해하는 것은 올바른 현지화에 중요합니다. 다음은 선택 프로세스에 대한 분류입니다.

### 우선 순위 기반 로케일 선택

AEM Forms은 다음 방법에 우선순위를 지정하여 적응형 양식에 대한 로케일을 결정합니다.

1. **URL 로케일 선택기 ([로케일])**:

   시스템은 를 사용하여 URL 내에 지정된 로케일의 우선 순위를 지정합니다. [로케일] 선택기. 이 형식을 사용하면 캐싱의 성능을 높일 수 있습니다.

   형식: URL은 http:/ 형식을 따릅니다.[AEM Forms 서버 URL]/content/forms/af/[afName].[로케일].html?wcmmode=disabled.

   예: https://[server]/content/forms/af/contact-us.hi.html은 힌디어로 양식을 렌더링합니다.


1. **afAcceptLang 요청 매개 변수**:

   사용자의 브라우저 로케일을 재정의하려면 `afAcceptLang` 매개 변수가 포함된 랜딩 페이지 URL의 매개 변수, URL의 매개 변수, URL의 매개 변수, URL의 매개 변수, URL의 매개 변수, URL의 매개 변수, URL의 매개 변수 등이 포함될 수 있습니다.

   예: https://[server]/forms/af/survey.ca-fr.html?afAcceptLang=ca-fr는 양식을 캐나다 프랑스어로 렌더링하도록 강제합니다.

1. **사용자의 브라우저 로케일(Accept-Language 헤더)**:

   다른 로케일이 지정되지 않은 경우 AEM Forms은 를 사용하여 전송되는 사용자의 브라우저 로케일을 고려합니다. `Accept-Language` 머리글입니다.


### 대체 메커니즘:


* 요청된 로케일에 대한 클라이언트 라이브러리(이 문서의 뒷부분에서 설명하는 새 로케일 추가 프로세스)를 사용할 수 없는 경우 AEM Forms은 로케일 내의 언어 코드를 기반으로 라이브러리를 확인합니다.

  예: en_ZA(남아프리카 영어)가 요청되고 en_ZA 라이브러리가 없는 경우 사용 가능한 경우 en(영어)을 사용합니다.

  적절한 클라이언트 라이브러리가 없으면 기본 사전(대부분 `en`) 양식의 작성 언어가 사용됩니다.

  로케일 정보가 없는 경우 적응형 양식은 개발 중에 사용된 원래 언어로 표시됩니다.


## 로케일 추가를 위한 사전 요구 사항

적응형 Forms에 대한 새 로케일 추가를 시작하기 전에 다음을 확인하십시오.

**소프트웨어:**

* IDE(일반 텍스트 편집기): 모든 일반 텍스트 편집기가 작동하지만 IDE(통합 개발 환경)와 같은 [Microsoft Visual Studio 코드](https://code.visualstudio.com/download) 에서는 보다 쉽게 편집할 수 있는 고급 기능을 제공합니다.

* Git: 이 버전 제어 시스템은 코드 변경 사항을 관리하는 데 필요합니다. 설치되지 않은 경우 다음에서 다운로드하십시오. [https://git-scm.com](https://git-scm.com).


**코드 저장소:**

적응형 Forms 핵심 구성 요소 저장소 복제: 로케일을 추가하려면 이 저장소의 클라이언트 라이브러리가 필요합니다. 저장소를 복제하려면 다음을 수행하십시오.

1. 명령줄 또는 터미널 창을 엽니다.

1. 저장소를 저장할 컴퓨터에서 원하는 위치(예: /adaptive-forms-core-components)로 이동합니다.

1. 다음 명령을 실행하여 저장소를 복제합니다.

   ```
   git clone https://github.com/adobe/aem-core-forms-components.git
   ```

   이 명령은 저장소를 다운로드하고 다음 이름의 폴더를 만듭니다. `aem-core-forms-components` 컴퓨터에 있습니다. 이 안내서 전체에서 이 폴더는 다음과 같습니다. `[Adaptive Forms Core Components repository]`


## 로케일 추가 {#add-localization-support-for-non-supported-locales}

핵심 구성 요소를 기반으로 하는 적응형 양식에 새 로케일에 대한 지원을 추가하려면 다음 단계를 따르십시오.

### AEM as a Cloud Service Git 리포지토리 복제

1. 명령줄을 열고 AEM as a Cloud Service 저장소를 저장할 디렉터리(예: )를 선택합니다. `/cloud-service-repository/`.

1. 아래 명령을 실행하여 저장소를 복제합니다.

   ```SHELL
   git clone https://git.cloudmanager.adobe.com/<organization-name>/<program id>/
   ```

   Git 저장소를 복제하려면 다음 정보가 필요합니다.

   * **조직 이름**: Adobe Experience Manager as a Cloud Service(AEM as a Cloud Service) 내에서 팀 또는 프로젝트를 식별합니다.

   * **프로그램 ID**: 저장소와 연결된 프로그램을 지정합니다.

   * **자격 증명**: 저장소에 안전하게 액세스하려면 사용자 이름과 암호(또는 개인 액세스 토큰)가 필요합니다.

   **이 정보는 어디에서 찾을 수 있습니까?**

   이러한 세부 정보를 찾는 단계별 지침은 Adobe Experience League 문서 &quot; 를 참조하십시오.[Git 액세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git)&quot;.

   **프로젝트가 준비되었습니다!**

   명령이 성공적으로 완료되면 로컬 디렉터리에 새 폴더가 생성됩니다. 이 폴더의 이름은 프로그램 이름을 따라 지정합니다(예: program-id). 이 폴더에는 AEM as a Cloud Service Git 저장소에서 다운로드한 모든 파일과 코드가 포함되어 있습니다.

   이 안내서 전체에서 이 폴더는 다음과 같습니다. `[AEMaaCS project directory]`.


### 가이드 현지화 서비스에 새 로케일 추가

1. 편집기에서 저장소 폴더를 엽니다.

   ![편집기의 저장소 폴더](/help/forms/assets/repository-folder-in-an-editor.png)

1. 를 찾습니다. `Guide Localization Service.cfg.json` 파일. 이 파일은 AEM Forms 애플리케이션에서 지원하는 로케일을 제어합니다. 이 파일을 편집하여 새 로케일을 추가할 수 있습니다.

   * **기존 파일**: 파일이 이미 있는 경우 AEM Forms 프로젝트 디렉터리 내에서 찾습니다. 일반적인 위치는 다음과 같습니다.

     ```Shell
     [AEMaaCS project directory]/ui.config/src/main/content/jcr_root/apps/<appid>/osgiconfig/config`. 
     ```

     바꾸기 `<appid>` (프로젝트별 앱 ID 포함) 다음을 찾을 수 있습니다. `<appid>` 의 AEM 프로젝트용 `archetype.properties` 파일.

     ![Archetype 속성](/help/forms/assets/archetype-properties.png)

   * **새 파일**: 파일이 없는 경우 위에 언급된 동일한 위치에 파일을 만들어야 합니다. 복사한 후 이 문서의 파일 이름을 붙여넣지 말고 수동으로 이름을 입력합니다. 파일 이름 `Guide Localization Service.cfg.json` 에는 공백이 포함되어 있습니다. 이는 의도적인 것이며 설명서에 오타가 아닙니다.

     지원되는 OOTB 로케일 목록이 있는 샘플 파일은 다음과 같습니다.

     ```
         {
             "supportedLocales":[
             "en",
             "fr",
             "de",
             "ja",
             "pt-br",
             "zh-cn",
             "zh-tw",
             "ko-kr",
             "it",
             "es"
             ]
         }
     ```

1. 원하는 언어의 로케일 코드를 파일에 추가합니다.
   1. 사용 [코드 목록](https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes) 원하는 언어를 나타내는 두 글자로 된 코드를 찾습니다.

   1. 로케일 코드를 `Guide Localization Service.cfg.json` 파일. 다음은 몇 가지 예입니다.

      * 왼쪽에서 오른쪽 언어:
         * 영어(미국): en-US
         * 스페인어(스페인): es-ES
         * 프랑스어(프랑스): fr-FR
      * 오른쪽에서 왼쪽 쓰기 언어:
         * 아랍어(아랍에미리트): ar-ae
         * 히브리어: he(또는 historical reference)
         * Farsi: fa

1. 변경 후 다음을 확인합니다. `Guide Localization Service.cfg.json` 파일은 유효한 JSON 파일로 형식이 올바르게 지정됩니다. JSON 형식 지정 시 오류가 발생하여 제대로 작동하지 않을 수 있습니다. 파일을 저장합니다.



### 샘플 클라이언트 라이브러리를 활용하여 로케일을 쉽게 추가할 수 있습니다

AEM Forms은 유용한 샘플 클라이언트 라이브러리를 제공합니다. `clientlib-it-custom-locale`를 입력하여 새 로케일 추가를 단순화합니다. 이 라이브러리는 [적응형 Forms 핵심 구성 요소 저장소](https://github.com/adobe/aem-core-forms-components), GitHub에서 사용 가능합니다.


시작하기 전에 의 로컬 복사본이 있는지 확인합니다. [적응형 Forms 핵심 구성 요소 저장소]. 그렇지 않은 경우 다음 명령과 함께 Git을 사용하여 쉽게 복제할 수 있습니다.

```SHELL
git clone https://github.com/adobe/aem-core-forms-components.git
```

이 명령은 clientlib-it-custom-locale 라이브러리를 포함한 전체 저장소를 시스템의 aem-core-forms-components라는 디렉터리에 다운로드합니다.

![로컬 컴퓨터의 적응형 Forms 핵심 구성 요소 저장소 디렉터리](/help/forms/assets/core-forms-components-repo-on-local-machine.png)

### 샘플 클라이언트 라이브러리 통합

이제 다음을 통합하겠습니다. `clientlib-it-custom-locale` AEM as a Cloud Service에 라이브러리를 추가합니다. [AEMaaCS 프로젝트 디렉터리]:

1. 샘플 클라이언트 라이브러리를 찾습니다.

   의 로컬 복사본 내 [적응형 Forms 핵심 구성 요소 저장소]를 클릭하고 다음 경로로 이동합니다.

   ```
       /aem-core-forms-components/it/apps/src/main/content/jcr_root/apps/forms-core-components-it/clientlibs
   ```

1. 라이브러리를 복사하여 붙여넣습니다.

   1. 다음을 복사합니다. `clientlib-it-custom-locale` 폴더를 삭제합니다.

      ![clientlib-it-custom-locale 복사](/help/forms/assets/clientlib-it-custom-locale-copy.png)

   1. 내에서 다음 디렉토리로 이동합니다. [AEMaaCS 프로젝트 디렉터리]:

      ```
      /ui.apps/src/main/content/jcr_root/apps/<app-id>/clientlib
      ```

      **중요 사항**: 바꾸기 `<app-id>` (애플리케이션의 실제 ID 포함)

   1. 복사한 항목 붙여넣기 `clientlib-it-custom-locale` 폴더를 이 디렉터리에 추가합니다.

      ![clientlib-it-custom-locale 붙여넣기](/help/forms/assets/clientlib-it-custom-locale-paste.png)


### 새 로케일에 대한 파일 만들기:

1. 로케일 디렉토리로 이동합니다.

   내 `[AEMaaCS project directory]`를 클릭하고 다음 경로로 이동합니다.

   ```
       /ui.apps/src/main/content/jcr_root/apps/<program-id>/clientlibs/clientlib-it-custom-locale/resources/i18n/
   ```

   **중요 사항**: 바꾸기 `<program-id>` (실제 애플리케이션 ID 포함)

1. 샘플 영어 언어 파일을 찾습니다.

   AEM Forms은 [GitHub의 샘플 영어 로케일 파일(.json)](https://github.com/adobe/aem-core-forms-components/blob/master/ui.af.apps/src/main/content/jcr_root/apps/core/fd/af-clientlibs/core-forms-components-runtime-all/resources/i18n/en.json).

   영어 파일에는 참조용 기본 문자열 집합이 포함되어 있습니다. 로케일별 파일은 영어 파일의 구조를 모방해야 합니다.

   아랍어, 히브리어, 페르시아어와 같은 언어의 경우, 영어와 같이 왼쪽에서 오른쪽으로(LTR) 대신 오른쪽에서 왼쪽으로(RTL) 텍스트를 읽습니다. 양식이 이러한 언어로 올바르게 표시되도록 하려면 샘플 로케일 파일을 안내서로 사용하는 것이 좋습니다. 이러한 파일은 RTL 언어의 텍스트, 날짜 및 기타 요소 서식을 지정하는 방법에 대한 참조를 제공합니다. 샘플 로케일 파일을 찾을 수 있습니다.

   * [아랍어](/help/forms/assets/ar-ae.json)
   * [히브리어](/help/forms/assets/he.json)
   * [페르시아어](/help/forms/assets/fa.json)

   이러한 샘플 파일을 활용하면 양식이 RTL 언어로 작업하는 사용자에게 원활한 경험을 제공할 수 있습니다.


1. 로케일 파일 만들기:

   1. 내에 새 .json 파일 만들기 `i18n` 디렉토리.
   1. 원하는 언어에 적합한 로케일 코드를 사용하여 파일의 이름을 지정합니다(예: 프랑스어의 경우 fr-FR.json, 아랍어의 경우 ar-ae.json). 이 파일의 구조는 영어 로케일 파일을 미러링해야 합니다.


1. 구조 및 번역:

   1. 텍스트 편집기에서 새로 만든 파일을 엽니다.

   1. 영어 값을 대상 언어에 해당하는 번역으로 바꿉니다.

   1. 문자열 번역이 완료되면 파일을 저장합니다.




### 사전에 로케일 지원 추가

이 단계는 영어(en), 독일어(de), 스페인어(es), 프랑스어(fr), 이탈리아어(it), 포르투갈어(pt-br), 중국어(간체 - zh_cn), 중국어(번체 - zh_tw), 일본어(ja) 및 한국어(ko_kr) 이외의 로케일만 적용됩니다.

1. 구성 폴더를 찾습니다.

   에서 다음 디렉토리로 이동합니다. [AEMaaCS 프로젝트 디렉터리]:

   ```
   /ui.content/src/main/content/jcr_root/etc
   ```

1. 필요한 폴더를 만듭니다(누락된 경우).

   다음과 같은 경우 `etc` 다음 내에 폴더가 없습니다. `jcr_root` 폴더를 생성합니다. 내부 `etc`, (이)라는 다른 폴더를 만듭니다. `languages` 만약 없어진 거라면

1. 로케일 구성 파일을 만듭니다.

   다음 범위 내 `languages` 폴더, (이)라는 이름의 새 파일 만들기 `.content.xml`. 복사한 후 이 문서의 파일 이름을 붙여넣지 말고 수동으로 이름을 입력합니다.

   ![이름이 인 새 파일 만들기 `.content.xml`](etc-content-xml.png)

   이 파일을 열고 다음 내용을 붙여넣고 바꿉니다. [로케일_코드] 를 사용하십시오(예: 아랍어의 경우 ar-ae).


   ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0"
         jcr:primaryType="nt:unstructured"
         languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi]"/>
   ```

   경고: 기존 목록을 바꾸지 마십시오. 대신 새 로케일 코드를 대괄호 안에 넣고 다음과 같이 쉼표로 구분합니다(예: ar-ae 사용).

   ```XML
   languages="[de,es,fr,it,pt-br,zh-cn,zh-tw,ja,ko-kr,hi,ar-ae]"
   ```

1. filter.xml에 새 폴더 포함:

   다음 위치로 이동 `/ui.content/src/main/content/meta-inf/vault/filter.xml` 파일 위치: [AEMaaCS 프로젝트 디렉터리].

   파일을 열고 끝에 다음 줄을 추가합니다.

   ```
   <filter root="/etc/languages"/>
   ```

   ![에서 생성된 폴더 추가 `filter.xml` 아래에 `/ui.content/src/main/content/meta-inf/vault/filter.xml`](langauge-filter.png)

1. 파일을 저장합니다.

### 새로 생성된 로케일을 AEM 환경에 배포

이제 적응형 Forms에 새 로케일을 사용하도록 모두 설정되었습니다. 다음을 수행할 수 있습니다.

* AEM as a Cloud Service 배포, [AEMaaCS 프로젝트 디렉터리]로컬 컴퓨터에서 새 로케일 구성을 시도하려면 로컬 개발 환경으로 이동하십시오. 로컬 개발 환경에 배포하려면 다음을 수행하십시오.

   1. 로컬 개발 환경이 실행 중인지 확인합니다. 아직 로컬 개발 환경을 설정하지 않았다면 의 안내서를 참조하십시오. [AEM Forms용 로컬 개발 환경 설정](/help/forms/setup-local-development-environment.md).

   1. 터미널 창이나 명령 프롬프트를 엽니다.

   1. 다음 위치로 이동 [AEMaaCS 프로젝트 디렉터리]

   1. 다음 명령을 실행합니다.

      ```
      mvn -PautoInstallPackage clean install
      ```

* AEM as a Cloud Service 배포, [AEMaaCS 프로젝트 디렉터리]을 클릭하여 Cloud Service 환경에 추가합니다. Cloud Service 환경에 배포하려면 다음을 수행하십시오.

   1. 변경 내용 커밋:

      새 로케일 구성을 추가한 후 로케일 추가를 설명하는 명확한 Git 메시지로 변경 사항을 커밋합니다(예: &quot;지원 추가됨&quot;). [로케일 이름]&quot;).

   1. 업데이트된 코드를 배포합니다.

      다음을 통해 코드 배포 트리거 [기존 전체 스택 파이프라인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=ko-KR#setup-pipeline). 이렇게 하면 새 로케일 지원을 통해 업데이트된 코드를 자동으로 빌드하고 배포합니다.

      파이프라인을 아직 설정하지 않았다면 의 안내서를 참조하십시오. [AEM Formsas a Cloud Service 용 파이프라인을 설정하는 방법](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=ko-KR#setup-pipeline).


## 새로 추가된 로케일이 있는 적응형 양식 미리 보기

다음 단계는 새로 추가된 로케일이 있는 적응형 양식을 미리 보는 과정을 안내합니다.

1. AEM Forms as a Cloud Service 인스턴스에 로그인합니다.
1. 다음으로 이동 **Forms** >  **Forms 및 문서**.
1. 적응형 양식을 선택하고 **사전 추가** 및 **사전을 번역 프로젝트에 추가** 마법사가 나타납니다.
1. 다음을 지정합니다. **프로젝트 제목** 및 선택 **타겟 언어** 드롭다운 메뉴 아래의 **사전을 번역 프로젝트에 추가** 마법사.
1. 클릭 **완료** 생성된 번역 프로젝트를 실행합니다.
1. 다음으로 이동 **Forms** >  **Forms 및 문서**.
1. 적응형 양식을 선택하고 **HTML으로 미리 보기** 옵션을 선택합니다.
1. 추가 `&afAcceptLang=<locale-name>` 미리보기 URL로 이동하고 return 키를 누릅니다. 바꾸기 `<locale-name>` 실제 로케일 코드를 사용하여 적응형 양식이 지정된 로케일에 표시됩니다.

## 새로운 현지화 기능 지원을 위한 모범 사례 {#best-practices}

* Adobe은 적응형 양식을 만든 후 번역 프로젝트를 만들 것을 권장합니다. 현지화 프로세스를 간소화합니다.
* 숫자 상자 및 날짜 선택기 구성 요소가 특정 로케일로 변환되면 형식 문제가 발생할 수 있습니다. 이를 완화하려면 **언어** 옵션이 의 구성 대화 상자에 통합되었습니다. [날짜 선택기 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/date-picker#format-tab) 및 [숫자 상자 구성 요소](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/numeric-box#formats-configure-tab).


* 새 필드 처리:

   * **기계 번역**: 기계 번역을 사용하는 경우 사전을 다시 만들고 다시 만들어야 합니다.[번역 프로젝트 실행](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms-core-components.md) 기존 적응형 양식에 새 필드를 추가한 후 초기 번역 프로젝트 이후에 추가된 새 필드는 번역되지 않은 상태로 유지됩니다.

   * **사람 번역**: 사람 번역 워크플로의 경우 의 UI를 사용하여 사전을 내보냅니다. `[AEM Forms Server]/libs/cq/i18n/gui/translator.html`. 새 필드의 사전을 업데이트하고 수정된 버전을 업로드합니다.


## 추가 참조 {#see-also}

{{see-also}}

* [적응형 Forms에 대한 기록 문서 생성](/help/forms/generate-document-of-record-core-components.md)
* [AEM Sites 페이지 또는 경험 조각에 적응형 양식 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

