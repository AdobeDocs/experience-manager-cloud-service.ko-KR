---
title: 적응형 Forms에 대한 비동기 제출을 구성하는 방법
description: 적응형 Forms에 대한 비동기 제출을 구성하는 방법을 알아봅니다. 적응형 Forms에 대한 비동기 제출 작동 방식에 대해 자세히 알아보십시오.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 026f4920-f8f9-4b08-b1b0-af50229633d7
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# 적응형 Forms 비동기 제출 {#asynchronous-submission-of-adaptive-forms}

일반적으로 웹 양식은 동기식으로 제출되도록 구성됩니다. 동기 제출 시 사용자가 양식을 제출하면 수신 확인 페이지, 감사 인사 페이지 또는 제출 실패 시 오류 페이지로 리디렉션됩니다. 그러나 단일 페이지 애플리케이션과 같은 최신 웹 경험은 웹 페이지가 정적으로 유지되고 클라이언트-서버 상호 작용이 백그라운드에서 발생하는 상황에서 인기를 얻고 있습니다. 적응형 Forms에 이 경험을 제공하도록 비동기 제출을 구성할 수 있습니다.

비동기 제출 시 사용자가 양식을 제출하면 개발자가 다른 양식 또는 웹 사이트의 별도의 섹션으로 리디렉션하는 것과 같은 별도의 환경에서 양식을 플러그인으로 제출합니다. 작성자는 다른 데이터 저장소에 데이터를 보내거나 사용자 지정 분석 엔진을 추가하는 등 별도의 서비스를 플러그인으로 추가할 수도 있습니다. 비동기 제출의 경우 적응형 양식은 양식이 다시 로드되지 않거나 제출된 양식 데이터가 서버에서 확인될 때 해당 URL이 변경되지 않으므로 단일 페이지 애플리케이션처럼 동작합니다.

적응형 Forms의 비동기 제출에 대한 자세한 내용은 을 참조하십시오.

## 비동기 제출 구성 {#configure}

적응형 양식에 대한 비동기 제출을 구성하려면 다음을 수행하십시오.

1. 적응형 양식 작성 모드에서 양식 컨테이너 개체를 선택하고 ![cmppr1](assets/configure-icon.svg) 속성을 엽니다.
1. 에서 **[!UICONTROL 제출]** 속성 섹션, 활성화 **[!UICONTROL 비동기 제출 사용]**.
1. 에서 **[!UICONTROL 제출 시]** 섹션에서 다음 옵션 중 하나를 선택하여 양식 제출 시 수행할 수 있습니다.

   * **[!UICONTROL URL로 리디렉션]**: 양식을 제출할 때 지정된 URL 또는 페이지로 리디렉션합니다. URL을 지정하거나 다음 위치에서 페이지의 경로를 찾아볼 수 있습니다 **[!UICONTROL 리디렉션 URL/경로]** 필드.
   * **[!UICONTROL 메시지 표시]**: 양식 제출 시 메시지를 표시합니다. 아래 텍스트 필드에 메시지를 작성할 수 있습니다 **[!UICONTROL 메시지 표시]** 선택 사항입니다. 텍스트 필드는 리치 텍스트 서식을 지원합니다.

1. 탭 ![check-button1](assets/save_icon.svg) 속성을 저장합니다.

## 비동기 제출 작동 방식 {#how-asynchronous-submission-works}

[!DNL Experience Manager Forms] 에서는 양식 제출을 위한 기본 성공 및 오류 핸들러를 제공합니다. 핸들러는 서버 응답을 기반으로 실행되는 클라이언트측 함수입니다. 양식이 제출되면 데이터가 서버에 전송되어 유효성 검사를 위해 서버에 전송되며, 클라이언트에게 전송하기 위해 성공 또는 오류 이벤트에 대한 정보를 제공합니다. 이 정보는 함수를 실행하기 위해 관련 처리기에 매개 변수로 전달됩니다.

