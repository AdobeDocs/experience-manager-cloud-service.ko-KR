---
title: 양식 생성 오류를 해결하는 방법
description: AEM Forms as a Cloud Service 환경에서 양식 생성 문제 해결.
feature: Adaptive Forms
role: User
exl-id: 169ea727-0941-4a1d-bc33-d9fe208b27ab
source-git-commit: 0b693cb51a96011235fa87a5899426c6b0c2509a
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# 양식 게시 중 문제{#form-creation-fails}

사용자가 AEM Forms as a Cloud Service 버전 `2024.5.16461`으로 업데이트한 후:

**일부 사용자**&#x200B;는 양식을 만드는 동안 문제가 발생할 수 있습니다. 사용자가 양식을 만들 때 만들기 대화 상자에 다음 오류 메시지가 표시되는 문제가 있습니다.

`A server error occurred. Try again after sometime.`

## 원인 {#cause-form-creation-fails}

작성자가 **먼저 서식 파일을 게시**&#x200B;하지 않고 양식을 게시하기 때문에 문제가 발생합니다. 이렇게 하면 `jcr:uuid` 및 다른 보호 및 시스템 생성 속성이 `<template-path>/initial/jcr:content` 노드에 추가되어 후속 양식 만들기에 오류가 발생합니다.

## 해결 방법 {#resolution-form-creation-fails}

이 문제를 해결하려면 다음 단계를 수행하십시오.

1. 양식에서 사용하는 템플릿에 `<template-path>/initial/jcr:content node` 경로에 `jcr:uuid` 및 다른 시스템에서 생성한 보호된 속성이 없는지 확인합니다.
1. 템플릿 콘솔을 사용하여 템플릿을 명시적으로 Publish 합니다.
1. 이제 템플릿이 게시되면 템플릿을 사용하여 새 양식을 만들어 보십시오.
1. 사용한 템플릿이 향후 릴리스에서 업데이트되는 경우 양식 작성 실패 문제를 방지하기 위해 템플릿을 다시 Publish(2단계에서 설명)합니다.


<!--

# Issue {#form-creation-fails}

After updating to AEM Forms as a Cloud Service version `2024.5.16461.20240524T172309Z`, When a user publishes a form using an unpublished template, it fails to create a form and shows an error:

`Property is protected: jcr:uuid = 09e0d6be-f619-4405-b021-27eb1c5326d3`

## Solution {#troubleshoot-form-creation-fails}

To resolve the issue, perform the following workaround steps:

1. Publish the template explicitly using the template console.
    
    >[!NOTE]
    > Prior to this step ensure that the (unpublished) template does not have `jcr:uuid` and other system generated properties under the initial content's `jcr:content node`. To sort out it, first, sanitize the template to publish it explicitly.

    >[!NOTE]
    > This action doesn't replicate the initial content node.
1. Now, when your template is published, try creating new forms using the template.
1. If the template is changed in the future, publish it again as mentioned in the step 1.

-->
