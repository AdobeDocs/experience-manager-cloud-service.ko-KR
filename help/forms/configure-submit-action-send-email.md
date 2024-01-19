---
Title: How to send an email on submission of an Adaptive Form?
Description: Explore the process to set up email notifications when submitting an Adaptive Form.
keywords: 적응형 양식에 대한 이메일 보내기 방법, 이메일 제출 액션, 적응형 양식 이메일, 양식 제출 이메일, 이메일 보내기 안내서
feature: Adaptive Forms, Core Components
source-git-commit: f1db04e6cd1f78c1530aefd29f5f036ca5e70873
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 24%

---


# 적응형 양식에 대한 이메일 제출 전송 작업 구성

다음 **[!UICONTROL 이메일 보내기]** 제출 액션을 사용하면 양식 제출에 성공하면 한 명 이상의 수신자에게 이메일을 보낼 수 있습니다. 이 제출 액션을 사용하면 양식 데이터를 사전 정의된 형식으로 포함할 수 있는 이메일을 만들 수 있습니다. 예를 들어 제출된 양식 데이터에서 고객 이름, 배송 주소, 주 이름과 우편번호를 검색하는 다음 템플릿을 고려합니다.


    ```
    ${customer_Name} 님, 안녕하세요.
    
    기본 배송 주소가 다음과 같이 설정됩니다.
    ${customer_Name},
    ${customer_Shipping_Address},
    ${customer_State},
    ${customer_ZIPCode}
    
    감사합니다.
    WKND
    
    ```


## 장점

이메일 전송 제출 액션을 사용하여 적응형 양식을 구성할 때의 몇 가지 장점은 다음과 같습니다.

* 양식 데이터가 지정된 이메일 수신자에게 직접 전송되므로 빠른 통신이 가능합니다.
* 양식 제출을 이메일 알림에 직접 통합하여 워크플로를 간소화하는 데 도움이 됩니다.
* 조직이 이메일 콘텐츠를 사용자 정의할 수 있도록 지원하므로 특정 통신 요구 사항에 적합합니다.

## 이메일 전송 제출 액션 구성 {#steps-to-configure-send-email-submit-action}

제출 액션을 구성하려면 다음 작업을 수행하십시오.

1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. **[!UICONTROL 제출]** 탭을 클릭합니다.
1. 다음에서 **[!UICONTROL 제출 액션]** 드롭다운 목록에서 다음을 선택합니다. **[!UICONTROL 이메일 보내기]**.

   ![이메일 보내기 작업 구성](/help/forms/assets/send-email-action-configuration.gif)
1. 에서 발신자의 이메일 ID 지정 **[!UICONTROL 출처:]** 텍스트 상자.
1. 에 수신자의 이메일 ID 추가 **[!UICONTROL 종료]** 텍스트 상자. 다음을 클릭하여 여러 수신자를 추가할 수 있습니다. **[!UICONTROL 추가]** 단추를 클릭합니다.
1. [선택 사항] 다음을 클릭하여 참조 및 숨은 참조를 위한 수신자 추가 **[!UICONTROL 추가]** 단추를 클릭합니다.
1. 에서 제목 줄 지정 **[!UICONTROL 제목]** 텍스트 상자.
1. 이메일 템플릿을 추가하여 이메일 전송 제출 액션을 구성합니다.
   * 를 사용하여 AEM 에셋에 저장된 외부 이메일 템플릿에 대한 경로를 지정할 수 있습니다. **[!UICONTROL 외부 템플릿 경로]** 옵션을 선택합니다.
   * 양식 제출을 위한 사용자 정의 이메일 템플릿을 **[!UICONTROL 이메일 템플릿]** 텍스트 상자.
1. [선택 사항] 다음 **[!UICONTROL 이메일 보내기]** 제출 액션은 첨부 파일 및 을 포함할 수 있는 옵션을 제공합니다. [기록 문서(DoR)](generate-document-of-record-core-components.md) 이메일.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

## 모범 사례 {#best-practices}

* 이메일 콘텐츠를 명확하고 간결하게 유지하는 것이 좋습니다. 사용자는 이메일의 목적과 수행해야 하는 모든 작업을 이해해야 합니다.
* 모든 양식 필드는 적응형 양식 내의 다른 패널에 배치되더라도 고유한 요소 이름을 갖는 것이 좋습니다.
* AEM as a Cloud Service를 사용하는 경우 아웃바운드 이메일을 암호화해야 합니다. 아웃바운드 이메일 기능은 기본적으로 비활성화되어 있습니다. 활성화하려면 지원 티켓을 다음으로 제출하십시오. [액세스 권한 요청](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=ko#sending-email).


## 관련 문서

{{af-submit-action}}


