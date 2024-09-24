---
title: 사용자 정의 도메인 이름 관리
description: Cloud Manager를 사용하여 사용자 정의 도메인 이름을 보고, 업데이트하고, 바꾸고, 삭제하는 방법을 알아봅니다.
exl-id: 6cab8cf2-22c0-4f4b-9c54-a1425e74ddd0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2d1382c84d872719332986baa5829d1623d9d9a6
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 34%

---


# 사용자 정의 도메인 이름 관리 {#managing-custom-domain-names}

Cloud Manager을 사용하면 사용자 정의 도메인 이름을 편집, 업데이트, 바꾸기 및 삭제할 수 있습니다.

## 사용자 정의 도메인 이름 구성 편집 {#view-and-update}

Cloud Manager Adobe에서 다음과 같은 이유로 사용자 정의 도메인 이름 구성을 편집할 수 있습니다.

* **환경 전환**: 최종 사용자(Publish) 또는 내부 사용자(작성자)에게 콘텐츠를 제공하는지 여부에 따라 올바른 구성을 적용합니다.
* **보안 업데이트**: 향상된 보안 또는 규정 준수를 위해 최신 SSL 인증서로 업그레이드하려는 경우.
* **배포 전략 변경**: 올바른 암호화 및 사이트 액세스를 위해 올바른 SSL 인증서가 특정 환경에 적용되도록 합니다.

**사용자 지정 도메인 이름 구성을 편집하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. 페이지 왼쪽 상단 모서리에서 햄버거 아이콘을 클릭하여 왼쪽 탐색 메뉴를 표시합니다.
1. **서비스** 제목에서 **CDN 구성**&#x200B;을 클릭합니다.
1. **CDN 구성** 페이지에서 편집할 CDN이 있는 행 끝에 있는 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.
1. **편집**&#x200B;을 클릭합니다.
1. **CDN 구성 편집** 대화 상자에서 다음을 수행합니다.
   * **계층** 드롭다운 목록에서 사용할 계층(Publish 또는 미리 보기)을 선택합니다.
   * **SSL 인증서** 드롭다운 목록에서 사용할 SSL 인증서를 선택합니다.
1. **업데이트**&#x200B;를 클릭합니다.


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
