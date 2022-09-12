---
title: Maven 프로젝트 버전 처리
description: AEM as a Cloud Service의 스테이징 및 프로덕션 배포를 위해 Cloud Manager는 고유한 증분 버전을 생성합니다.
exl-id: 658bcbed-0733-45da-a3e3-9a5f817099c5
source-git-commit: 21607fadf33dac038c7f794b933b92f60b8e20a9
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 3%

---


# Maven 프로젝트 버전 처리 {#maven-project-version-handling}

AEM as a Cloud Service의 스테이징 및 프로덕션 배포를 위해 Cloud Manager는 고유한 증분 버전을 생성합니다

이 버전은 [파이프라인 실행 세부 사항 페이지](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) 및 활동 페이지라고도 합니다. 빌드가 실행되면 Maven 프로젝트가 업데이트되어 이 버전을 사용할 수 있으며, 태그가 해당 버전의 이름으로 Git 리포지토리에 생성됩니다.

원래 프로젝트 버전이 특정 기준을 충족하는 경우 업데이트된 Maven 프로젝트 버전은 원래 프로젝트 버전과 Cloud Manager 생성 버전을 모두 병합합니다. 그러나 태그는 항상 생성된 버전을 사용합니다. 이러한 병합이 수행되려면 원래 프로젝트 버전을 세 개의 버전 세그먼트로 만들어야 합니다(예: `1.0.0` 또는 `1.2.3`, 하지만 아님 `1.0` 또는 `1`, 그리고 원래 버전은 `-SNAPSHOT`.

>[!IMPORTANT]
>
>이 원래 프로젝트 버전 값은 `<version>` 최상위 수준의 요소 `pom.xml` git 리포지토리 분기에 있는 파일입니다.

원래 버전이 이러한 기준을 충족한다면 생성된 버전이 원래 버전에 새 버전 세그먼트로 추가됩니다. 생성된 버전은 적절한 정렬 및 버전 처리를 포함하도록 약간 수정됩니다. 예를 들어, `2019.926.121356.0000020490` 결과는 다음과 같습니다.

| 버전 | 버전 `pom.xml` | 댓글 |
|---|---|---|
| `1.0.0` | `1.0.0.2019_0926_121356_0000020490` | 올바르게 형식화된 원래 버전 |
| `1.0.0-SNAPSHOT` | `2019.926.121356.0000020490` | 스냅샷 버전, 덮어쓰기 |
| `1` | `2019.926.121356.0000020490` | 불완전한 버전, 덮어쓰기 |

>[!NOTE]
>
>원래 버전이 Cloud Manager 초기화 버전에 통합되었는지 여부에 관계없이 원래 버전은 이름의 Maven 속성으로 사용할 수 있습니다 `cloudManagerOriginalVersion`.
