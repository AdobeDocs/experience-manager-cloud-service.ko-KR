---
title: AEM 적응형 양식에서 hCaptcha&reg;를 사용하는 방법
description: hCaptcha&reg; 서비스를 통해 손쉽게 양식 보안을 강화할 수 있습니다. 단계별 안내서가 포함되어 있습니다.
topic-tags: Adaptive Forms, author
keywords: Captcha&reg; 서비스, 적응형 Forms, CAPTCHA 과제, 보트 방지, 양식 제출 보안, 양식 스팸 방지
feature: Adaptive Forms, Foundation Components
role: User, Developer
exl-id: dc7ca723-1008-472a-b6eb-8e9ed6332a16
source-git-commit: 914139a6340f15ee77024793bf42fa30c913931e
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 19%

---

# AEM Forms 환경을 hCaptcha®와 연결합니다. {#connect-your-forms-environment-with-hcaptcha-service}

<span class="preview"> 이 기능은 얼리 어답터 프로그램 중입니다. 공식 이메일 ID를 사용하여 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램에 참여하고 기능에 대한 액세스 권한을 요청할 수 있습니다. </span>

CAPTCHA(컴퓨터와 인간을 구분하기 위해 완전히 자동화된 공공 튜링 테스트)는 인간과 자동화된 프로그램 또는 봇을 구별하기 위해 온라인 거래에서 일반적으로 사용되는 프로그램입니다. 문제를 제기하고 사용자 응답을 평가하여 사이트와 상호 작용하는 것이 인간인지 봇인지 판단합니다. 테스트가 실패할 경우 사용자가 진행하지 못하도록 차단하고 봇이 스팸을 게시하거나 악의적인 목적으로 상호 작용하는 것을 방지하여 온라인 거래를 안전하게 할 수 있도록 도와줍니다.

AEM Forms as a Cloud Service은 다음 CAPTCHA 솔루션을 지원합니다.

