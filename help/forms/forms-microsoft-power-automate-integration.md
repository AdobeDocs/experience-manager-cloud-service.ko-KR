---
title: 적응형 양식을 Microsoft&reg; Power Automate와 통합하는 방법
description: 적응형 양식을 Microsoft&reg; Power Automate와 통합합니다.
exl-id: a059627b-df12-454d-9e2c-cc56986b7de6
keywords: power automate에 AEM forms 연결, Power Automate AEM Forms, Adaptive Forms에 power automate 통합, Adaptive Forms에서 Power Automate로 데이터 전송
feature: Adaptive Forms, Foundation Components, Core Components, Edge Delivery Services
role: Admin, User, Developer
source-git-commit: 03f92d950744e653e4ef509bac3c3b4709477e41
workflow-type: tm+mt
source-wordcount: '1546'
ht-degree: 17%

---


# Microsoft® Power Automate와 적응형 양식 연결 {#connect-adaptive-form-with-power-automate}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/adaptive-forms-basic-authoring/forms-microsoft-power-automate-integration) |
| AEM as a Cloud Service | 이 문서 |

<span class="preview"> GovCloud를 사용하고 있고 GCC(정부 클라우드 컴퓨팅) 테넌트에 연결해야 하는 경우, 공식 주소에서 aem-forms-ea@adobe.com으로 이메일을 보내 얼리 어답터 프로그램을 통한 액세스를 요청하십시오. </span>

제출 시 Microsoft® Power Automate Cloud Flow를 실행하도록 적응형 양식을 구성할 수 있습니다. 구성된 적응형 양식은 캡처된 데이터, 첨부 파일 및 기록 문서를 처리를 위해 Power Automate Cloud Flow로 전송합니다. 이렇게 하면 Microsoft® Power Automate의 강력한 기능을 활용하면서 사용자 정의 데이터 캡처 환경을 구축하여 캡처된 데이터를 중심으로 비즈니스 로직을 구축하고 고객 워크플로를 자동화할 수 있습니다.

적응형 Forms 편집기는 **Microsoft® Power Automate 플로우 호출** 제출 액션을 제공하여 적응형 양식 데이터, 첨부 파일 및 기록 문서를 Power Automate Cloud Flow로 전송합니다.

AEM as a Cloud Service에서는 양식 제출을 처리하기 위한 다양한 제출 액션을 제공합니다. [적응형 양식 제출 액션](/help/forms/aem-forms-submit-action.md) 문서에서 이러한 옵션에 대해 자세히 알아볼 수 있습니다.


## 장점

다음은 적응형 양식을 Microsoft® Power Automate와 통합한 후 수행할 수 있는 작업에 대한 몇 가지 예입니다.

* Power Automate 비즈니스 프로세스에서 적응형 양식 데이터 사용
* Power Automate를 사용하여 캡처된 데이터를 500개 이상의 데이터 소스 또는 공개적으로 사용 가능한 API로 전송
* 캡처된 데이터에 대해 복잡한 계산 수행
* 미리 정의된 일정에 따라 적응형 양식 데이터를 스토리지 시스템에 저장

## 사전 요구 사항

적응형 양식과 Microsoft® Power Automate를 연결하려면 다음이 필요합니다.

