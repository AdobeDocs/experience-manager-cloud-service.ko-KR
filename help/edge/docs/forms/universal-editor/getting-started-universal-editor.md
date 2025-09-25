---
title: 범용 편집기를 사용하여 AEM Forms용 Edge Delivery Services 시작하기
description: 범용 편집기의 WYSIWYG 작성 기능을 갖춘 Edge Delivery Services를 사용하여 고성능 양식을 만들고 게시하는 방법에 대해 알아봅니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
exl-id: 24a23d98-1819-4d6b-b823-3f1ccb66dbd8
source-git-commit: fd3c53cf5a6d1c097a5ea114a831ff626ae7ad7e
workflow-type: ht
source-wordcount: '2608'
ht-degree: 100%

---


# 범용 편집기를 사용하여 AEM Forms용 Edge Delivery Services 시작하기

| 작성 방법 | 안내서 |
|---------------------------------|-----------------------------------------------------------------------|
| **범용 편집기 (WYSIWYG)** | 이 문서 |
| **문서 기반 작성** | [문서 기반 튜토리얼](/help/edge/docs/forms/tutorial.md) |

AEM Forms용 Edge Delivery Services는 고성능 웹 게재와 범용 편집기의 WYSIWYG 작성을 결합합니다. 이 안내서는 빠르게 로드되는 양식을 만들고, 사용자 정의하고, 게시하는 방법에 대해 다룹니다.

## 학습 내용

이 튜토리얼을 완료하면 다음과 같은 작업을 수행할 수 있습니다.

- 적응형 양식 블록으로 GitHub 저장소 설정
- Edge Delivery Services와 통합된 AEM 사이트 만들기
- 범용 편집기를 사용하여 양식 작성 및 게시
- 로컬 개발 환경 구성

## 경로 선택

시나리오와 일치하는 접근 방식을 선택합니다.

![경로 선택 결정 안내서](/help/edge/docs/forms/universal-editor/assets/choose-your-path.svg)
*그림: 올바른 구현 경로를 선택하는 데 도움이 되는 시각적 안내서*

