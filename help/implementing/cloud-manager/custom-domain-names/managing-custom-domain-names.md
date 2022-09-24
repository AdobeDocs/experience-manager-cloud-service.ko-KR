---
title: 맞춤형 도메인 이름 관리
description: Cloud Manager를 사용하여 사용자 지정 도메인 이름을 보고, 업데이트하고, 대체하고, 삭제하는 방법을 알아봅니다.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
source-git-commit: 955f4bb55434eeb1a429a1972714b71c5370de1e
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 5%

---

# 맞춤형 도메인 이름 관리 {#managing-custom-domain-names}

Cloud Manager를 사용하면 사용자 지정 도메인 이름을 보고, 업데이트하고, 바꾸고, 삭제할 수 있습니다.

## 보기 및 업데이트 {#view-and-update}

를 사용하십시오 **보기 및 업데이트** 메뉴 아래의 제품에서 사용할 수 있습니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 로 이동합니다 **환경** 화면 **개요** 페이지.

1. 보거나 업데이트할 사용자 지정 도메인 이름의 행을 식별합니다.

1. 행의 맨 오른쪽 끝에 있는 줄임표 단추를 클릭합니다.

1. 을(를) 선택합니다 **보기 및 업데이트** 선택 사항입니다.

## 사용자 지정 도메인 이름의 SSL 인증서 업데이트 {#update-cert}

따라가시면 됩니다 [사용자 지정 도메인 이름을 보고 업데이트하는 동일한 단계](#view-and-update) 사용자 지정 도메인 이름의 SSL 인증서를 업데이트하려면

>[!NOTE]
>
>SSL 인증서가 유효해야 합니다. [이미 구성됨](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) 업데이트하려는 사용자 지정 도메인 이름을 포함합니다.

## 맞춤형 도메인 이름 삭제 {#deleting}

을 사용하는 사용자 **비즈니스 소유자** 또는 **배포 관리자** 역할은 Cloud Manager를 사용하여 사용자 지정 도메인 이름을 삭제할 수 있습니다.

### 모든 관련 환경에서 사용자 지정 도메인 이름 삭제 {#delete-cdn-all}

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 로 이동합니다 **환경** 화면 **개요** 페이지.

1. 로 이동합니다 **도메인 설정** 페이지의 **환경** 화면.

1. 삭제할 사용자 지정 도메인 이름의 행을 식별합니다.

1. 행의 맨 오른쪽 끝에 있는 줄임표 단추를 클릭합니다.

1. 선택 **삭제**.

   ![사용자 지정 도메인 이름 삭제](/help/implementing/cloud-manager/assets/cdn/cdn-delete.png)

1. 제출을 확인합니다.

### 특정 환경에서 사용자 지정 도메인 이름 삭제 {#delete-cdn-specific}

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.
1. 로 이동합니다 **환경** 화면 **개요** 페이지.
1. 에서 **환경** 페이지에서 관심 환경의 세부 사항 화면으로 이동합니다.
1. 도메인 이름 테이블에서 삭제할 사용자 지정 도메인 이름의 행을 식별합니다.
1. 행의 맨 오른쪽 끝에 있는 줄임표 단추를 클릭합니다.
1. 선택 **삭제**.
1. 제출을 확인합니다.
