---
title: 소스 코드 저장소 - Cloud Services
description: 소스 코드 저장소 - Cloud Services
source-git-commit: 23349f3350631f61f80b54b69104e5a19841272f
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 1%

---


# 소스 코드 저장소 {#source-code-repository}

Cloud Manager 프로그램은 자체 git 리포지토리를 사용하여 자동으로 제공됩니다.

사용자가 Cloud Manager git 리포지토리에 액세스하려면 명령줄 도구, 독립 실행형 시각적 Git 클라이언트 또는 Eclipse, IntelliJ, NetBeans와 같은 사용자의 IDE가 있는 Git 클라이언트를 사용해야 합니다.

Git 클라이언트가 설정되면 Cloud Manager UI에서 Git 리포지토리를 관리할 수 있습니다. Cloud Manager UI를 사용하여 Git을 관리하는 방법에 대한 자세한 내용은 [Git](/help/implementing/cloud-manager/accessing-git.md)액세스 를 참조하십시오.

AEM Cloud 애플리케이션 개발을 시작하려면 Cloud Manager 리포지토리에서 리포지토리를 생성하려는 로컬 컴퓨터의 위치로 애플리케이션 코드의 로컬 복사본을 체크 아웃해야 합니다.

```java
$ git clone {URL}
```

>[!NOTE]
>
>사용자는 코드 사본을 체크 아웃하고 로컬 코드 리포지토리에서 변경 작업을 수행할 수 있습니다. 준비가 완료된 사용자는 코드 변경 사항을 Cloud Manager의 원격 코드 리포지토리에 다시 커밋할 수 있습니다.
