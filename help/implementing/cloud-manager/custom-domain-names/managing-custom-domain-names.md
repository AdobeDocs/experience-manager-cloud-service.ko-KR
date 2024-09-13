---
title: 사용자 정의 도메인 이름 관리
description: Cloud Manager를 사용하여 사용자 정의 도메인 이름을 보고, 업데이트하고, 바꾸고, 삭제하는 방법을 알아봅니다.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b222b4384b1c2a21ecbb244d149ce7e51cc7990f
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 60%

---


# 사용자 정의 도메인 이름 관리 {#managing-custom-domain-names}

Cloud Manager를 사용하여 사용자 정의 도메인 이름을 보고, 업데이트하고, 바꾸고, 삭제할 수 있습니다.

## 사용자 정의 도메인 이름 보기 및 업데이트 {#view-and-update}

**보기 및 업데이트** 메뉴를 사용하여 사용자 정의 도메인 이름의 세부 정보를 볼 수 있습니다.

**사용자 지정 도메인 이름을 보고 업데이트하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. **개요** 페이지에서 **환경** 화면으로 이동합니다.

1. 보거나 업데이트할 사용자 정의 도메인 이름의 행을 식별합니다.

1. 행의 오른쪽 끝에 있는 줄임표 버튼을 클릭합니다.

1. **보기 및 업데이트** 옵션을 선택합니다.

## 사용자 정의 도메인 이름의 SSL 인증서 업데이트 {#update-cert}

[동일한 단계에 따라 사용자 정의 도메인 이름을 보고 업데이트](#view-and-update)하여 사용자 정의 도메인 이름의 SSL 인증서를 업데이트할 수 있습니다.

>[!NOTE]
>
>SSL 인증서는 유효하고 [이미 구성됨](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md)이어야 하며 업데이트하려는 사용자 지정 도메인 이름을 포함해야 합니다.

## 사용자 정의 도메인 이름 삭제 {#deleting}

**비즈니스 소유자** 또는 **배포 관리자** 역할을 가진 사용자는 Cloud Manager를 사용하여 사용자 정의 도메인 이름을 삭제할 수 있습니다.

### 연결된 모든 환경에서 사용자 정의 도메인 이름 삭제 {#delete-cdn-all}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. **개요** 화면에서 **도메인 설정** 페이지로 이동합니다.

1. 삭제하려는 사용자 정의 도메인 이름의 행을 식별합니다.

1. 행의 오른쪽 끝에 있는 줄임표 버튼을 클릭합니다.

1. **삭제**&#x200B;를 선택합니다.

1. 제출을 확인합니다.

### 특정 환경에서 사용자 정의 도메인 이름 삭제 {#delete-cdn-specific}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.
1. **개요** 페이지에서 **환경** 화면으로 이동합니다.
1. **환경** 페이지에서 관심 환경의 세부 정보 화면으로 이동합니다.
1. 도메인 이름 테이블에서 삭제하려는 사용자 정의 도메인 이름의 행을 식별합니다.
1. 행의 오른쪽 끝에 있는 줄임표 버튼을 클릭합니다.
1. **삭제**&#x200B;를 선택합니다.
1. 제출을 확인합니다.
