---
title: 저장소 액세스
description: Cloud Manager의 셀프서비스 git 계정 관리를 사용하여 git 저장소에 액세스하고 관리하는 방법을 알아봅니다.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
source-git-commit: 9ec45753f56d0576e75f148ca0165c0ccd621f23
workflow-type: ht
source-wordcount: '232'
ht-degree: 100%

---

# 저장소 액세스 {#accessing-repos}

Cloud Manager의 셀프서비스 git 계정 관리를 사용하여 git 저장소에 액세스하고 관리하는 방법을 알아봅니다.

## 셀프서비스 저장소 계정 관리 사용 {#self-service-repos}

Cloud Manager를 사용하면 파이프라인 카드에 있는 **저장소 정보 액세스** 버튼을 사용하여 저장소 정보를 쉽게 검색할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **프로그램 개요** 페이지에서 **파이프라인** 카드로 이동한 다음 **저장소 정보 액세스** 버튼을 찾아 git 저장소에 액세스하고 관리합니다.

   ![환경 카드의 저장소 정보 액세스 버튼](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. **저장소 정보 보기** 버튼을 클릭하여 다음 정보가 표시되는 대화 상자를 엽니다.

   * Cloud Manager git 저장소의 URL
   * git 사용자 이름
   * git 암호. 이 값은 **암호 생성** 버튼을 클릭할 때 표시됩니다.

   ![저장소 정보 보기](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

사용자는 이러한 자격 증명을 사용하여 저장소의 로컬 복사본을 복제하고 해당 로컬 저장소를 변경할 수 있으며 준비가 되면 Cloud Manager의 원격 코드 저장소에 코드 변경 사항을 다시 커밋할 수 있습니다.

**저장소 정보 액세스** 옵션은 **파이프라인** 카드의 **비프로덕션** 파이프라인 탭에서도 사용할 수 있습니다.

![비프로덕션 탭의 저장소 정보 액세스 버튼](/help/implementing/cloud-manager/assets/repos/access-repo-nonprod.png)

>[!NOTE]
>
>**저장소 정보 액세스** 옵션은 **개발자** 또는 **배포 관리자** 역할이 있는 사용자에게 표시됩니다.
