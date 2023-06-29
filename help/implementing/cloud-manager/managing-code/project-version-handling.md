---
title: Maven 프로젝트 버전 처리
description: AEM as a Cloud Service의 스테이지 및 프로덕션 배포의 경우 Cloud Manager는 고유한 증분 버전을 생성합니다.
exl-id: 658bcbed-0733-45da-a3e3-9a5f817099c5
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 94%

---


# Maven 프로젝트 버전 처리 {#maven-project-version-handling}

AEM as a Cloud Service의 스테이지 및 프로덕션 배포의 경우 Cloud Manager는 고유한 증분 버전을 생성합니다.

이 버전은 다음에 표시됩니다. [파이프라인 실행 세부 정보 페이지](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) 및 활동 페이지를 참조하십시오. 빌드가 실행되면 이 버전을 사용하도록 Maven 프로젝트가 업데이트되고 해당 버전을 이름으로 하는 태그가 git 저장소에 생성됩니다.

원본 프로젝트 버전이 특정 기준을 충족하면 업데이트된 Maven 프로젝트 버전이 원본 프로젝트 버전과 Cloud Manager 생성 버전을 모두 병합합니다. 그러나 태그는 항상 생성된 버전을 사용합니다. 이 병합이 발생하려면 원본 프로젝트 버전은 `1.0` 또는 `1`이 아닌 `1.0.0` 또는 `1.2.3`과 같은 정확히 세 개의 버전 세그먼트로 형성되어야 하며 원본 버전은 `-SNAPSHOT`로 끝나서는 안 됩니다.

>[!IMPORTANT]
>
>이 원본 프로젝트 버전 값은 git 저장소 분기에 있는 최상위 `pom.xml` 파일의 `<version>` 요소에 정적으로 설정해야 합니다.

원본 버전이 이러한 기준을 충족하면 생성된 버전이 새 버전 세그먼트로 원본 버전에 추가됩니다. 생성된 버전은 적절한 정렬 및 버전 처리를 포함하도록 약간 수정됩니다. 예를 들어 생성된 버전 `2019.926.121356.0000020490`의 결과는 다음과 같다고 가정합니다.

| 버전 | `pom.xml`의 버전 | 설명 |
|---|---|---|
| `1.0.0` | `1.0.0.2019_0926_121356_0000020490` | 적절히 구성된 원본 버전 |
| `1.0.0-SNAPSHOT` | `2019.926.121356.0000020490` | 스냅샷 버전, 덮어씀 |
| `1` | `2019.926.121356.0000020490` | 불완전한 버전, 덮어씀 |

>[!NOTE]
>
>원래 버전이 Cloud Manager 초기화 버전에 통합되었는지 여부와 상관없이 원래 버전은 `cloudManagerOriginalVersion`이라는 이름의 Maven 속성으로 사용할 수 있습니다.
