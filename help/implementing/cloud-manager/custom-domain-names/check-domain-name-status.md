---
title: 도메인 이름 상태 확인
description: 도메인 이름 상태 확인
translation-type: tm+mt
source-git-commit: f11cb3b56f51046779300626d1deb037dd687309
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---


# 도메인 이름 상태 확인 중 {#check-status}

도메인 설정 페이지의 환경 테이블에서 도메인 이름에 대한 상태 아이콘을 클릭하여 도메인 이름을 성공적으로 확인했는지 여부를 확인할 수 있습니다.

>[!NOTE]
>사용자 지정 도메인 추가 마법사의 확인 단계에서 저장을 선택하면 Cloud Manager에서 TXT 확인을 자동으로 트리거합니다. 이후 확인을 위해 상태 옆에 있는 **확인** 아이콘을 다시 선택해야 합니다.

클라우드 관리자는 TXT 값을 통해 도메인 소유권을 확인하고 다음 상태 메시지 중 하나를 표시합니다.

* **도메인 확인**
실패 TXT 값이 없거나 오류가 있는 것이 감지되었습니다. 지침에 따라 다시 시도하십시오. 준비가 되면 
*상태 옆에 있는* 다시 확인 아이콘.

* **도메인 확인 진행**
중입니다. 확인 중입니다. 이 상태는 일반적으로 
*상태 옆에 있는* 다시 확인 아이콘.

* **확인된 배포**
FailedTXT 확인이 성공했습니다. 하지만 CDN 배포가 실패했습니다. Adobe 담당자가 자동으로 통보를 받게 됩니다.

* **도메인 확인 및**
배포됨 이 상태는 사용자 지정 도메인 이름을 사용할 준비가 되었음을 나타냅니다.
   >[!NOTE]
   >이때 사용자 지정 도메인 이름은 테스트할 준비가 되었으며 Cloud Manager 도메인 이름을 가리키게 됩니다. 자세한 내용은 [DNS 설정 구성](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md)을 참조하십시오.

* **사용자**
지정 도메인 이름의 삭제를 진행 중입니다.

* **사용자**
지정 도메인 이름을 삭제하지 못했습니다. 다시 시도해야 합니다. 자세한 내용은 [사용자 지정 도메인 이름](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md) 삭제를 참조하십시오.

