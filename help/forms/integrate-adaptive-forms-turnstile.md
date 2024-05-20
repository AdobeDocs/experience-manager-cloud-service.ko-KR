---
title: AEM 적응형 양식에서 Turnstile을 사용하는 방법
description: 턴스타일 서비스를 통해 손쉽게 양식 보안을 강화할 수 있습니다. 내부의 단계별 가이드!
topic-tags: Adaptive Forms, author
feature: Adaptive Forms, Foundation Components
hide: true
hidefromtoc: true
source-git-commit: 54914728ee892f14ab8d669051504a52942a6c01
workflow-type: tm+mt
source-wordcount: '856'
ht-degree: 2%

---

# AEM Forms 환경과 턴스타일 연결 {#connect-your-forms-environment-with-turnstile-service}

<span class="preview"> 이 기능은 얼리어답터 프로그램(Early Adopter Program)에 있습니다. 공식 이메일 ID에서 aem-forms-ea@adobe.com에 작성하여 얼리어답터 프로그램에 참여하고 기능에 대한 액세스를 요청할 수 있습니다. </span>


Cloudflare의 Turnstile Captcha는 자동화된 봇, 악의적인 공격, 스팸 및 원치 않는 자동화된 트래픽으로부터 양식 및 사이트를 보호하는 것을 목표로 하는 보안 조치입니다. 양식 제출을 허용하기 전에 양식 제출에 대한 확인란을 표시하여 사람인지 확인합니다. AEM Forms은 적응형 Forms에서 Turnstile Captcha를 as a Cloud Service으로 지원합니다.

<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

## AEM Forms 환경을 Turnstile과 통합하기 위한 사전 요구 사항 {#prerequisite}

