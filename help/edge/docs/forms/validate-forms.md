---
title: 스프레드시트에서 Forms으로 - 적응형 양식 블록 필드 유효성 검사 마스터하기
description: 스프레드시트 및 적응형 양식 블록 필드를 사용하여 강력한 양식을 더 빨리 만드십시오! 이 안내서는 EDS 양식 블록 필드에 대한 사용자 정의 유효성 검사를 구축하는 데 도움이 됩니다.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: fd2e5df72e965ea6f9ad09b37983f815954f915c
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 17%

---


# 양식 필드에 유효성 검사 추가

적응형 양식 블록에는 유효성 검사 기능이 내장되어 있습니다. 이러한 유효성 검사는 선택한 필드 유형 및 제공하는 추가 속성에 따라 최신 브라우저에서 자동으로 적용됩니다.

## 필드 유형 및 유효성 검사 이해

적응형 양식 블록은 다양한 기능을 지원합니다 [HTML-5 입력 유형](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types)텍스트, 이메일, 번호, 날짜 등을 포함합니다. 또한 다음과 같은 기능이 있습니다. [텍스트 영역](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea), select 및 필드 세트와 함께 HTML-5에 고유한 포괄적인 입력 유효성 검사 기능이 제공됩니다.

HTML 필드 유형을 사용하여 사용자가 입력할 수 있는 데이터 유형을 정의합니다. 필드 유형마다 내장된 유효성 검사 규칙이 다릅니다.

이메일: 이 필드 유형은 일반 이메일 주소 형식에 대해 사용자 입력을 자동으로 확인합니다. 잘못된 이메일을 입력하면 오류 메시지가 표시됩니다.
숫자: 이 필드 유형은 숫자 입력만 허용합니다. 숫자가 아닌 문자를 입력하면 오류가 표시됩니다.
일자: 이 필드 유형은 표준 일자 형식에 대해 사용자 입력을 검증합니다. 적절한 범위를 벗어난 날짜는 유효하지 않은 것으로 표시될 수도 있습니다.
URL: 이 필드 유형은 유효한 URL 형식에 대해 사용자 입력의 유효성을 검사합니다. 잘못된 URL을 입력하면 오류 메시지가 표시됩니다.
전화: 이 필드 유형은 전화 번호용으로 특별히 설계되었으며 특정 국가 형식을 기반으로 유효성 검사를 트리거할 수 있습니다(보편적으로 지원되지 않음).


## 더 보기

* [양식 만들기 및 미리 보기](/help/edge/docs/forms/create-forms.md)
* [양식을 활성화하여 데이터 전송](/help/edge/docs/forms/submit-forms.md)
* [사이트 페이지에 양식 게시](/help/edge/docs/forms/publish-forms.md)
* [양식 필드에 유효성 검사 추가](/help/edge/docs/forms/validate-forms.md)
* [양식의 테마 및 스타일 변경](/help/edge/docs/forms/style-theme-forms.md)