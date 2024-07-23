---
title: 적응형 양식에서 사용자 정의 함수 만들기 및 추가
description: AEM Forms은 사용자가 규칙 편집기 내에서 자체 함수를 만들고 사용할 수 있도록 하는 사용자 지정 함수를 지원합니다.
keywords: 사용자 지정 함수를 추가하고, 사용자 지정 함수를 사용하고, 사용자 지정 함수를 만들고, 규칙 편집기에서 사용자 지정 함수를 사용합니다.
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: f5c17382052b4d116deaae564f1a2b9fdbb5ea0a
workflow-type: tm+mt
source-wordcount: '1523'
ht-degree: 3%

---


# 핵심 구성 요소를 기반으로 적응형 양식에 대한 사용자 지정 기능 만들기

핵심 구성 요소를 기반으로 하는 적응형 Forms은 사용자 입력에 따라 콘텐츠 및 동작을 조정하여 다이내믹한 사용자 경험을 제공합니다. 사용자 정의 기능을 사용하면 개발자가 기능을 확장하여 양식이 특정 요구 사항을 충족할 수 있습니다. 개발자는 사용자 정의 기능을 통합하여 복잡한 논리를 구현하고 프로세스를 자동화하며 특정 비즈니스 요구 사항 또는 사용자의 기대에 부합하는 고유한 상호 작용을 도입할 수 있습니다. 양식이 다양한 조건에 적응할 뿐만 아니라 다양한 사용 사례에 대해 보다 정확하고 효과적인 솔루션을 제공하도록 보장합니다.
이 문서에서는 핵심 구성 요소를 사용하여 적응형 Forms에 대한 사용자 지정 기능을 만드는 단계를 안내합니다.

## 고려 사항

* `parameter type` 및 `return type`은(는) `None`을(를) 지원하지 않습니다.

* 사용자 지정 함수 목록에서 지원되지 않는 함수는 다음과 같습니다.
   * 생성기 함수
   * 비동기/대기 함수
   * 메서드 정의
   * 클래스 메서드
   * 기본 매개 변수
   * 나머지 매개 변수

## 사용자 지정 함수를 만들기 위한 사전 요구 사항

적응형 Forms에 사용자 지정 기능을 추가하기 전에 다음을 확인하십시오.

**소프트웨어:**

* **IDE(일반 텍스트 편집기)**: 모든 일반 텍스트 편집기가 작동할 수 있지만, Microsoft Visual Studio Code와 같은 IDE(통합 개발 환경)에서는 쉽게 편집할 수 있는 고급 기능을 제공합니다.

* **Git:** 코드 변경 내용을 관리하려면 이 버전 제어 시스템이 필요합니다. 설치되지 않은 경우 https://git-scm.com에서 다운로드하십시오.


## 사용자 정의 함수 만들기 {#create-custom-function}

