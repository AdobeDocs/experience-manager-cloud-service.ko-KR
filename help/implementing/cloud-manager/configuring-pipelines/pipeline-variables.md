---
title: 파이프라인 변수 구성
description: Cloud Manager에서 파이프라인 변수를 사용하여 빌드에 대한 특정 구성 변수를 관리하는 방법을 알아봅니다.
exl-id: cfcef2e2-0590-457d-a0f9-6092a6d9e0e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 9cde6e63ec452161dbeb1e1bfb10c75f89e2692c
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 18%

---

# 파이프라인 변수 구성 {#configuring-pipeline-variables}

빌드 프로세스는 git 저장소에 배치하기에 부적절하거나 동일한 분기를 사용하는 파이프라인 실행 간에 달라져야 하는 특정 구성 변수에 따라 달라질 수 있습니다. Cloud Manager을 사용하면 이러한 데이터를 파이프라인 변수로 관리할 수 있습니다.

## 파이프라인 변수 {#pipeline-variables}

Cloud Manager을 사용하여 여러 가지 방법으로 파이프라인 변수를 구성할 수 있습니다.

* [Cloud Manager UI 사용](#ui)
* [Cloud Manager CLI 사용](#cli)
* [Cloud Manager API 사용](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Variables/operation/getPipelineVariables)

변수는 일반 텍스트로 저장되거나 사용하지 않을 때 암호화될 수 있습니다. 두 경우 모두 `pom.xml` 파일 또는 다른 빌드 스크립트 내에서 참조할 수 있는 환경 변수로 빌드 환경 내에서 변수를 사용할 수 있습니다.

### 파이프라인 변수 이름 지정 규칙 {#naming-conventions}

변수 이름은 다음 규칙을 준수해야 합니다.

* 변수에는 영숫자와 밑줄(`_`)만 포함될 수 있습니다.
* 이름은 모두 대문자로 해야 합니다.
* 파이프라인당 200개의 변수 제한이 있습니다.
* 각 이름은 100자 이하여야 합니다.
* 각 `string` 변수 값은 2048자 미만이어야 합니다.
* 각 `secretString` 형식 변수 값은 500자 이하여야 합니다.

## Cloud Manager 사용자 인터페이스 {#ui}

파이프라인 변수는 Cloud Manager 사용자 인터페이스를 통해 구성 및 관리할 수 있습니다. 파이프라인 변수를 추가, 편집 및 삭제하려면 파이프라인을 편집할 수 있는 권한이 있어야 합니다.

파이프라인이 실행 중인 경우 변수 관리가 차단됩니다.

### 파이프라인 변수 추가 {#add-ui}

1. [파이프라인 관리](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md)할 때 파이프라인 변수를 만들 파이프라인의 줄임표 버튼을 클릭하고 컨텍스트 메뉴에서 **변수 보기/편집**&#x200B;을 선택합니다.

   ![파이프라인 변수 보기/편집](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. **변수 구성** 창이 열립니다. 표의 첫 행에 변수 세부 정보를 입력하고 **추가**&#x200B;를 클릭합니다.

   * **구성 이름**&#x200B;은(는) 변수에 대한 고유 식별자로, [파이프라인 변수 이름 지정 규칙](#naming-conventions)을(를) 가리켜야 합니다.
   * **Value**&#x200B;은(는) 변수가 보유한 값입니다.
   * **단계 적용됨**&#x200B;은(는) 변수가 적용되는 파이프라인의 단계입니다. 필수입니다.
      * **빌드**
      * **기능 테스트**
      * **UI 테스트**
   * **Type**&#x200B;은(는) 변수가 일반 텍스트인지 또는 암호로 암호화되었는지 정의합니다.

   ![변수 추가](/help/implementing/cloud-manager/assets/pipeline-variables-add-variable.png)

1. 가 테이블에 추가됩니다. 필요에 따라 변수를 추가한 다음 **저장**&#x200B;을 탭하거나 클릭하여 파이프라인에 추가한 변수를 저장합니다.

### 파이프라인 변수 편집 {#edit-ui}

1. [파이프라인 관리](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md)할 때 파이프라인 변수를 만들 파이프라인의 줄임표 버튼을 클릭하고 컨텍스트 메뉴에서 **변수 보기/편집**&#x200B;을 선택합니다.

   ![파이프라인 변수 보기/편집](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. **변수 구성** 창이 열립니다. 편집할 변수의 줄임표 버튼을 클릭하고 **편집**&#x200B;을 선택합니다.

   ![변수 편집](/help/implementing/cloud-manager/assets/pipeline-variables-edit.png)

1. 필요에 따라 변수 값을 업데이트하고 **적용**(행 끝에 있는 확인 표시)을 클릭하여 변경 내용을 적용하거나 **취소**(뒤로 화살표)를 클릭하여 변경 내용을 되돌립니다.

   * 변수 값만 편집할 수 있습니다.

   ![변수 편집](/help/implementing/cloud-manager/assets/pipeline-variables-edit-save.png)

1. **저장**&#x200B;을 클릭합니다.

변수를 삭제하려면 **변수 구성** 창의 파이프라인 변수 줄임표 메뉴에서 **편집** 대신 **삭제**&#x200B;을(를) 선택하십시오.

## Cloud Manager CLI 사용 {#cli}

이 CLI 명령은 변수를 설정합니다.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

이 명령은 변수를 나열합니다.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Maven `pom.xml` 파일 내에서 사용할 경우, 일반적으로 다음과 유사한 구문을 사용하여 이러한 변수를 Maven 속성에 매핑하는 것이 유용합니다.

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
