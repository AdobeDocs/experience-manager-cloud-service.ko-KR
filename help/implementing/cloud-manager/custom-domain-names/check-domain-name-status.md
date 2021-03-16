---
title: 도메인 이름 상태 확인
description: 도메인 이름 상태 확인
translation-type: tm+mt
source-git-commit: dbf64ec2b4b7e5c549ef5942b1c7bd0ca75eb66f
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# 도메인 이름 상태 확인 중 {#check-status}

[도메인 설정] 페이지의 [환경]에 있는 테이블에서 도메인 이름에 대한 상태 아이콘을 클릭하여 도메인 이름이 성공적으로 확인되었는지 여부를 확인할 수 있습니다.

>[!NOTE]
>사용자 지정 도메인 추가 마법사의 확인 단계에서 저장을 선택하면 Cloud Manager에서 TXT 확인을 자동으로 트리거합니다. 후속 확인을 위해 상태 옆에 있는 **다시 확인** 아이콘을 적극적으로 선택해야 합니다.

Cloud Manager는 TXT 값을 통해 도메인 소유권을 확인하고 다음 상태 메시지 중 하나를 표시합니다.

* **도메인 확인**
FailedTXT 값이 없거나 오류가 발생했습니다. 지침을 따라 다시 시도하십시오. 준비가 되면 
*상태* 옆에 있는 아이콘을 다시 확인하십시오.

* **도메인 확인 진행**
중 확인 진행 중 이 상태는 일반적으로 
*상태* 옆에 있는 아이콘을 다시 확인하십시오.

* **확인된 배포**
FailedTXT 확인이 성공했습니다. 그러나 CDN 배포는 실패했습니다. Adobe 담당자가 자동으로 알림을 받게 됩니다.

* **도메인 확인됨 및**
배포됨 이 상태는 사용자 지정 도메인 이름을 사용할 준비가 되었음을 나타냅니다.
   >[!NOTE]
   >이때 사용자 지정 도메인 이름은 테스트할 준비가 되었으며 Cloud Manager 도메인 이름을 가리키게 됩니다. 자세한 내용은 [DNS 설정 구성](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md)을 참조하십시오.

* **사용자**
지정 도메인 이름의 삭제를 진행 중입니다.

* **사용자**
지정 도메인 이름을 삭제하지 못했습니다. 다시 시도해야 합니다. 자세한 내용은 [사용자 지정 도메인 이름](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md) 삭제를 참조하십시오.


## IP 허용 목록 {#pre-existing-cdn}에 대한 기존 CDN 구성

IP 허용 목록, SSL 인증서 또는 사용자 정의 도메인 이름에 대한 기존 CDN 구성을 포함하는 환경을 보유한 고객은 **IP 허용 목록** 및 **환경** 세부 정보 페이지에 다음 메시지를 보게 됩니다. 고객이 UI를 통해 기존의 모든 환경 구성을 완전히 마이그레이션한 후 UI에 표시되는 메시지는 사라지고 메시지가 사라지는 데 영업일 기준 1-2일이 걸릴 수 있습니다.

>[!NOTE]
>기존 구성을 보고 관리하려면 UI를 통해 해당 구성을 추가해야 합니다. 자세한 내용은 [사용자 지정 도메인 이름](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) 추가를 참조하십시오.

![](/help/implementing/cloud-manager/assets/ip-allow-list-1.png)

![](/help/implementing/cloud-manager/assets/ip-allow-list-2.png)
