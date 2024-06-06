---
title: 개인 저장소에 대한 GitHub 구성 확인
description: 개인 저장소에 대한 각 끌어오기 요청의 유효성을 검사하기 위해 자동으로 생성되는 파이프라인을 제어하는 방법에 대해 알아봅니다.
source-git-commit: 73bd693d47f37b453209208816dfed15d65e9e09
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 7%

---


# 개인 저장소에 대한 GitHub 구성 확인 {#github-check-config}

개인 저장소에 대한 각 끌어오기 요청의 유효성을 검사하기 위해 자동으로 생성되는 파이프라인을 제어하는 방법에 대해 알아봅니다.

## GitHub 검사 구성 {#configuration}

사용 시 [개인 저장소,](private-repositories.md#using) a [전체 스택 코드 품질 파이프라인](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) 이(가) 자동으로 만들어집니다. 이 파이프라인은 가져오기 요청이 업데이트될 때마다 시작됩니다.

다음을 만들어 이러한 검사를 제어할 수 있습니다. `.cloudmanager/pr_pipelines.yml` 개인 저장소의 기본 분기에 있는 파일입니다.

```yaml
github:
  shouldDeletePreviousComment: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR 
    importantMetricsFailureBehavior: CONTINUE
```

| 매개변수 | 가능한 값 | 기본값 | 설명 |
|---|---|---|---|
| `shouldDeletePreviousComment` | `true` 또는 `false` | `false` | 자신의 github 가져오기 요청에 대한 코드 스캔 결과와 함께 마지막 주석만 유지할지 아니면 모두 유지할지 여부 |
| `type` | `CI_CD` | 해당 사항 없음 | CI/CD 파이프라인 동작 정의 |
| `template.programID` | 정수 | 파이프라인 변수가 재사용되지 않음 | 를 재사용하는 데 사용할 수 있습니다. [파이프라인 변수](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) 각 PR에 의해 자동으로 만들어지는 기존 파이프라인 중 하나에 설정됩니다. |
| `template.pipelineID` | 정수 | 파이프라인 변수가 재사용되지 않음 | 를 재사용하는 데 사용할 수 있습니다. [파이프라인 변수](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) 각 PR에 의해 자동으로 만들어지는 기존 파이프라인 중 하나에 설정됩니다. |
| `namePrefix` | 문자열 | `Full Stack Code Quality Pipeline for PR` | 자동으로 생성되는 파이프라인의 이름을 설정하는 데 사용됩니다. |
| `importantMetricsFailureBehavior` | `CONTINUE` 또는 `FAIL` 또는 `PAUSE` | `CONTINUE` | 파이프라인의 중요한 지표 동작을 설정합니다<br>`CONTINUE` = 중요한 지표가 실패하면 파이프라인이 자동으로 앞으로 이동합니다.<br>`FAIL` = 중요한 지표가 실패하면 파이프라인이 실패 상태로 완료됩니다<br>`PAUSE` = 코드 스캔 단계는 중요한 지표가 실패하면 WAITING 상태를 받게 되며 수동으로 다시 시작해야 합니다 |
