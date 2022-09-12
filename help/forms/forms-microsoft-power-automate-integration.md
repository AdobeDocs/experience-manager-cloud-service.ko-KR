---
title: 적응형 양식과 Microsoft® Power Automate 통합
description: 적응형 양식을 Microsoft® Power Automate와 통합합니다.
hide: true
hidefromtoc: true
exl-id: a059627b-df12-454d-9e2c-cc56986b7de6
source-git-commit: ccc4d487cb180273284276cf9cdf18680a3efcb8
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 5%

---

# Microsoft® Power Automate로 적응형 양식 연결 {#connect-adaptive-form-with-power-automate}

제출 시 Microsoft® Power Automated Cloud Flow를 실행하도록 적응형 양식을 구성할 수 있습니다. 구성된 적응형 양식은 캡처된 데이터, 첨부 파일 및 기록 문서를 처리를 위해 Power Automate Cloud Flow로 전송합니다. 이렇게 하면 Microsoft® Power Automate의 강력한 기능을 활용하면서 사용자 정의 데이터 캡처 환경을 구축하여 캡처된 데이터를 중심으로 비즈니스 로직을 구축하고 고객 워크플로를 자동화할 수 있습니다. 다음은 적응형 양식을 Microsoft® Power 자동화와 통합한 후 수행할 수 있는 작업의 몇 가지 예입니다.

* 고급 자동화 비즈니스 프로세스에서 적응형 Forms 데이터 사용
* Power Automate를 사용하여 캡처된 데이터를 500개 이상의 데이터 소스 또는 공개적으로 사용 가능한 API로 전송
* 캡처된 데이터에 대해 복잡한 계산 수행
* 사전 정의된 일정에 따라 스토리지 시스템에 적응형 Forms 데이터를 저장합니다