또한 양식 작성자와 개발자는 양식 수준에서 규칙을 작성하여 기본 핸들러를 재정의할 수 있습니다. 자세한 내용은 [규칙을 사용하여 기본 처리기 재정의](#custom).

먼저 성공 및 오류 이벤트에 대한 서버 응답을 검토할 수 있습니다.

### 제출 성공 이벤트에 대한 서버 응답 {#server-response-for-submission-success-event}

제출 성공 이벤트에 대한 서버 응답의 구조는 다음과 같습니다.

```json
{oneOf: [
{  properties : {
     contentType : {"type" : "string",  "enum" : ["xmlschema", "jsonschema"]},
    data : {type : "string", description : "Form data in XML or  JSON  format"},
   thankYouOption : {type : "string"}
   }},
  properties : {
     contentType : {"type" : "string",  "enum" : ["xmlschema", "jsonschema"]},
    data : {type : "string", description : "Form data in XML or  JSON  format"},
   thankYouContent: {type: "string"}
   }
]

}
```

양식 제출이 성공하면 서버 응답에는 다음이 포함됩니다.

* 양식 데이터 형식 유형: XML 또는 JSON
* XML 또는 JSON 형식의 양식 데이터
* 페이지로 리디렉션하거나 양식에 구성된 대로 메시지를 표시하는 선택 사항입니다
* 양식에 구성된 페이지 URL 또는 메시지 콘텐츠

성공 처리기는 서버 응답을 읽고 구성된 페이지 URL로 리디렉션하거나 메시지를 표시합니다.

### 제출 오류 이벤트에 대한 서버 응답 {#server-response-for-submission-error-event}

제출 오류 이벤트에 대한 서버 응답의 구조는 다음과 같습니다.

```json
{
   errorCausedBy : "<CAPTCHA_VALIDATION or SERVER_SIDE_VALIDATION>",

   errors : [
               { "somExpression" : "<SOM Expression>",
                 "errorMessage"  : "<Error Message>"
               },
               ...
             ]
 }
```

양식 제출 시 오류가 발생하는 경우 서버 응답에는 다음이 포함됩니다.

* 오류, 실패한 CAPTCHA 또는 서버측 유효성 검사 원인
* 유효성 검사에 실패한 필드의 SOM 표현식과 해당 오류 메시지가 포함된 오류 객체 목록

오류 처리기는 서버 응답을 읽고 이에 따라 양식에 오류 메시지를 표시합니다.

## 규칙을 사용하여 기본 처리기 재정의 {#custom}

양식 개발자와 작성자는 양식 수준에서 규칙을 작성하여 기본 핸들러를 재정의할 수 있습니다. 성공 및 오류 이벤트에 대한 서버 응답은 개발자가 다음을 사용하여 액세스할 수 있는 양식 수준에서 표시됩니다 `$event.data` 규칙 아래에 그룹화됩니다.

성공 및 오류 이벤트를 처리할 규칙을 작성하려면 다음 단계를 수행하십시오.

1. 작성 모드에서 적응형 양식을 열고 양식 개체를 선택한 다음 ![edit-rules1](assets/edit-rules-icon.svg) 규칙 편집기를 엽니다.
1. 선택 **[!UICONTROL 양식]** 양식 객체 트리에서 **[!UICONTROL 만들기]**.
1. 선택 **[!UICONTROL 이(가) 성공적으로 제출되었습니다.]** 또는 **[!UICONTROL 제출 실패]** 에서 **[!UICONTROL 상태 선택]** 드롭다운 목록.
1. 정의 **[!UICONTROL Then]** 선택한 상태에 대한 작업입니다. 예를 들어, **[!UICONTROL 다음으로 이동]** 그런 다음 URL을 입력하거나 붙여넣습니다. 또한 **[!UICONTROL 함수]** 탭으로 이동합니다.

   ![전송 처리기 성공](assets/form-submission-handler.png)

1. 탭 **[!UICONTROL 완료]** 규칙을 저장하려면 을 클릭합니다.
