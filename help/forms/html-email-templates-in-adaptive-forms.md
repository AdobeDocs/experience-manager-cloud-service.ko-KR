---
title: Formsas a Cloud Service 에서 적응형 Forms 템플릿 HTML
description: 적응형 양식과 함께 이메일 템플릿을 사용하는 방법을 알아봅니다.
feature: Adaptive Forms, Core Components
role: User, Developer
hide: true
hidefromtoc: true
source-git-commit: eb2c451019e1c9d6f48558154ee58598bd1f2e02
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 0%

---

# 적응형 Forms의 이메일 템플릿

적응형 Forms을 사용하면 HTML 및 일반 텍스트 이메일 템플릿을 사용할 수 있습니다. HTML 이메일 템플릿을 사용하면 양식 제출 시 풍부하고 개인화된 시각적으로 매력적인 이메일을 보낼 수 있습니다. 양식 데이터로 이러한 이메일을 사용자 정의하고 이미지 및 링크와 같은 다양한 이메일 태그를 사용하여 개선할 수 있습니다. 적응형 Forms을 사용하면 HTML 템플릿이 포함된 파일을 업로드하거나 일반 텍스트 편집기를 사용하여 이러한 템플릿을 만들 수 있습니다.

![HTML 전자 메일 템플릿](/help/forms/assets/html-email.png)

이 문서는 적응형 Forms에서 이메일 템플릿을 구성하고 사용하는 데 도움이 됩니다. 이를 통해 다음과 같은 작업을 수행할 수 있습니다.

