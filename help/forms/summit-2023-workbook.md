---
title: 핵심 구성 요소 및 Headless를 사용하여 매력적인 Forms 구축
seo-title: Build Engaging Forms Using Core Components and Headless
description: 핵심 구성 요소 및 Headless를 사용하여 매력적인 Forms 구축
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
hide: true
hidefromtoc: true
source-git-commit: b68902ef4f7c61f77aa0d03ad718d5bf3023dea0
workflow-type: tm+mt
source-wordcount: '2465'
ht-degree: 1%

---


# 핵심 구성 요소 및 Headless를 사용하여 매력적인 Forms 구축

## 랩 개요

이 실습형 랩에서는 다음을 배울 수 있습니다.

AEM Forms을 사용하여 AEM Sites과 일치하는 최신 핵심 구성 요소를 사용하여 적응형 양식을 쉽게 만들고 적응형 양식을 웹, 모바일 및 채팅에 Headless 양식으로 전달하여 옴니채널 데이터 캡처 경험을 활성화하는 방법 또한 스타일 지정, 사용자 지정 및 프론트엔드 개발에 대한 모범 사례에 대해 알아봅니다.

## 주요 개선 사항

* **비즈니스 민첩성**: 비즈니스 사용자는 여러 채널에 대한 양식 환경을 쉽게 작성할 수 있습니다.

* **강력한 프론트엔드 개발자**: 프론트엔드 개발자로서 Headless 양식을 사용하여 최종 사용자 경험을 제어할 수 있습니다.

* **개발자 속도**: 개발자로서 Sites 및 Forms 구성 요소를 쉽고 일관되게 사용자 지정할 수 있습니다.

## 사전 요구 사항

Cloud Service 샌드박스로 AEM Forms

## 단원 1

### 목표

AEM Forms as a Cloud Service 환경을 숙지하십시오.

### 단원 컨텍스트

이 단원에서는 사용자 인터페이스를 탐색하여 AEM Forms as a Cloud Service 환경에 익숙해집니다.

### 운동

1. 브라우저를 열고 Cloud Service 작성자 환경의 URL을 입력합니다. 예:
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. 공유된 자격 증명에 따라 Cloud Service 작성자 환경에 로그인합니다. 예: 사용자 이름: [L716+001@summitlab.us](mailto:L716%2B001@summitlab.us)
암호: 
**Adobe123!**

1. 로그인한 후 AEM Forms UI로 이동합니다. 클릭 **Forms**.

   ![](/help/forms/assets/screenshot2028113829.png)

1. 클릭 **Forms 및 문서**. 환경 설정 또는 정보와 관련된 팝업을 모두 닫습니다.

   ![](/help/forms/assets/screenshot2028113929.png)

   사용 가능한 모든 양식이 표시됩니다.

   ![](/help/forms/assets/screenshot2028114029.png)

## 단원 2

### 목표

최신 핵심 구성 요소를 사용하여 적응형 양식을 작성하고 양식을 구성하고 제출합니다.

## 단원 컨텍스트

이 단원에서는 비즈니스 사용자로서, 데이터 캡처를 위한 표준화된 OOTB 핵심 구성 요소로 적응형 양식 작성을 사용하여 웹, 모바일 및 채팅과 같은 여러 채널에 대한 적응형 양식을 작성합니다.

## 운동

1. 양식에 대한 제출 엔드포인트 만들기:

   1. 열기 <https://requestbin.com/> 새 브라우저 탭에서.
      ![](/help/forms/assets/screenshot2028114329.png)

   1. 클릭 **공용 BIN 만들기** 끝점 URL을 복사합니다.
      ![](/help/forms/assets/screenshot202023-03-0120at206.10.0020pm.png)

