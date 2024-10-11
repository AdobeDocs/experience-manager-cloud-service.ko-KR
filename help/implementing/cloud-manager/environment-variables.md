---
title: Cloud Manager의 환경 변수
description: 표준 환경 변수는 OSGi 구성에서 사용할 수 있도록 Cloud Manager을 통해 구성 및 관리하고 런타임 환경에 제공할 수 있습니다.
exl-id: 5cdd5532-11fe-47a3-beb2-21967b0e43c6
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2573eb5f8a8ff21a8e30b94287b554885cd1cd89
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 28%

---


# Cloud Manager의 환경 변수 {#environment-variables}

표준 환경 변수는 Cloud Manager를 통해 구성 및 관리할 수 있습니다. 런타임 환경에 제공되며 OSGi 구성에서 사용할 수 있습니다.

환경 변수는 변경되는 내용에 따라 환경별 값 또는 환경 비밀일 수 있습니다.

## 환경 변수 정보 {#overview}

환경 변수는 AEM as a Cloud Service 사용자에게 다음과 같은 이점을 제공합니다.

* 이를 통해 코드와 애플리케이션의 비헤이비어가 컨텍스트와 환경에 따라 달라질 수 있습니다. 예를 들어 비용이 많이 드는 실수를 피하기 위해 프로덕션 또는 스테이징 환경과 비교하여 개발 환경에서 다른 구성을 활성화하는 데 사용할 수 있습니다.
* 한 번만 구성 및 설정하면 되며 필요할 때 업데이트 및 삭제할 수 있습니다.
* 해당 값은 언제든지 업데이트할 수 있으며 코드를 변경하거나 배포할 필요 없이 즉시 적용됩니다.
* 구성에서 코드를 분리하여 버전 제어에 민감한 정보를 포함할 필요가 없습니다.
* 코드 외부에 있기 때문에 AEM as a Cloud Service 애플리케이션의 보안을 향상시킵니다.

환경 변수를 사용하는 일반적인 사용 사례는 다음과 같습니다.

* AEM 애플리케이션을 다양한 외부 엔드포인트와 연결
* 코드베이스에 직접 저장하는 대신 암호 저장 시 참조 사용
* 프로그램에 여러 개발 환경이 존재하고 일부 구성이 환경마다 다른 경우

## 환경 변수 추가 {#add-variables}

Adobe 여러 변수를 추가하려면 첫 번째 변수를 추가한 다음 **환경 구성** 대화 상자에서 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) **추가**&#x200B;을 사용하여 변수를 추가하는 것이 좋습니다. 이 메서드는 한 번의 업데이트로 환경에 추가할 수 있음을 의미합니다.