AEM Forms 핵심 구성 요소에 대해 Turnstile을 구성하려면 다음을 수행해야 합니다. [회전식 사이트키와 비밀키](https://developers.cloudflare.com/turnstile/get-started/) Turnstile 웹 사이트에서.

## AEM Forms용 Turnstile을 구성하는 단계{#steps-to-configure-turnstile}

1. AEM Forms as a Cloud Service 환경에서 구성 컨테이너를 만듭니다. 구성 컨테이너에는 AEM을 외부 서비스에 연결하는 데 사용되는 클라우드 구성이 포함됩니다. AEM Forms 환경을 Turnstile과 연결하도록 구성 컨테이너를 만들고 구성하려면 다음을 수행합니다.
   1. AEM Forms as a Cloud Service 인스턴스를 엽니다.
   1. **[!UICONTROL 도구 > 일반 > 구성 브라우저]**&#x200B;로 이동합니다.
   1. 구성 브라우저에서 기존 폴더를 선택하거나 폴더를 만들 수 있습니다. 폴더를 만들고 이 폴더에 대해 클라우드 구성 옵션을 활성화하거나 기존 폴더에 대해 클라우드 구성 옵션을 활성화할 수 있습니다.

      * **폴더를 만들고 이 폴더에 대한 클라우드 구성 옵션을 활성화하려면**:
         1. 구성 브라우저에서 **[!UICONTROL 만들기]**.
         1. 구성 만들기 대화 상자에서 이름, 제목을 지정하고 **[!UICONTROL 클라우드 구성]** 옵션을 선택합니다.
         1. **[!UICONTROL 만들기]**&#x200B;를 클릭합니다.
      * 기존 폴더에 대해 클라우드 구성 옵션을 활성화하려면 다음을 수행하십시오.
         1. 구성 브라우저에서 폴더를 선택하고 **[!UICONTROL 속성]**.
         1. 구성 속성 대화 상자에서 다음을 활성화합니다 **[!UICONTROL 클라우드 구성]**.
         1. 선택 **[!UICONTROL 저장 및 닫기]** 구성을 저장하고 대화 상자를 종료합니다.

1. Cloud Service 구성:
   1. AEM 작성자 인스턴스에서 ![tools-1](assets/tools-1.png) > **[!UICONTROL Cloud Service]** 및 선택 **[!UICONTROL 개찰구]**.
      ![Ui의 턴스타일](assets/turnstile-in-ui.png)
   1. 이전 섹션에서 설명한 대로 작성되거나 업데이트된 구성 컨테이너를 선택합니다. **[!UICONTROL 만들기]**를 선택합니다.
      ![구성 회전식 문](assets/config-hcaptcha.png)
   1. 지정 **[!UICONTROL 위젯 유형]** 관리되는 경우 위젯 유형이 사전 요구 사항에서 얻은 키에 따라 변경될 수 있습니다. **[!UICONTROL 제목]**, **[!UICONTROL 이름]**, **[!UICONTROL 사이트 키]**, 및 **[!UICONTROL 비밀 키]** 턴스타일 서비스용 [전제 조건에서 획득됨](#prerequisite). **[!UICONTROL 만들기]**&#x200B;를 선택합니다.

      ![AEM Forms 환경과 턴스타일을 연결하도록 Cloud Service 구성](assets/config-turntstile.png)

>[!NOTE]
> 이미 턴스타일 유효성 검사를 위해 미리 채워져 있으므로 사용자는 클라이언트측 JavaScript 유효성 검사 URL 및 서버측 유효성 검사 URL을 수정할 필요가 없습니다.

Turnstile Captcha 서비스가 구성되면 적응형 양식에서 사용할 수 있습니다.

## 적응형 양식에서 턴스타일 사용{#using-turnstile-foundation-components}

1. AEM Forms as a Cloud Service 인스턴스를 엽니다.
1. 다음으로 이동 **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.
1. 적응형 양식 선택 및 선택 **[!UICONTROL 속성]**. 의 경우 **[!UICONTROL 구성 컨테이너]** 옵션을 선택한 다음 AEM Forms과 Turnstile을 연결하는 클라우드 구성이 포함된 구성 컨테이너를 선택하고 **[!UICONTROL 저장 및 닫기]**.

   이러한 구성 컨테이너가 없는 경우 섹션 을 참조하십시오 [AEM Forms 환경과 턴스타일 연결](#connect-your-forms-environment-with-turnstile-service) 구성 컨테이너를 만드는 방법을 알아봅니다.

   ![구성 컨테이너 선택](/help/forms/assets/captcha-properties.png)

1. 적응형 양식 선택 및 선택 **[!UICONTROL 편집]**. 적응형 양식이 적응형 Forms 편집기에서 열립니다.
1. 구성 요소 브라우저에서 **[!UICONTROL Captcha]** 구성 요소를 적응형 양식에 추가합니다.
1. 다음 항목 선택 **[!UICONTROL Captcha]** 구성 요소를 클릭하고 속성을 클릭합니다. ![속성 아이콘](assets/configure-icon.svg) 아이콘. 속성 대화 상자가 열립니다.

   ![설정](assets/turnstile-setting-v1.png)

   다음 속성을 지정합니다.

   * **[!UICONTROL 제목]:** Captcha 구성 요소의 제목을 지정합니다. 양식 및 규칙 편집기에서 고유한 이름으로 양식 구성 요소를 쉽게 식별할 수 있습니다.
   * **[!UICONTROL 유효성 확인 메시지]:** 양식 제출 시 Captcha의 유효성을 검사하기 위한 유효성 검사 메시지를 제공합니다.
   * **[!UICONTROL Captcha 유효성 검사]:** 옵션 중 하나를 선택하여 Captcha의 유효성을 검사할 수 있습니다.
      * 양식 제출 시
      * 사용자 작업
   * **[!UICONTROL Captcha 서비스]:** Captcha 서비스를 선택하면 여기서 Cloudfare Turnstile Captcha 서비스를 선택합니다.
   * **[!UICONTROL Captcha 구성]:** Turnstile용으로 구성된 클라우드 구성을 선택하십시오. 예를 들어, 여기에서 **관리되는 키**.
     >[!NOTE]
     >유사한 목적으로 환경에 여러 클라우드 구성을 가질 수 있습니다. 그러므로, 서비스를 신중하게 선택하십시오. 서비스가 나열되지 않으면 다음을 참조하십시오. [AEM Forms 환경과 턴스타일 연결](#connect-your-forms-environment-with-turnstile-service) AEM Forms 환경과 턴스타일 서비스를 연결하는 Cloud Service을 만드는 방법을 알아봅니다.

   * **오류 메시지:** Captcha 제출이 실패할 때 사용자에게 표시할 오류 메시지를 제공합니다.
   * **Captcha 크기:** [턴스타일 챌린지] 대화 상자의 표시 크기를 선택합니다. 사용 **[!UICONTROL 콤팩트]** 작은 크기 및 을 표시하는 옵션 **[!UICONTROL 기본]** 비교적 큰 크기의 턴스타일 챌린지 대화 상자를 표시하는 옵션입니다.


     >[!NOTE]
     >이는 관리 및 비대화형 위젯 유형에 적용됩니다. 위젯 유형이 보이지 않으면 크기 속성이 필요하지 않으며 비활성화됩니다.

1. **[!UICONTROL 완료]**&#x200B;를 선택합니다.

이제 양식 작성기가 성공적으로 턴스타일 서비스에 의해 제기된 문제를 지우는 합법적인 양식만 양식 제출이 허용됩니다.

![회전식 챌린지](assets/turnstile-challenge.png)

## 자주 묻는 질문

* **Q: 적응형 양식에 Captcha 구성 요소를 두 개 이상 사용할 수 있습니까?**
* **Ans:** 적응형 양식에서 Captcha 구성 요소를 두 개 이상 사용하는 것은 지원되지 않습니다. 또한, 지연 로드로 표시된 조각 또는 패널에서는 Captcha 구성 요소를 사용하지 않는 것이 좋습니다.

## 추가 참조 {#see-also}

{{see-also}}