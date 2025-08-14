---
title: Edge Delivery Services을 사용하여 적응형 Forms 만들기 및 게시
description: 기술적 정확성과 명확성에 초점을 맞춰 AEM에서 Edge Delivery Services 템플릿을 사용하여 적응형 Forms을 만들고, 작성하고, 게시하기 위한 단계별 지침입니다.
keywords: 적응형 양식, edge delivery 서비스, 범용 편집기, 양식 작성, AEM 양식, 양식 게시
feature: Edge Delivery Services
role: User, Developer
level: Beginner
exl-id: 1eab3a3d-5726-4ff8-90b9-947026c17e22
source-git-commit: 07160248d5b5817d155a118475878ce04a687a32
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 1%

---


# Edge Delivery Services을 사용하여 적응형 Forms 만들기 및 게시

이 문서에서는 AEM에서 Edge Delivery Services 템플릿을 사용하여 적응형 Forms을 만들고, 구성하고, 게시하기 위한 단계별 지침을 제공합니다. 양식 작성에서 프로덕션 배포에 이르는 전체 워크플로우를 다룹니다.

이 안내서를 끝까지 읽으면 다음 방법을 배울 수 있습니다.

- Edge Delivery Services 템플릿을 사용하여 양식 만들기
- 범용 편집기를 사용하여 양식 작성
- 양식 구성 및 Edge Delivery Services 게시
- 게시된 양식에 액세스하고 배포 확인



## 사전 요구 사항

계속하기 전에 다음 전제 조건을 충족하는지 확인하십시오.


- **AEM Forms as a Cloud Service**: Forms 라이선스가 있는 활성 작성자 인스턴스입니다.
- **GitHub 계정**: 저장소 관리에 사용할 개인 또는 조직 계정입니다.
- **저장소 설정**: 다음 중 하나를 선택하십시오.
   - **새 프로젝트**: [적응형 Forms 블록을 사용하여 새 AEM 프로젝트 만들기](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block). 저장소는 Edge Delivery Services용으로 사전 구성되어 있습니다.
   - **기존 프로젝트**: [기존 저장소에 적응형 Forms 블록 추가](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project) 및 구성을 업데이트하십시오.

