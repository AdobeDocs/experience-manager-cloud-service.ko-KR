---
description: 적응형 양식을 제출할 때 이메일 알림을 설정하는 프로세스를 살펴보십시오.
keywords: 적응형 양식에 대한 이메일 보내기 방법, 이메일 제출 액션, 적응형 양식 이메일, 양식 제출 이메일, 이메일 보내기 안내서
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
exl-id: 70386e57-345b-4edb-97f1-3fd52ea9ff4f
title: 적응형 양식에 대한 제출 액션을 구성하는 방법
role: User, Developer
source-git-commit: 1be7bafc1d93a65a81eeb2f7e86cac33cde7aa35
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 19%

---

# 적응형 양식의 이메일 보내기 제출 액션 구성

**[!UICONTROL 전자 메일 보내기]** 제출 액션을 사용하면 양식을 성공적으로 제출하면 한 명 이상의 받는 사람에게 전자 메일을 보낼 수 있습니다. 이 제출 액션을 사용하면 양식 데이터를 사전 정의된 형식으로 포함할 수 있는 이메일을 만들 수 있습니다. 예를 들어 제출된 양식 데이터에서 고객 이름, 배송 주소, 주 이름과 우편번호를 검색하는 다음 템플릿을 고려합니다.


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

이메일 보내기 제출 액션을 사용하여 적응형 양식을 구성하면 다음과 같은 장점이 있습니다.

* 양식 데이터가 지정된 이메일 수신자에게 직접 전송되므로 빠른 통신이 가능합니다.
* 양식 제출을 이메일 알림에 직접 통합하여 워크플로를 간소화할 수 있습니다.
* 조직은 이메일 콘텐츠를 사용자 정의하여 특정 커뮤니케이션 요구 사항에 적합하게 만들 수 있습니다.

>[!BEGINTABS]

>[!TAB 기초 구성 요소]

Foundation 구성 요소에 대해 전자 메일 제출 액션을 구성하려면 다음 작업을 수행하십시오.

1. 편집할 적응형 양식을 열고 적응형 양식 컨테이너 속성의 **[!UICONTROL 제출]** 섹션으로 이동합니다.
1. **[!UICONTROL 작업 제출]** 드롭다운 목록에서 **[!UICONTROL 전자 메일 보내기]**&#x200B;를 선택합니다.

   ![전자 메일 보내기의 작업 구성](/help/forms/assets/send-email-fc.png)

1. **[!UICONTROL 보낸 사람]** 텍스트 상자에 보낸 사람의 전자 메일 ID를 지정하십시오.
1. **[!UICONTROL 받는 사람의 전자 메일 ID를]** 텍스트 상자에 추가합니다. **[!UICONTROL 추가]** 단추를 클릭하여 여러 수신자를 추가할 수 있습니다.
1. [선택 사항] **[!UICONTROL 추가]** 단추를 클릭하여 참조 및 숨은 참조 받는 사람을 추가합니다.
1. **[!UICONTROL 제목]** 텍스트 상자에 제목 줄을 지정하십시오.
1. 이메일 템플릿을 추가하여 이메일 전송 제출 액션을 구성합니다.
   * **[!UICONTROL 외부 템플릿 경로]** 옵션을 사용하여 AEM 에셋에 저장된 외부 이메일 템플릿에 대한 경로를 지정할 수 있습니다.
   * **[!UICONTROL 전자 메일 서식 파일]** 텍스트 상자에 양식 제출을 위한 사용자 지정 전자 메일 서식 파일을 추가할 수도 있습니다.
1. [선택 사항] **[!UICONTROL 전자 메일 보내기]** 제출 액션은 전자 메일에 첨부 파일 및 [DoR(기록 문서)](generate-document-of-record-core-components.md)을(를) 포함하는 옵션을 제공합니다.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

>[!TAB 핵심 구성 요소]

핵심 구성 요소에 대해 이메일 제출 전송 작업을 구성하려면 다음 작업을 수행하십시오.

1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. **[!UICONTROL 제출]** 탭을 클릭합니다.
1. **[!UICONTROL 작업 제출]** 드롭다운 목록에서 **[!UICONTROL 전자 메일 보내기]**&#x200B;를 선택합니다.

   ![전자 메일 보내기의 작업 구성](/help/forms/assets/send-email-action-configuration.gif)