* [적응형 양식에 대한 HTML 템플릿 구성](#configure-an-html-template-for-an-adaptive-form)
* [적응형 양식에 대한 일반 텍스트 이메일 템플릿 구성](#configure-a-plain-text-template-for-an-adaptive-form)
* [전자 메일 템플릿에서 양식 데이터 사용](#use-form-data-in-your-email-templates)


다음은 관련 단계에 대한 간략한 개요입니다.

1. 편집할 적응형 양식을 엽니다.
1. [전자 메일 보내기](/help/forms/configure-submit-action-send-email.md) 제출 액션을 구성합니다.
1. HTML 템플릿을 선택 또는 업로드하거나, 이메일 템플릿을 수동으로 입력합니다.
1. 이메일 구성을 테스트합니다.

## 적응형 양식에 대한 HTML 템플릿 구성

[**전자 메일 보내기** 제출 액션](/help/forms/configure-submit-action-send-email.md)을 사용하여 제출 시 전자 메일을 보내도록 적응형 양식을 설정할 수 있습니다. 이 작업은 HTML 템플릿을 구성하는 두 가지 방법을 제공합니다.

### 옵션 1: HTML 템플릿이 들어 있는 파일 선택

계속하기 전에 HTML 템플릿을 AEM Forms 환경에 업로드했는지 확인하십시오.

1. 편집할 적응형 양식을 엽니다.
1. **콘텐츠 브라우저**(으)로 이동하여 **안내서 컨테이너**&#x200B;를 선택하고 속성 아이콘을 탭합니다. 제목이 `Adaptive Form Container`인 대화 상자가 나타납니다.
1. **제출** 탭으로 이동하여 **전자 메일 보내기** 제출 액션을 선택하십시오.

   ![전자 메일 제출 액션 보내기](/help/forms/assets/send-email-action.png)

1. **외부 템플릿 사용** 옵션을 사용하도록 설정합니다.
1. **HTML 템플릿 사용** 옵션을 사용하도록 설정합니다.
1. 외부 템플릿 경로 옵션에 대한 폴더 아이콘을 클릭하고 HTML 템플릿을 찾아 선택합니다.
1. 구성을 저장하려면 **완료**&#x200B;를 클릭하세요.

이제 HTML 템플릿이 적응형 양식에 대해 구성되었습니다.

### 옵션 2: 수동으로 HTML 템플릿 입력 또는 붙여넣기

1. 편집할 적응형 양식을 엽니다.
1. **콘텐츠 브라우저**(으)로 이동하여 **안내서 컨테이너**&#x200B;를 선택하고 속성 아이콘을 탭합니다. 제목이 `Adaptive Form Container`인 대화 상자가 나타납니다.
1. **제출** 탭으로 이동하여 **전자 메일 보내기** 제출 액션을 선택하십시오.
1. **HTML 템플릿 사용** 옵션을 사용하도록 설정합니다.
1. 입력한 **전자 메일 서식 파일** 상자에 HTML 코드를 직접 입력하거나 붙여 넣으십시오.


## 적응형 양식에 대한 일반 텍스트 템플릿 구성

[**전자 메일 보내기** 제출 액션](/help/forms/configure-submit-action-send-email.md)을 사용하여 제출 시 전자 메일을 보내도록 적응형 양식을 설정할 수 있습니다. 이 작업은 일반 텍스트 템플릿을 구성하는 두 가지 방법을 제공합니다.

### 옵션 1: 템플릿이 포함된 파일 선택

계속하기 전에 HTML 템플릿을 AEM Forms 환경에 업로드했는지 확인하십시오.

1. 편집할 적응형 양식을 엽니다.
1. **콘텐츠 브라우저**(으)로 이동하여 **안내서 컨테이너**&#x200B;를 선택하고 속성 아이콘을 탭합니다. 제목이 `Adaptive Form Container`인 대화 상자가 나타납니다.
1. **제출** 탭으로 이동하여 **전자 메일 보내기** 제출 액션을 선택하십시오.
1. **외부 템플릿 사용** 옵션을 사용하도록 설정합니다.
1. **외부 템플릿 경로** 옵션에 대한 폴더 아이콘을 클릭하고 일반 텍스트 템플릿을 찾아 선택합니다.
1. 완료 를 클릭하여 구성을 저장합니다.

이제 적응형 양식에 맞게 템플릿이 구성되었습니다.

### 옵션 2: 수동으로 HTML 템플릿 입력 또는 붙여넣기

1. 편집할 적응형 양식을 엽니다.
1. **콘텐츠 브라우저**(으)로 이동하여 **안내서 컨테이너**&#x200B;를 선택하고 속성 아이콘을 탭합니다. 제목이 `Adaptive Form Container`인 대화 상자가 나타납니다.
1. **제출** 탭으로 이동하여 **전자 메일 보내기** 제출 액션을 선택하십시오.
1. 제공된 **전자 메일 서식 파일** 상자에 일반 텍스트 서식 파일 코드를 직접 입력하거나 붙여 넣으십시오.

## 전자 메일 템플릿에서 양식 데이터 사용

자리 표시자를 사용하여 전자 메일 템플릿에 양식 데이터를 포함할 수 있습니다. 이러한 자리 표시자는 이메일을 보낼 때 동적으로 실제 양식 필드 값으로 대체됩니다. 예:

* ${name}: 이름이 &quot;name&quot;인 필드의 값.
* ${email}: 이름이 &quot;email&quot;인 필드의 값.
* ${message}: 이름이 &quot;message&quot;인 필드의 값

### 샘플 HTML 이메일 템플릿

다음은 양식 데이터 자리 표시자를 사용하는 HTML 이메일 템플릿의 예입니다.

```HTML
    <!DOCTYPE html>
    <html>
    <head>
        <title>Form Submission</title>
        <style>
            body {
                font-family: Arial, sans-serif;
                line-height: 1.6;
                color: #333;
            }
            h2 {
                color: #0056b3;
            }
        </style>
    </head>
    <body>
        <h2>Thank You for Your Submission</h2>
        <p>Dear ${name},</p>
        <p>We have received your submission with the following details:</p>
        <ul>
            <li><strong>Email:</strong> ${email}</li>
            <li><strong>Phone Number:</strong> ${phone_number}</li>
            <li><strong>Message:</strong> ${message}</li>
        </ul>
        <p>We will get back to you soon!</p>
        <p>Best regards,</p>
        <p>Your Team</p>
    </body>
    </html>
```

### 샘플 일반 텍스트 이메일 템플릿

다음은 일반 텍스트 이메일 템플릿의 예입니다.

```TXT
    
    Subject: Thank You for Your Submission
    
    Dear ${name},
    
    We have received your submission with the following details:
    
    - Email: ${email}
    - Phone Number: ${phone_number}
    - Message: ${message}
    
    We will get back to you soon!
    
    Best regards,
    Your Team
```

## 이메일 템플릿 HTML 우수 사례

* 이메일 클라이언트와의 호환성을 위해 스타일이 인라인인지 확인하십시오.
* 모바일 디바이스에서 더 나은 경험을 위해 템플릿을 반응형으로 만듭니다.
* Litmus 또는 Email on Acid와 같은 도구를 사용하여 다양한 이메일 클라이언트에서 이메일을 미리 볼 수 있습니다.
* 자리 표시자 이름이 양식 필드 이름과 정확히 일치하는지 확인합니다.
* HTML 템플릿에서 누락되었거나 잘못된 태그가 있는지 확인하십시오.
* [전자 메일 보내기](/help/forms/configure-submit-action-send-email.md) 제출 액션이 올바르게 구성되어 있는지 확인하십시오.