환경 변수를 추가, 업데이트 또는 삭제하려면 [**배포 관리자** 역할](/help/onboarding/cloud-manager-introduction.md#role-based-premissions)의 구성원이어야 합니다.

**환경 변수를 추가하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 관리할 프로그램을 선택합니다.
1. 사이드 메뉴에서 **환경**&#x200B;을 클릭합니다.
1. **환경** 페이지에서 환경 변수를 추가할 환경이 있는 테이블의 행을 선택합니다.
1. 환경의 세부 정보 페이지에서 **구성** 탭을 클릭합니다.
1. ![추가/업데이트 - 원 아이콘 추가](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **추가/업데이트**를 클릭합니다.
환경 변수를 처음 추가하는 경우 페이지 중앙에 있는 **구성 추가**&#x200B;를 클릭합니다.

   ![구성 탭](assets/configuration-tab.png)

1. **환경 구성** 대화 상자에서 표의 첫 행에 세부 정보를 입력합니다.

   | 필드 | 설명 |
   | --- | --- |
   | 이름 | 구성 변수의 고유 이름입니다. 환경에서 사용되는 특정 변수를 식별합니다. 다음 명명 규칙을 준수해야 합니다.<ul><li>변수에는 영숫자와 밑줄(`_`)만 포함될 수 있습니다.</li><li>환경당 200개의 변수 제한이 있습니다.</li><li>각 이름은 100자 이하여야 합니다.</li></ul> |
   | 값 | 변수가 보유한 값입니다. |
   | 적용된 단계 | 변수가 적용되는 서비스를 선택합니다. 모든 서비스에 변수를 적용하려면 **모두**&#x200B;를 선택하십시오.<ul><li>**모두**</li><li>**작성자**</li><li>**Publish**</li><li>**미리보기**</li></ul> |
   | 유형 | 변수가 일반인지 비밀인지 선택합니다. |

   ![변수 추가](assets/add-variable.png)

1. ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg)**추가**&#x200B;을 클릭합니다.

   필요에 따라 변수를 추가합니다.

1. **저장**&#x200B;을 클릭합니다.

   **업데이트 중** 상태의 회전기가 표의 오른쪽 위 모서리에 표시됩니다. 새로 추가된 변수의 왼쪽에는 회전기가 표시됩니다. 이러한 상태는 구성이 적용되어 환경이 업데이트되고 있음을 나타냅니다. 완료된 후에 새 환경 변수가 표에 표시됩니다.

![변수 업데이트](assets/updating-variables.png)

## 환경 변수 업데이트 {#update-variables}

환경 변수를 만든 후에는 ![추가/업데이트 - 원형 추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **추가/업데이트**&#x200B;를 사용하여 업데이트하여 **환경 구성** 대화 상자를 열 수 있습니다.

Adobe 여러 변수를 업데이트하려면 **저장**&#x200B;을 클릭하기 전에 **환경 구성** 대화 상자를 사용하여 필요한 모든 변수를 한 번에 업데이트하는 것이 좋습니다. 이렇게 하면 한 번의 업데이트로 환경에 여러 변수를 추가할 수 있습니다.

**환경 변수를 업데이트하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 관리할 프로그램을 선택합니다.
1. 사이드 메뉴에서 **환경**&#x200B;을 클릭합니다.
1. **환경** 페이지에서 변수를 업데이트할 환경이 있는 테이블의 행을 선택합니다.
1. 환경의 세부 정보 페이지에서 **구성** 탭을 클릭합니다.
1. ![추가/업데이트 - 원 아이콘 추가](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **추가/업데이트**&#x200B;를 클릭합니다.
1. **환경 구성** 대화 상자에서 변경할 변수 행의 마지막 열에 있는 ![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.
1. 드롭다운 메뉴에서 **편집**&#x200B;을 클릭합니다.

   ![변수 편집 또는 삭제](assets/edit-delete-variable.png)

1. 필요에 따라 환경 변수의 값을 업데이트합니다.
암호를 편집할 때 값은 볼 수 없고 업데이트만 가능합니다.

   ![변수 편집](assets/edit-variable.png)

1. 다음 중 하나를 수행하십시오.

   * 변경 내용을 적용하려면 ![적용 - 확인 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg)을 클릭하십시오.
   * 변경을 취소하려면 ![실행 취소 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Undo_18_N.svg)을 클릭하십시오.

1. **저장**&#x200B;을 클릭합니다.

   **업데이트 중** 상태의 회전기가 표의 오른쪽 위 모서리에 표시됩니다. 업데이트된 변수 왼쪽에 회전기가 나타나기도 합니다. 이러한 상태는 구성이 적용되어 환경이 업데이트되고 있음을 나타냅니다. 완료되면 업데이트된 환경 변수가 표에 표시됩니다.

## 환경 변수 삭제 {#delete-env-variable}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 관리할 프로그램을 선택합니다.
1. 사이드 메뉴에서 **환경**&#x200B;을 클릭합니다.
1. **환경** 페이지에서 변수를 업데이트할 환경이 있는 테이블의 행을 선택합니다.
1. 환경의 세부 정보 페이지에서 **구성** 탭을 클릭합니다.
1. ![추가/업데이트 - 원 아이콘 추가](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **추가/업데이트**&#x200B;를 클릭합니다.
1. **환경 구성** 대화 상자에서 변경할 변수 행의 마지막 열에 있는 ![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.
1. 드롭다운 메뉴에서 **삭제**&#x200B;를 클릭하여 변수를 즉시 제거합니다.
1. **저장**&#x200B;을 클릭합니다.

## 환경 변수 사용 {#using}

환경 변수를 사용하면 `pom.xml` 구성을 보다 안전하고 유연하게 만들 수 있습니다. 예를 들어 암호를 하드 코딩할 필요가 없으며 환경 변수의 값을 기반으로 구성을 조정할 수 있습니다.

다음과 같이 XML을 통해 환경 변수 및 비밀에 액세스할 수 있습니다.

`${env.VARIABLE_NAME}`

`pom.xml` 파일에서 두 가지 유형의 변수를 모두 사용하는 방법에 대한 예는 [프로젝트 설정](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repository-support-password-protected-maven-repositories)을 참조하십시오.

자세한 내용은 [공식 Maven 설명서](https://maven.apache.org/settings.html#quick-overview)를 참조하십시오.

## 환경 변수 가용성 {#availability}

환경 변수는 다음과 같이 여러 위치에서 사용할 수 있습니다.

| 환경 변수를 사용할 수 있는 경우 | 설명 |
| --- | --- |
| 작성, 미리보기 및 게시 | 일반 환경 변수와 비밀은 작성, 미리보기 및 게시 환경에서 사용할 수 있습니다. |
| Dispatcher | [Dispatcher](https://experienceleague.adobe.com/ko/docs/experience-manager-dispatcher/using/dispatcher)에서는 일반 환경 변수만 사용할 수 있습니다.<ul><li>시크릿은 사용할 수 없습니다.</li><li>`IfDefine` 지시문에서는 환경 변수를 사용할 수 없습니다.</li><li>배포하기 전에 [로컬에서 Dispatcher](https://experienceleague.adobe.com/ko/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools)를 사용하여 환경 변수 사용을 확인합니다.</li></ul> |
| OSGi 구성 | [OSGi 구성](/help/implementing/deploying/configuring-osgi.md)에서 일반 환경 변수와 암호를 모두 사용할 수 있습니다. |
| 파이프라인 변수 | 환경 변수 외에도 빌드 단계 중에 노출되는 파이프라인 변수도 있습니다. [빌드 환경](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#pipeline-variables)의 파이프라인 변수에 대해 자세히 알아보세요. |

