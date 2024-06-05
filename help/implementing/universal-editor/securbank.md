---
title: 범용 편집기용 SecurBank 샘플 앱
description: 콘텐츠 제작 시간을 단축할 수 있는 범용 편집기의 강력한 기능, 유연성 및 유용성을 선보이도록 설계된 SecurBank 앱을 사용하여 실습 경험을 갖춘 범용 편집기에 대해 알아보십시오.
exl-id: 97e1395f-b51e-4cee-b1d0-2466a08f96af
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 1%

---

# 범용 편집기용 SecurBank 샘플 앱 {#securbank}

콘텐츠 제작 시간을 단축할 수 있는 범용 편집기의 강력한 기능, 유연성 및 유용성을 선보이도록 설계된 SecurBank 앱을 사용하여 실습 경험을 갖춘 범용 편집기에 대해 알아보십시오.

## 사전 요구 사항 {#prerequisites}

* 을(를) (으)로 할당해야 합니다. **AEM 관리자** [제품 프로필](/help/journey-onboarding/assign-profiles-aem.md) 를 클릭하여 SecurBank 앱을 설치합니다.
* 다음을 수행해야 합니다. [Node.js](https://nodejs.org) 로컬 개발을 위해 버전 20 이상이 설치되었습니다.

## SecurBank 설치 {#installation}

SecurBank 앱의 설치는 직진이지만 AEM의 많은 영역에 as a Cloud Service으로 접촉하기 때문에 많은 단계가 수반됩니다. 다음은 주요 단계에 대한 개요입니다.

1. [Cloud Manager에서 샌드박스 프로그램을 만듭니다.](#create-sandbox-program)
1. [프로그램의 git 저장소를 복제하고 SecurBank AEM 프로젝트 콘텐츠로 업데이트합니다.](#clone-and-update)
1. [파이프라인을 실행하여 SecurBank AEM 프로젝트를 배포합니다.](#run-pipeline)
1. [로컬 웹 앱 개발을 위한 Cloud Manager 자격 증명을 검색합니다.](#retrieve-credentials)
1. [SecurBank 웹 앱을 다운로드하여 구성합니다.](#download-web-app)
1. [SecurBank 웹 앱을 실행합니다.](#run-web-app)

다음 섹션에서는 필요한 개별 작업에 대해 자세히 설명합니다.

### Cloud Manager에서 샌드박스 프로그램을 만듭니다. {#create-sandbox-program}

SecurBank를 설치할 수 있는 새 Cloud Manager 프로그램이 필요합니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직 선택

1. SecurBank 앱에 대한 새 샌드박스 프로그램을 만듭니다.

   * 선택할 때 기본 옵션 사용 **솔루션 및 추가 기능**.
   * 샌드박스 프로그램을 만드는 방법에 대한 자세한 내용은 문서를 참조하십시오. [샌드박스 프로그램 만들기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md)

### 프로그램의 git 저장소를 복제하고 SecurBank AEM 프로젝트 콘텐츠로 업데이트합니다. {#clone-and-update}

1. 프로그램이 만들어지면 프로그램을 열고 **저장소** 탭, 탭 또는 클릭 **저장소 정보 액세스** 단추를 클릭하여 열기 **저장소 정보** 대화 상자를 통해 샌드박스 환경의 git 저장소에 액세스하는 데 필요한 자격 증명을 확인할 수 있습니다.

   * 저장소 정보에 액세스하는 방법에 대한 자세한 내용은 문서를 참조하십시오 [저장소에 액세스합니다.](/help/implementing/cloud-manager/managing-code/accessing-repos.md)

1. 에서 자격 증명 사용 **저장소 정보** 대화 상자에서 로컬 컴퓨터의 저장소를 복제합니다.

1. 로컬 클론의 폴더를 찾아 열고 숨겨진/점 파일을 제외한 모든 컨텐츠를 삭제합니다.

1. GitHub에서 최신 SecurBank AEM 프로젝트 코드 검색 [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank`](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425-securbank) 다음을 클릭: **코드** 그런 다음 **ZIP 다운로드** 드롭다운에서 을 클릭합니다.

1. 로컬 파일 시스템에서 zip 파일의 압축을 풀고 샌드박스 프로그램의 로컬 복제본에 있는 빈 폴더로 이동합니다.

1. 터미널을 사용하여 복제된 프로젝트의 폴더로 전환하고 모든 콘텐츠를 커밋한 다음 git으로 푸시합니다.

   1. `git add --all`
   1. `git commit -m "Adding SecurBank app code"`
   1. `git push`

### 파이프라인을 실행하여 SecurBank AEM 프로젝트를 배포합니다. {#run-pipeline}

샌드박스 저장소에 커밋된 SecurBank용 AEM 프로젝트를 사용하여 파이프라인으로 배포할 수 있습니다.

1. (으)로 돌아가기 **개요** cloud Manager에서 샌드박스 프로그램의 탭과 전체 스택 비프로덕션 파이프라인 실행

   * 파이프라인 실행에 대한 모든 옵션을 선택 취소합니다.
   * 파이프라인 실행에 대한 자세한 내용은 문서를 참조하십시오. [파이프라인 관리.](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines)

### 로컬 웹 앱 개발을 위한 Cloud Manager 자격 증명을 검색합니다. {#retrieve-credentials}

SecurBank 앱을 실행하려면 먼저 Cloud Manager 자격 증명이 있어야 앱을 Cloud Manager에 연결할 수 있습니다.

1. 파이프라인이 실행 중이면 **개요** cloud Manager에서 탭을 클릭하고 환경 이름 옆에 있는 줄임표 버튼을 탭하거나 클릭하여 선택합니다. **개발자 콘솔**.

1. 개발자 콘솔에서 다음을 선택합니다. **통합** 탭을 클릭한 다음 **로컬 토큰** 탭하고 탭하거나 클릭 **로컬 개발 토큰 가져오기**.

1. 액세스 토큰으로 JSON 파일이 생성됩니다. 개발자 콘솔을 닫고 Cloud Manager로 돌아가기 전에 향후 단계에서 사용할 수 있도록 토큰 자체(나머지 JSON은 필요하지 않음)만 보안 위치에 복사합니다.

1. Cloud Manager로 돌아가기 **개요** 탭을 클릭하고 환경의 URL을 마우스 오른쪽 단추로 클릭하여 복사하고 향후 단계에서 사용할 수 있도록 안전한 위치에 저장합니다.

### SecurBank 웹 앱을 다운로드하여 구성합니다. {#download-web-app}

이제 SecurBank 웹 앱을 다운로드하여 구성할 수 있습니다.

1. GitHub에서 최신 SecurBank 앱 코드 검색 [`https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events`](https://github.com/Adobe-Marketing-Cloud/summit-2024-l425/tree/ue-z-final-with-events) 다음을 클릭: **코드** 그런 다음 **ZIP 다운로드** 드롭다운에서 을 클릭합니다.

1. 로컬 파일 시스템에서 zip 파일의 압축을 해제합니다.

1. 기본 코드 편집기를 시작하고 SecurBank 앱 프로젝트에서 숨김 환경 파일을 엽니다. `summit-2024-l425-ue-z-final-with-events/react-app/.env`.

1. 다음 사항을 변경합니다. `.env` 파일을 만들고 변경 사항을 저장합니다.

   * 대상 `REACT_APP_HOST_URI` 이전에 복사한 환경 URL의 값을 붙여넣습니다.
   * 대상 `REACT_APP_DEV_TOKEN` 이전에 복사한 로컬 개발 토큰의 값을 붙여넣습니다.

### SecurBank 웹 앱을 실행합니다. {#run-web-app}

Cloud Manager와 로컬에서 모두 설정하는 경우 SecurBank 웹 앱을 실행할 수 있습니다.

1. 로컬 컴퓨터의 명령줄에서 `react-app` 다운로드 및 압축 해제한 SecurBank 앱 프로젝트의 폴더입니다.

1. 내 `react-app` 폴더 를 사용하여 SecurBank 앱 설치 `node -i` 명령입니다.

1. 설치가 완료되면 다음을 사용하여 SecurBank 앱을 시작합니다. `npm start` 명령입니다.

1. 설치 및 시작이 성공하면 다음과 같이 표시됩니다.

* 터미널에서 다음 출력.

  ```text
  Compiled successfully!
  
  You can now view securbank in the browser.
  
    Local:            https://localhost:3000
    On Your Network:  https://192.168.1.15:3000
  
  Note that the development build is not optimized.
  To create a production build, use npm run build.
  
  webpack compiled successfully
  ```

   * 그리고 브라우저 창이 URL로 열립니다 `https://localhost:3000`.

      * 개발 목적이므로 유효한 인증서가 제공되지 않습니다. 따라서 브라우저에 알리고 페이지에 액세스할 수 있도록 해야 할 수 있습니다.

축하합니다! 이제 브라우저에서 SecurBank 앱이 성공적으로 실행되는 것을 볼 수 있습니다.

콘텐츠가 아직 표시되지 않으면 **개발로 배포** 실행한 파이프라인이 정상적으로 완료되었습니다.

![브라우저의 SecurBank 앱](assets/securbank.png)
