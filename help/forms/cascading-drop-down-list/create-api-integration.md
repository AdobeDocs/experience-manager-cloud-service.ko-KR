---
title: API 통합 만들기
description: 적응형 Forms 표현식을 사용하여 자동 유효성 검사, 계산을 추가하고 섹션의 가시성을 켜거나 끕니다.
feature: Adaptive Forms, Foundation Components
role: User
hide: true
hidefromtoc: true
source-git-commit: 53e476981874597bfb7f9293e67b2d135c72b318
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 3%

---


# API 통합 만들기

이 자습서에서는 2개의 API 통합이 만들어집니다

- GetAllCountries가 국가 목록을 반환합니다.
- GetChildren - geonameId로 표현되는 국가 또는 주의 바로 아래 하위 항목을 반환합니다.

## GetAllCountries - API 통합 구성

- API 통합 구성

   - 표시 이름: GetAllCountries는 →에서 이 API에 대한 레이블을 지정합니다.

   - API URL: `https://secure.geonames.org/countryInfoJSON` - 호출 중인 끝점입니다.

   - HTTP 메서드: GET - 간단한 GET 요청을 만드는 것입니다.

   - 콘텐츠 유형: JSON - 응답은 JSON 형식으로 표시됩니다.

- 옵션:

   - 암호화 필요 선택 해제 - HTTPS 이외의 암호화 계층은 없습니다.

   - 클라이언트에서 실행 확인 - 호출이 서버측이 아닌 클라이언트/브라우저에서 실행됩니다.
- 인증 유형
   - 없음 - GeoNames API는 헤더에 OAuth 또는 API 키가 필요하지 않으므로
- 입력:
   - 입력 섹션은 API로 전송되는 항목을 정의합니다
   - **사용자 이름** → 유형: 문자열, 쿼리에서 전송됨, 기본값: gbedekar.
   - 모든 요청은 ?username=gbedekar를 URL에 추가합니다.
- 출력
   - 출력은 추출하고 사용할 JSON 응답의 필드를 정의합니다.
GeoNames 응답은 다음과 같습니다.

  ![json-response](assets/geonames-data.png)
   - geonames 배열 내부에서 두 개의 필드를 매핑했습니다.

     geonames[*].geonameId →이 숫자로 표시됨

     geonames[*].countryName이(가) 문자열로 →.

     [*]은(는) 배열의 각 국가마다 반복됨을 의미합니다.



![모든 국가 가져오기](assets/api-integration.png)


## GetChildren

geoNamesId가 쿼리 매개 변수로 전달된 위치의 바로 아래 자식을 GeoNames에 묻습니다

- API 통합 구성

   - 표시 이름: GetAllCountries는 →에서 이 API에 대한 레이블을 지정합니다.

   - API URL: `https://secure.geonames.org/children`이(가) 호출 중인 끝점을 →.

   - HTTP 메서드: GET→ 간단한 GET 요청을 만드는 중입니다.

   - 콘텐츠 유형: JSON → 응답이 JSON 형식으로 필요합니다.

- 옵션:

   - 암호화 필요 선택 → HTTPS 이외의 암호화 레이어가 없습니다.

   - 호출이 서버측이 아닌 클라이언트/브라우저에서 실행될 → 클라이언트에서 실행 이 확인되었습니다.
- 인증 유형
   - 없음 - GeoNames API는 헤더에 OAuth 또는 API 키가 필요하지 않으므로
- 입력:
   - API로 전송되는 항목 정의
   - **사용자 이름** → 유형: 문자열, 쿼리에서 전송됨, 기본값: gbedekar.
   - 모든 요청은 ?username=gbedekar를 URL에 추가합니다.
   - **geonameId** -> 형식: 문자열. geonameId로 표현되는 국가/주의 하위 항목 반환
   - **type** =>문자열. json으로 설정하면 JSON 형식으로 응답이 반환됩니다.
- 출력
   - 추출 및 사용할 JSON 응답의 필드를 정의합니다.
GeoNames 응답은 다음과 같습니다.

  ![json-response](assets/child-elements-data.png)
   - geonames 배열 내부에서 두 개의 필드를 매핑했습니다.

     geonames[*].geonameId →이 숫자로 표시됨

     문자열 이름 [*].name→(으)로 변경됨

     [*]은(는) 배열의 각 국가마다 반복됨을 의미합니다.


![get-children](assets/get-children-api-integration.png)
