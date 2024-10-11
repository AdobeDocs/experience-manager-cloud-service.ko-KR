---
title: Cloud Manager의 파이프라인 변수
description: Cloud Manager에서 파이프라인 변수를 사용하여 빌드에 대한 특정 구성 변수를 관리하는 방법을 알아봅니다.
exl-id: cfcef2e2-0590-457d-a0f9-6092a6d9e0e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2573eb5f8a8ff21a8e30b94287b554885cd1cd89
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 14%

---

# Cloud Manager의 파이프라인 변수 {#configuring-pipeline-variables}

빌드 프로세스는 Git 저장소에 저장해서는 안 되는 특정 구성 변수를 사용할 수 있습니다. 또는 동일한 분기에서 실행되는 파이프라인 간에 조정해야 할 수 있습니다. Cloud Manager을 사용하면 이러한 설정을 파이프라인 변수로 관리할 수 있습니다.

## 파이프라인 변수 기본 정보 {#pipeline-variables}

Cloud Manager을 사용하여 여러 가지 방법으로 파이프라인 변수를 구성할 수 있습니다.

* [Cloud Manager 사용자 인터페이스 사용](#ui)
* [Cloud Manager CLI 사용](#cli)
* [Cloud Manager API 사용](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Variables/operation/getPipelineVariables)

변수는 일반 텍스트로 저장되거나 사용하지 않을 때 암호화될 수 있습니다. 두 경우 모두 `pom.xml` 파일 또는 다른 빌드 스크립트 내에서 참조할 수 있는 환경 변수로 빌드 환경 내에서 변수를 사용할 수 있습니다.

## Cloud Manager을 통해 파이프라인 변수 추가 {#ui}

Cloud Manager 사용자 인터페이스를 통해 파이프라인 변수를 구성하고 관리할 수 있습니다. 특히 여러 단계에서 다양한 구성이 필요한 경우 파이프라인 관리를 간소화하는 데 도움이 됩니다.

파이프라인 변수를 추가, 편집 및 삭제하려면 파이프라인을 편집할 수 있는 권한이 있어야 합니다.

파이프라인이 실행 중인 경우 변수 관리가 차단됩니다.

**Cloud Manager을 통해 파이프라인 변수를 추가하려면:**

1. [파이프라인을 관리](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md)할 때 파이프라인 변수를 만들 파이프라인의 ![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.

1. 드롭다운 메뉴에서 **변수 보기/편집**&#x200B;을 클릭합니다.

   ![파이프라인 변수 보기/편집](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. **변수 구성** 대화 상자에서 표의 첫 행에 세부 정보를 입력합니다.

   | 필드 | 설명 |
   | --- | --- |
   | 이름 | 구성 변수의 고유 이름입니다. 파이프라인에서 사용되는 특정 변수를 식별합니다. 다음 명명 규칙을 준수해야 합니다.<ul><li>변수에는 영숫자와 밑줄(`_`)만 포함될 수 있습니다.</li><li>이름은 모두 대문자로 해야 합니다.</li><li>파이프라인당 200개의 변수 제한이 있습니다.</li><li>각 이름은 100자 이하여야 합니다.</li><li>각 `string` 변수 값은 2048자 미만이어야 합니다.</li><li>각 `secretString` 형식 변수 값은 500자 이하여야 합니다.</li></ul> |
   | 값 | 변수가 보유한 값입니다. |
   | 적용된 단계 | 필수. 변수가 적용되는 파이프라인의 단계:<ul><li>**빌드** - 변수는 빌드 프로세스 중에 적용됩니다.</li><li>**기능 테스트** - 변수는 기능 테스트 단계에서 사용됩니다.</li><li>**UI 테스트** - 변수는 UI 테스트 단계 동안 사용됩니다.</li></ul> |
   | 유형 | 변수가 일반 텍스트이거나 암호로 암호화되어 있는지 선택합니다. |

   ![변수 추가](/help/implementing/cloud-manager/assets/pipeline-variables-add-variable.png)

1. **추가**&#x200B;를 클릭합니다.

   필요에 따라 변수를 추가합니다.

1. **저장**&#x200B;을 클릭합니다.

## 파이프라인 변수 편집 {#edit-ui}

1. [파이프라인을 관리](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md)할 때 파이프라인 변수를 편집할 파이프라인의 ![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.

1. 드롭다운 메뉴에서 **변수 보기/편집**&#x200B;을 클릭합니다.

   ![파이프라인 변수 보기/편집](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. **변수 구성** 대화 상자에서 변경할 변수의 ![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.

1. 드롭다운 메뉴에서 **편집**&#x200B;을 클릭합니다.

   ![변수 편집](/help/implementing/cloud-manager/assets/pipeline-variables-edit.png)

1. 필요에 따라 변수 값을 업데이트합니다.

   변수의 값만 변경할 수 있습니다.

1. 다음 중 하나를 수행하십시오.

   * 변경 내용을 적용하려면 ![적용 - 확인 표시 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg)을 클릭하십시오.
   * 변경 내용을 되돌리려면 ![실행 취소 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Undo_18_N.svg)을 클릭하십시오.

1. **저장**&#x200B;을 클릭합니다.

## 파이프라인 변수 삭제 {#delete-ui}

1. [파이프라인을 관리](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md)할 때 파이프라인 변수를 삭제할 파이프라인의 ![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.

1. 드롭다운 메뉴에서 **변수 보기/편집**&#x200B;을 클릭합니다.

   ![파이프라인 변수 보기/편집](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. **변수 구성** 대화 상자에서 제거할 변수의 ![줄임표 - 자세히 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.

1. 드롭다운 메뉴에서 **삭제**&#x200B;를 클릭합니다.


## Cloud Manager CLI를 사용하여 파이프라인 변수 설정 {#cli}

CLI(명령줄 인터페이스)의 이 명령은 변수를 설정합니다.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

이 명령은 변수를 나열합니다.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Maven `pom.xml` 파일에서 사용하는 경우 다음 예제와 유사한 구문을 사용하여 이러한 변수를 Maven 속성에 연결하는 것이 유용합니다.

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```
