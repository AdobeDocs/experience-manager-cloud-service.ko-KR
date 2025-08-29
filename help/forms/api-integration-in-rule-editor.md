---
title: Forms용 규칙 편집기에 API 통합
description: 양식 데이터 모델을 사용하지 않고 핵심 구성 요소를 기반으로 적응형 Forms을 위한 API를 통합하는 방법을 포함하여 규칙 편집기에서 서비스 호출에 대한 최신 개선 사항에 대해 알아봅니다.
feature: Adaptive Forms, Core Components, Edge Delivery Services
role: User, Developer
level: Beginner, Intermediate
keywords: 규칙 편집기에서 API 통합, 서비스 개선 사항 호출
exl-id: fc51f86d-e672-4513-b473-6700757a0c3d
source-git-commit: 80dde7ddaa08d752391b4004d7c93e5baac9716e
workflow-type: tm+mt
source-wordcount: '1021'
ht-degree: 0%

---

# 규칙 편집기에서 API 통합

<span>규칙 편집기에서 API 통합이 얼리어답터 프로그램 중입니다. 공식 전자 메일 ID로 `aem-forms-ea@adobe.com`에 작성하여 얼리어답터 프로그램에 참여하고 기능에 대한 액세스를 요청할 수 있습니다.</span>

적응형 Forms의 시각적 규칙 편집기는 양식 데이터 모델을 만들지 않고 직접 API 통합을 지원합니다. API URL(JSON 형식)을 입력하거나 cURL 명령을 통해 구성을 가져와서 API 끝점에 연결할 수 있습니다. 통합되면 **서비스 호출** 액션을 사용하여 API를 호출할 수 있습니다.

양식 필드를 API 구성에 정의된 입력 매개 변수에 직접 매핑할 수 있습니다. 마찬가지로 해당 API 응답에 대한 **이벤트 페이로드** 옵션을 사용하여 출력 매개 변수를 양식 필드에 매핑할 수 있습니다.

또한 서비스를 호출할 때 시각적 규칙 편집기를 사용하여 **성공** 및 **실패 처리기**&#x200B;를 정의할 수 있습니다. 성공 처리기는 성공적인 API 호출 후 실행할 작업을 지정하는 반면, 실패 처리기는 오류가 발생할 때 양식이 응답하는 방식을 정의합니다.

>[!NOTE]
>
> 규칙 편집기의 API 통합은 범용 편집기에서 작성된 [Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)에도 적용됩니다.

## 비교: API 통합 메서드