* [hCaptcha](#integrate-aem-forms-environment-with-hcaptcha-captcha)
* [Cloudflare 턴스타일](/help/forms/integrate-adaptive-forms-turnstile.md)
* [Google recaptcha](/help/forms/captcha-adaptive-forms.md)

## AEM Forms 환경과 hCaptcha Captcha 통합

hCaptcha® 서비스는 봇, 스팸 및 자동화된 남용으로부터 양식을 보호합니다. 확인란 위젯 챌린지를 제기하고 사용자의 답변을 평가하여 양식과 상호 작용하는 것이 인간인지 또는 봇인지 판단합니다. 테스트가 실패할 경우 사용자가 진행하지 못하도록 차단하고 봇이 스팸을 게시하거나 악의적인 활동으로 상호 작용하는 것을 방지하여 온라인 거래를 안전하게 할 수 있도록 도와줍니다.

AEM Forms as a Cloud Service은 적응형 Forms에서 hCaptcha®를 지원합니다. 양식 제출 시 확인란 위젯 문제를 제시하는 데 사용할 수 있습니다.

<!-- ![hCaptcha&reg;](assets/hCaptcha&reg;-challenge.png)-->

## AEM Forms 환경을 hCaptcha®와 통합하기 위한 사전 요구 사항 {#prerequisite}

AEM Forms으로 hCaptcha®를 구성하려면 hCaptcha® 웹 사이트에서 [hCaptcha® 사이트 키 및 비밀 키](https://docs.hcaptcha.com/switch/#get-your-hcaptcha-sitekey-and-secret-key)를 가져와야 합니다.

## hCaptcha를 구성하는 ® {#steps-to-configure-hcaptcha}

1. AEM Forms as a Cloud Service 환경에서 구성 컨테이너를 만듭니다. 구성 컨테이너에는 AEM을 외부 서비스에 연결하는 데 사용되는 클라우드 구성이 포함됩니다. AEM Forms 환경을 hCaptcha®와 연결하도록 구성 컨테이너를 만들고 구성하려면 다음을 수행하십시오.
   1. AEM Forms as a Cloud Service 인스턴스를 엽니다.
   1. **[!UICONTROL 도구 > 일반 > 구성 브라우저]**&#x200B;로 이동합니다.
   1. 구성 브라우저에서 기존 폴더를 선택하거나 폴더를 만들 수 있습니다. 폴더를 만들고 이 폴더에 대해 클라우드 구성 옵션을 활성화하거나 기존 폴더에 대해 클라우드 구성 옵션을 활성화할 수 있습니다.

      * **폴더를 만들고 폴더 클라우드 구성 옵션을 활성화하려면**:
         1. 구성 브라우저에서 **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
         1. 구성 만들기 대화 상자에서 이름, 제목을 지정하고 **[!UICONTROL 클라우드 구성]** 옵션을 선택합니다.
         1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
      * 기존 폴더에 대해 클라우드 구성 옵션을 활성화하려면 다음을 수행하십시오.
         1. 구성 브라우저에서 폴더를 선택하고 **[!UICONTROL 속성]**&#x200B;을 선택합니다.
         1. 구성 속성 대화 상자에서 **[!UICONTROL 클라우드 구성]**&#x200B;을 사용하도록 설정합니다.
         1. 구성을 저장하고 대화 상자를 종료하려면 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택하십시오.

1. Cloud Service 구성:
   1. AEM 작성자 인스턴스에서 ![도구-1](assets/tools-1.png) > **[!UICONTROL 클라우드 서비스]**(으)로 이동한 다음 **[!UICONTROL hCaptcha®]**&#x200B;을(를) 선택합니다.

      ui의 ![hCaptcha®](assets/hcaptcha-in-ui.png)
   1. 이전 섹션에서 설명한 대로 작성되거나 업데이트된 구성 컨테이너를 선택합니다. **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

      ![구성 hCaptcha®](assets/config-hcaptcha.png)
   1. [필수 구성 요소에서 구한](#prerequisite)hCaptcha® 서비스 **[!UICONTROL Title]**, **[!UICONTROL Name]**, **[!UICONTROL 사이트 키]** 및 **[!UICONTROL 비밀 키]**&#x200B;를 지정하십시오. **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

      ![AEM Forms 환경을 hCaptcha®와 연결하도록 Cloud Service 구성](assets/create-hcaptcha-config.png)

>[!NOTE]
> [클라이언트측 JavaScript 유효성 검사 URL](https://docs.hcaptcha.com/#add-the-hcaptcha-widget-to-your-webpage) 및 [서버측 유효성 검사 URL](https://docs.hcaptcha.com/#verify-the-user-response-server-side)은(는) hCaptcha® 유효성 검사를 위해 이미 미리 채워져 있으므로 사용자가 수정할 필요가 없습니다. 일부 국가의 경우 끝점이 다를 수 있습니다. 자세한 내용은 [hCaptcha® FAQ](https://docs.hcaptcha.com/faq#does-hcaptcha-support-access-by-users-in-china)를 참조하십시오.

hCAPTCHA 서비스가 구성되면 적응형 양식에서 사용할 수 있습니다.

## 적응형 양식에서 hCaptcha® 사용{#using-hCaptcha®-foundation-components}

1. AEM Forms as a Cloud Service 인스턴스를 엽니다.
1. **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**&#x200B;로 이동합니다.
1. 적응형 양식을 선택하고 **[!UICONTROL 속성]**&#x200B;을 선택합니다. **[!UICONTROL 구성 컨테이너]** 옵션의 경우 AEM Forms과 hCaptcha®를 연결하는 클라우드 구성이 포함된 구성 컨테이너를 선택하고 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택합니다.

   이러한 구성 컨테이너가 없는 경우 [AEM Forms 환경을 hCaptcha®와 연결](#connect-your-forms-environment-with-hcaptcha-service) 섹션을 참조하여 구성 컨테이너를 만드는 방법을 알아보십시오.

   ![구성 컨테이너 선택](/help/forms/assets/captcha-properties.png)

1. 적응형 양식을 선택하고 **[!UICONTROL 편집]**&#x200B;을 선택합니다. 적응형 양식이 적응형 Forms 편집기에서 열립니다.
1. 구성 요소 브라우저에서 **[!UICONTROL Captcha]** 구성 요소를 적응형 양식으로 드래그 앤 드롭합니다.
1. **[!UICONTROL Captcha]** 구성 요소를 선택하고 속성 ![속성 아이콘](assets/configure-icon.svg) 아이콘을 클릭합니다. 속성 대화 상자가 열립니다.

   ![대체 텍스트](assets/hcaptcha-properties.png)

   다음 속성을 지정합니다.

   * **[!UICONTROL 제목]:** Captcha 구성 요소의 제목을 지정하면 양식과 규칙 편집기에서 고유한 이름으로 양식 구성 요소를 쉽게 식별할 수 있습니다.
   * **[!UICONTROL 유효성 검사 메시지]:** 양식 제출 시 Captcha 유효성 검사에 대한 유효성 검사 메시지를 제공합니다.
   * **[!UICONTROL Captcha 유효성 검사]:** 옵션 중 하나를 선택하여 Captcha의 유효성을 검사할 수 있습니다.
      * 양식 제출 시
      * 사용자 작업
   * **[!UICONTROL Captcha 서비스]:** Captcha 서비스를 선택하십시오. 여기서 hCaptcha® 서비스를 선택하십시오.
   * **[!UICONTROL Captcha 구성]:** hCaptcha®에 대해 구성된 클라우드 구성을 선택하십시오.

     >[!NOTE]
     >
     > 유사한 목적으로 환경에 여러 클라우드 구성을 가질 수 있습니다. 그러므로, 서비스를 신중하게 선택하십시오. 서비스가 목록에 없으면 [AEM Forms 환경과 hCaptcha® 연결](#connect-your-forms-environment-with-hcaptcha-service)을 참조하여 AEM Forms 환경과 hCaptcha® 서비스를 연결하는 Cloud Service을 만드는 방법에 대해 알아보십시오.

   * **오류 메시지:** Captcha 제출이 실패할 때 사용자에게 표시할 오류 메시지를 제공합니다.
   * **Captcha 크기:** hCaptcha® 챌린지 대화 상자의 표시 크기를 선택합니다. 작은 크기의 확인란을 표시하려면 **[!UICONTROL 작게]** 옵션을 사용하고, 비교적 큰 크기의 hCaptcha® 과제 대화 상자를 표시하려면 **[!UICONTROL 보통]** 옵션을 사용하거나, 사용자 인터페이스에서 확인란 위젯을 명시적으로 렌더링하지 않고 hCaptcha®의 유효성을 검사하려면 **[!UICONTROL 보이지 않음]**&#x200B;을 사용하십시오.

1. **[!UICONTROL 완료]**&#x200B;를 선택합니다.

이제 양식 제출에 대해 hCaptcha® 서비스가 제기한 문제를 양식 작성기가 성공적으로 해결한 적법한 양식만 허용됩니다.

**hCaptcha®는 Intuition Machines, Inc.의 등록 상표입니다.**

## 자주 묻는 질문

* **Q: 적응형 양식에서 두 개 이상의 Captcha 구성 요소를 사용할 수 있습니까?**
* **Ans:** 적응형 양식에서 둘 이상의 Captcha 구성 요소를 사용할 수 없습니다. 또한, 지연 로드로 표시된 조각 또는 패널에서는 Captcha 구성 요소를 사용하지 않는 것이 좋습니다.

## 추가 참조 {#see-also}

{{see-also}}
