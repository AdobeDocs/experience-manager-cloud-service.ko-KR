---
title: SSL 인증서 삭제 - SSL 인증서 관리
description: SSL 인증서 삭제 - SSL 인증서 관리
translation-type: tm+mt
source-git-commit: 99eb33c3c42094f787d853871aee3a3607856316
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# SSL 인증서 {#deleting-an-ssl-certificate} 삭제

>[!IMPORTANT]
>Cloud Manager에서 인증서를 제거하는 작업은 실행 취소할 수 없는 영구 작업입니다. Cloud Manager 사용자 인터페이스에서 필수 SSL 파일을 삭제하기 전에 로컬에 저장하는 것이 좋습니다.

클라우드 관리자에서 SSL 인증서를 삭제하려면 사용자가 비즈니스 소유자 또는 배포 관리자 역할에 있어야 합니다. 클라우드 관리자는 이와 연결된 도메인이 하나 이상 있는 SSL 인증서를 삭제할 수 없습니다.  SSL 인증서를 삭제하려면 먼저 관련 도메인을 모두 삭제해야 합니다. 자세한 내용은 [사용자 지정 도메인 이름](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md) 삭제를 참조하십시오.

SSL 인증서를 삭제하려면 아래 절차를 따르십시오.

1. **환경** 페이지에서 **SSL 인증서** 화면으로 이동합니다.
   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-3.png)
1. 삭제할 SSL 인증서 이름이 나열되는 행을 확인합니다.
1. **선택...행의 맨 오른쪽 끝에 있는** 메뉴
1. **삭제**를 선택합니다.
   ![](/help/implementing/cloud-manager/assets/ssl/ssl-cert-delete01.png)
1. **SSL 인증서 삭제** 대화 상자에서 제출을 확인합니다.
