---
title: GitHub 검사 주석
description: GitHub가 비공개 저장소에 대한 주석 PR을 검사하여 유용한 피드백을 제공하는 방법을 알아봅니다.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 100%

---


# GitHub 검사 주석 {#github-annotations}

GitHub가 비공개 저장소에 대한 주석 PR을 검사하여 유용한 피드백을 제공하는 방법을 알아봅니다.

## 개요 {#overview}

Cloud Manager 프로그램에 [비공개 저장소](private-repositories.md)를 사용하는 경우 모든 가져오기 요청에 대해 GitHub의 검사가 자동으로 실행됩니다. 코드 관련 문제를 가능한 한 빨리 이해하는 데 도움이 되는 유용한 정보가 주석으로 추가되어 있습니다.

![GitHub 검사 주석의 예](assets/github-check-annotations.png)

[SonarQube](/help/implementing/cloud-manager/custom-code-quality-rules.md)에서 감지된 [코드 품질](/help/implementing/cloud-manager/code-quality-testing.md) 문제가 명확하게 나열되어 있습니다.

![코드 문제 주석의 예](assets/github-check-annotations-example.png)

문제가 있는 정확한 코드 행이 제공되며 해당 코드를 클릭하면 관련 코드가 표시됩니다. 이러한 주석은 가져오기 요청에서 변경된 것뿐만 아니라 모든 코드 문제에 대해 제공됩니다.

![코드 문제 주석의 예](assets/github-check-annotations-example-code.png)

주석이 달린 모든 행은 GitHub 가져오기 요청의 **변경된 파일** 탭에 집계됩니다. 가져오기 요청에서 변경되지 않은 파일에 대한 주석이 해당 섹션에 나타납니다.

![변경된 파일 탭 주석의 예](assets/github-check-annotations-files-changed.png)

## 코드 품질 파이프라인 {#code-quality-pipelines}

[코드 품질](/help/implementing/cloud-manager/code-quality-testing.md) 결과는 **검사** 탭 하단에서 Cloud Manager가 자동으로 트리거하는 파이프라인에서도 볼 수 있습니다. 또한 가져오기 요청 검사의 **세부 사항**&#x200B;에서도 액세스할 수 있습니다.

![주석의 예](assets/github-check-annotations-code-quality.png)

![주석의 예](assets/github-check-annotations-code-quality-2.png)

문제를 CSV 형식으로 시각화할 수도 있습니다. 이는 [Cloud Manager에서 파이프라인 실행에 대한 세부 정보 보기](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details)로 검색할 수 있습니다.