1. 마법사 인터페이스를 사용하여 적응형 양식을 작성합니다.

   1. 단원 1에 사용된 브라우저 탭에서 AEM Forms as Cloud Service 웹 인터페이스로 이동하고 Forms 및 문서로 이동합니다.
      ![](/help/forms/assets/screenshot2028114029.png)

   1. 클릭 **만들기** 적응형 양식을 선택합니다.
      ![](/help/forms/assets/screenshot2028114629.png)

   1. 다음 항목 선택 **핵심 구성 요소가 포함된 빈 항목** 템플릿 선택 화면에서 템플릿(아래 참조):
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. 다음을 클릭합니다. **스타일** 탭을 클릭하고 다음을 선택합니다. **wknd-테마** 아래 표시된 테마:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. 다음을 클릭합니다. **제출** 탭을 클릭하고 다음을 선택합니다. **REST 끝점에 제출** 카드 및 의 공용 저장소를 지정합니다.
      **POST 요청용 URL** 아래에 표시된 필드:
      ![](/help/forms/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. **만들기**&#x200B;를 클릭합니다. 양식에 이름과 제목을 지정합니다. 예를 들어, **접촉선**. **만들기**를 클릭합니다.
      ![](/help/forms/assets/screenshot2028123329.png)

   1. 적응형 양식 편집기가 열립니다. 환경 설정 또는 정보에 대한 팝업이나 대화 상자를 모두 닫습니다. 왼쪽 레일에서 구성 요소 브라우저를 클릭하고 **바닥글** 구성 요소를 사용하여 빈 양식의 맨 아래에 놓습니다.
      ![](/help/forms/assets/screenshot2028121929.png)

   1. 추가 **머리글** 구성 요소를 사용하여 양식 맨 위에 놓습니다.
      ![](/help/forms/assets/screenshot2028122029.png)

   1. 추가 **제목** 구성 요소를 양식의 가운데로 가져옵니다.
      ![](/help/forms/assets/screenshot2028122129.png)

   1. 추가 **텍스트 입력** 제목 구성 요소 뒤에 있는 구성 요소입니다.
      ![](/help/forms/assets/screenshot2028122329.png)

   1. 추가 **숫자 입력** 구성 요소.
      ![](/help/forms/assets/screenshot2028122429.png)

   1. 추가 **전송 단추** 구성 요소를 양식에 추가합니다.
      ![](/help/forms/assets/screenshot2028122529.png)

   1. 다음을 클릭합니다. **제목** 구성 요소 **팝업 메뉴** 이 표시됩니다. 다음을 클릭합니다. **편집 아이콘** 을 클릭하여 레이블을 편집합니다.
      ![](/help/forms/assets/screenshot2028122629.png)

   1. 입력 `Contact Us` 제목 텍스트로 사용됩니다.
      ![](/help/forms/assets/screenshot2028122829.png)

   1. 다음을 클릭합니다. **텍스트 입력** 구성 요소를 사용하여 팝업 메뉴를 표시합니다. 다음을 클릭합니다. **편집 아이콘** 을 클릭하여 레이블을 편집합니다.
      ![](/help/forms/assets/screenshot2028122929.png)

   1. 입력 **전체 이름** 필드 레이블로 사용됩니다.
      ![](/help/forms/assets/screenshot2028123029.png)

   1. 다음을 클릭합니다. **숫자 입력** 구성 요소를 사용하여 팝업 메뉴를 표시합니다. 다음을 클릭합니다. **편집 아이콘** 을 클릭하여 레이블을 편집합니다.
      ![](/help/forms/assets/screenshot2028123129.png)

   1. 다음을 입력합니다. **전화 번호** 를 필드 레이블로 사용하십시오.
      ![](/help/forms/assets/screenshot2028123829.png)


1. 양식에 유효성 검사 추가:

   1. 다음을 클릭합니다. **전화 번호** 구성 요소를 사용하여 팝업 메뉴를 표시합니다. 다음을 클릭합니다. **렌치 아이콘** 을 클릭하여 필드를 구성합니다.
      ![](/help/forms/assets/screenshot2028123429.png)

   1. 를 엽니다. **유효성 검사 탭**, 필드를 표시합니다. **필수**, 및 클릭 **완료**. 성공 메시지가 표시됩니다.
      ![](/help/forms/assets/screenshot2028123529.png)

      ![](/help/forms/assets/screenshot2028123629.png)

   1. 클릭 **미리 보기** 최종 사용자 관점에서 양식을 미리 봅니다.
      ![](/help/forms/assets/screenshot2028125529.png)

   1. 더미 데이터로 양식 채우기
      ![](/help/forms/assets/screenshot2028125629.png)

   1. 양식 제출
      ![](/help/forms/assets/screenshot2028125729.png)

   1. Request bin 탭에서 제출된 데이터를 확인합니다.
      ![](/help/forms/assets/screenshot2028125829.png)

이제 나머지 연습을 수행하려면 미리 만든 등록 양식을 사용하십시오.

1. AEM Forms 관리 인터페이스(예: ) 열기 `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`을 누르고 등록 양식을 선택합니다.

   ![](/help/forms/assets/screenshot2028115529.png)

1. **게시**&#x200B;를 클릭합니다. 

   ![](/help/forms/assets/screenshot2028115629.png)

   성공 메시지가 표시됩니다.

   ![](/help/forms/assets/screenshot2028115729.png)

   양식의 게시 URL은 와 유사합니다. `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`.

1. 게시된 양식을 보려면 위 URL의 프로그램 ID(pXXXXXX) 및 환경 ID(eXXXXXX)를 사용자 환경의 ID로 바꾸십시오.

## 단원 3

### 목표

프론트엔드 개발 모범 사례를 사용하여 스타일을 업데이트합니다.

### 단원 컨텍스트

이 단원에서는 프론트엔드 개발자로서 이전에 만든 적응형 양식의 스타일을 쉽게 업데이트할 수 있는 방법에 대해 알아봅니다.

### 운동

테마의 로컬 저장소 설정:

1. 관리자 권한으로 명령 프롬프트 또는 셸을 엽니다.

   ![](/help/forms/assets/screenshot2028115829.png)

1. 명령 프롬프트에서 다음 명령을 사용하여 **c:\git** 폴더

   ```Shell
   cd c:\git
   ```

1. 다음 명령을 사용하여 테마 프론트엔드 코드를 복제합니다.

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. 나열된 순서로 다음 명령을 사용하여 **aem-forms-theme-canvas** Visual Studio Code를 열고 디렉터리를 엽니다.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/forms/assets/screenshot2028126029.png)

