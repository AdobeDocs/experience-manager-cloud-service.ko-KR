---
title: 범용 편집기를 사용하여 AEM Forms용 Edge Delivery Services 시작하기
description: 범용 편집기의 WYSIWYG 작성과 함께 Edge Delivery Services을 사용하여 고성능 양식을 만들고 게시하는 방법을 알아봅니다.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
exl-id: 24a23d98-1819-4d6b-b823-3f1ccb66dbd8
source-git-commit: 6400662cb1c7a504f69db7091091452e99dd6ce9
workflow-type: tm+mt
source-wordcount: '2117'
ht-degree: 1%

---


# 범용 편집기를 사용하여 AEM Forms용 Edge Delivery Services 시작하기

| 작성 방법 | 안내서 |
|---------------------------------|-----------------------------------------------------------------------|
| **Universal Editor (WYSIWYG)** | 이 문서 |
| **문서 기반 작성** | [문서 기반 자습서](/help/edge/docs/forms/tutorial.md) |

Edge Delivery Services for AEM Forms은 범용 편집기에서 고성능 웹 게재를 WYSIWYG 작성과 결합합니다. 이 안내서에서는 빠른 로드 양식 만들기, 사용자 지정 및 게시를 다룹니다.

## 수행할 작업

이 자습서를 마치면 다음 작업을 수행할 수 있습니다.

- 적응형 Forms 블록을 사용하여 GitHub 저장소 설정
- Edge Delivery Services과 통합된 AEM 사이트 만들기
- 범용 편집기를 사용하여 양식 작성 및 게시
- 로컬 개발 환경 구성

## 경로 선택

시나리오와 일치하는 접근 방식을 선택합니다.

![경로 결정 가이드 선택](/help/edge/docs/forms/universal-editor/assets/choose-your-path.svg)
*그림: 올바른 구현 경로를 선택하는 데 도움이 되는 시각적 안내서*

