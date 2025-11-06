---
title: 외부 Git 저장소를 사용하도록 Edge Delivery 사이트 구성
description: Edge Delivery 사이트를 개인 또는 엔터프라이즈 Git 저장소에 연결하는 방법에 대해 알아봅니다.
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 1dbaef34-efa3-4287-b7b1-f60db938146d
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 100%

---

# 외부 Git 저장소를 사용하도록 Edge Delivery 사이트 구성

Cloud Manager에 이미 온보딩된 모든 프라이빗 Git 저장소에서 코드를 가져오도록 Edge Delivery 사이트를 구성할 수 있습니다.

**지원되는 Git 공급업체**

| 지원 수준 | 공급업체 | 메모 |
| --- | --- | --- |
| 일반 가용성 | • GitHub Enterprise(자체 호스팅 버전)<br>• Bitbucket(클라우드 버전)<br>• GitLab(클라우드 및 자체 호스팅 버전) | 활성화 요청 없이 연결 |
| Alpha 프로그램 | Azure DevOps(클라우드 버전) | [액세스 요청](mailto:grp-cloudmanager_byog@adobe.com) |
| Beta 프로그램 | Adobe 호스팅 저장소(Cloud Manager에서 생성됨) | [액세스 요청](mailto:grp-cloudmanager_byog@adobe.com) |

**외부 Git 저장소를 사용하도록 Edge Delivery 사이트 구성하려면 다음 작업을 수행합니다.**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 외부 Git 저장소를 사용하도록 Edge Delivery 사이트를 구성할 Edge Delivery Services가 구성된 프로그램을 선택합니다.
1. 왼쪽 레일의 **프로그램** 제목 아래에서 **![개요 아이콘](/help/implementing/cloud-manager/edge-delivery/assets/overview.svg) 개요**&#x200B;를 클릭합니다.
1. **프로그램 개요** 페이지에서 **Edge Delivery** 탭을 클릭합니다.
1. **Edge Delivery 사이트** 표에서 외부 저장소를 사용하도록 구성할 사이트 행 끝에 있는 ![기타 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭한 다음 **자체 Git 가져오기**&#x200B;를 클릭합니다.
1. 자체 Git 가져오기 대화 상자의 **저장소 이름** 드롭다운 목록에서 `READY` 상태의 Git 저장소를 선택한 다음 **확인**&#x200B;을 클릭합니다.

   Cloud Manager가 일회성 시크릿 토큰을 반환합니다. 사이트를 재구성하면 Cloud Manager가 새 시크릿 토큰을 생성합니다.

1. 토큰을 복사하여 [BYO Git](https://www.aem.live/developer/byo-git) 안내서에 설명된 대로 **helix-admin**&#x200B;의 사이트 구성에 추가합니다.
1. Cloud Manager로 돌아가서 외부 저장소를 사용하도록 방금 구성한 사이트 행 끝에 있는 ![기타 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭한 다음 **코드 동기화**&#x200B;를 클릭합니다.
1. 동기화할 분기를 선택하고 **동기화**&#x200B;를 클릭합니다.

이제 모든 분기의 모든 커밋이 자동 동기화를 트리거합니다. 전체 수동 동기화가 필요한 경우 **코드 동기화**&#x200B;를 다시 사용합니다.