1. 선택 **상위 폴더에 있는 모든 파일의 작성자를 신뢰합니다.** 및 클릭 **예, 작성자를 믿습니다.**.

   ![](/help/forms/assets/screenshot2028116229.png)

1. 클라우드 서비스 게시 환경에서 호스팅된 양식을 렌더링하려면 `env_template` 파일.  파일 이름을 바꾸려면 **env_template** 파일 및 선택 **이름 바꾸기** 옵션을 선택합니다.

   ![](/help/forms/assets/screenshot2028116429.png)

   </br>

   ![](/help/forms/assets/screenshot2028116529.png)

1. .env 파일에서 변수에 대해 다음 값을 설정하고 파일을 저장합니다.

   * **AEM_URL**: 클라우드 서비스 게시 환경을 지정합니다. 예, `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**: 양식의 경로를 지정합니다. 예를 들어 양식 경로가 `/content/forms/af/registration`, 이 변수의 값은 다음과 같습니다. `registration`.

   ![](/help/forms/assets/screenshot2028116429.png)


1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * 를 통해 npm을 업데이트하라는 메시지가 표시되는 경우 `npm notice Run npm nstall -g npm@9.6.0`명령, 메시지를 무시합니다.
   > * 통합 문서에서 지시하지 않는 한 다른 npm 명령을 실행하지 마십시오.


1. 이제 다음 명령을 실행하여 양식을 미리 봅니다.

   ```Shell
   npm run live
   ```

   ![](/help/forms/assets/screenshot2028117229.png)

   위의 명령이 실행되면 다음을 기다립니다. `webpack compiled` 메시지. 양식이 브라우저 탭에 표시됩니다.

   >[!NOTE]
   >
   >를 실행한 후 브라우저에서 빈 화면이 표시되는 경우 `npm run live` 3-4분 이상 명령, 변경 `localhost` 를 브라우저 URL에서 127.0.0.1로 변경하고 히트합니다. **입력**.


   ![](/help/forms/assets/screenshot2028115129.png)


1. Visual Studio Code에서 `PROJECT\src\site\_variables.scss` 파일. 다음 사항에 주목합니다. `$error` 색상은 빨간색 음영입니다.

   ![](/help/forms/assets/screenshot2028120729.png)

1. 브라우저에서 양식을 제출하여 **이름** 필드.

   ![](/help/forms/assets/screenshot2028120829.png)

1. 설정 **$error** 색상 대상 **#5736eb** 파일을 저장합니다.

   ![](/help/forms/assets/screenshot2028120729.png)

1. 브라우저를 새로 고치고 양식을 제출합니다. 이름 필드의 오류 색상이 그에 따라 변경되었습니다.

   ![](/help/forms/assets/screenshot2028121129.png)

1. 명령 프롬프트에서 **CTRL+C**, 입력 **Y**, 및 누르기 **입력** npm 프로세스를 종료하는 키. npm 서버가 다음 연습 세트와 충돌하지 않도록 중지하는 것이 중요합니다.
1. Visual Studio 코드 및 명령 프롬프트 창을 닫습니다.

## 제4과

### 목표

양식을 웹/모바일 및 기타 인터페이스로 Headless 양식으로 렌더링합니다.

### 단원 컨텍스트

이 단원에서는 프론트엔드 개발자로서 React 스펙트럼 디자인 프레임워크를 사용하여 이전에 만든 적응형 양식을 Headless 양식으로 렌더링할 수 있는 방법에 대해 알아봅니다.

### 운동

React Starter 프로젝트를 사용하여 로컬 저장소 설정:

1. 관리자 권한을 사용하여 명령 프롬프트를 엽니다.

   ![](/help/forms/assets/screenshot2028115829.png)

1. 명령 프롬프트에서 다음 명령을 사용하여 **c:\git** 폴더

   ```Shell
   cd c:\git
   ```

1. 다음 명령을 사용하여 적응형 양식 React 스타터 프로젝트를 복제합니다.

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028117329.png)

1. 나열된 순서로 다음 명령을 사용하여 **react-starter-kit-aem-headless-forms** Visual Studio Code를 열고 디렉터리를 엽니다.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028117529.png)


   Visual Studio Code 창이 열립니다.

   ![](/help/forms/assets/screenshot2028117429.png)

Cloud Service 게시 환경에서 호스팅된 양식을 렌더링하려면 다음을 수행하십시오.

1. env_template 파일의 이름을 .env 파일로 바꿉니다. 이름을 바꾸려면 **env_template** 파일 및 선택 **이름 바꾸기** 옵션을 선택합니다.

   ![](/help/forms/assets/screenshot2028117629.png)

   ![](/help/forms/assets/screenshot2028117729.png)

1. .env 파일에서 변수에 대해 다음 값을 설정합니다. 변수를 업데이트한 후 파일을 저장합니다.

   * **AEM_URL**: Cloud Service 게시 환경의 URL을 지정합니다. 예, `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**: 이전 단원에서 만든 적응형 양식의 경로를 지정합니다. 예, `/content/forms/af/registration/`

      ![](/help/forms/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. 명령 창을 열고 react-starter-kit-aem-headless-forms 디렉토리에 있는지 확인하고 다음 명령을 실행합니다.

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028118029.png)