- **AEM-GitHub 연결**: [AEM 인스턴스와 GitHub 리포지토리 간의 연결을 설정합니다](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#get-started-with-the-aem-forms-boilerplate-repository-template).
- **Edge Delivery Services**: 자동 배포용으로 저장소가 구성되어 있는지 확인하십시오.
- **권한**: 양식을 만들고 게시하는 데 필요한 액세스 권한이 있는지 확인하십시오.

- GitHub 저장소에 적응형 Forms 블록이 포함되어 있는지 확인합니다.



## 양식 작성 및 게시 워크플로

이 프로세스는 다음 세 가지 주요 단계로 구성됩니다.

- **1단계:** [양식 만들기](#step-1-form-creation)
- **2단계:** [양식 작성 및 디자인](#step-2-form-authoring-and-design)
- **3단계:** [구성 및 게시](#step-3-configuration-and-publishing)

각 단계에는 올바른 설정을 확인하는 유효성 검사 단계가 포함되어 있습니다.


### 1단계: 양식 만들기

1. **양식 만들기 액세스**
   - AEM Forms as a Cloud Service 작성자 인스턴스에 로그인합니다.
   - **Adobe Experience Manager** > **Forms** > **Forms 및 문서**&#x200B;로 이동합니다.
   - **만들기** > **적응형 Forms**&#x200B;을 클릭합니다.

1. **템플릿 선택**
   - **Source** 탭에서 **Edge Delivery Services 기반 템플릿**&#x200B;을(를) 선택합니다.
   - **만들기** 단추가 활성화됩니다.

     ![EDS 양식 만들기](/help/edge/assets/create-eds-forms.png)

1. **옵션 구성(선택 사항)**
   - **데이터 Source 탭**: 필요한 경우 데이터 통합을 선택합니다.
   - **제출 탭**: 제출 액션을 선택합니다(나중에 구성할 수 있음).
   - **배달 탭**: 게시/게시 취소 일정을 설정합니다.

1. **양식 설정 완료**
   - **만들기**&#x200B;를 클릭하여 양식 만들기 마법사를 엽니다.
   - 다음을 입력합니다.
      - **이름**: 내부 식별자(공백 없음, 하이픈 사용).
      - **제목**: 폼의 표시 이름입니다.
      - **GitHub URL**: 저장소 URL(예: `https://github.com/your-org/your-repo`).

   ![양식 생성 마법사](/help/edge/assets/create-form-wizard.png)

1. **유효성 검사**
   - **만들기**&#x200B;를 클릭한 후 다음을 확인하십시오.
      - 양식이 유니버설 편집기에서 열립니다.
      - GitHub URL이 올바르게 연결됩니다.
      - 구성 요소 팔레트를 사용할 수 있습니다.
      - 양식 캔버스가 표시됩니다.

   ![유니버설 편집기 인터페이스](/help/edge/assets/author-form.png)

**결과:** 유니버설 편집기에서 양식을 작성할 준비가 되었습니다.

### 2단계: 양식 작성 및 디자인


1. **구성 요소 라이브러리에 액세스**
   - 범용 편집기에서 컨텐츠 브라우저를 엽니다.
   - 콘텐츠 트리에서 **적응형 양식** 구성 요소로 이동합니다.

   ![콘텐츠 트리 탐색](/help/edge/assets/content-tree.png)

1. **양식 필드 추가**
   - 구성 요소 라이브러리를 열려면 **추가** 아이콘을 클릭하십시오.
   - **적응형 양식 구성 요소** 목록에서 구성 요소를 선택하십시오.
   - 구성 요소를 양식 캔버스로 끌어서 놓습니다.

   ![구성 요소 추가](/help/edge/assets/add-component.png)

1. **양식 디자인**
   - 속성 패널에서 필드 속성을 구성합니다.
   - 유효성 검사 규칙 및 비헤이비어를 설정합니다.
   - 필요에 따라 스타일 및 레이아웃을 조정합니다.

   ![등록 양식 작성](/help/edge/assets/contact-us.png)

#### 유효성 검사

- 모든 필수 필드가 표시됩니다.
- 필드 속성이 올바르게 구성되었습니다.
- 레이아웃은 응답하고 액세스할 수 있습니다.
- 유효성 검사 규칙이 예상대로 작동합니다.

#### 다음 단계

- 데이터 처리를 위해 [제출 액션을 구성](/help/edge/docs/forms/universal-editor/submit-action.md)합니다.
- 고급 기능에 대한 [유니버설 편집기 안내서](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#author-forms-using-wysiwyg).

### 3단계: 구성 및 게시

Edge Delivery Services을 구성하고 양식을 게시합니다.

**구성:** 자동(수동 설정 필요 없음).

- GitHub 저장소 연결 및 Edge Delivery Services 구성은 양식을 만드는 동안 만들어집니다.
- 게시 끝점은 자동으로 구성됩니다.

**확인:**

- 구성이 양식 설정에 표시되는지 확인합니다.
- GitHub URL이 올바르게 연결되어 있는지 확인합니다.

![자동 EDS 구성](/help/edge/assets/aem-instance-eds-configuration.png)

#### 양식 게시

1. 유니버설 편집기에서 **게시** 단추(오른쪽 상단)를 클릭합니다.
2. 대화 상자에서 게시 성공을 확인합니다.
3. 스테이징된 버전 및 라이브 버전에 대해 생성된 URL을 확인합니다.

   ![유니버설 편집기 게시](/help/edge/assets/publish-form.png)

- [Publishing 안내서](/help/edge/docs/forms/universal-editor/publish-forms.md)

## 양식 URL

게시된 양식은 Edge Delivery Services URL을 통해 액세스할 수 있습니다.

### URL 구조

- **준비(미리 보기/테스트):**

  ```
  https://<branch>--<repo>--<owner>.aem.page/content/forms/af/<form_name>
  ```

- **라이브(프로덕션):**

  ```
  https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>
  ```

#### URL 매개 변수

- `<branch>`: GitHub 분기 이름(예: `main`, `develop`)
- `<repo>`: GitHub 저장소 이름(예: `my-forms-project`)
- `<owner>`: GitHub 조직 또는 사용자 이름(예: `company-name`)
- `<form_name>`: AEM에 정의된 양식 식별자(예: `contact-us`)

#### 예

`contact-us` 조직의 `forms-project` 저장소에 있는 `acme-corp` 양식의 예:

- **준비:** `https://main--forms-project--acme-corp.aem.page/content/forms/af/contact-us`
- **라이브:** `https://main--forms-project--acme-corp.aem.live/content/forms/af/contact-us`

#### 환경의 차이점

- 테스트를 위한 **준비(.page):** 최신 변경 사항입니다.
- **Live(.live):** 프로덕션용 콘텐츠를 게시했습니다.

![URL 구조](/help/edge/docs/forms/universal-editor/assets/url-structure.svg)
*Edge Delivery Services 양식 URL 구조 분류*

#### 시각적 예

**Edge Delivery Services 템플릿:**

- 스테이징됨: ![스테이징된 버전 등록](/help/forms/assets/registration-form-staged-version.png)
- Live: ![Live 버전 등록](/help/forms/assets/registration-form-live-version.png)

## 문제 해결

다음은 Edge Delivery Services이 포함된 AEM Forms에 대한 일반적인 문제 및 솔루션입니다.

+++양식 로드 안 됨

**문제:** 양식 URL이 404 또는 빈 페이지를 반환합니다.

**해상도:**

- URL에서 `.html` 확장을 제거합니다.
- 양식이 게시되었는지 확인합니다.
- GitHub 저장소에서 적응형 Forms 블록을 확인합니다.
- 양식 이름이 URL과 일치하는지 확인합니다(대/소문자 구분).

+++

+++구성 문제

**문제:** Edge Delivery Services 구성이 작동하지 않습니다.

**해상도:**

- GitHub URL이 `https://github.com/owner/repository` 형식인지 확인하십시오.
- 구성에 올바른 분기 이름을 사용하십시오.
- 저장소 액세스(공개 또는 인증)를 확인합니다.
- 올바른 GitHub 세부 정보는 `fstab.yaml`을(를) 확인하십시오.

+++

+++게시 문제

**문제:** 변경 내용이 라이브 사이트에 표시되지 않습니다.

**해상도:**

- CDN 캐시를 새로 고칠 때까지 2~3분 정도 기다립니다.
- 게시 워크플로우가 완료되었는지 확인합니다.
- 먼저 스테이징된(.page) 환경에서 테스트하십시오.
- GitHub 저장소가 업데이트되었는지 확인합니다.

+++

+++유니버설 편집기 문제

**문제:** 양식 또는 구성 요소가 로드되지 않아 편집할 수 없습니다.

**해상도:**

- 지원되는 브라우저(Chrome, Firefox, Safari)를 사용합니다.
- 브라우저 캐시와 쿠키를 지웁니다.
- 네트워크 연결을 확인합니다.
- 작성자 권한을 확인합니다.

+++

+++양식 제출 오류

**문제:** 양식 제출이 작동하지 않습니다.

**해상도:**

- 양식 속성에서 제출 액션을 구성합니다.
- 제출 엔드포인트를 수동으로 테스트합니다.
- 양식을 포함하는 경우 CORS 설정을 확인합니다.
- 필수 필드가 구성되어 있는지 확인합니다.

+++

+++성능 문제

**문제:** 양식 로드 속도가 느리거나 성능이 저하됩니다.

**해상도:**

- 이미지를 최적화합니다.
- 불필요한 구성 요소를 제거합니다.
- Edge Delivery Services CDN 활용.
- 사용자 지정 JavaScript/CSS를 최소화합니다.

+++

+++도움말 보기

문제가 지속되는 경우:

1. Adobe Experience Cloud 서비스 상태를 확인합니다.
2. [Edge Delivery Services 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html?lang=ko)를 검토하십시오.
3. [Adobe Experience League 커뮤니티](https://experienceleaguecommunities.adobe.com/?profile.language=ko)를 방문하십시오.
4. Adobe 고객 지원 센터에 문의하십시오.

+++

## 다음 단계

양식 작성 및 게시를 완료한 후 다음 사항을 고려하십시오.

- [제출 동작 구성](/help/edge/docs/forms/universal-editor/submit-action.md): 데이터 처리 및 통합을 설정합니다.
- [양식 데이터 모델](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md): 양식을 백엔드 데이터 소스에 연결합니다.
- [Edge Delivery Services 모범 사례](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/overview.html?lang=ko): 성능을 최대화합니다.
- [양식 분석](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/analytics.html): 양식 성능 및 사용자 동작을 추적합니다.

