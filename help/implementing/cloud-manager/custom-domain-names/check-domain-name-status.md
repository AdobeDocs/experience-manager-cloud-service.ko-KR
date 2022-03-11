---
title: 도메인 이름 상태 확인
description: 도메인 이름 상태 확인
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
source-git-commit: 4533cbc689d69cbe126791b4426123f890754507
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# 도메인 이름 상태 확인 {#check-status}

도메인 설정 페이지의 환경 테이블에서 도메인 이름에 대한 상태 아이콘을 클릭하여 도메인 이름이 성공적으로 확인되었는지 여부를 확인할 수 있습니다.

>[!NOTE]
>사용자 지정 도메인 추가 마법사의 확인 단계에서 저장 을 선택하면 Cloud Manager가 TXT 확인을 자동으로 트리거합니다. 이후 확인의 경우 **다시 확인** 아이콘 옆에 표시됩니다.

Cloud Manager는 TXT 값을 통해 도메인 소유권을 확인하고 다음 상태 메시지 중 하나를 표시합니다.

* **도메인 확인 실패**
TXT 값이 없거나 오류와 함께 감지되었습니다. 지침을 따르고 다시 시도하십시오. 준비가 완료된 경우 
*다시 확인* 아이콘 옆에 표시됩니다.

* **도메인 확인 진행 중**
확인 중입니다. 이 상태는 일반적으로 
*다시 확인* 아이콘 옆에 표시됩니다.

* **확인됨, 배포 실패**
TXT 확인을 완료했습니다. 그러나 CDN 배포가 실패했습니다. Adobe 담당자에게 문의하십시오.

* **도메인 확인 및 배포**
이 상태는 사용자 지정 도메인 이름을 사용할 준비가 되었음을 나타냅니다.
   >[!NOTE]
   >이때 사용자 지정 도메인 이름이 테스트되고 Cloud Manager 도메인 이름을 가리킬 준비가 되었습니다. 을(를) 참조하십시오. [DNS 설정 구성](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) 추가 정보

* **삭제**
사용자 지정 도메인 이름을 삭제하는 중입니다.

* **삭제 실패**
사용자 지정 도메인 이름을 삭제하지 못했습니다. 다시 시도해야 합니다. 을(를) 참조하십시오. [사용자 지정 도메인 이름 삭제](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md) 추가 정보


## 사용자 지정 도메인 이름에 대한 기존 CDN 구성 {#pre-existing-cdn}

IP 허용 목록, SSL 인증서 또는 사용자 지정 도메인 이름에 대한 기존 CDN 구성을 포함하는 환경을 사용하는 고객은 **IP 허용 목록** 그리고 **환경** 세부 사항 페이지. 고객이 UI를 통해 기존 환경 구성을 모두 마이그레이션한 후 UI에 표시되는 메시지는 사라지며, 메시지가 사라지려면 영업일 기준으로 1~2일이 걸릴 수 있습니다.

>[!NOTE]
>기존 구성을 보고 관리하려면 UI를 통해 구성을 추가해야 합니다. 을(를) 참조하십시오. [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) 자세한 내용

![](/help/implementing/cloud-manager/assets/ip-allow-list-message1.png)

![](/help/implementing/cloud-manager/assets/ip-allow-list-message2.png)