응용 Forms 편집기에서는 다음을 제공합니다. **Microsoft® 전원 자동화 흐름 호출** 적응형 양식 데이터, 첨부 파일 및 기록 문서를 전송하는 제출 작업은 Power Automate Cloud Flow로 전송됩니다. 제출 작업을 사용하여 캡처한 데이터를 Microsoft® Power Automate로 보내려면 [Forms as a Cloud Service 인스턴스를 Microsoft® Power Automate로 연결](forms-microsoft-power-automate-integration.md#connect-forms-server-with-power-automate)

## 사전 요구 사항

적응형 양식을 Microsoft® Power Automate와 연결하려면 다음이 필요합니다.

* Microsoft® Power Automatic Premium 라이센스.
* Microsoft® [전원 자동화 플로우](https://docs.microsoft.com/en-us/power-automate/create-flow-solution) 사용 `When an HTTP request is received` 적응형 양식 제출 데이터를 수락하도록 트리거합니다.


* Forms 작성자 및 Forms 관리자 권한이 있는 Experience Manager 사용자.
* Power Automate에 연결하는 데 사용되는 계정이 Power Automate 플로우의 소유자인지 확인합니다.


## Forms as a Cloud Service 인스턴스를 Microsoft® Power Automate로 연결 {#connect-forms-server-with-power-automate}

다음 작업을 수행하여 Forms as a Cloud Service 인스턴스를 Microsoft® Power Automate와 연결합니다.

1. Microsoft® Azure Active Directory 응용 프로그램 만들기
1. Microsoft® Power Create Databasse Cloud Configuration을 자동화합니다.
1. Microsoft® Power Automatic Flow Service Cloud 구성 만들기
1. Microsoft® Power Automatic Databasse Cloud 구성을 게시합니다.

### Microsoft® Azure Active Directory 응용 프로그램 만들기 {#ms-power-automate-application}

1. 에 로그인합니다. [Azure 포털](https://portal.azure.com/).
1. 선택 [!UICONTROL Azure Active Directory] 왼쪽 탐색에서 를 클릭합니다.
1. 기본 디렉토리 페이지에서 [!UICONTROL 앱 등록] 왼쪽 패널에서 생성합니다.
1. 앱 등록 페이지에서 새 등록을 클릭합니다.
1. 페이지에서 이름, 지원되는 계정 유형 및 리디렉션 URI를 지정합니다. 리디렉션 URI에서 다음을 지정하고 저장을 클릭합니다.
   * `https://[Forms as a Cloud Service Server]/libs/fd/powerautomate/content/dataverse/config.html`
   * `https://[Forms as a Cloud Service Server]/libs/fd/powerautomate/content/flowservice/config.html`

   ![Azure Active Directory 응용 프로그램 등록](assets/power-automate-application.png)

   >[!NOTE]
   >필요한 경우 인증 페이지에서 추가 리디렉션 URI를 지정할 수도 있습니다.
   > 지원되는 계정 유형에 대해 사용 사례에 따라 단일 테넌트, 여러 테넌트 또는 개인 Microsoft 계정을 선택합니다


1. 인증 페이지에서 다음 옵션을 활성화하고 저장을 클릭합니다.


   * 액세스 토큰(암시적 흐름에 사용됨)
   * ID 토큰(암시적 및 하이브리드 흐름에 사용됨)

1. API 권한 페이지에서 권한 추가 를 클릭합니다.
1. Microsoft® API에서 Flow Service 를 선택하고 다음 권한을 선택합니다.
   * Flows.Manage.All
   * Flows.Read.All

   권한 추가 를 클릭하여 권한을 저장합니다.
1. API 권한 페이지에서 권한 추가 를 클릭합니다. 조직에서 사용하고 검색하는 API를 선택합니다 `DataVerse`.
1. user_impersonation을 활성화하고 권한 추가를 클릭합니다.
1. (선택 사항) Certificates &amp; Secret 페이지에서 새 클라이언트 암호를 클릭합니다. 클라이언트 암호 추가 화면에서 암호가 만료될 설명과 기간을 제공한 다음 추가를 클릭합니다. 비밀 문자열이 생성됩니다.
1. 조직별 참고 사항 유지 [Dynamics 환경 URL](https://docs.microsoft.com/en-us/power-automate/web-api#compose-http-requests).

### Microsoft® Power Automatic Databasse Cloud 구성 만들기 {#microsoft-power-automate-dataverse-cloud-configuration}

1. AEM Forms 작성자 인스턴스에서 **[!UICONTROL 도구]** ![망치](assets/hammer.png) > **[!UICONTROL 일반]** > **[!UICONTROL 구성 브라우저]**.
1. 설정 **[!UICONTROL 구성 브라우저]** 페이지, 탭 **[!UICONTROL 만들기]**.
1. 에서 **[!UICONTROL 구성 만들기]** 대화 상자에서 다음을 지정합니다 **[!UICONTROL 제목]** 구성에 대해 **[!UICONTROL 클라우드 구성]**, 탭 **[!UICONTROL 만들기]**. 이를 통해 Cloud Service를 저장하는 구성 컨테이너가 생성됩니다. 폴더 이름에는 공백이 없어야 합니다.
1. 다음으로 이동 **[!UICONTROL 도구]** ![망치](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® 전원 자동 데이터 버스]** 이전 단계에서 만든 구성 컨테이너를 엽니다.

   >[!NOTE]
   >
   >적응형 양식을 만들 때 **[!UICONTROL 구성 컨테이너]** 필드.
1. 구성 페이지에서 **[!UICONTROL 만들기]** 만들기 [!DNL Microsoft® Power Automate Flow Service] AEM Forms의 구성.
1. 설정 **[!UICONTROL Microsoft® Power Automate용 데이터 버스 서비스 구성]** 페이지에서, **[!UICONTROL 클라이언트 ID]** (응용 프로그램 ID라고도 함), **[!UICONTROL 클라이언트 암호]**, **[!UICONTROL OAuth URL]** 및 **[!UICONTROL 동적 환경 URL]**. 의 클라이언트 ID, 클라이언트 암호, OAuth URL 및 동적 환경 URL 사용 [Microsoft® Azure Active Directory 응용 프로그램](#ms-power-automate-application) 이전 섹션에서 작성했습니다. Microsoft® Azure Active Directory 응용 프로그램 UI에서 끝점 옵션을 사용하여 OAuth URL을 찾습니다

![Microsoft Power에서 엔드포인트 옵션 사용 자동 애플리케이션 UI를 사용하여 OAuth URL을 찾습니다](assets/endpoints.png)
Microsoft® Power Automate 애플리케이션 UI에서 엔드포인트 옵션 을 사용하여 OAuth URL을 찾습니다

1. 탭 **[!UICONTROL Connect]** . 메시지가 표시되면 Microsoft® Azure 계정에 로그인합니다. 탭 **[!UICONTROL 저장]**.

### Microsoft® Power Automatic Flow Service Cloud 구성 만들기.

1. 다음으로 이동 **[!UICONTROL 도구]** ![망치](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® Power Automatic Flow Service]** 이전 섹션에서 만든 구성 컨테이너를 엽니다.

   >[!NOTE]
   >
   >적응형 양식을 만들 때 **[!UICONTROL 구성 컨테이너]** 필드.
1. 구성 페이지에서 **[!UICONTROL 만들기]** 만들기 [!DNL Microsoft® Power Automate Flow Service] AEM Forms의 구성.
1. 설정 **[!UICONTROL Microsoft® Power Automatic에 대한 데이터베이스 구성]** 페이지에서, **[!UICONTROL 클라이언트 ID]** (응용 프로그램 ID라고도 함), **[!UICONTROL 클라이언트 암호]**, **[!UICONTROL OAuth URL]** 및 **[!UICONTROL 동적 환경 URL]**. 클라이언트 ID, 클라이언트 암호, OAuth URL 및 Dynamics 환경 ID를 사용합니다. Microsoft® Azure Active Directory 응용 프로그램 UI에서 끝점 옵션을 사용하여 OAuth URL을 찾습니다. 를 엽니다. [내 흐름](https://us.flow.microsoft.com) 내 흐름 을 링크하고 탭하면 URL에 나열된 ID를 Dynamics 환경 ID로 사용합니다.
1. 탭 **[!UICONTROL Connect]**. 메시지가 표시되면 Microsoft® Azure 계정에 로그인합니다. 탭 **[!UICONTROL 저장]**.

### Microsoft® Power Automatic Databasse 및 Microsoft® Power Automatic Flow Service Cloud 구성 모두 게시 {#publish-microsoft-power-automate-dataverse-cloud-configuration}

1. 다음으로 이동 **[!UICONTROL 도구]** ![망치](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® 전원 자동 데이터 버스]** 이전 페이지에서 만든 구성 컨테이너를 열고 [Microsoft® Power Automatic Databasse Cloud 구성 만들기](#microsoft-power-automate-dataverse-cloud-configuration) 섹션을 참조하십시오.
1. 을(를) 선택합니다 `dataverse` 구성 및 탭 **[!UICONTROL 게시]**.
1. 게시 페이지에서 을 선택합니다 **[!UICONTROL 모든 구성]** 탭 **[!UICONTROL 게시]**. Power Automatic Databasode 및 Power Automatic Flow Service Cloud 구성을 모두 게시합니다.

이제 Forms as a Cloud Service 인스턴스가 Microsoft® Power Automate에 연결됩니다. 이제 적용형 Forms 데이터를 고급 자동화 흐름으로 보낼 수 있습니다.

## Microsoft 호출® 전원 자동화 플로우 제출 작업을 사용하여 데이터를 Power Automatic Flow에 보냅니다. {#use-the-invoke-microsoft-power-automate-flow-submit-action}

다음에 [Forms as a Cloud Service 인스턴스를 Microsoft® Power Automate로 연결](#connect-forms-server-with-power-automate)다음 작업을 수행하여 양식 제출 시 캡처된 데이터를 Microsoft® 플로우에 보내도록 적응형 양식을 구성합니다.

1. 작성자 인스턴스에 로그인하고 적응형 양식을 선택한 다음 를 클릭합니다. **[!UICONTROL 속성]**.
1. 구성 컨테이너에서 섹션에서 만든 컨테이너를 찾아 선택합니다 [Microsoft® Power Automatic Databasse Cloud 구성 만들기](#microsoft-power-automate-dataverse-cloud-configuration), 탭 **[!UICONTROL 저장 후 닫기]**.
1. 편집할 적응형 양식을 열고 다음으로 이동합니다 **[!UICONTROL 제출]** 적응형 양식 컨테이너 속성의 섹션.
1. 속성 컨테이너에서 **[!UICONTROL 작업 제출]** 선택 **[!UICONTROL 전원 자동화 흐름 호출]** 선택 사항입니다. 사용 가능한 전원 자동화 흐름 목록 제공 **[!UICONTROL 전원 자동화 플로우]** 선택 사항입니다. 필요한 흐름을 선택하면 적응형 Forms 데이터가 제출 시 해당 워크플로우에 제출됩니다.

![제출 작업 구성](assets/submission.png)

>[!NOTE]
>
> 적응형 양식을 제출하기 전에 `When an HTTP Request is received` JSON 스키마 아래에 포함된 트리거가 Power Automatic 플로우에 추가됩니다.

```
        {
            "type": "object",
            "properties": {
                "attachments": {
                    "type": "array",
                    "items": {
                        "type": "object",
                        "properties": {
                            "filename": {
                                "type": "string"
                            },
                            "data": {
                                "type": "string"
                            },
                            "contentType": {
                                "type": "string"
                            },
                            "size": {
                                "type": "integer"
                            }
                        },
                        "required": [
                            "filename",
                            "data",
                            "contentType",
                            "size"
                        ]
                    }
                },
                "templateId": {
                    "type": "string"
                },
                "templateType": {
                    "type": "string"
                },
                "data": {
                    "type": "string"
                },
                "document": {
                    "type": "object",
                    "properties": {
                        "filename": {
                            "type": "string"
                        },
                        "data": {
                            "type": "string"
                        },
                        "contentType": {
                            "type": "string"
                        },
                        "size": {
                            "type": "integer"
                        }
                    }
                }
            }
        }
```

