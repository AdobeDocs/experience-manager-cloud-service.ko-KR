---
title: Maven 프로젝트 버전 처리
description: Maven 프로젝트 버전 처리 - Cloud Services
translation-type: tm+mt
source-git-commit: cedc14b0d71431988238d6cb4256936a5ceb759b
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 6%

---


# Maven 프로젝트 버전 처리 {#maven-project-version-handling}


## Understanding Maven Project Version Handling {#understanding-project-version}

스테이지 및 프로덕션 배포의 경우 Cloud Manager는 고유한 증가된 버전을 생성합니다.

이 버전은 활동 페이지뿐만 아니라 파이프라인 실행 세부 정보 페이지에서 확인할 수 있습니다. 빌드가 실행되면 Maven 프로젝트가 업데이트되어 이 버전을 사용할 수 있으며 해당 버전을 이름으로 갖는 태그가 git 리포지토리에 생성됩니다.

원래 프로젝트 버전이 특정 기준을 충족하는 경우 업데이트된 Maven 프로젝트 버전은 원본 프로젝트 버전과 Cloud Manager에서 생성된 버전을 모두 병합합니다. 하지만 태그는 항상 생성된 버전을 사용합니다. 이 병합이 이루어지려면 원래 프로젝트 버전은 세 개의 버전 세그먼트로 구성되어야 합니다(예: 1.0.0 또는 1.2.3, 1.0 또는 1 제외). 그리고 원래 버전은 -SNAPSHOT으로 종료되어서는 안 됩니다.

원본 버전이 이 기준을 충족하면 생성된 버전이 새 버전 세그먼트로 원본 버전에 추가됩니다. 생성된 버전은 적절한 정렬 및 버전 처리를 포함하도록 약간 수정됩니다. 예를 들어 2019.926.121356.0000020490의 생성된 버전을 가정할 경우:

| **버전** | **pom.xml 버전** | **주석** |
|---|---|---|
| 1.0.0 | 1.0.0.2019_0926_121356_0000020490 | 원래 버전 형식 제대로 지정 |
| 1.0.0-스냅샷 | 2019.926.121356.0000020490 | 스냅샷 버전, 덮어쓰기 |
| 1 | 2019.926.121356.0000020490 | 불완전한 버전, 덮어쓰기 |

>[!NOTE]
>
>원본 버전이 Cloud Manager가 초기화한 버전에 포함되었는지 여부에 관계없이 원래 버전은 *cloudManagerOriginalVersion이라는 이름의 Maven 속성으로 사용할 수 있습니다.*
