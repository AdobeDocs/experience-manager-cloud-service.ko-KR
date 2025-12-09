---
title: 대화형 통신(IC) 편집기 시작하기
description: 대화형 커뮤니케이션을 통해 조직은 개인화된 데이터 기반 커뮤니케이션을 디자인하고 제공할 수 있습니다.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
source-git-commit: d24e88b545a17e50c1e80e1aedbb1d0adf55f609
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 11%

---


# 대화형 통신(IC) 편집기 시작하기

>[!NOTE]
>
> 대화형 통신 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 액세스 권한을 요청하려면 회사 이메일 주소를 통해 `aem-forms-ea@adobe.com`으로 이메일을 보내시기 바랍니다.

>[!IMPORTANT]
>
> **변경될 수 있는 설명서**: 이 프롬프트 라이브러리는 현재 제품과의 일치 여부를 테스트 중이며 업데이트 및 개정이 이루어질 수 있습니다. 얼리 어답터 프로그램이 진행되는 동안 Forms Experience Builder가 계속 발전함에 따라 프롬프트. 예시 및 모범 사례가 변경될 수 있습니다.

Adobe Experience Manager(AEM) Forms의 **대화형 통신(IC) 편집기**&#x200B;를 통해 조직은 디지털 채널과 인쇄 채널 전반에 걸쳐 명세서, 송장, 서신과 같은 개인화된 데이터 기반 통신을 디자인하고 제공할 수 있습니다. 이 안내서에서는 온보딩에서 IC 편집기 인터페이스 탐색에 이르기까지 시작하는 방법에 대한 개요를 제공합니다.


## 온보딩 및 액세스

### 액세스 요구 사항

대화형 통신을 사용하려면 AEM Forms as a Cloud Service 환경에 **AEM Forms 추가 기능**&#x200B;이 포함되어 있는지, 계정에 적절한 권한이 있는지 확인하십시오.

### 브라우저 확인

지원되는 브라우저 및 클라이언트 플랫폼을 확인하려면 연결된 문서 [지원되는 클라이언트 플랫폼](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/overview/supported-platforms)을 참조하세요.

>[!NOTE]
>
> **릴리스 주기가 빠른 브라우저 지원:**
> Firefox, Chrome, Edge는 정기적으로 업데이트를 릴리스합니다. Adobe는 해당 브라우저에서 향후 제공되는 버전에 대해서도 위에 나열된 지원 수준을 유지하기 위해 최선을 다하고 있습니다.

### 사용자 역할 및 권한 구성

IC 편집기 기능에 대한 액세스는 [AEM 내의 사용자 역할](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/accessing/aem-users-groups-and-permissions)에 의해 관리됩니다. 다음은 대화형 커뮤니케이션의 생성 및 관리와 관련된 주요 역할입니다.

| **역할** | **설명** | **주요 권한** |
| --------------------- | ---------------------------------------------------------- | -------------------------------------------- |
| **양식 작성자** | 대화형 통신을 만들고 편집합니다. | IC 만들기, 편집, 미리 보기 및 게시 |
| **템플릿 작성자** | 대화형 커뮤니케이션용 재사용 가능한 템플릿을 디자인합니다. | 템플릿을 만들고 잠그고 레이아웃을 정의합니다. |
| **관리자** | 사용자 액세스, 권한 및 구성을 관리합니다. | 역할 할당, 템플릿 관리, IC 게시 |
| **FDM 작성자** | 데이터 통합을 위해 [FDM(양식 데이터 모델)을 만들고 관리합니다](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/create-form-data-models). | 데이터 소스 및 모델을 생성, 편집 및 구성합니다. |

>[!NOTE]
>
> 사용자가 해당 기능에 액세스하려면 적절한 AEM 그룹(예: `forms-user`, `fdm-author`, `template-authors`)에 속하는지 확인하십시오.

## IC 편집기 액세스

1. **AEM Forms as a Cloud Service** 인스턴스에 로그인합니다.
2. **Forms > 대화형 통신**(으)로 이동합니다.
3. **대화형 통신**→ **만들기**&#x200B;를 클릭합니다.
4. **템플릿**&#x200B;을(를) 선택하고 데이터 원본을 구성한 다음 **만들기**&#x200B;을(를) 클릭하여 **대화형 통신 편집기**&#x200B;를 엽니다.