| 측면 | 양식 데이터 모델(FDM)과 API 통합 | 직접 API 통합(*API 통합 만들기*&#x200B;를 통해) |
|--------------------------------|---------------------------------------------------------------------|-----------------------------------------------------------|
| **용도** | 여러 양식에서 중앙 집중식 재사용 가능한 API 통합 | 빠른 양식 전용 API 통합 |
| **설치 위치** | 양식 데이터 모델 편집기(AEM 콘솔)에서 작성 및 편집됨 | 적응형 양식 규칙 편집기에서 직접 만들고 편집함 |
| **복잡성** | 높은 설정 노력(매핑 및 구성 필요) | 단순하고 가벼운 성능 |
| **가장 적합한 대상** | 여러 양식을 사용하는 엔터프라이즈 또는 대규모 사용 사례 | 작은 양식, 프로토타입 또는 일회용 API 호출 |

## API 통합 구성

아래 스크린샷에는 API 통합 구성 창이 표시됩니다.

![API 통합 구성](/help/forms/assets/api-integration-configuration.png)

### 주요 구성 옵션

**API 통합 구성**

* **cURL에서 가져오기**: API URL, HTTP 메서드, 헤더 및 매개 변수와 같은 세부 정보를 수동으로 입력하는 대신 준비된 cURL 명령을 붙여넣어 API 통합을 구성합니다.
* **표시 이름**: API 서비스의 사용자 지정 이름입니다.
* **API URL**: API 서비스의 끝점입니다.
* **HTTP 메서드 선택**: API 호출에 사용되는 HTTP 요청 메서드입니다.
* **콘텐츠 형식**: 요청 및 응답 형식을 정의합니다.
* **암호화 필요**: (선택 사항) 전송 중에 중요한 데이터를 암호화합니다.
* **클라이언트에서 실행**: 활성화되면 서버 대신 클라이언트(브라우저)에서 API 호출이 수행됩니다.

**인증 유형**

* **옵션**: 없음, 기본, API 키, OAuth 2.0.

**입력 매개 변수**

* **입력에 대한 JSON 업로드**: 샘플 JSON 파일을 업로드하여 입력 매핑을 자동으로 채웁니다.
   * **이름**: API에 필요한 입력 매개 변수 이름입니다.
   * **Type**: 입력의 데이터 형식(문자열, 숫자, 부울 등)입니다.
   * **In**: 매개 변수의 위치(쿼리, 헤더 또는 본문)입니다.
   * **기본값**: 사용자가 제공하지 않는 경우 미리 채워진 값입니다.
   * **추가**: 추가 입력 매개 변수를 추가하는 옵션입니다.

**출력 매개 변수**

* **출력에 대한 JSON 업로드**: 자동 생성 매핑에 대한 샘플 API 응답을 업로드합니다.
   * **이름**: API 응답의 출력 매개 변수 이름입니다.
   * **Type**: 출력 매개 변수의 데이터 형식(문자열, 숫자 등)이 필요합니다.
   * **In**: 매핑된 값이 필요한 위치를 정의합니다.
   * **추가/삭제**: 새 매핑을 추가하거나 기존 매핑을 제거합니다.

## 사용 사례: 비자 신청 양식에서 국가 필드 채우기

>[!VIDEO](https://video.tv.adobe.com/v/3471606/rule-editor-api-integration/?quality=12&learn=on)

**시나리오**: 정부 기관에서 다음 필드가 포함된 온라인 비자 신청 양식을 제공합니다.

1. 전체 이름(텍스트)
2. 생년월일(날짜)
3. 시민권 국가(드롭다운)
4. 여권 번호(텍스트)
5. 여권 발급 국가(드롭다운)
6. 대상 국가(드롭다운)
7. 도착 예정일(일자)

이 양식은 정적 국가 목록을 유지하는 대신 **getcountryname API**&#x200B;를 사용하여 국가 정보(대륙, 자본, ISO Alpha 코드 등)를 동적으로 가져옵니다.

`https://secure.geonames.org/countryInfoJSON?username=aemforms`

이렇게 하면 지원자들이 양식을 작성하는 동안 항상 최신의 정확한 국가 목록을 볼 수 있습니다.

### 규칙 편집기에서 API 통합을 사용한 구현

규칙 편집기에서 **API 통합 만들기** 단추를 클릭하여 양식 데이터 모델을 만들지 않고 API를 통합할 수 있습니다.

![API 통합 만들기](/help/forms/assets/create-api-integration.png)

규칙 편집기의 **API 통합 구성**&#x200B;에 이름이 **getcountryname**&#x200B;인 API 서비스가 구성되어 있습니다.

![API 나머지 끝점 구성](/help/forms/assets/api-restendpoint.png)

* **API 끝점 URL** → `https://secure.geonames.org/countryInfoJSON?username=aemforms`
* GET→ **HTTP 메서드**
* **콘텐츠 형식** → JSON
* **입력** → `username`이(가) 쿼리 매개 변수(`aemforms`)(으)로 전달되었습니다.
* **,**, `continent`, `capital` 및 `countrynames`과(와) 같은 `isoAlpha3`출력`languages` → 응답 필드가 양식 필드에 매핑됩니다.

**비자 신청서 양식**&#x200B;에서 **시민권 국가**, **여권 발급 국가** 및 **대상 국가**&#x200B;의 세 드롭다운 필드는 **서비스 호출** 작업에 바인딩되어 있습니다.

양식이 로드되면 **서비스 호출**&#x200B;에서 API의 국가 목록을 가져옵니다. 그런 다음 응답이 매핑되어 드롭다운 옵션이 자동으로 채워집니다.

예를 들어 사용자가 **Country of Citizenship**&#x200B;을 열면 API 응답에서 국가 목록이 동적으로 표시됩니다.

![invoke-service-api-integration](/help/forms/assets/invoke-service-api-integration.png)

![API 통합 출력](/help/forms/assets/api-integration-output.png)

마찬가지로 **Country of Passport Issuance** 및 **Destination Country**&#x200B;에서 동일한 API 호출을 사용하여 세 필드 모두에서 일관되고 최신 데이터를 유지합니다.

## API 실패에 대한 재시도 메커니즘 구현

API 요청이 실패하면 사용자에게 오류를 보고하기 전에 요청을 다시 시도하는 것이 유용한 경우가 많습니다. **function.js** 파일에 사용자 지정 코드를 작성하여 폴링 및 다시 시도 메커니즘을 구현할 수 있습니다.

다음 예에서는 최대 2번의 재시도 및 재시도 간 지수 백오프를 통해 API 실패를 처리하는 방법을 보여 줍니다.

```javascript
/**
 * Handles request retries with up to 2 retry attempts
 * @param {function} requestFn - The request function to execute
 * @return {Promise} A promise that resolves with the response or rejects after all retries
 */
function retryHandler(requestFn) {
    const MAX_RETRIES = 2;
    
    /**
     * Attempts the request with retry metadata
     * @param {number} retryCount - Current retry attempt count
     * @return {Promise} The request promise
     */
    function attemptRequest(retryCount = 0) {
        // Include retry metadata if this is a retry
        const requestOptions = retryCount > 0 ? {
            headers: {
                'X-Retry': 'true',
                'X-Retry-Count': retryCount.toString(),
                'X-Retry-Time': new Date().toISOString()
            },
            body: {
                retry: true,
                retryCount: retryCount,
                timestamp: Date.now()
            }
        } : undefined;

        return requestFn(requestOptions)
            .then(function(response) {
                if (response && response.status >= 400) {
                    console.warn('Request failed with status ' + response.status);
                    throw new Error('Request failed with status ' + response.status);
                }
                return response;
            })
            .catch(function(error) {
                console.warn('Request attempt ' + (retryCount + 1) + ' failed:', error.message);
                
                // Retry if max attempts not reached
                if (retryCount < MAX_RETRIES) {
                    console.log('Retrying request, attempt ' + (retryCount + 2) + ' of ' + (MAX_RETRIES + 1));
                    
                    // Exponential backoff delay: 1s, 2s, 4s...
                    const delay = Math.pow(2, retryCount) * 1000;
                    
                    return new Promise(function(resolve) {
                        setTimeout(resolve, delay);
                    }).then(function() {
                        return attemptRequest(retryCount + 1);
                    });
                } else {
                    // All retries exhausted
                    console.error('All retry attempts failed. Final error:', error.message);
                    throw new Error('Request failed after ' + (MAX_RETRIES + 1) + ' attempts: ' + error.message);
                }
            });
    }
    
    // Start the first attempt
    return attemptRequest(0);
}
```

위의 코드에서 **retryHandler** 함수는 오류가 발생한 경우 자동으로 다시 시도하여 API 요청을 관리합니다. 이 메서드는 요청 함수(requestFn)를 사용하여 최대 2회까지 요청을 시도하고 다시 시도할 때마다 메타데이터를 추가합니다.

>[!NOTE]
>
> 사용자 지정 기능을 추가하는 방법에 대한 자세한 단계는 [핵심 구성 요소를 기반으로 하는 적응형 Forms을 위한 사용자 지정 기능 소개](/help/forms/create-and-use-custom-functions.md) 문서를 참조하십시오.

## 자주 묻는 질문

* **적응형 Forms에서 API를 통합하려면 양식 데이터 모델을 만들어야 합니까?**\
  아니요. 시각적 규칙 편집기를 사용하면 양식 데이터 모델을 만들지 않고도 **API 통합 만들기** 옵션을 사용하여 API를 직접 통합할 수 있습니다. 이 접근 방식은 경량 또는 양식별 사용 사례에 가장 적합합니다.

* **규칙 편집기에서 API 호출을 보호할 수 있습니까?**\
  예. API 통합 구성은 **기본, API 키 및 OAuth 2.0**&#x200B;과 같은 인증 옵션을 제공합니다. 중요한 데이터가 안전하게 전송되도록 **암호화 필요**&#x200B;를 사용하도록 설정할 수도 있습니다.
