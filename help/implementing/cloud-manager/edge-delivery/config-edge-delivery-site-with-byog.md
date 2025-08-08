---
title: 외부 Git 저장소를 사용하도록 Edge Delivery 사이트 구성
description: Edge Delivery 사이트를 개인 또는 엔터프라이즈 Git 저장소에 연결하는 방법을 알아봅니다.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 62134c5b67d610f801c407e696e761ed05e02c87
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 7%

---


# 외부 Git 저장소를 사용하도록 Edge Delivery 사이트 구성

Cloud Manager에 이미 온보딩된 개인 Git 저장소에서 코드를 가져오도록 Edge Delivery 사이트를 구성할 수 있습니다.

**지원되는 Git 공급업체**

| 지원 수준 | 공급업체 | 메모 |
| --- | --- | --- |
| 일반 출시 | · GitHub Enterprise(자체 호스팅 버전)<br>· Bitbucket(클라우드 버전)<br>· GitLab(클라우드 및 자체 호스팅 버전) | 지원 요청 없이 연결 |
| Alpha 프로그램 | Azure DevOps(클라우드 버전) | [액세스 요청](mailto:grp-cloudmanager_byog@adobe.com) |
| Beta 프로그램 | Adobe에서 호스팅하는 저장소(Cloud Manager에서 만들어짐) | [액세스 요청](mailto:grp-cloudmanager_byog@adobe.com) |

**외부 Git 저장소를 사용하도록 Edge Delivery 사이트를 구성하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 Edge Delivery Services이 구성된 프로그램을 선택합니다. 여기에서 외부 Git 저장소를 사용하도록 Edge Delivery 사이트를 구성할 수 있습니다.
1. 왼쪽 레일의 **프로그램** 제목 아래에서 **![개요 아이콘](/help/implementing/cloud-manager/edge-delivery/assets/overview.svg) 개요**&#x200B;를 클릭합니다.
1. **프로그램 개요** 페이지에서 **Edge Delivery** 탭을 클릭합니다.
1. **Edge Delivery 사이트** 표에서 외부 리포지토리를 사용하도록 사이트를 구성할 행 끝에 있는 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭한 다음 **고유한 Git 가져오기**&#x200B;를 클릭합니다.
1. Git 가져오기 대화 상자의 **저장소 이름** 드롭다운 목록에서 `READY` 상태의 Git 저장소를 선택한 다음 **확인**&#x200B;을 클릭합니다.

   Cloud Manager이 1회 비밀 토큰을 반환합니다. 사이트를 다시 구성하면 Cloud Manager에서 새 암호 토큰을 생성합니다.

1. **BYO Git 안내서**&#x200B;에 설명된 대로 토큰을 복사하고 [helix-admin](https://www.aem.live/developer/byo-git)에서 사이트 구성을 추가하십시오.
1. Cloud Manager으로 돌아가서 외부 리포지토리를 사용하도록 방금 구성한 사이트의 행 끝에 있는 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭한 다음 **코드 동기화**&#x200B;를 클릭합니다.
1. 동기화할 분기를 선택하고 **동기화**&#x200B;를 클릭합니다.

이제 모든 분기의 각 커밋은 자동 동기화를 트리거합니다. 전체 수동 동기화가 필요할 때마다 **동기화 코드**&#x200B;를 다시 사용하십시오.