편집기는 인쇄 및 웹 버전의 커뮤니케이션을 디자인, 미리보기 및 관리할 수 있는 통합된 환경을 제공합니다.

## 인터페이스 탐색

**대화형 통신 편집기** 인터페이스는 작성자가 모든 디자인 도구 및 구성 옵션에 직관적으로 액세스할 수 있도록 설계되었습니다.

![IC 문서 찾기](/help/forms/interactive-communication/assets/navigate-the-interface.png)

### &#x200B;1. 상단 도구 모음

![IC 문서 찾기](/help/forms/interactive-communication/assets/tool-bar.png)

**위치:** 최상위 섹션

**목적:** 환경 액세스 및 전역 작업을 제공합니다.

**포함:**

사용자 설정 및 환경 액세스를 관리하기 위해 **Adobe Experience Cloud 환경**(예: 스테이징)을 **프로젝트 제목**, **Beta 피드백**, **알림** 및 **프로필 컨트롤**&#x200B;과 함께 표시합니다.

### &#x200B;2. 탭 표시줄(디자인/기본 탭 및 파일 제어)

![IC 문서 찾기](/help/forms/interactive-communication/assets/tab-bar.png)

**위치:** 맨 위 머리글 아래

**목적:** 보기 및 통신 파일을 관리합니다.

**포함:**

레이아웃 및 재사용 가능한 요소 디자인을 위해 **탭:** **디자인 보기**&#x200B;와(과) **기본 페이지 보기** 간을 전환합니다.

**파일 이름:** 현재 통신 제목(예: ic-11)을 표시합니다.

**컨트롤 보기:** 규칙, 만들기, 확대/축소(85%), 실행 취소/다시 실행, 삭제, PDF 미리 보기 및 저장과 같은 옵션

### &#x200B;3. 왼쪽 패널(탐색 및 구성 요소 도구)

![IC 문서 찾기](/help/forms/interactive-communication/assets/left-panel.png)

인터페이스 왼쪽 **위치:**

**목적:** 프로젝트 구조, 재사용 가능한 자산 및 데이터 바인딩에 액세스합니다.

**포함:**

* **홈 페이지:** 사용자를 기본 IC(대화형 통신) 홈 화면으로 이동하여 기존 IC와 폴더를 보고 관리할 수 있습니다.

* **메뉴 패널:** 눈금자, 개체 경계, 눈금에 맞춤, 기능 개체에 맞춤, XDP 가져오기 기능 등의 보기 관련 옵션을 표시합니다.

* **계층 구조 보기:** 통신의 구성 요소 구조를 표시하여 페이지, 패널 및 하위 폼의 구성을 표시합니다.

* **구성 요소 라이브러리:**&#x200B;에는 캔버스로 끌 수 있는 텍스트, 이미지, 하위 양식 및 바코드와 같은 디자인 요소가 포함되어 있습니다.

* **조각:** 미리 정의된 디자인과 콘텐츠 블록을 여러 통신에서 다시 사용할 수 있습니다.

* **데이터 모델:** 동적 데이터를 바인딩하기 위해 기본 양식 데이터 모델(FDM)에 통신을 연결합니다.

### &#x200B;4. 중앙 Workspace(디자인 캔버스)

![IC 문서 찾기](/help/forms/interactive-communication/assets/canvas.png)

인터페이스의 **위치:** 가운데

대화형 커뮤니케이션을 디자인하기 위한 **목적:** 기본 작업 영역.

**기능:**

* 라이브러리에서 구성 요소 드래그 앤 드롭

* 시각적 레이아웃 정렬 및 서식 지정

* 페이지, 하위 양식 및 필드 추가 또는 편집

* 왼쪽 하단의 컨트롤을 사용하여 페이지 간(예: &quot;1/1&quot;) 탐색

* 게시하기 전에 최종 레이아웃 미리 보기

### &#x200B;5. 오른쪽 패널(속성 패널)

![IC 문서 찾기](/help/forms/interactive-communication/assets/right-panel.png)

화면의 오른쪽 **위치:**

**목적:** 구성 요소 동작 및 스타일을 사용자 지정합니다.

**포함:**

* 일반 설정(이름, 유형, 흐름/위치)

* 레이아웃 및 모양 옵션

* 페이지 매김, 위치, 현재 상태 및 데이터 바인딩 컨트롤