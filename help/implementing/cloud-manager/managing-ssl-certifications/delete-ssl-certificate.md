---
title: SSL 인증서 삭제 - SSL 인증서 관리
description: SSL 인증서 삭제 - SSL 인증서 관리
exl-id: 43f66871-cca4-4709-95d0-68aa715c0da2
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# SSL 인증서 삭제 {#deleting-an-ssl-certificate}

>[!IMPORTANT]
>Cloud Manager에서 인증서를 제거하는 것은 실행을 취소할 수 없는 영구 작업입니다. 가장 좋은 방법은 Cloud Manager 사용자 인터페이스에서 필요한 SSL 파일을 삭제하기 전에 로컬에 저장하는 것입니다.

Cloud Manager에서 SSL 인증서를 삭제하려면 비즈니스 소유자 또는 배포 관리자 역할에 있어야 합니다. Cloud Manager에서는 연결된 도메인이 하나 이상 있는 SSL 인증서를 삭제할 수 없습니다.  연관된 모든 도메인은 SSL 인증서를 삭제하기 전에 삭제해야 합니다. 을(를) 참조하십시오. [사용자 지정 도메인 이름 삭제](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md) 추가 정보

SSL 인증서를 삭제하려면 아래 절차를 따르십시오.

1. 로 이동합니다 **SSL 인증서** 화면 **환경** 페이지.
   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)
1. 삭제할 SSL 인증서 이름이 나열된 행을 식별합니다.
1. 을(를) 선택합니다 **...** 메뉴의 맨 오른쪽 끝
1. 선택 **삭제**.
   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-delete01.png)
1. 에서 제출 확인 **SSL 인증서 삭제** 대화 상자