1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028118129.png)

   위의 명령은 반응 스펙트럼 프론트엔드 라이브러리를 사용하여 headless 방식으로 AEM에서 가져온 양식 정의를 렌더링하는 로컬 개발 서버를 시작합니다.

   >[!NOTE]
   >
   > 
   > 를 실행한 후 브라우저에서 빈 화면이 표시되는 경우 `npm start` 3-4분 이상 명령, 변경 `localhost` 를 브라우저 URL에서 127.0.0.1로 변경하고 히트합니다. **입력**.

   ![](/help/forms/assets/screenshot2028118229.png)

이 Headless 양식에서 규칙 실행을 확인해 보겠습니다.

1. 다음 항목 선택 **5% 할인을 받으려면 상자를 선택합니다.** 옵션을 선택합니다. 신용 카드를 적용하는 후속 옵션이 비활성화됩니다.

   ![](/help/forms/assets/screenshot2028126229.png)

1. 선택 취소 **5% 할인을 받으려면 상자를 선택합니다.** 신용 카드 옵션을 활성화하려면 다음을 수행하십시오.

   ![](/help/forms/assets/screenshot2028126329.png)

비즈니스 사용자로 서버의 양식을 변경하고 Headless 양식에 반영된 변경 사항을 자동으로 보겠습니다.

