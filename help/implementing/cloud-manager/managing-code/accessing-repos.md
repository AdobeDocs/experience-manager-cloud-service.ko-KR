---
title: 저장소에 액세스
description: Cloud Manager의 셀프 서비스 git 계정 관리를 사용하여 Git 리포지토리에 액세스하고 관리하는 방법을 알아봅니다.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
source-git-commit: 4729574eb31e01077f0d2a35efcef6d134f6aa5c
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 2%

---

# 저장소에 액세스 {#accessing-repos}

Cloud Manager의 셀프 서비스 git 계정 관리를 사용하여 Git 리포지토리에 액세스하고 관리하는 방법을 알아봅니다.

## 셀프 서비스 저장소 계정 관리 사용 {#self-service-repos}

Cloud Manager를 사용하면 **보고서 정보에 액세스** 파이프라인 카드에서 눈에 띄게 사용 가능한 단추.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 다음으로 이동 **파이프라인** 카드 **프로그램 개요** 페이지를 열고 **보고서 정보에 액세스** git 리포지토리에 액세스하고 관리하는 단추.

   ![환경 카드에서 보고서 정보 액세스 단추](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. 을(를) 클릭합니다. **보고서 정보 보기** 보려는 대화 상자를 여는 단추:

   * Cloud Manager git 저장소의 URL입니다.
   * Git 사용자 이름.
   * Git 암호이며, **암호 생성** 버튼을 클릭합니다.

   ![](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

이러한 자격 증명을 사용하여 사용자는 리포지토리의 로컬 복사본을 복제하고 해당 로컬 리포지토리를 변경할 수 있으며, 준비가 되면 모든 코드 변경 내용을 Cloud Manager의 원격 코드 리포지토리에 다시 적용할 수 있습니다.

다음 **보고서 정보에 액세스** 옵션을 사용할 수도 있습니다 **비프로덕션** 의 파이프라인 탭 **파이프라인** 카드.

![비프로덕션 탭의 보고서 정보 액세스 단추](/help/implementing/cloud-manager/assets/repos/access-repo-nonprod.png)

>[!NOTE]
>
>다음 **보고서 정보에 액세스** 옵션이 **개발자** 또는 **배포 관리자** 역할.