| **경로 A: 새 프로젝트** | **경로 B: 기존 프로젝트** |
|----------------------------------------|-------------------------------------------|
| 사전 구성된 템플릿으로 시작 | 현재 AEM 프로젝트에 양식 추가 |
| **새로운 구현 최상:** | **우수 사례:** 기존 AEM Sites |
| **받은 항목:** 사전 구성된 Forms 블록 | **받은 항목:** Forms이 기존 사이트에 추가됨 |
| **단계:** Forms→ 템플릿 → 설정 | **단계:** 통합 → 구성 → Forms |
| [경로 A로 시작](#path-a-create-new-project-with-forms) | [경로 B로 시작](#path-b-add-forms-to-existing-project) |

## 사전 요구 사항

시작하기 전에 다음을 확인하십시오.

### 필수 액세스 권한

- 저장소를 만들 수 있는 권한이 있는 **GitHub 계정**
- **AEM as a Cloud Service** 작성 액세스

### 기술 요구 사항

- **Git 기본 사항**: 복제, 커밋, 푸시 작업
- **웹 기술**: HTML, CSS, JavaScript 기본 사항
- 로컬 개발용 **Node.js**(버전 16+ 권장)
- **npm** 또는 **yarn** 패키지 관리자

### 권장되는 지식

- AEM Sites 개념에 대한 기본 이해
- 양식 디자인 원리에 대한 친숙도
- WYSIWYG 편집기 경험

>[!TIP]
>
> AEM을 처음 사용하십니까? [AEM Sites 시작 안내서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/quick-start.html)로 시작합니다.

## 경로 A: Forms으로 새 프로젝트 만들기

**새로운 구현 또는 개념 입증 모범 사례:**

AEM Forms Boilerplate는 적응형 Forms 블록이 통합된 사전 구성된 템플릿을 제공합니다.

### 단계 개요

1. 템플릿에서 GitHub 저장소 설정
2. AEM 코드 동기화 설치
3. AEM 프로젝트 연결 구성
4. AEM 사이트 만들기 및 게시
5. 범용 편집기를 사용하여 양식 추가

각 단계를 살펴보겠습니다.

+++1단계: 템플릿에서 GitHub 저장소 만들기

1. **AEM Forms Boilerplate 템플릿에 액세스**
   - [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms)&#x200B;(으)로 이동

   ![AEM Forms Boilerplate 템플릿](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   *그림: 적응형 Forms 블록이 사전 구성된 AEM Forms Boilerplate 저장소*

2. **저장소 만들기**
   - **이 템플릿 사용** > **새 저장소 만들기**&#x200B;를 클릭합니다.

   ![템플릿에서 저장소 만들기](/help/edge/docs/forms/assets/use-eds-form-template.png)
   *그림: 템플릿을 사용하여 새 저장소 만들기*

3. **저장소 설정 구성**
   - **소유자**: GitHub 계정 또는 조직 선택
   - **저장소 이름**: 설명하는 이름(예: `my-forms-project`)을 선택하세요.
   - **가시성**: **공개** 선택(Edge Delivery Services 권장)
   - **저장소 만들기** 클릭

   ![저장소 구성](/help/edge/docs/forms/assets/name-eds-repo.png)
   *그림: 공개 표시로 새 저장소 구성*

**유효성 검사:** AEM Forms Boilerplate 템플릿을 기반으로 하는 새 GitHub 리포지토리가 있는지 확인합니다.

+++

+++2단계: AEM 코드 동기화 설치

AEM 코드 동기화는 AEM 작성 환경과 GitHub 저장소 간의 콘텐츠 변경 사항을 자동으로 동기화합니다.

1. **GitHub 앱 설치**
   - [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new)&#x200B;(으)로 이동

2. **액세스 권한 구성**
   - **저장소만 선택** 선택
   - 새로 만든 저장소 선택
   - **저장** 클릭

   ![AEM 코드 동기화 설치](/help/edge/docs/forms/assets/aem-code-sync-up.png)
   *그림: 리포지토리별 권한으로 AEM 코드 동기화 설치*

**검사점:** AEM 코드 동기화가 설치되었으며 저장소에 액세스할 수 있습니다.

+++

+++3단계: AEM 통합 구성

`fstab.yaml` 파일은 콘텐츠 동기화를 위해 GitHub 리포지토리를 AEM 작성 환경에 연결합니다.

1. **저장소로 이동**
   - 새로 생성된 GitHub 저장소로 이동
   - AEM Forms Boilerplate 파일이 표시됩니다.

2. **fstab.yaml 파일 만들기**
   - 루트 디렉터리에서 **파일 추가** > **새 파일 만들기**&#x200B;를 클릭합니다.
   - 파일 이름을 `fstab.yaml`로 지정합니다.

   ![fstab.yaml 파일 만들기](/help/edge/docs/forms/assets/open-fstab.png)
   *그림: fstab.yaml 구성 파일 만들기*

3. **AEM 연결 세부 정보 추가**

   다음 구성을 복사하여 붙여넣고 자리 표시자를 바꿉니다.

   ```yaml
   mountpoints:
     /: https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main
   ```

   **바꾸기:**
   - `<aem-author>`: AEM as a Cloud Service 작성자 URL(예: `author-p12345-e67890.adobeaemcloud.com`)
   - `<owner>`: GitHub 사용자 이름 또는 조직
   - `<repository>`: 저장소 이름

   **예:**

   ```yaml
   mountpoints:
     /: https://author-p12345-e67890.adobeaemcloud.com/bin/franklin.delivery/mycompany/my-forms-project/main
   ```

   ![fstab.yaml 파일 편집](/help/edge/docs/forms/assets/edit-fstab-file.png)
   *그림: AEM 통합을 위한 탑재 지점 구성*

4. **구성 커밋**
   - 커밋 메시지 추가: &quot;AEM 통합 구성 추가&quot;
   - **새 파일 커밋** 클릭

   ![fstab 변경 내용 커밋](/help/edge/docs/forms/assets/commit-fstab-changes.png)
   *그림: fstab.yaml 구성 커밋*

**유효성 검사:** AEM에 대한 GitHub 리포지토리 연결을 확인합니다.

    >[!NOTE]
    >
    >빌드 문제가 있습니까? [GitHub 빌드 문제 해결](#troubleshooting-github-build-issues)을 참조하세요.

+++

+++4단계: GitHub 저장소에 연결된 AEM 사이트 만들기

1. **AEM Sites 콘솔에 액세스**
   - AEM as a Cloud Service 작성 인스턴스에 로그인합니다
   - **사이트**(으)로 이동

   ![AEM Sites 콘솔](/help/edge/assets/select-sites.png)
   *그림: AEM Sites 콘솔 액세스*

2. **사이트 만들기 시작**
   - **만들기** > **템플릿의 사이트**&#x200B;를 클릭합니다.

   ![사이트 만들기 옵션](/help/edge/docs/forms/assets/create-sites.png)
   *그림: 템플릿에서 새 사이트 만들기*

3. **Edge Delivery Services 템플릿 선택**
   - **Edge Delivery Services 사이트** 템플릿 선택
   - **다음** 클릭

   ![사이트 템플릿 선택](/help/edge/docs/forms/assets/select-site-template.png)
   *그림: Edge Delivery Services 사이트 템플릿 선택*

   >[!NOTE]
   >
   >**템플릿을 사용할 수 없습니까?** Edge Delivery Services 템플릿이 표시되지 않는 경우:
   >
   >1. 템플릿을 업로드하려면 **가져오기**&#x200B;를 클릭하십시오.
   >2. [GitHub 릴리스](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases)에서 템플릿 다운로드

4. **사이트 구성**

   다음 정보를 입력합니다.

   | 필드 | 값 | 예 |
   |-----------------|-----------------------------|-----------------------------------------|
   | **사이트 제목** | 사이트에 대한 수사적 이름 | &quot;내 Forms 프로젝트&quot; |
   | **사이트 이름** | URL에 친숙한 이름 | &quot;my-forms-project&quot; |
   | **GitHub URL** | 저장소 URL | `https://github.com/mycompany/my-forms-project` |

   ![사이트 구성](/help/edge/docs/forms/assets/create-aem-site.png)
   *그림: GitHub 통합을 사용하여 새 AEM 사이트 구성*

5. **사이트 생성 완료**
   - 설정 검토
   - **만들기**&#x200B;를 클릭합니다.

   ![사이트 생성 확인](/help/edge/docs/forms/assets/click-ok-aem-site.png)
   *그림: 사이트 생성 확인*

   **성공!** 이제 AEM 사이트가 만들어지고 GitHub에 연결됩니다.

6. **유니버설 편집기에서 열기**
   - 사이트 콘솔에서 새 사이트를 찾습니다
   - `index` 페이지 선택
   - **편집** 클릭

   ![유니버설 편집기에서 사이트 편집](/help/edge/docs/forms/assets/edit-site.png)
   *그림: 편집할 사이트 열기*

   범용 편집기가 새 탭에서 열리고 WYSIWYG 작성 기능이 제공됩니다.

   ![유니버설 편집기 인터페이스](/help/edge/docs/forms/assets/site-in-universal-editor.png)
   *그림: WYSIWYG 편집을 위해 유니버설 편집기에서 사이트를 열었습니다*

**유효성 검사:** AEM 사이트가 양식을 작성할 준비가 되었는지 확인합니다.

+++

+++5단계: 사이트 게시

게시를 사용하면 Edge Delivery Services에서 전역 액세스에 사이트를 사용할 수 있습니다.

1. **사이트 콘솔에서 빠른 게시**
   - AEM Sites 콘솔로 돌아가기
   - 사이트 페이지 선택(또는 Ctrl+A를 사용하여 모두 선택)
   - **빠른 게시** 클릭

   ![AEM 사이트 게시](/help/edge/docs/forms/assets/publish-sites.png)
   *그림: 빠른 게시를 위한 페이지 선택*

2. **게시 확인**
   - 확인 대화 상자에서 **게시**&#x200B;를 클릭합니다

   ![빠른 게시 대화 상자](/help/edge/docs/forms/assets/quick-publish.png)
   *그림: 게시 작업 확인*

   **대체 요소:** 게시 단추를 사용하여 유니버설 편집기에서 직접 게시할 수도 있습니다.

   ![유니버설 편집기에서 게시](/help/edge/docs/forms/assets/qui.png)
   *그림: 유니버설 편집기에서 직접 게시*

3. **라이브 사이트에 액세스**

   이제 사이트의 라이브 위치:

   ```
   https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/
   ```

   **URL 구조 설명:**
   - `<branch>`: GitHub 분기(일반적으로 `main`)
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

**다음:** [첫 번째 양식 만들기](#create-your-first-form)

+++

## 경로 B: 기존 프로젝트에 Forms 추가

**우수 사례:** 기존 AEM Sites(Edge Delivery Services 사용)

Edge Delivery Services을 사용하는 AEM 프로젝트가 이미 있는 경우 적응형 Forms 블록을 통합하여 양식 기능을 추가할 수 있습니다.

### 경로 B 사전 요구 사항

- [AEM Boilerplate XWalk](https://github.com/adobe-rnd/aem-boilerplate-xwalk)을(를) 사용하여 빌드된 기존 AEM 프로젝트
- 로컬 개발 환경 설정
- 프로젝트 저장소에 대한 Git 액세스

**AEM Forms Boilerplate을 사용하시겠습니까?** 프로젝트가 [AEM Forms Boilerplate](https://github.com/adobe-rnd/aem-boilerplate-forms)&#x200B;(으)로 만들어진 경우 양식이 이미 통합되었습니다. [첫 번째 양식 만들기](#create-your-first-form)(으)로 건너뛰기

각 단계를 살펴보겠습니다.

### 단계 개요

1. 적응형 Forms 블록 파일 복사
2. 프로젝트 구성 업데이트
3. ESLint 규칙 구성
4. 변경 내용 작성 및 커밋

+++1단계: Forms 블록 파일 복사

1. **로컬 프로젝트로 이동**

   ```bash
   cd /path/to/your/aem-project
   ```

2. **AEM Forms Boilerplate에서 필요한 파일 다운로드**

   [AEM Forms Boilerplate 저장소](https://github.com/adobe-rnd/aem-boilerplate-forms)에서 다음 파일을 복사합니다.

   | 소스 | 대상 | 용도 |
   |------------------------------------------------------------------------|----------------------------|----------------------------|
   | [`blocks/form/`](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/blocks/form) | `blocks/form/` | 핵심 양식 기능 |
   | [`scripts/form-editor-support.js`](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.js) | `scripts/form-editor-support.js` | 유니버설 편집기 통합 |
   | [`scripts/form-editor-support.css`](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.css) | `scripts/form-editor-support.css` | 편집기 스타일 |

3. **편집기 지원 업데이트**
   - `/scripts/editor-support.js` 파일을 AEM Forms Boilerplate의 [editor-support.js로 바꾸기](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/editor-support.js)

**유효성 검사:** 양식 블록 파일이 프로젝트에 있는지 확인하십시오.

+++

+++2단계: 구성 요소 구성 업데이트

1. **섹션 모델 업데이트**

   `/models/_section.json`을(를) 열고 양식 구성 요소를 필터에 추가합니다.

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

   **기능:** 유니버설 편집기 구성 요소 선택기에서 양식 구성 요소를 사용하도록 설정합니다.

**유효성 검사:** 양식 구성 요소가 유니버설 편집기에 표시되는지 확인합니다.

+++

+++3단계: ESLint 구성(선택 사항)

**이 단계인 이유:** 양식별 파일에서 링크 오류를 방지하고 올바른 유효성 검사 규칙을 구성합니다.

1. **.eslintignore 업데이트**

   `/.eslintignore`에 다음 줄 추가:

   ```bash
   # Form block rule engine files
   blocks/form/rules/formula/*
   blocks/form/rules/model/*
   blocks/form/rules/functions.js
   scripts/editor-support.js
   scripts/editor-support-rte.js
   ```

2. **.eslintrc.js 업데이트**

   `rules`의 `/.eslintrc.js` 개체에 다음 규칙을 추가합니다.

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

**유효성 검사:** ESLint가 양식 구성 요소에서 작동하는지 확인합니다.

+++

+++4단계: 빌드 및 배포

1. **종속성 및 빌드 설치**

   ```bash
   # Install any new dependencies
   npm install
   
   # Build component definitions
   npm run build:json
   ```

   **기능:**
   - 양식 구성 요소로 `component-definition.json` 업데이트
   - 양식 모델로 `component-models.json` 생성
   - 필터링 규칙을 사용하여 `component-filters.json`을(를) 만듭니다

2. **생성된 파일 확인**

   프로젝트 루트의 다음 파일에 양식 관련 개체가 포함되어 있는지 확인하십시오.
   - `component-definition.json`
   - `component-models.json`
   - `component-filters.json`

3. **변경 내용 커밋 및 푸시**

   ```bash
   git add .
   git commit -m "Add Adaptive Forms Block integration"
   git push origin main
   ```

**유효성 검사:** 프로젝트에 양식 기능이 포함되어 있는지 확인하십시오.

+++

**다음:** [첫 번째 양식 만들기](#create-your-first-form)

## 첫 번째 양식 만들기

**적용 대상:** 경로 A와 경로 B 사용자 모두

이제 프로젝트가 양식 기능으로 설정되었으므로 범용 편집기의 WYSIWYG 인터페이스를 사용하여 첫 번째 양식을 만들어 보겠습니다.

### 양식 작성 프로세스 개요

1. 페이지에 **적응형 양식 블록 추가**
2. **양식 구성 요소 추가**(텍스트 입력, 단추 등)
3. **구성 요소 속성 구성**
4. 양식 **미리 보기 및 테스트**
5. 업데이트된 페이지를 **게시**

각 단계를 살펴보겠습니다.

+++1단계: 적응형 양식 블록 추가

1. **유니버설 편집기에서 페이지 열기**
   - AEM의 **사이트** 콘솔로 이동
   - 양식을 추가할 페이지를 선택하십시오(예: `index`).
   - **편집** 클릭

   페이지가 WYSIWYG 편집용 유니버설 편집기에서 열립니다.

2. **적응형 양식 구성 요소 추가**
   - **콘텐츠 트리** 패널(왼쪽 사이드바) 열기
   - 양식을 추가하려는 섹션으로 이동합니다.
   - **추가**(+) 아이콘 클릭
   - 구성 요소 목록에서 **적응형 양식** 선택

   ![적응형 양식 블록 추가](/help/edge/docs/forms/assets/add-adaptive-form-block.png)
   *그림: 페이지에 적응형 양식 블록 추가*

**유효성 검사:** 양식 컨테이너가 비어 있는지 확인하십시오.

+++

+++2단계: 양식 구성 요소 추가

1. **양식 블록으로 이동**
   - 콘텐츠 트리에서 새로 추가한 적응형 양식 섹션을 찾습니다

   ![적응형 양식 블록 추가됨](/help/edge/docs/forms/assets/adative-form-block.png)
   *그림: 콘텐츠 트리의 적응형 양식 블록*

2. **양식 구성 요소 추가**

   다음 두 가지 방법으로 구성 요소를 추가할 수 있습니다.

   **메서드 A: 추가하려면 클릭**
   - 양식 섹션에서 **추가**(+) 아이콘을 클릭합니다.
   - **적응형 양식 구성 요소** 목록에서 구성 요소 선택

   **메서드 B: 끌어서 놓기**
   - 구성 요소 패널에서 양식으로 구성 요소를 바로 드래그합니다

   ![양식 구성 요소 추가](/help/edge/docs/forms/assets/add-component.png)
   *그림: 양식에 구성 요소 추가*

   **권장 시작 구성 요소:**
   - 텍스트 입력(이름, 이메일)
   - 텍스트 영역(메시지용)
   - 제출 버튼

3. **구성 요소 속성 구성**
   - 양식 구성 요소 선택
   - **속성** 패널(오른쪽 사이드바)을 사용하여 다음을 구성하십시오.
      - 레이블 및 자리 표시자
      - 유효성 검사 규칙
      - 필수 필드 설정

   ![구성 요소 속성 패널](/help/edge/docs/forms/assets/component-properties.png)
   *그림: 구성 요소 속성 구성*

4. **양식 미리 보기**

   양식은 다음과 같이 표시됩니다.

   ![양식 미리 보기 완료](/help/edge/docs/forms/assets/added-form-aem-sites.png)
   *그림: 범용 편집기로 만든 예제 양식*

**유효성 검사:** 양식을 게시할 준비가 되었는지 확인합니다.

>[!IMPORTANT]
>
> 변경 내용을 적용한 후 페이지를 게시하여 브라우저에서 업데이트를 확인해야 합니다.

+++

+++3단계: 양식 게시

1. **유니버설 편집기에서 게시**
   - 범용 편집기에서 **게시** 단추를 클릭합니다.

   ![양식 게시](/help/edge/docs/forms/assets/publish-form.png)
   *그림: 유니버설 편집기에서 양식 게시*

2. **게시 확인**
   - 확인 대화 상자에서 **게시**&#x200B;를 클릭합니다

   ![게시 확인](/help/edge/docs/forms/assets/publish-form1.png)
   *그림: 게시 작업 확인*

   게시를 확인하는 성공 메시지가 표시됩니다.

   ![게시 성공](/help/edge/docs/forms/assets/publish-form2.png)
   *그림: 게시 확인 성공*

3. **Live 양식 보기**

   이제 양식이 다음 위치에 있습니다.

   ```
   https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/
   ```

   **예제 URL:**

   ```
   https://main--my-forms-project--mycompany.aem.page/content/my-forms-project/
   ```

   ![Live 양식 페이지](/help/edge/docs/forms/assets/publish-index-page.png)
   *그림: Edge Delivery Services에 게시된 양식 페이지*

**축하합니다!** 이제 양식이 활성 상태이며 제출 서류를 수집할 준비가 되었습니다.

+++

### 다음 단계

작업 양식이 있으므로 다음과 같은 작업을 수행할 수 있습니다.

- CSS 및 JavaScript 파일을 편집하여 **스타일 사용자 지정**
- 유효성 검사 규칙 및 조건부 논리와 같은 **고급 양식 기능 추가**
- 더 빠른 반복을 위해 **로컬 개발 설정**
- 특정 사용 사례에 대해 **독립 실행형 양식 만들기**

>[!TIP]
>
> **자세히 알아보기:** [유니버설 편집기에서 독립 실행형 양식 만들기](/help/edge/docs/forms/universal-editor/create-forms.md)

## 로컬 개발 환경 설정

**가장 적합한 방법:** 양식 스타일 및 동작을 사용자 지정하려는 개발자

로컬 개발 환경을 사용하면 게시 주기를 거치지 않고 변경 작업을 수행하고 즉시 확인할 수 있습니다.

+++AEM CLI 및 로컬 개발 설정

1. **AEM CLI 설치**

   AEM CLI는 로컬 개발 작업을 단순화합니다.

   ```bash
       npm install -g @adobe/aem-cli
   ```

2. **리포지토리 복제**

   ```bash
   git clone https://github.com/<owner>/<repo>
   cd <repo>
   ```

   `<owner>` 및 `<repo>`을(를) 실제 GitHub 세부 정보로 바꾸십시오.

3. **로컬 개발 서버 시작**

   ```bash
   aem up
   ```

   이렇게 하면 핫 리로드 기능이 있는 로컬 서버가 시작됩니다.

4. **사용자 지정**

   - 양식 스타일 및 동작을 위해 `blocks/form/` 디렉터리에서 파일 편집
   - 스타일링을 위해 `form.css` 수정
   - 동작에 대해 `form.js` 업데이트

   **의 브라우저에서**&#x200B;변경 내용을 즉시 확인`http://localhost:3000`

5. **변경 내용 배포**

   ```bash
   git add .
   git commit -m "Custom form styling"
   git push origin main
   ```

   변경 사항은 다음 위치에서 사용할 수 있습니다.
   - **미리 보기:** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>`
   - **프로덕션:** `https://<branch>--<repo>--<owner>.aem.live/content/<site-name>`

+++


## 문제 해결

### 일반적인 문제 및 솔루션

+++GitHub 빌드 문제

**문제:** 빌드 오류 또는 링크 오류

**솔루션 1: 린팅 오류 처리**

린팅 오류가 발생하는 경우:

1. 프로젝트 루트에서 `package.json` 열기
2. `lint` 스크립트 찾기:

   ```json
   "scripts": {
     "lint": "npm run lint:js && npm run lint:css"
   }
   ```

3. 일시적으로 린팅 비활성화:

   ```json
   "scripts": {
     "lint": "echo 'skipping linting for now'"
   }
   ```

4. 변경 사항 커밋 및 푸시

**솔루션 2: 모듈 경로 오류**

&quot;모듈 &#39;/scripts/lib-franklin.js&#39;에 대한 경로를 확인할 수 없음&quot;이 표시되는 경우:

1. `blocks/form/form.js`(으)로 이동
2. 가져오기 문을 업데이트합니다.

   ```javascript
   // Change this:
   import { ... } from '/scripts/lib-franklin.js';
   
   // To this:
   import { ... } from '/scripts/aem.js';
   ```

+++

+++유니버설 편집기 문제

**문제:** 양식 구성 요소가 유니버설 편집기에 표시되지 않음

**솔루션:**

- AEM 코드 동기화가 설치되어 실행 중인지 확인
- `fstab.yaml`에 올바른 AEM 작성자 URL이 있는지 확인
- AEM 인스턴스에 조기 액세스 기능이 활성화되어 있는지 확인합니다.
- `component-definition.json`에 양식 구성 요소가 포함되어 있는지 확인

**문제:** 게시 후 변경 내용이 표시되지 않음

**솔루션:**

- CDN 캐시 새로 고침 대기
- 브라우저 캐시 확인(시크릿/비공개 모드 시도)
- 올바른 URL 형식이 사용되고 있는지 확인

+++

+++양식 기능 문제

**문제:** 양식 제출이 작동하지 않음

**솔루션:**

- 제출 버튼 구성 요소가 있는지 확인합니다.
- 양식 작업 URL 구성 확인
- 양식 유효성 검사 규칙 확인
- 미리보기 모드에서 먼저 테스트

**문제:** 스타일 문제

**솔루션:**

- `blocks/form/`에서 CSS 파일 경로 확인
- 브라우저 캐시 지우기
- CSS 구문 확인
- 로컬 개발 환경에서 테스트

+++