1. 브라우저에서 AEM Forms 관리 인터페이스를 엽니다. 예를 들어, [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments).

1. 다음 항목 선택 **등록** 양식 및 클릭 **편집.** 적응형 양식 편집기에서 양식이 열립니다.

   ![](/help/forms/assets/screenshot2028118529.png)

1. 다음 항목 선택 **전화 번호** 필드를 클릭하고 **편집 아이콘(연필 아이콘)** 을 클릭합니다. 팝업 도구 모음이 표시되지 않으면 을 클릭하여 편집 모드로 전환합니다. **편집** 오른쪽 상단의 단추, 왼쪽 **미리 보기** 단추를 클릭합니다.

   ![](/help/forms/assets/screenshot2028119629.png)

1. 레이블을 모바일 번호로 변경합니다. 양식의 빈 공간을 클릭하면 양식에 대한 변경 사항이 저장됩니다.

   ![](/help/forms/assets/screenshot2028119729.png)

업데이트된 양식을 게시하여 변경 사항을 게시 환경에 전파하겠습니다.

1. AEM Forms 관리 인터페이스 탭에서 등록 양식을 선택하고 **게시 취소**. 표시되지 않는 경우 **게시 취소** 버튼을 클릭하고 3단계로 건너뛰어 변경 사항을 직접 게시합니다.

   ![](/help/forms/assets/screenshot2028119829.png)

1. 클릭 **게시 취소**. 클릭 **닫기** 각 대화 상자에서

   ![](/help/forms/assets/screenshot2028119929.png)

   ![](/help/forms/assets/screenshot2028120029.png)


1. 브라우저를 새로 고친 후 등록 양식을 선택하고 을 클릭합니다. **게시**.

   ![](/help/forms/assets/screenshot2028120129.png)


1. **게시**&#x200B;를 클릭합니다. 클릭 **닫기** 해당 대화 상자에서 확인할 수 있습니다.

   ![](/help/forms/assets/screenshot2028120329.png)

   ![](/help/forms/assets/screenshot2028120429.png)

1. Headless 양식이 표시된 브라우저 탭을 새로 고칩니다. 전화번호 레이블이 모바일 번호로 변경되었습니다.

   ![](/help/forms/assets/screenshot2028120529.png)

1. 를 시작하는 데 사용되는 명령 프롬프트 창을 엽니다. **react-starter-kit-aem-headless-forms** 프로젝트, 누르기 **CTRL+C**&#x200B;를 클릭한 다음 을 입력합니다 **Y** npm 프로세스를 종료하려면 Enter 키를 누릅니다. npm 서버가 다음 연습 세트와 충돌하지 않도록 중지하는 것이 중요합니다.