| **경로 A: 새 프로젝트** | **경로 B: 기존 프로젝트** |
|----------------------------------------|-------------------------------------------|
| 미리 구성된 템플릿으로 시작 | 현재 AEM 프로젝트에 양식 추가 |
| 새로운 구현에 **가장 적합** | 기존 AEM Sites에 **가장 적합** |
| **이점:** 사전 구성된 양식 블록 | **이점:** 기존 사이트에 양식 추가 |
| **단계:** 템플릿 → 설정 → 양식 | **단계:** 통합 → 구성 → 양식 |
| [경로 A로 시작](#path-a-create-new-project-with-forms) | [경로 B로 시작](#path-b-add-forms-to-existing-project) |

## 사전 요구 사항

범용 편집기를 사용하는 AEM Forms용 Edge Delivery Services를 원활하고 성공적으로 경험하려면 계속 진행하기 전에 다음 전제 조건을 검토하고 확인하십시오.

### 액세스 요구 사항

- **GitHub 계정**: 새 저장소를 생성하려면 권한이 있는 GitHub 계정이 있어야 합니다. 이는 프로젝트 소스 코드를 관리하고 팀과 공동 작업하는 데 필수적입니다.
- **AEM as a Cloud Service 작성 액세스**: AEM as a Cloud Service 환경에 대한 작성자 레벨 액세스 권한이 있는지 확인합니다. 이 액세스 권한은 양식을 만들고, 편집하고, 게시하는 데 필요합니다.

### 기술 요구 사항

- **Git에 대한 이해**: 저장소 복제, 변경 사항 커밋, 업데이트 푸시와 같은 기본 Git 작업을 수행하는 데 능숙해야 합니다. 이러한 기술은 소스 제어 및 프로젝트 공동 작업을 위한 기본 사항입니다.
- **웹 기술에 대한 이해**: HTML, CSS 및 JavaScript에 대한 실무 지식이 권장됩니다. 이러한 기술은 양식 사용자 정의 및 문제 해결의 기반을 형성합니다.
- **Node.js(버전 16 이상)**: Node.js는 로컬 개발 및 빌드 도구 실행에 필요합니다. 시스템에 버전 16 이상이 설치되어 있는지 확인합니다.
- **패키지 관리자(npm 또는 yarn)**: 프로젝트 종속성 및 스크립트를 관리하려면 npm(Node Package Manager) 또는 yarn이 필요합니다.

### 권장 배경

- **AEM Sites** 개념: 사이트 구조 및 콘텐츠 작성 등 AEM Sites에 대한 기본적인 이해는 양식을 효과적으로 탐색하고 통합하는 데 도움이 됩니다.
- **양식 디자인 원칙**: 유용성, 접근성 및 데이터 유효성 검사와 같은 양식 디자인 모범 사례에 익숙하면 효과적이고 사용자 친화적인 양식을 만들 수 있습니다.
- **WYSIWYG 편집기 사용 경험**: WYSIWYG(What You See Is What You Get) 편집기 사용에 대한 사전 경험이 있으면 범용 편집기의 시각적 작성 기능을 보다 효율적으로 활용하는 데 도움이 됩니다.

>[!TIP]
>
> AEM을 처음 사용하십니까? [AEM Sites 시작 안내서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/quick-start.html?lang=ko)로 시작합니다.

## 경로 A: Forms를 사용하여 새 프로젝트 만들기

**권장 대상:** 새로운 프로젝트, 파일럿 또는 개념 증명 이니셔티브

AEM Forms 상용구를 활용하여 프로젝트 설정을 가속화합니다. 이 상용구는 적응형 양식 블록을 원활하게 통합하는 즉시 사용 가능한 템플릿을 제공하여 AEM Site 내에서 양식을 신속하게 작성하고 배포할 수 있습니다.

### 개요

통합된 양식으로 새 프로젝트를 성공적으로 시작하려면 다음을 수행합니다.

1. AEM Forms 상용구 템플릿을 사용하여 GitHub 저장소를 만듭니다.
2. AEM Code Sync를 설정하여 AEM과 저장소 간의 콘텐츠 동기화를 자동화합니다.
3. GitHub 프로젝트와 AEM 환경 간의 연결을 구성합니다.
4. 새 AEM Site를 설정하고 게시합니다.
5. 범용 편집기를 사용하여 양식을 추가하고 관리합니다.

다음 섹션에서는 각 단계를 자세히 안내하여 원활하고 효율적인 프로젝트 설정 경험을 보장합니다.

+++1단계: 템플릿에서 GitHub 저장소 만들기

1. **AEM Forms 상용구 템플릿에 액세스**
   - [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms)로 이동

   ![AEM Forms 상용구 템플릿](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   *그림: 사전 구성된 적응형 양식 블록이 있는 AEM Forms 상용구 저장소*

2. **저장소 만들기**
   - **이 템플릿 사용** > **새 저장소 만들기**&#x200B;를 클릭합니다.

   ![템플릿으로 저장소 만들기](/help/edge/docs/forms/assets/use-eds-form-template.png)
   *그림: 템플릿을 사용하여 새 저장소 만들기*

3. **저장소 설정 구성**
   - **소유자**: GitHub 계정 또는 조직 선택
   - **저장소 이름**: 설명적인 이름 선택 (예: `my-forms-project`)
   - **가시성**: **공개** 선택 (Edge Delivery Services에 권장됨)
   - **저장소 만들기**&#x200B;를 클릭합니다.

   ![저장소 구성](/help/edge/docs/forms/assets/name-eds-repo.png)
   *그림: 공개 가시성을 갖춘 새 저장소 구성*

**유효성 검사:** AEM Forms 상용구 템플릿을 기반으로 한 새 GitHub 저장소가 있는지 확인합니다.

+++

+++2단계: AEM Code Sync 설치

AEM Code Sync는 AEM 저작 환경과 GitHub 저장소 간에 콘텐츠 변경 사항을 자동으로 동기화합니다.

1. **GitHub 앱 설치**
   - [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new)로 이동

2. **액세스 권한 구성**
   - **선택한 저장소만** 선택
   - 새로 만든 저장소 선택
   - **저장** 클릭

   ![AEM Code Sync 설치](/help/edge/docs/forms/assets/aem-code-sync-up.png)
   *그림: 저장소별 권한으로 AEM Code Sync 설치*

**체크포인트:** AEM Code Sync가 설치되었으며 이제 저장소에 액세스할 수 있습니다.

+++

+++3단계: AEM 통합 구성

`fstab.yaml` 파일은 콘텐츠 동기화를 위해 GitHub 저장소를 AEM 저작 환경에 연결합니다.

1. **저장소로 이동**
   - 새로 만든 GitHub 저장소로 이동
   - AEM Forms 상용구 파일을 확인해야 합니다.

2. **fstab.yaml 파일 만들기**
   - 루트 디렉터리에서 **파일 추가** > **새 파일 만들기**&#x200B;를 클릭
   - `fstab.yaml`로 파일 이름 지정

   ![fstab.yaml 파일 만들기](/help/edge/docs/forms/assets/open-fstab.png)
   *그림: fstab.yaml 구성 파일 만들기*

3. **AEM 연결 세부 정보 추가**

   다음 구성을 복사하여 붙여넣고 플레이스홀더를 바꿉니다.

   ```yaml
   mountpoints:
     /: 
     url: https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main
     type: "markup" 
     suffix: ".html" 
   ```

   **바꾸기:**
   - `<aem-author>`: AEM as a Cloud Service 작성자 URL (예: `author-p12345-e67890.adobeaemcloud.com`)
   - `<owner>`: GitHub 사용자 이름 또는 조직
   - `<repository>`: 저장소 이름

   **예:**

   ```yaml
   mountpoints:
     /: https://author-p12345-e67890.adobeaemcloud.com/bin/franklin.delivery/mycompany/my-forms-project/main
   ```

   ![fstab.yaml 파일 편집](/help/edge/docs/forms/assets/edit-fstab-file.png)
   *그림: AEM 통합을 위한 마운트 지점 구성*

4. **구성 커밋**
   - 커밋 메시지 추가: “AEM 통합 구성 추가”
   - **새 파일 커밋** 클릭

   ![fstab 변경 사항 커밋](/help/edge/docs/forms/assets/commit-fstab-changes.png)
   *그림: fstab.yaml 구성 커밋*

**유효성 검사:** AEM에 대한 GitHub 저장소 연결을 확인합니다.

>[!NOTE]
>
> 빌드 문제가 있습니까? [GitHub 빌드 문제 해결](#troubleshooting-github-build-issues)을 참조하십시오.

+++

+++4단계: GitHub 저장소에 연결된 AEM 사이트를 만듭니다.

1. **AEM Sites 콘솔 액세스**
   - AEM as a Cloud Service 작성자 인스턴스에 로그인
   - **Sites**&#x200B;로 이동

   ![AEM Sites 콘솔](/help/edge/assets/select-sites.png)
   *그림: AEM Sites 콘솔 액세스*

2. **사이트 생성 시작**
   - **만들기** > **템플릿으로 사이트 만들기** 선택

   ![사이트 생성 옵션](/help/edge/docs/forms/assets/create-sites.png)
   *그림: 템플릿으로 새 사이트 생성*

3. **Edge Delivery Services 템플릿 선택**
   - **Edge Delivery Services 사이트** 템플릿 선택
   - **다음** 클릭

   ![사이트 템플릿 선택](/help/edge/docs/forms/assets/select-site-template.png)
   *그림: Edge Delivery Services 사이트 템플릿 선택*

   >[!NOTE]
   >
   >**템플릿을 사용할 수 없습니까?** Edge Delivery Services 템플릿이 표시되지 않는 경우:
   >
   >1. **가져오기**&#x200B;를 클릭하여 템플릿 업로드
   >2. [GitHub 릴리스](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases)에서 템플릿 다운로드

4. **사이트 구성**

   다음 정보를 입력합니다.

   | 필드 | 값 | 예 |
   |-----------------|-----------------------------|-----------------------------------------|
   | **사이트 제목** | 사이트에 대한 설명적인 이름 | “내 양식 프로젝트” |
   | **사이트 이름** | URL에 적합한 이름 | “my-forms-project” |
   | **GitHub URL** | 저장소 URL | `https://github.com/mycompany/my-forms-project` |

   ![사이트 구성](/help/edge/docs/forms/assets/create-aem-site.png)
   *그림: GitHub 통합으로 새 AEM 사이트 구성*

5. **사이트 생성 완료**
   - 설정 검토
   - **만들기**&#x200B;를 클릭합니다.

   ![사이트 생성 확인](/help/edge/docs/forms/assets/click-ok-aem-site.png)
   *그림: 사이트 생성 확인*

   **성공** AEM 사이트가 이제 생성되어 GitHub에 연결되었습니다.

6. **범용 편집기에서 열기**
   - Sites 콘솔에서 새 사이트 찾기
   - `index` 페이지 선택
   - **편집** 클릭

   ![범용 편집기에서 사이트 편집](/help/edge/docs/forms/assets/edit-site.png)
   *그림: 편집을 위해 사이트 열기*

   범용 편집기가 새 탭에서 열리고 WYSIWYG 작성 기능이 제공됩니다.

   ![범용 편집기 인터페이스](/help/edge/docs/forms/assets/site-in-universal-editor.png)
   *그림: WYSIWYG 편집을 위해 범용 편집기에서 열린 사이트*

**유효성 검사:** AEM 사이트에서 양식 작성을 수행할 준비가 되었는지 확인합니다.

+++

+++5단계: 사이트 게시

게시를 통해 귀하의 사이트를 Edge Delivery Services에 제공하면 전 세계에서 액세스할 수 있습니다.

1. **Sites 콘솔에서 빠른 게시**
   - AEM Sites 콘솔로 돌아가기
   - 사이트 페이지 선택 (또는 Ctrl+A를 눌러 모두 선택)
   - **빠른 게시** 클릭

   ![AEM 사이트 게시](/help/edge/docs/forms/assets/publish-sites.png)
   *그림: 빠른 게시를 위해 페이지 선택*

2. **게시 확인**
   - 확인 대화 상자에서 **게시**&#x200B;를 클릭합니다.

   ![빠른 게시 대화 상자](/help/edge/docs/forms/assets/quick-publish.png)
   *그림: 게시 작업 확인*

   **대안:** 범용 편집기에서 게시 버튼을 사용하여 직접 게시할 수도 있습니다.

   ![범용 편집기에서 게시](/help/edge/docs/forms/assets/qui.png)
   *그림: 범용 편집기에서 직접 게시*

3. **라이브 사이트 액세스**

   이제 사이트가 다음 위치에서 활성화됩니다.

   ```
   https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/
   ```

   **URL 구조 설명:**
   - `<branch>`: GitHub 분기 (일반적으로 `main`)
   - `<repo>`: 저장소 이름
   - `<owner>`: GitHub 사용자 이름 또는 조직
   - `<site-name>`: AEM 사이트 이름

   **예:**

   ```
   https://main--my-forms-project--mycompany.aem.page/content/my-forms-project/
   ```

**유효성 검사:** 사이트가 Edge Delivery Services에서 활성화되어 있는지 확인합니다.

>[!TIP]
>
> **URL 패턴:**
>
> - **홈 페이지:** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`
> - **기타 페이지:** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/<page-name>`

**다음 단계:** [첫 번째 양식 만들기](#create-your-first-form)

+++

## 경로 B: 기존 프로젝트에 양식 추가

Edge Delivery Services를 제공하는 기존 AEM Sites에 **가장 적합**

Edge Delivery Services를 사용하는 기존 AEM 프로젝트가 이미 있는 경우 적응형 양식 블록을 통합하여 양식 기능을 추가할 수 있습니다.

### 경로 B의 사전 요구 사항

기존 AEM 프로젝트에 양식을 통합하려면 다음 전제 조건이 충족되었는지 확인합니다.

- [AEM 상용구 XWalk](https://github.com/adobe-rnd/aem-boilerplate-xwalk)를 사용하여 기존 AEM 프로젝트를 만들었습니다.
- [로컬 개발 환경이 설정](#set-up-local-development-environment)되어 있습니다.
- 프로젝트 저장소에 Git 액세스 권한이 있으므로 필요에 따라 변경 사항을 복제, 수정 및 푸시할 수 있습니다.

>[!NOTE]
>
> 프로젝트가 [AEM Forms 상용구](https://github.com/adobe-rnd/aem-boilerplate-forms)를 사용하여 원래 설정된 경우 양식 기능이 이미 포함되어 있습니다. 이 경우 [첫 번째 양식 만들기](#create-your-first-form) 섹션으로 이동할 수 있습니다.

다음 안내서는 기존 프로젝트에 양식 기능을 추가하기 위한 체계적인 접근 방식을 제공합니다. 각 단계는 범용 편집기 환경 내에서 원활한 통합 및 최적의 기능을 보장하도록 설계되었습니다.

### 개요

다음 높은 수준의 단계를 완료하게 됩니다.

1. 적응형 양식 블록 파일을 프로젝트에 복사합니다.
2. 양식 구성 요소를 인식하고 지원하도록 프로젝트의 구성을 업데이트합니다.
3. ESLint 규칙을 조정하여 새 파일 및 코딩 패턴을 수용합니다.
4. 프로젝트를 빌드하고 변경 사항을 저장소에 커밋합니다.

+++1단계: 양식 블록 파일 복사

1. **로컬 프로젝트로 이동**

   ```bash
   cd /path/to/your/aem-project
   ```

2. **AEM Forms 상용구에서 필요한 파일 다운로드**

   [AEM Forms 상용구 저장소](https://github.com/adobe-rnd/aem-boilerplate-forms)에서 다음 파일을 복사합니다.

   | 소스 | 대상 | 용도 |
   |------------------------------------------------------------------------|----------------------------|----------------------------|
   | [`blocks/form/`](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/blocks/form) | `blocks/form/` | 핵심 양식 기능 |
   | [`scripts/form-editor-support.js`](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.js) | `scripts/form-editor-support.js` | 범용 편집기 통합 |
   | [`scripts/form-editor-support.css`](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.css) | `scripts/form-editor-support.css` | 편집기 스타일 지정 |

3. **편집기 지원 업데이트**
   - `/scripts/editor-support.js` 파일을 [AEM Forms 상용구의 editor-support.js](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/editor-support.js)로 바꾸기

**유효성 검사:** 양식 블록 파일이 프로젝트에 있는지 확인합니다.

+++

+++2단계: 구성 요소 구성 업데이트

1. **섹션 모델 업데이트**

   `/models/_section.json`을 열고 필터에 양식 구성 요소를 추가합니다.

   ```json
   {
        "filters": [
        {
      "id": "section",
      "components": [
           "text",
           "image",
           "button",
        "form",
        "embed-adaptive-form"
      ]
       }
     ]
   }
   ```

   **이 작업의 기능:** 범용 편집기 구성 요소 선택기에서 양식 구성 요소를 활성화합니다.

**유효성 검사:** 범용 편집기에 양식 구성 요소가 나타나는지 확인합니다.

+++

+++3단계: ESLint 구성 (선택 사항)

**이 단계를 수행하는 이유:** 양식별 파일의 린팅 오류를 방지하고 적절한 유효성 검사 규칙을 구성합니다.

1. **.eslintignore 업데이트**

   `/.eslintignore`에 다음 행을 추가합니다.

   ```bash
   # Form block rule engine files
   blocks/form/rules/formula/*
   blocks/form/rules/model/*
   blocks/form/rules/functions.js
   scripts/editor-support.js
   scripts/editor-support-rte.js
   ```

2. **.eslintrc.js 업데이트**

   `/.eslintrc.js`의 `rules` 오브젝트에 다음 규칙을 추가합니다.

   ```javascript
   {
     "rules": {
       // Existing rules...
   
       // Form component cell limits
    'xwalk/max-cells': ['error', {
         '*': 4, // default limit
      form: 15,
      wizard: 12,
      'form-button': 7,
      'checkbox-group': 20,
      checkbox: 19,
      'date-input': 21,
      'drop-down': 19,
      email: 22,
      'file-input': 20,
      'form-fragment': 15,
      'form-image': 7,
      'multiline-input': 23,
      'number-input': 22,
      panel: 17,
      'radio-group': 20,
      'form-reset-button': 7,
      'form-submit-button': 7,
      'telephone-input': 20,
      'text-input': 23,
      accordion: 14,
      modal: 11,
      rating: 18,
      password: 20,
         tnc: 12
       }],
   
       // Disable this rule for forms
       'xwalk/no-orphan-collapsible-fields': 'off'
     }
   }
   ```

**유효성 검사:** ESLint가 양식 구성 요소와 함께 작동하는지 확인합니다.

+++

+++4단계: 빌드 및 배포

1. **종속성 설치 및 빌드**

   ```bash
   # Install any new dependencies
   npm install
   
   # Build component definitions
   npm run build:json
   ```

   **이 작업의 기능:**
   - 양식 구성 요소로 `component-definition.json` 업데이트
   - 양식 모델로 `component-models.json` 생성
   - 필터링 규칙으로 `component-filters.json` 생성

2. **생성된 파일 확인**

   프로젝트 루트에 있는 다음 파일에 양식 관련 오브젝트가 포함되어 있는지 확인합니다.
   - `component-definition.json`
   - `component-models.json`
   - `component-filters.json`

3. **변경 사항 커밋 및 푸시**

   ```bash
   git add .
   git commit -m "Add Adaptive Forms Block integration"
   git push origin main
   ```

**유효성 검사:** 프로젝트에 양식 기능이 포함되어 있는지 확인합니다.

+++

**다음 단계:** [첫 번째 양식 만들기](#create-your-first-form)

## 첫 번째 양식 만들기

**이 섹션을 따라야 하는 대상:**\
이 섹션은 경로 A(새 프로젝트) 또는 경로 B(기존 프로젝트)를 따르는 사용자와 관련이 있습니다.

이제 양식 제작을 위해 프로젝트를 준비했으므로 범용 편집기의 직관적인 WYSIWYG 저작 환경을 사용하여 첫 번째 양식을 만들 준비가 되었습니다. 다음 단계는 AEM Site 내에서 양식을 디자인, 구성 및 게시하기 위한 구조화된 접근 방식을 제공합니다.

### 개요

범용 편집기에서 양식을 만드는 프로세스는 다음과 같은 몇 가지 주요 단계로 구성됩니다.

1. **적응형 양식 블록 삽입**\
   선택한 페이지에 적응형 양식 블록을 추가하여 시작합니다.

2. **양식 구성 요소 추가**\
   텍스트 필드, 버튼 및 기타 입력 요소와 같은 구성 요소를 삽입하여 양식을 채웁니다.

3. **구성 요소 속성 구성**\
   양식의 요구 사항을 충족하도록 각 구성 요소의 설정 및 속성을 조정합니다.

4. **양식 미리보기 및 테스트**\
   미리보기 기능을 사용하여 게시하기 전에 양식의 모양과 비헤이비어를 확인합니다.

5. **업데이트된 페이지 게시**\
   페이지가 만족스러우면 페이지를 게시하여 최종 사용자가 양식을 사용할 수 있도록 합니다.

다음 섹션에서는 이러한 각 단계를 자세히 안내하여 원활하고 효과적인 양식 생성 경험을 보장합니다.

+++1단계: 적응형 양식 블록 추가

1. **범용 편집기에서 페이지를 엽니다.**
   - AEM의 **Sites** 콘솔로 이동합니다.
   - 양식을 추가할 페이지(예: `index`)를 선택합니다.
   - **편집** 클릭

   WYSIWYG 편집을 위해 페이지가 범용 편집기에서 열립니다.

2. **적응형 양식 구성 요소 추가**
   - **콘텐츠 트리** 패널(왼쪽 사이드바)을 엽니다.
   - 양식을 추가하려는 섹션으로 이동합니다.
   - **추가**(+) 아이콘을 클릭합니다.
   - 구성 요소 목록에서 **적응형 양식**&#x200B;을 선택합니다.

   ![적응형 양식 블록 추가](/help/edge/docs/forms/assets/add-adaptive-form-block.png)
   *그림: 페이지에 적응형 양식 블록 추가*

**유효성 검사:** 양식 컨테이너가 비어 있는지 확인합니다.

+++

+++2단계: 양식 구성 요소 추가

1. **양식 블록으로 이동**
   - 콘텐츠 트리에서 새로 추가된 적응형 양식 섹션을 찾습니다.

   ![추가된 적응형 양식 블록](/help/edge/docs/forms/assets/adative-form-block.png)
   *그림: 콘텐츠 트리의 적응형 양식 블록*

2. **양식 구성 요소 추가**

   다음 두 가지 방법으로 구성 요소를 추가할 수 있습니다.

   **방법 A: 클릭하여 추가**
   - 양식 섹션에서 **추가**(+) 아이콘을 클릭합니다.
   - **적응형 양식 구성 요소** 목록에서 원하는 구성 요소를 선택합니다.

   **방법 B: 드래그 앤 드롭**
   - 구성 요소 패널에서 양식으로 구성 요소를 직접 드래그합니다.

   ![양식 구성 요소 추가](/help/edge/docs/forms/assets/add-component.png)
   *그림: 양식에 구성 요소 추가*

   **권장되는 스타터 구성 요소:**
   - 텍스트 입력 (이름, 이메일)
   - 텍스트 영역 (메시지)
   - 제출 버튼

3. **구성 요소 속성 구성**
   - 양식 구성 요소 선택
   - **속성** 패널(오른쪽 사이드바)을 사용하여 다음을 구성합니다.
      - 레이블 및 플레이스홀더
      - 유효성 검사 규칙
      - 필수 필드 설정

   ![구성 요소 속성 패널](/help/edge/docs/forms/assets/component-properties.png)
   *그림: 구성 요소 속성 구성*

4. **양식 미리보기**

   양식이 다음과 같이 표시됩니다.

   ![완료된 양식 미리보기](/help/edge/docs/forms/assets/added-form-aem-sites.png)
   *그림: 범용 편집기로 만든 예제 양식*

**유효성 검사:** 양식을 게시할 준비가 되었는지 확인합니다.

>[!IMPORTANT]
>
> 변경 사항을 적용한 후에는 페이지를 게시해야 브라우저에서 업데이트를 확인할 수 있습니다.

+++

+++3단계: 양식 게시

1. **범용 편집기에서 게시**
   - 범용 편집기에서 **게시** 버튼을 클릭합니다.

   ![게시 양식](/help/edge/docs/forms/assets/publish-form.png)
   *그림: 범용 편집기에서 양식 게시*

2. **게시 확인**
   - 확인 대화 상자에서 **게시**&#x200B;를 클릭합니다.

   ![게시 확인](/help/edge/docs/forms/assets/publish-form1.png)
   *그림: 게시 작업 확인*

   게시를 확인하는 성공 메시지가 표시됩니다.

   ![게시 성공](/help/edge/docs/forms/assets/publish-form2.png)
   *그림: 정상적 게시 확인*

3. **실시간 양식 보기**

   이제 양식이 다음 위치에서 활성화됩니다.

   ```
   https://<branch>--<repo>--<owner>.aem.live/content/<site-name>/
   ```

   **예제 URL:**

   ```
   https://main--my-forms-project--mycompany.aem.live/content/my-forms-project/
   ```

   ![라이브 양식 페이지](/help/edge/docs/forms/assets/publish-index-page.png)
   *그림: Edge Delivery Services에 게시된 양식 페이지*

**축하합니다!** 이제 양식이 활성화되어 제출물을 수집할 준비가 되었습니다.

+++

### 다음 단계

이제 작동하는 양식을 만들었으므로 다음과 같은 작업을 수행할 수 있습니다.

- CSS 및 JavaScript 파일을 편집하여 **스타일 사용자 정의**
- 유효성 검사 규칙 및 조건 논리와 같은 **고급 양식 기능 추가**
- 더 빠른 반복을 위한 **로컬 개발 설정**
- 특정 사용 사례에 맞는 **독립형 양식 생성**

>[!TIP]
>
> **자세히 알아보기:** [범용 편집기에서 독립형 양식 만들기](/help/edge/docs/forms/universal-editor/create-forms.md)

## 로컬 개발 환경 설정

양식 스타일 및 비헤이비어를 사용자 정의하려는 개발자에게 **가장 적합**

로컬 개발 환경을 사용하면 게시 주기를 거치지 않고 변경 사항을 적용하고 즉시 확인할 수 있습니다.

+++AEM CLI 및 로컬 개발 설정

1. **AEM CLI 설치**

   AEM CLI는 로컬 개발 작업을 간소화합니다.

   ```bash
       npm install -g @adobe/aem-cli
   ```

2. **저장소 복제**

   ```bash
   git clone https://github.com/<owner>/<repo>
   cd <repo>
   ```

   `<owner>` 및 `<repo>`를 실제 GitHub 세부 사항을 포함하도록 바꿉니다.

3. **로컬 개발 서버 시작**

   ```bash
   aem up
   ```

   이렇게 하면 핫 리로드 기능이 있는 로컬 서버가 시작됩니다.

4. **사용자 정의**

   - 양식 스타일 지정 및 비헤이비어를 위해 `blocks/form/` 디렉터리에서 파일을 편집합니다.
   - 스타일 지정을 위해 `form.css`를 수정합니다.
   - 비헤이비어를 위해 `form.js`를 업데이트합니다.

   `http://localhost:3000`에서 브라우저의 **변경 사항을 즉시 확인**&#x200B;합니다.

5. **변경 내용 배포**

   ```bash
   git add .
   git commit -m "Custom form styling"
   git push origin main
   ```

   변경 내용은 다음 위치에서 사용할 수 있습니다.
   - **미리보기:** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>`
   - **프로덕션:** `https://<branch>--<repo>--<owner>.aem.live/content/<site-name>`

+++


## 문제 해결

### 일반적인 문제 및 솔루션

+++GitHub 빌드 문제

**문제:** 빌드 실패 또는 린팅 오류

**솔루션 1: 린팅 오류 처리**

린팅 오류가 발생하는 경우:

1. 프로젝트 루트에서 `package.json`을 엽니다.
2. `lint` 스크립트를 찾습니다.

   ```json
   "scripts": {
     "lint": "npm run lint:js && npm run lint:css"
   }
   ```

3. 린팅을 일시적으로 비활성화합니다.

   ```json
   "scripts": {
     "lint": "echo 'skipping linting for now'"
   }
   ```

4. 변경 내용을 커밋하고 푸시합니다.

**솔루션 2: 모듈 경로 오류**

“모듈 &#39;../../scripts/lib-franklin.js&#39;에 대한 경로를 확인할 수 없음” 메시지가 표시되는 경우:

1. 다음으로 이동 `blocks/form/form.js`
2. Import 문을 업데이트합니다.

   ```javascript
   // Change this:
   import { ... } from '/scripts/lib-franklin.js';
   
   // To this:
   import { ... } from '/scripts/aem.js';
   ```

+++

+++양식 기능 문제

**문제:** 양식 제출이 작동하지 않음

**솔루션:**

- 제출 버튼 구성 요소가 있는지 확인합니다.
- 양식 작업 URL 구성을 확인합니다.
- 양식 유효성 검사 규칙을 확인합니다.
- 먼저 미리보기 모드에서 테스트합니다.

**문제:** 스타일 지정 문제

**솔루션:**

- `blocks/form/`에서 CSS 파일 경로를 확인합니다.
- 브라우저 캐시를 지웁니다.
- CSS 구문을 확인합니다.
- 로컬 개발 환경에서 테스트합니다.

+++

+++범용 편집기 문제

**문제:** 범용 편집기에 양식 구성 요소가 표시되지 않음

**솔루션:**

- AEM Code Sync가 설치되어 있고 실행 중인지 확인합니다.
- `fstab.yaml`에 올바른 AEM 작성자 URL이 있는지 확인합니다.
- AEM 인스턴스에 얼리 액세스가 활성화되어 있는지 확인합니다.
- `component-definition.json`에 양식 구성 요소가 포함되어 있는지 확인합니다.

**문제:** 게시 후 변경 사항이 표시되지 않음

**솔루션:**

- CDN 캐시가 새로 고쳐질 때까지 기다립니다.
- 브라우저 캐시를 확인합니다(시크릿/비공개 모드에서 시도).
- 올바른 URL 형식이 사용되고 있는지 확인합니다.

+++