규칙 편집기에서 사용자 지정 함수를 호출할 클라이언트 라이브러리를 만듭니다. 자세한 내용은 [클라이언트측 라이브러리 사용](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html#developing)을 참조하십시오.

사용자 정의 함수를 만드는 단계는 다음과 같습니다.
1. [클라이언트 라이브러리 만들기](#create-client-library)
1. [적응형 양식에 클라이언트 라이브러리 추가](#use-custom-function)

### 클라이언트 라이브러리 만들기 {#create-client-library}

클라이언트 라이브러리를 추가하여 사용자 정의 함수를 추가할 수 있습니다. 클라이언트 라이브러리를 만들려면 다음 단계를 수행하십시오.

**리포지토리 복제**

[AEM Forms as a Cloud Service 리포지토리 복제](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=ko-KR#accessing-git):

1. 명령줄 또는 터미널 창을 엽니다.

1. 저장소를 저장할 시스템에서 원하는 위치로 이동합니다.

1. 다음 명령을 실행하여 저장소를 복제합니다.

   `git clone [Git Repository URL]`

이 명령은 저장소를 다운로드하고 시스템에 복제된 저장소의 로컬 폴더를 만듭니다. 이 안내서에서는 이 폴더를 [AEMaaCS 프로젝트 디렉터리](으)로 참조합니다.

**클라이언트 라이브러리 폴더 추가**

새 클라이언트 라이브러리 폴더를 [AEMaaCS 프로젝트 디렉터리]에 추가하려면 다음 단계를 수행합니다.

1. 편집기에서 [AEMaaCS 프로젝트 디렉터리]를 엽니다.

   ![사용자 지정 함수 폴더 구조](/help/forms/assets/custom-library-folder-structure.png)

1. `ui.apps` 찾기.
1. 새 폴더를 추가합니다. 예를 들어 `experience-league`(으)로 이름이 지정된 폴더를 추가합니다.
1. `/experience-league/` 폴더로 이동하여 `ClientLibraryFolder`을(를) 추가합니다. 예를 들어 이름이 `customclientlibs`인 클라이언트 라이브러리 폴더를 만듭니다.

   `Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/`

**클라이언트 라이브러리 폴더에 파일 및 폴더 추가**

추가된 클라이언트 라이브러리 폴더에 다음을 추가합니다.

* .content.xml 파일
* js.txt 파일
* js 폴더

`Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/experience-league/customclientlibs/`

1. `.content.xml`에서 다음 코드 행을 추가합니다.

   ```javascript
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="cq:ClientLibraryFolder"
   categories="[customfunctionscategory]"/>
   ```

   >[!NOTE]
   >
   > `client library folder` 및 `categories` 속성의 이름을 선택할 수 있습니다.

1. `js.txt`에서 다음 코드 행을 추가합니다.

   ```javascript
         #base=js
       function.js
   ```
1. `js` 폴더에서 사용자 지정 함수를 포함하는 `function.js`(으)로 Javascript 파일을 추가합니다.

   ```javascript
    /**
        * Calculates Age
        * @name calculateAge
        * @param {object} field
        * @return {string} 
    */
   
    function calculateAge(field) {
    var dob = new Date(field);
    var now = new Date();
   
    var age = now.getFullYear() - dob.getFullYear();
    var monthDiff = now.getMonth() - dob.getMonth();
   
    if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
    age--;
    }
   
    return age;
    }
   ```
1. 파일을 저장합니다.

![사용자 지정 함수 폴더 구조](/help/forms/assets/custom-function-added-files.png)

**filter.xml에 새 폴더 포함**:

1. [AEMaaCS 프로젝트 디렉터리]에서 `/ui.apps/src/main/content/META-INF/vault/filter.xml` 파일로 이동합니다.

1. 파일을 열고 끝에 다음 줄을 추가합니다.

   `<filter root="/apps/experience-league" />`
1. 파일을 저장합니다.

![사용자 지정 함수 필터 xml](/help/forms/assets/custom-function-filterxml.png)

**새로 만든 클라이언트 라이브러리 폴더를 AEM 환경에 배포합니다**

Cloud Service 환경에 AEM as a Cloud Service [AEMaaCS 프로젝트 디렉터리]를 배포합니다. Cloud Service 환경에 배포하려면 다음을 수행하십시오.

1. 변경 내용 커밋

   1. 아래 명령을 사용하여 저장소의 변경 내용을 추가하고, 커밋하고, 푸시합니다.

   ```javascript
       git add .
       git commit -a -m "Adding custom functions"
       git push
   ```

1. 업데이트된 코드를 배포합니다.

   1. 기존 전체 스택 파이프라인을 통해 코드 배포를 트리거합니다. 이렇게 하면 업데이트된 코드가 자동으로 빌드 및 배포됩니다.

아직 파이프라인을 설정하지 않았다면 [AEM Formsas a Cloud Service 에 대한 파이프라인 설정 방법](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=ko-KR#setup-pipeline)에 대한 안내서를 참조하십시오.

파이프라인이 실행되면 클라이언트 라이브러리에 추가된 사용자 지정 함수를 [적응형 양식 규칙 편집기](/help/forms/rule-editor-core-components.md)에서 사용할 수 있게 됩니다.

### 적응형 양식에 클라이언트 라이브러리 추가{#use-custom-function}

클라이언트 라이브러리를 Forms CS 환경에 배포한 후에는 적응형 양식에서 해당 기능을 사용하십시오. 적응형 양식에 클라이언트 라이브러리를 추가하려면

1. 편집 모드에서 양식을 엽니다. 편집 모드에서 양식을 열려면 양식을 선택하고 **[!UICONTROL 편집]**&#x200B;을 선택합니다.
1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. **[!UICONTROL 기본]** 탭을 열고 드롭다운 목록에서 **[!UICONTROL 클라이언트 라이브러리 범주]**&#x200B;의 이름을 선택합니다(이 경우 `customfunctionscategory` 선택).

   ![사용자 지정 함수 클라이언트 라이브러리를 추가](/help/forms/assets/clientlib-custom-function.png)

   >[!NOTE]
   >
   > **[!UICONTROL 클라이언트 라이브러리 범주]** 필드 내에서 쉼표로 구분된 목록을 지정하여 여러 범주를 추가할 수 있습니다.

1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

[JavaScript 주석](##js-annotations)을 사용하여 [적응형 양식의 규칙 편집기](/help/forms/rule-editor-core-components.md)에서 사용자 지정 함수를 사용할 수 있습니다.

## 적응형 양식에서 사용자 정의 함수 사용

적응형 양식에서는 [규칙 편집기 내에서 사용자 지정 함수](/help/forms/rule-editor-core-components.md)를 사용할 수 있습니다. JavaScript 파일(`Function.js` 파일)에 다음 코드를 추가하여 생년월일(YYYY-MM-DD)을 기준으로 연령을 계산합니다. 생년월일을 입력으로 취하여 연령을 반환하는 사용자 지정 함수를 `calculateAge()`(으)로 만듭니다.

```javascript
    /**
        * Calculates Age
        * @name calculateAge
        * @param {object} field
        * @return {string} 
    */

    function calculateAge(field) {
    var dob = new Date(field);
    var now = new Date();

    var age = now.getFullYear() - dob.getFullYear();
    var monthDiff = now.getMonth() - dob.getMonth();

    if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
    age--;
    }

    return age;
    }
```

위의 예에서 사용자가 생년월일을 형식(YYYY-MM-DD)으로 입력하면 사용자 지정 함수 `calculateAge`이(가) 호출되고 연령을 반환합니다.

![규칙 편집기에서 Agae 사용자 지정 함수 계산](/help/forms/assets/custom-function-calculate-age.png)

이제 양식을 미리 보기하여 사용자 정의 함수가 규칙 편집기를 통해 어떻게 구현되는지 살펴보겠습니다.

![규칙 편집기 양식 미리 보기에서 Agae 사용자 지정 함수 계산](/help/forms/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> 다음 [사용자 지정 함수](/help/forms/assets//customfunctions.zip) 폴더를 참조할 수 있습니다. [패키지 관리자](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager)를 사용하여 AEM 인스턴스에 이 폴더를 다운로드하여 설치하십시오.

## 사용자 정의 함수의 기능

AEM Forms의 사용자 지정 기능은 양식의 기능을 확장하고 개인화하는 강력한 솔루션을 제공합니다. 사용자 지정 함수를 사용하여 조직의 특정 요구 사항을 충족할 수 있습니다.

이러한 함수는 특정 필드 작업, 전역 필드 사용 및 비동기 작업, 캐싱 메커니즘 통합 등 다양한 기능을 지원합니다. 이러한 유연성으로 인해 양식이 복잡한 요구 사항에 맞게 조정되고 효율적이고 맞춤화된 사용자 경험을 제공할 수 있습니다. 이러한 고급 기능을 활용하면 양식 상호 작용을 강화하고 성능을 최적화하여 AEM 양식의 기능을 개선하고 반응성을 높일 수 있습니다.

사용자 정의 함수의 기능에 대해 자세히 살펴보겠습니다.

### 사용자 지정 함수에서의 비동기 지원 {#support-of-async-functions}

비동기 사용자 지정 함수는 규칙 편집기 목록에 표시되지 않습니다. 그러나 동기 함수 표현식을 사용하여 만든 사용자 지정 함수 내에서 비동기 함수를 호출할 수 있습니다.

![동기화 및 비동기 사용자 지정 함수](/help/forms/assets/workflow-for-sync-async-custom-fumction.png)

>[!NOTE]
>
> 사용자 지정 함수에서 비동기 함수를 호출하는 경우 비동기 함수를 사용하면 사용자 지정 함수 내에서 각 함수가 사용된 결과를 사용하여 여러 작업을 동시에 실행할 수 있다는 이점이 있습니다.

사용자 지정 함수를 사용하여 비동기 함수를 호출하는 방법은 아래 코드를 참조하십시오.

```javascript
    
    async function asyncFunction() {
    const response = await fetch('https://petstore.swagger.io/v2/store/inventory');
    const data = await response.json();
    return data;
    }

    /**
    * callAsyncFunction
    * @name callAsyncFunction callAsyncFunction
    */
    function callAsyncFunction() {
    asyncFunction()
        .then(responseData => {
        console.log('Response data:', responseData);
        })
        .catch(error => {
         console.error('Error:', error);
    });
}
```

위의 예에서 asyncFunction 함수는 `asynchronous function`입니다. `https://petstore.swagger.io/v2/store/inventory`에 `GET`을(를) 요청하여 비동기 작업을 수행합니다. `await`을(를) 사용하여 응답을 기다리고 `response.json()`을(를) 사용하여 응답 본문을 JSON으로 구문 분석한 다음 데이터를 반환합니다. `callAsyncFunction` 함수는 `asyncFunction` 함수를 호출하고 콘솔에 응답 데이터를 표시하는 동기 사용자 지정 함수입니다. `callAsyncFunction` 함수는 동기식이지만 비동기 asyncFunction 함수를 호출하고 그 결과를 `then` 및 `catch` 문으로 처리합니다.

작동 여부를 확인하려면 단추를 추가하고 단추 클릭 시 비동기 함수를 호출하는 단추에 대한 규칙을 만들어 보겠습니다.

![비동기 함수에 대한 규칙을 만드는 중](/help/forms/assets/rule-for-async-funct.png)

사용자가 `Fetch` 단추를 클릭하면 사용자 지정 함수 `callAsyncFunction`이(가) 호출되어 비동기 함수 `asyncFunction`이(가) 호출되는지 보여 주려면 아래 콘솔 창의 그림을 참조하십시오. Inspect 콘솔 창에서 버튼에 대한 응답을 봅니다. 클릭:

![콘솔 창](/help/forms/assets/async-custom-funct-console.png)


### 사용자 지정 함수에서 필드 및 전역 범위 개체 지원 {#support-field-and-global-objects}

필드 개체는 텍스트 필드, 확인란 등 양식 내의 개별 구성 요소 또는 요소를 나타냅니다. Globals 개체에는 사용자 지정 함수 내에서 양식을 수정하는 방법, 대상 필드 인스턴스 및 양식 인스턴스와 같은 읽기 전용 변수가 포함되어 있습니다.

>[!NOTE]
>
> `param {scope} globals`은(는) 마지막 매개 변수여야 하며 적응형 양식의 규칙 편집기에 표시되지 않습니다.

### 사용자 지정 함수에서 캐싱 지원

적응형 Forms은 규칙 편집기에서 사용자 지정 함수 목록을 검색하는 동안 응답 시간을 개선하기 위해 사용자 지정 함수에 대한 캐싱을 구현합니다. `Fetched following custom functions list from cache`(으)로 표시되는 메시지가 `error.log` 파일에 나타납니다.

캐시를 지원하는 ![사용자 지정 함수](/help/forms/assets/custom-function-cache-error.png)

사용자 지정 함수가 수정되면 캐싱이 무효화되고 구문 분석됩니다.

## 문제 해결

* 사용자 정의 함수에 대한 코드가 들어 있는 JavaScript 파일에 오류가 있는 경우 사용자 정의 함수가 적응형 양식의 규칙 편집기에 나열되지 않습니다. 사용자 지정 함수 목록을 확인하려면 `error.log` 파일로 이동하여 오류를 확인할 수 있습니다. 오류가 발생하면 사용자 지정 함수 목록이 비어 있습니다.

  ![오류 로그 파일](/help/forms/assets/custom-function-list-error-file.png)

  오류가 없는 경우 사용자 지정 함수를 가져와서 `error.log` 파일에 나타납니다. `Fetched following custom functions list`(으)로 표시되는 메시지가 `error.log` 파일에 있습니다.

  ![적절한 사용자 지정 함수를 가진 오류 로그 파일](/help/forms/assets/custom-function-list-fetched-in-error.png)

## 다음 단계

이제 핵심 구성 요소를 기반으로 하는 적응형 양식에 대한 다양한 [사용자 지정 함수의 예](/help/forms/custom-function-core-components-use-cases.md)를 살펴보겠습니다.

## 추가 참조

{{see-also-rule-editor}}