1. Visual Studio 코드 및 명령 프롬프트 창을 닫습니다.


## 단원 5

### 목표

Google Material UI를 사용하여 양식을 Headless 양식으로 렌더링

### 단원 컨텍스트

이 단원에서 프론트엔드 개발자는 Google Material UI를 사용하여 이전에 headless 양식으로 만든 적응형 양식을 렌더링하는 방법을 알아봅니다.

### 운동

재료 UI 스타터 프로젝트를 사용하여 로컬 리포지토리 설정:

1. 관리자 권한을 사용하여 명령 프롬프트를 엽니다.

   ![](/help/forms/assets/screenshot2028115829.png)


1. 명령 프롬프트에서 다음 명령을 사용하여 **c:\git** 폴더:

   ```Shell
   cd c:\git
   ```

1. 나열된 순서로 다음 명령을 실행하여 mui 폴더를 만들고 다음 명령을 사용하여 mui 폴더로 이동합니다.

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. 다음 명령을 사용하여 적응형 양식 React 스타터 프로젝트를 복제합니다.

   ```Shell
   git clone -b mui https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/forms/assets/screenshot2028126529.png)

1. 나열된 순서로 다음 명령을 사용하여 **react-starter-kit-aem-headless-forms** 폴더를 만들고 Visual Studio Code에서 코드를 엽니다.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/forms/assets/screenshot2028126829.png)

Cloud Service 게시 환경에서 호스팅된 양식을 렌더링하려면 다음을 수행하십시오.

1. 이름 바꾸기 **env_template** 파일 위치: **.env** 파일. 이름을 바꾸려면 **env_template** 파일 및 선택 **이름 바꾸기**.

   ![](/help/forms/assets/screenshot2028126629.png)

1. .env 파일에서 변수에 대해 다음 값을 설정합니다. 변수를 업데이트한 후 파일을 저장합니다. 사용 **CTRL + S** 파일 저장을 위해 조합을 전환합니다.

   * **AEM_URL**: Cloud Service 게시 환경의 URL을 지정합니다. 예를 들어, [https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH**: 이전 단원에서 만든 적응형 양식의 경로를 지정합니다. 예: /content/forms/af/registration/

      ![](/help/forms/assets/screenshot2028126929.png)

1. 명령 창을 열고 다음을 확인합니다. **react-starter-kit-aem-headless-forms** 디렉터리를 지정하고 다음 명령을 실행합니다.

   ```Shell
   npm install
   ```

   ![](/help/forms/assets/screenshot2028127029.png)

1. 명령 프롬프트 창에서 다음 명령을 실행합니다.

   ```Shell
   npm start
   ```

   ![](/help/forms/assets/screenshot2028127129.png)

   이 명령은 로컬 개발 서버를 시작하고 Google Material UI 프론트엔드 라이브러리를 사용하여 AEM에서 가져온 양식 정의를 headless 방식으로 렌더링합니다.

   >[!NOTE]
   >
   >를 실행한 후 브라우저에서 빈 화면이 표시되는 경우 `npm start` 3-4분 이상 명령, 변경 `localhost` 를 브라우저 URL에서 127.0.0.1로 변경하고 히트합니다. **입력**.

   ![](/help/forms/assets/screenshot2028127229.png)

1. 이 양식 렌디션에서 동일한 비즈니스 논리의 실행을 평가하려면 다음을 수행합니다.

   선택 **5% 할인을 받으려면 상자를 선택합니다.**. 후속 옵션 **We.Finance 법인 신용카드 양식을 신청하시겠습니까?** 이(가) 비활성화됩니다.

   ![](/help/forms/assets/screenshot2028127329.png)

## 단원 6

### 목표

재질 UI 구성 요소 변형을 사용하여 헤드리스 양식의 대체 디자인을 만듭니다

### 단원 컨텍스트

이 단원에서는 프론트엔드 개발자로서 비즈니스 사용자가 이전에 만든 적응형 양식에 대해 재료 UI를 사용하여 다양한 구성 요소의 대체 표현을 만드는 방법을 알아봅니다.

### 운동

Headless 프로젝트에서 구성 요소의 변형을 업데이트합니다. 재질 UI 텍스트 입력 구성 요소의 변형을 (으)로 변경하려면 `OutlinedInput`:

1. 시각적 코드에서 다음을 열어 텍스트 입력 구성 요소로 이동합니다. `index.tsx` 파일 위치: `src/components/textinput/index.tsx`.

1. 추가 `//` 코드 라인 103의 시작 부분에서. 줄을 주석으로 변환합니다.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. 다른 구성 요소 변형을 사용하려면 104행에 다음을 추가하고 파일을 저장합니다. 사용 **CTRL + S** 파일 저장을 위해 조합을 전환합니다.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/forms/assets/screenshot2028127629.png)

   &#39;ForendedInput&#39; 변형에 올바른 대소문자를 사용해야 합니다. 그렇지 않으면 컴파일이 실패합니다. 로컬 개발 환경 컴파일이 명령 프롬프트에서 자동으로 시작됩니다. 다음 메시지가 표시될 때까지 기다리십시오

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. 자동으로 새로 고쳐지지 않는 경우 브라우저를 새로 고쳐 텍스트 입력 구성 요소가 다른 변형을 사용하는지 확인합니다.

   ![](/help/forms/assets/screenshot2028127729.png)


   이 변경 사항은 AEM Forms Server에서 양식 정의를 변경하지 않은 최종 사용자에 대해 발생하며 고려되는 Headless 채널에만 적용됩니다. 예를 들어 이 랩의 웹 채널입니다.

   ![](/help/forms/assets/screenshot2028127529.png)


