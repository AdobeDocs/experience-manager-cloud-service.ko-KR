---
title: 소스 코드 저장소 - 클라우드 서비스
description: 소스 코드 저장소 - 클라우드 서비스
translation-type: tm+mt
source-git-commit: 114bc678fc1c6e3570d6d2a29bc034feb68aa56d

---


# 소스 코드 저장소 {#source-code-repository}

Cloud Manager 프로그램은 자체 git 리포지토리로 자동 프로비저닝됩니다.

사용자가 Cloud Manager git 리포지토리에 액세스하려면 명령줄 도구, 독립 실행형 시각적 Git 클라이언트 또는 Eclipse, IntelliJ, NetBeans와 같은 사용자의 IDE가 포함된 Git 클라이언트를 사용해야 합니다.

Git 클라이언트가 설정되면 Cloud Manager UI에서 Git 리포지토리를 관리할 수 있습니다. Cloud Manager UI를 사용하여 Git을 관리하는 방법에 대한 자세한 내용은 Git 액세스를 [참조하십시오](/help/implementing/cloud-manager/accessing-git.md).

AEM Cloud 응용 프로그램 개발을 시작하려면, Cloud Manager 리포지토리에서 해당 리포지토리를 만들 로컬 컴퓨터의 위치로 응용 프로그램 코드의 로컬 복사본을 체크 아웃하여 해당 로컬 복사본을 만들어야 합니다.

```java
$ git clone {URL}
```

>[!NOTE]
>
> 사용자는 자신의 코드 사본을 체크 아웃하고 로컬 코드 리포지토리에서 변경할 수 있습니다. 준비가 되면 사용자는 코드 변경 내용을 Cloud Manager의 원격 코드 저장소로 다시 커밋할 수 있습니다.