* Microsoft® Power Automate Premium 라이센스.
* 적응형 양식 제출 데이터를 수락하기 위한 [&#x200B; 트리거를 사용하는 Microsoft® &#x200B;](https://docs.microsoft.com/en-us/power-automate/create-flow-solution)Power Automate 흐름`When an HTTP request is received`.
* [Forms 작성자](/help/forms/forms-groups-privileges-tasks.md) 및 [Forms 관리자](/help/forms/forms-groups-privileges-tasks.md) 권한이 있는 Experience Manager 사용자
* Microsoft® Power Automate에 연결하는 데 사용되는 계정은 적응형 양식에서 데이터를 받도록 구성된 Power Automate 흐름의 소유자입니다

## Forms as a Cloud Service 인스턴스와 Microsoft® Power Automate 연결 {#connect-forms-server-with-power-automate}

다음 작업을 수행하여 Forms as a Cloud Service 인스턴스를 Microsoft® Power Automate에 연결합니다.

1. [Microsoft 만들기](#ms-power-automate-application)
1. [Microsoft 만들기](#microsoft-power-automate-dataverse-cloud-configuration)
1. [Microsoft 만들기](#create-microsoft-power-automate-flow-cloud-configuration)
1. [Microsoft 게시](#publish-microsoft-power-automate-dataverse-cloud-configuration)

### Microsoft® Azure Active Directory 응용 프로그램 만들기 {#ms-power-automate-application}

1. [Azure 포털](https://portal.azure.com/)에 로그인합니다.
1. 왼쪽 탐색에서 [!UICONTROL Azure Active Directory]를 선택합니다.
1. 기본 디렉터리 페이지의 왼쪽 패널에서 [!UICONTROL 앱 등록]을 선택합니다.
1. 앱 등록 페이지에서 새 등록을 클릭합니다.
1. 페이지에서 이름, 지원되는 계정 유형 및 리디렉션 URI를 지정합니다. 리디렉션 URI에서 다음을 지정하고 저장을 클릭합니다.
   * `https://[Forms as a Cloud Service Server]/libs/fd/powerautomate/content/dataverse/config.html`
   * `https://[Forms as a Cloud Service Server]/libs/fd/powerautomate/content/flowservice/config.html`

   ![Azure Active Directory 응용 프로그램 등록](assets/power-automate-application.png)

   >[!NOTE]
   >필요한 경우 인증 페이지에서 추가 리디렉션 URI를 지정할 수도 있습니다.
   > 지원되는 계정 유형의 경우 사용 사례에 따라 단일 테넌트, 여러 테넌트 또는 개인 Microsoft® 계정을 선택하십시오


1. 인증 페이지에서 다음 옵션을 활성화하고 저장을 클릭합니다.


   * 액세스 토큰(암시적 흐름에 사용됨)
   * ID 토큰(암시적 흐름과 하이브리드 흐름에 사용)

1. API 권한 페이지에서 `Add a permission`을(를) 클릭합니다.

1. Microsoft® API에서 `Power Automate`을(를) 선택하고 다음 권한을 선택합니다.
   * Flows.Manage.All
   * Flows.Read.All
   * GCC 권한(GCC(정부 클라우드 컴퓨팅) 테넌트에 연결하려는 경우 선택 사항)
`Add permissions`을(를) 클릭하여 권한을 저장합니다.
1. API 권한 페이지에서 `Add a permission`을(를) 클릭합니다. 내 조직에서 사용하는 API를 선택하고 `DataVerse`을(를) 검색한 다음 `user_impersonation` `Add` 권한을 클릭합니다.
1. (선택 사항) 인증서 및 암호 페이지에서 새 클라이언트 암호를 클릭합니다. 클라이언트 암호 추가 화면에서 암호가 만료될 수 있는 설명 및 기간을 입력하고 추가를 클릭합니다. 비밀 문자열이 생성됩니다.
1. 조직별 [Dynamics 환경 URL](https://docs.microsoft.com/en-us/power-automate/web-api#compose-http-requests)을(를) 메모해 두십시오.

### Microsoft® Power Automate Dataverse 클라우드 구성 만들기 {#microsoft-power-automate-dataverse-cloud-configuration}

1. AEM Forms 작성자 인스턴스에서 **[!UICONTROL 도구]** ![hammer](assets/hammer.png) > **[!UICONTROL 일반]** > **[!UICONTROL 구성 브라우저]**&#x200B;로 이동합니다.
1. **[!UICONTROL 구성 브라우저]** 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 선택합니다.
1. **[!UICONTROL 구성 만들기]** 대화 상자에서 구성에 대한 **[!UICONTROL 제목]**&#x200B;을 지정하고 **[!UICONTROL 클라우드 구성]**&#x200B;을 사용하도록 설정하고 **[!UICONTROL 만들기]**&#x200B;를 선택합니다. 이를 통해 Cloud Service를 저장하는 구성 컨테이너가 생성됩니다. 폴더 이름에는 공백이 없어야 합니다.
1. **[!UICONTROL 도구]** ![hammer](assets/hammer.png) > **[!UICONTROL 클라우드 서비스]** > **[!UICONTROL Microsoft® Power Automate Dataverse]**(으)로 이동한 후 이전 단계에서 만든 구성 컨테이너를 엽니다.


   >[!NOTE]
   >
   >적응형 양식을 만들 때 **[!UICONTROL 구성 컨테이너]** 필드에 컨테이너 이름을 지정하십시오.

1. 구성 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 선택하여 AEM Forms에서 [!DNL Microsoft® Power Automate Flow Service] 구성을 만듭니다.
1. **[!UICONTROL Microsoft® Power Automate에 대한 Dataverse 서비스 구성]** 페이지에서 **[!UICONTROL 클라이언트 ID]**(응용 프로그램 ID라고도 함), **[!UICONTROL 클라이언트 암호]**, **[!UICONTROL OAuth URL]** 및 **[!UICONTROL 동적 환경 URL]**&#x200B;을 지정합니다. 이전 섹션에서 만든 [Microsoft® Azure Active Directory 응용 프로그램](#ms-power-automate-application)의 클라이언트 ID, 클라이언트 암호, OAuth URL 및 동적 환경 URL을 사용합니다. Microsoft® Azure Active Directory 애플리케이션 UI의 끝점 옵션을 사용하여 OAuth URL 찾기

   ![Microsoft Power Automate 응용 프로그램 UI의 끝점 옵션을 사용하여 OAuth URL 찾기](assets/endpoints.png)

1. **[!UICONTROL 연결]** 을 선택합니다. 메시지가 표시되면 Microsoft® Azure 계정에 로그인합니다. **[!UICONTROL 저장]**&#x200B;을 선택합니다.

### Microsoft® Power Automate 플로우 서비스 클라우드 구성 생성 {#create-microsoft-power-automate-flow-cloud-configuration}

1. **[!UICONTROL 도구]** ![hammer](assets/hammer.png) > **[!UICONTROL 클라우드 서비스]** > **[!UICONTROL Microsoft® Power Automate 플로우 서비스]**(으)로 이동하여 이전 섹션에서 만든 구성 컨테이너를 엽니다.


   >[!NOTE]
   >
   >적응형 양식을 만들 때 **[!UICONTROL 구성 컨테이너]** 필드에 컨테이너 이름을 지정하십시오.

1. 구성 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 선택하여 AEM Forms에서 [!DNL Microsoft® Power Automate Flow Service] 구성을 만듭니다.

1. (선택 사항) GCC 테넌트에 연결하려면 `Connect to Microsoft GCC` 확인란을 선택하십시오.

   >[!NOTE]
   >
   > GCC(정부 클라우드 컴퓨팅) 테넌트에 연결하려면 Microsoft Azure 포털에서 GCC 권한을 선택합니다.


   ![Power Automate 클라우드 구성](/help/forms/assets/power-automate.png)

1. **[!UICONTROL Microsoft® Power Automate에 대한 Dataverse 구성]** 페이지에서 **[!UICONTROL 클라이언트 ID]**(응용 프로그램 ID라고도 함), **[!UICONTROL 클라이언트 암호]**, **[!UICONTROL OAuth URL]** 및 **[!UICONTROL 동적 환경 URL]**&#x200B;을 지정합니다. 클라이언트 ID, 클라이언트 암호, OAuth URL 및 Dynamics 환경 ID를 사용합니다. Microsoft® Azure Active Directory 응용 프로그램 UI의 끝점 옵션을 사용하여 OAuth URL을 찾습니다. [내 흐름](https://us.flow.microsoft.com) 링크를 열고 [내 흐름]을 선택합니다. URL에 나열된 ID를 Dynamics 환경 ID로 사용합니다.

1. **[!UICONTROL 연결]**&#x200B;을 선택합니다. 메시지가 표시되면 Microsoft® Azure 계정에 로그인합니다. **[!UICONTROL 저장]**&#x200B;을 선택합니다.

### Microsoft® Power Automate Dataverse 및 Microsoft® Power Automate Flow Service 클라우드 구성 모두 게시 {#publish-microsoft-power-automate-dataverse-cloud-configuration}

1. **[!UICONTROL 도구]** ![hammer](assets/hammer.png) > **[!UICONTROL 클라우드 서비스]** > **[!UICONTROL Microsoft® Power Automate Dataverse]**(으)로 이동한 후 이전 [Microsoft® Power Automate Dataverse 클라우드 구성 만들기](#microsoft-power-automate-dataverse-cloud-configuration) 섹션에서 만든 구성 컨테이너를 엽니다.
1. `dataverse` 구성을 선택하고 **[!UICONTROL 게시]**&#x200B;를 선택합니다.
1. 게시 페이지에서 **[!UICONTROL 모든 구성]**&#x200B;을 선택하고 **[!UICONTROL 게시]**&#x200B;를 선택합니다. Power Automate Dataverse 및 Power Automate Flow Service 클라우드 구성을 모두 게시합니다.

이제 Forms as a Cloud Service 인스턴스가 Microsoft® Power Automate와 연결됩니다. 이제 적응형 Forms 데이터를 Power Automate 흐름에 보낼 수 있습니다.

## Microsoft 호출® Power Automate 플로우 제출 액션을 사용하여 Power Automate 플로우에 데이터 전송 {#use-the-invoke-microsoft-power-automate-flow-submit-action}

[Microsoft® Power Automate와 Forms as a Cloud Service 인스턴스를 연결](#connect-forms-server-with-power-automate)한 후 다음 작업을 수행하여 캡처된 데이터를 양식 제출 시 Microsoft® 플로우로 전송하도록 적응형 양식을 구성하십시오.

>[!BEGINTABS]

>[!TAB 기초 구성 요소]

1. 작성자 인스턴스에 로그인하고 적응형 양식을 선택한 다음 **[!UICONTROL 속성]**&#x200B;을 클릭합니다.
1. 구성 컨테이너에서 [Microsoft 만들기® Power Automate Dataverse 클라우드 구성](#microsoft-power-automate-dataverse-cloud-configuration) 섹션에서 만든 컨테이너를 찾아 선택한 다음 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택합니다.
1. 편집할 적응형 양식을 열고 적응형 양식 컨테이너 속성의 **[!UICONTROL 제출]** 섹션으로 이동합니다.
1. 속성 컨테이너에서 **[!UICONTROL 작업 제출]**&#x200B;에 대해 **[!UICONTROL Power Automate 흐름 호출]** 옵션을 선택하고 **[!UICONTROL Power Automate 흐름 선택]**&#x200B;합니다. 필요한 플로우를 선택하면 적응형 Forms 데이터가 제출 시 해당 플로우에 제출됩니다.

   ![제출 액션 구성](assets/submission.png)
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

>[!NOTE]
>
> 적응형 양식을 제출하기 전에 아래 JSON 스키마를 사용하는 `When an HTTP Request is received` 트리거가 Power Automate 흐름에 추가되었는지 확인하십시오.

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

>[!TAB 핵심 구성 요소]

1. 작성자 인스턴스에 로그인하고 적응형 양식을 선택한 다음 **[!UICONTROL 속성]**&#x200B;을 클릭합니다.
1. 구성 컨테이너에서 [Microsoft 만들기® Power Automate Dataverse 클라우드 구성](#microsoft-power-automate-dataverse-cloud-configuration) 섹션에서 만든 컨테이너를 찾아 선택한 다음 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택합니다.
1. 콘텐츠 브라우저를 열고 적응형 양식의 **[!UICONTROL 안내서 컨테이너]** 구성 요소를 선택합니다.
1. 안내서 컨테이너 속성 ![안내서 속성](/help/forms/assets/configure-icon.svg) 아이콘을 클릭합니다. 적응형 양식 컨테이너 대화 상자가 열립니다.
1. **[!UICONTROL 제출]** 탭을 클릭합니다.
1. 제출 작업 드롭다운 목록에서 **[!UICONTROL Power Automate 흐름 호출]** 옵션을 선택하고 **[!UICONTROL Power Automate 흐름 선택]**. 필요한 플로우를 선택하면 적응형 Forms 데이터가 제출 시 해당 플로우에 제출됩니다.

   ![제출 액션 구성](/help/forms/assets/power-automate-cc.png)
1. **[!UICONTROL 완료]**&#x200B;를 클릭합니다.

>[!NOTE]
>
> 적응형 양식을 제출하기 전에 아래 JSON 스키마를 사용하는 `When an HTTP Request is received` 트리거가 Power Automate 흐름에 추가되었는지 확인하십시오.

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

>[!TAB 범용 편집기]

1. 작성자 인스턴스에 로그인하고 적응형 양식을 선택합니다.
1. 구성 컨테이너에서 [Microsoft 만들기® Power Automate Dataverse 클라우드 구성](#microsoft-power-automate-dataverse-cloud-configuration) 섹션에서 만든 컨테이너를 찾아 선택한 다음 **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택합니다.
1. 편집할 적응형 양식을 엽니다.
1. 편집기에서 **양식 속성 편집** 확장을 클릭합니다.
**양식 속성** 대화 상자가 나타납니다.

   >[!NOTE]
   >
   > * 범용 편집기 인터페이스에 **양식 속성 편집** 아이콘이 표시되지 않으면 Extension Manager에서 **양식 속성 편집** 확장 기능을 활성화합니다.
   > * 범용 편집기에서 확장 기능을 활성화하거나 비활성화하는 방법을 알아보려면 [Extension Manager 기능 하이라이트](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) 문서를 참조하십시오.


1. **제출** 탭을 클릭하고 **[!UICONTROL Power Automate 흐름 호출]** 제출 액션을 선택합니다. 필요한 플로우를 선택하면 적응형 Forms 데이터가 제출 시 해당 플로우에 제출됩니다.

   ![제출 액션 구성](/help/forms/assets/power-automate-ue.png)
1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 클릭합니다.

>[!NOTE]
>
> 적응형 양식을 제출하기 전에 아래 JSON 스키마를 사용하는 `When an HTTP Request is received` 트리거가 Power Automate 흐름에 추가되었는지 확인하십시오.

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

>[!ENDTABS]

<!--
## See also

* [Create an Adaptive Form](creating-adaptive-form-core-components.md)
* [Configure a Submit Action](configure-submit-actions-core-components.md)
* [Adobe Experience Manager Connector for Microsoft&reg; Power Automate](https://learn.microsoft.com/en-us/connectors/adobeexperiencemanag/)
* [Connect Adaptive Form to Microsoft&reg; Power Automate](/help/forms/configure-submit-actions-core-components.md#microsoft-power-automate)
-->


## 관련 문서

{{af-submit-action}}

<!--

>[!MORELIKETHIS]
>
>* [Connect Adaptive Form to Microsoft Power Automate](/help/forms/configure-submit-actions-core-components.md#microsoft-power-automate)

-->