1. Visual Studio 코드 및 명령 프롬프트 창을 닫습니다.

## 자주 묻는 질문(FAQ)

+++ 적응형 양식 마법사를 공개적으로 사용할 수 있습니까?

예, AEM Forms에서 Cloud Service으로 사용할 수 있습니다.

+++


+++ 핵심 구성 요소를 공개적으로 사용할 수 있습니까?

예. 적응형 Forms 핵심 구성 요소는 AEM Forms에서 Cloud Service으로 사용할 수 있습니다.

+++

+++ 헤드리스 양식을 공개적으로 사용할 수 있습니까?

예. 헤드리스 양식은 AEM Forms에서 Cloud Service으로 사용할 수 있습니다.

+++

+++ Headless 양식에는 별도의 라이센스가 필요합니까?

아니요. Headless 양식은 양식 제출 횟수와 동일한 라이선스 가치 지표를 사용합니다.

+++

+++ AEM 6.5 Forms에서 핵심 구성 요소 및 Headless 양식을 사용할 수 있습니까?

예. 적응형 양식 핵심 구성 요소와 Headless 양식은 모두 AEM Forms 6.5 서비스 팩 16 이상에서 사용할 수 있습니다.

+++


## 다음 단계

Headless 양식을 사용하여 적응형 양식을 작성하고 여러 채널에 전달하는 방법을 배웠으므로 이제 새로운 기술을 사용할 수 있습니다. 규모에 맞게 최종 사용자에게 뛰어난 데이터 캡처 경험을 만들어 제공함으로써 즐겁게 작업하십시오!

## 리소스

* [적응형 양식 핵심 구성 요소 소개](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html)

* [핵심 구성 요소를 사용하여 적응형 양식 만들기](https://experienceleague.corp.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html)

* [핵심 구성 요소 기반 AF의 스타일 업데이트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=en)

* [Headless 적응형 양식](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=en)

* [Headless React 스타터 키트 사용](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=en)