1. **[!UICONTROL 보낸 사람]** 텍스트 상자에 보낸 사람의 전자 메일 ID를 지정하십시오.
1. **[!UICONTROL 받는 사람의 전자 메일 ID를]** 텍스트 상자에 추가합니다. **[!UICONTROL 추가]** 단추를 클릭하여 여러 수신자를 추가할 수 있습니다.
1. [선택 사항] **[!UICONTROL 추가]** 단추를 클릭하여 참조 및 숨은 참조 받는 사람을 추가합니다.
1. **[!UICONTROL 제목]** 텍스트 상자에 제목 줄을 지정하십시오.
1. 이메일 템플릿을 추가하여 이메일 전송 제출 액션을 구성합니다.
   * **[!UICONTROL 외부 템플릿 경로]** 옵션을 사용하여 AEM 에셋에 저장된 외부 이메일 템플릿에 대한 경로를 지정할 수 있습니다.
   * **[!UICONTROL 전자 메일 서식 파일]** 텍스트 상자에 양식 제출을 위한 사용자 지정 전자 메일 서식 파일을 추가할 수도 있습니다.
1. [선택 사항] **[!UICONTROL 전자 메일 보내기]** 제출 액션은 전자 메일에 첨부 파일 및 [DoR(기록 문서)](generate-document-of-record-core-components.md)을(를) 포함하는 옵션을 제공합니다.
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

>[!TAB 범용 편집기]

범용 편집기에서 이메일 전송 작업을 구성하려면 다음 작업을 수행하십시오.

1. 편집할 적응형 양식을 엽니다.
1. 편집기에서 **양식 속성 편집** 확장을 클릭합니다.
**양식 속성** 대화 상자가 나타납니다.

   >[!NOTE]
   >
   > * 범용 편집기 인터페이스에 **양식 속성 편집** 아이콘이 보이지 않는 경우 Extension Manager에서 **양식 속성 편집** 확장을 사용하도록 설정하십시오.
   > * 범용 편집기에서 확장을 활성화하거나 비활성화하는 방법에 대해 알아보려면 [Extension Manager 기능 하이라이트](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) 문서를 참조하십시오.


1. **제출** 탭을 클릭하고 **[!UICONTROL 전자 메일 보내기]** 제출 액션을 선택합니다.

   ![전자 메일 유니버설 편집기 보내기](/help/forms/assets/send-email-ue.png)

1. **[!UICONTROL 보낸 사람]** 텍스트 상자에 보낸 사람의 전자 메일 ID를 지정하십시오.
1. **[!UICONTROL 받는 사람의 전자 메일 ID를]** 텍스트 상자에 추가합니다. **[!UICONTROL 추가]** 단추를 클릭하여 여러 수신자를 추가할 수 있습니다.
1. [선택 사항] **[!UICONTROL 추가]** 단추를 클릭하여 참조 및 숨은 참조 받는 사람을 추가합니다.
1. **[!UICONTROL 제목]** 텍스트 상자에 제목 줄을 지정하십시오.
1. 이메일 템플릿을 추가하여 이메일 전송 제출 액션을 구성합니다.
   * **[!UICONTROL 외부 템플릿 경로]** 옵션을 사용하여 AEM 에셋에 저장된 외부 이메일 템플릿에 대한 경로를 지정할 수 있습니다.
   * **[!UICONTROL 전자 메일 서식 파일]** 텍스트 상자에 양식 제출을 위한 사용자 지정 전자 메일 서식 파일을 추가할 수도 있습니다.
1. [선택 사항] **[!UICONTROL 전자 메일 보내기]** 제출 액션은 전자 메일에 첨부 파일 및 [DoR(기록 문서)](generate-document-of-record-core-components.md)을(를) 포함하는 옵션을 제공합니다.
1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭합니다.

>[!ENDTABS]

## 모범 사례 {#best-practices}

* 이메일 콘텐츠를 명확하고 간결하게 유지하는 것이 좋습니다. 사용자는 이메일의 목적과 수행해야 하는 모든 작업을 이해해야 합니다.
* 모든 양식 필드는 적응형 양식 내의 다른 패널에 배치되더라도 고유한 요소 이름을 갖는 것이 좋습니다.
* AEM as a Cloud Service를 사용하는 경우 아웃바운드 이메일을 암호화해야 합니다. 아웃바운드 이메일 기능은 기본적으로 비활성화되어 있습니다. 활성화하려면 [액세스 권한 요청](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=ko#sending-email)에 지원 티켓을 제출하세요.

## 관련 문서

{{af-submit-action}}
