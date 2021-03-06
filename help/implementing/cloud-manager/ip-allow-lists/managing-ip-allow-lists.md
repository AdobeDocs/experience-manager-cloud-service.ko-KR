---
title: IP 허용 목록 관리
description: Cloud Manager에서 IP 허용 목록 상태를 보고, 편집하고, 삭제하고, 확인하는 방법을 알아봅니다.
source-git-commit: 878381f9c5780864f218a00a272b1600d578dcca
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 1%

---


# IP 허용 목록 관리 {#manage-ip-allow-lists}

Cloud Manager에서 IP 허용 목록 상태를 보고, 편집하고, 삭제하고, 확인하는 방법을 알아봅니다.

## IP 허용 목록 보기 및 업데이트 {#update-ip-allow-lists}

의 사용자 **비즈니스 소유자** 또는 **배포 관리자** 역할은 다음 단계에 따라 IP 허용 목록을 보고 업데이트할 수 있습니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.
1. 다음으로 이동 **환경** 화면 **개요** 페이지.
1. 로 이동합니다 **IP 허용 목록** 페이지의 **환경** 화면.
1. 보거나 업데이트할 IP 허용 목록에 대한 행을 식별합니다.
1. 행의 오른쪽 끝에 있는 줄임표 단추를 클릭합니다.
1. 을(를) 선택합니다 **보기 및 업데이트** 선택 사항입니다.
1. 다음 **보기 및 업데이트** 규칙이 적용되는 환경 및 서비스와 함께 규칙을 정의하는 이름, IP 주소(또는 범위)가 마법사에 표시됩니다.
1. 이름 또는 IP 주소를 변경하고 제출을 확인합니다.

새 IP 범위를 IP 허용 목록에 추가하거나 제거하면 이전에 적용한 모든 해당 환경/서비스에 자동으로 적용되거나 적용되지 않습니다.

이전 업데이트가 진행 중이며 완료되지 않은 동안에는 IP 허용 목록을 업데이트할 수 없습니다.

## IP 허용 목록 상태 확인 {#check-allow-list-status}

다음 단계에 따라 IP 허용 목록 상태를 확인합니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 다음으로 이동 **환경** 화면 **개요** 페이지.

1. 을(를) 클릭합니다. **상태** 아이콘 사용 **환경** 화면 및 을(를) 선택하고 **IP 허용 목록** 페이지.

1. Cloud Manager에 설명된 대로 허용 목록 상태가 표시됩니다 [을 참조하십시오.](#status)

### IP 허용 목록 상태 {#status}

[IP 허용 목록 상태를 확인할 때](#check-allow-list-status) 다음 값 중 하나를 보유할 수 있습니다.

* **적용됨** - IP 허용 목록이 하나 이상의 환경에 성공적으로 적용되었습니다.

* **업데이트 중** - IP 허용 목록에 대한 업데이트가 진행 중이며 여기에는 하나 이상의 응용 프로그램 또는 목록 적용 취소가 포함될 수 있습니다.

   * 각 응용 프로그램/응용 프로그램은 자체 상태인 **시작되지 않음**, **진행 중**, **완료**, 또는 **실패**.

* **실패** - 하나 이상의 응용 프로그램 또는 업데이트 응용 프로그램 해제 프로세스가 실패했습니다.
   * 각 응용 프로그램 및 응용 프로그램 취소는 해당 상태와 함께 나열됩니다.
      * 상태는 입니다. **실패** 업데이트에서 애플리케이션/애플리케이션 하나가 실패하면
      * 상태는 다음과 같이 유지됩니다. **실패** 모든 실패가 지워질 때까지
         * 을(를) 선택해야 합니다 **다시 시도** 아이콘 옆에 있는 아이콘을 클릭하여 오류를 지웁니다.
      * IP 허용 목록을 **실패** 상태.

* **삭제** - IP 허용 목록 삭제 진행 중
   * 삭제에는 모든 서비스에서 목록을 적용하는 작업이 포함됩니다.
   * 각 응용 프로그램은 자체 상태 와 함께 나열됩니다. **시작되지 않음**, **진행 중**, **완료**, 또는 **실패**.
   * 삭제 작업이 완료되면 IP 허용 목록이 다음을 수행합니다.
      * 더 이상 IP 허용 목록 표에 나타나지 않습니다.
      * 더 이상 Cloud Manager의 프로그램에서 서비스에 적용되지 않습니다.

* **삭제 실패** - 삭제 작업 중에 하나 이상의 응용 프로그램이 실패했습니다.

   * 각 응용 프로그램이 상태와 함께 나열됩니다 **완료** 또는 **실패**.
   * 상태는 다음과 같습니다 **삭제 실패** 하나의 애플리케이션 해제에 장애가 발생하는 경우
   * 상태는 다음과 같이 유지됩니다. **삭제 실패** 모든 실패가 지워질 때까지
      * 선택해야 합니다 **삭제** 테이블의 행 맨 오른쪽에 있는 줄임표 메뉴에서 오류를 지웁니다.
   * 상태가 인 동안에는 IP 허용 목록을 업데이트할 수 없습니다 **실패**.

## IP 허용 목록 삭제 {#delete-allow-list}

의 사용자 **비즈니스 소유자** 또는 **배포 관리자** 역할은 다음 단계에 따라 IP 허용 목록을 보고 업데이트할 수 있습니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.
1. 다음으로 이동 **환경** 화면 **개요** 페이지.
1. 로 이동합니다 **IP 허용 목록** 페이지의 **환경** 화면.
1. 삭제할 IP 허용 목록 행을 확인합니다.
1. 행의 맨 오른쪽 끝에서 줄임표 메뉴를 선택합니다.
1. **삭제**&#x200B;를 클릭합니다. 
1. 제출을 확인합니다.

IP 허용 목록을 삭제하면 모든 서비스에서 자동으로 적용되지 않고 테이블에서 삭제됩니다.

## 기존 CDN 구성 {#pre-existing-cdn}

IP 허용 목록에 대한 기존 CDN 구성이 있는 경우, **IP 허용 목록** 페이지에 이러한 구성을 UI를 통해 추가하여 Cloud Manager에서 볼 수 있고 구성할 수 있도록 합니다.

UI를 사용하여 기존 환경 구성을 모두 마이그레이션하면 메시지가 사라집니다. 메시지가 사라지려면 영업일 기준으로 1~2일이 걸릴 수 있습니다.

문서를 참조하십시오 [IP 허용 목록 추가](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) 자세한 내용

또한 **SSL 인증서** 그리고 **환경** SSL 인증서 또는 사용자 지정 도메인 이름에 대한 기존 CDN 구성이 있는 환경의 페이지.
