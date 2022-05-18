---
title: 도메인 이름 상태 확인
description: 사용자 지정 도메인 이름이 Cloud Manager에서 성공적으로 확인되었는지 확인하는 방법을 알아봅니다.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
source-git-commit: ba0226b5ad3852dd5f72dd7e0ace650035f5ac6a
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 0%

---


# 도메인 이름 상태 확인 {#check-status}

Cloud Manager 내에서 사용자 지정 도메인 이름의 상태를 확인할 수 있습니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 로 이동합니다 **환경** 화면 **개요** 페이지.

1. 클릭 **도메인 설정** 왼쪽 탐색 패널

1. 을(를) 클릭합니다. **상태** 아이콘 을 클릭하여 도메인 이름을 지정합니다.

Cloud Manager는 TXT 값을 통해 도메인 소유권을 확인하고 다음 상태 메시지 중 하나를 표시합니다.

* **도메인 확인 실패** - TXT 값이 없거나 오류가 발생하여 감지됩니다.

   * 제공된 지침에 따라 문제를 해결하십시오.
   * 준비가 완료된 경우 **다시 확인** 아이콘 옆에 표시됩니다.

* **도메인 확인 진행 중** - 확인 진행 중.

   * 이 상태는 일반적으로 **다시 확인** 아이콘 옆에 표시됩니다.

* **확인됨, 배포 실패** - TXT 확인이 성공했지만 CDN 배포가 실패했습니다.

   * 이러한 경우 Adobe 담당자에게 문의하십시오.

* **도메인 확인 및 배포** - 이 상태는 사용자 지정 도메인 이름을 사용할 준비가 되었음을 나타냅니다.

   * 이때 사용자 지정 도메인 이름이 테스트되고 Cloud Manager 도메인 이름을 가리킬 준비가 되었습니다.
   * 문서를 참조하십시오 [DNS 설정 구성](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) 추가 정보

* **삭제** - 사용자 지정 도메인 이름을 삭제하는 중입니다.

* **삭제 실패** - 사용자 지정 도메인 이름을 삭제하지 못하여 다시 시도해야 합니다.

   * 문서를 참조하십시오 [사용자 지정 도메인 이름 관리](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) 추가 정보

선택하면 Cloud Manager에서 자동으로 TXT 확인을 트리거합니다 **저장** 의 검증 단계에서 **사용자 지정 도메인 추가** 마법사 이후 확인을 위해 상태 옆에 있는 확인 아이콘을 다시 선택해야 합니다.

## 도메인 이름 오류 {#domain-error}

이 섹션에서는 표시되는 오류와 이를 해결하는 방법에 대해 설명합니다.

**도메인이 설치되지 않음** - 레코드가 적절히 업데이트되었는지 확인한 후에도 TXT 레코드의 도메인 유효성 검사 중에 이 오류가 표시됩니다.

**오류 설명** - 도메인을 등록한 초기 계정에 제대로 잠글 수 있으며, 다른 계정은 권한을 요청하지 않고 하위 도메인을 등록할 수 없습니다. 또한 Apex 도메인과 연관된 하위 도메인만 하나의 기본 서비스 및 계정에 할당할 수 있습니다. AEM Cloud Service 도메인에 사용된 동일한 Apex 및 하위 도메인을 연결하는 기존 Apple 계정이 있는 경우 이 오류가 표시됩니다.

**오류 해결** - 다음과 같이 오류가 수정되었습니다.

* Cloud Manager에 도메인을 설치하기 전에 기존 계정에서 에이펙스 및 하위 도메인을 제거하십시오. 이 옵션을 사용하여 Apex 도메인 및 모든 하위 도메인을 AEM as a Cloud Service 기본 계정에 연결합니다. 자세한 내용은 [기본 설명서에서 도메인 작업](https://docs.fastly.com/en/guides/working-with-domains) 추가 세부 정보.

* Apex 도메인에 다른 Apple 계정에 연결하려는 AEM as a Cloud Service 및 비AEM as a Cloud Service 사이트에 대한 하위 도메인이 여러 개 있는 경우 Cloud Manager에 도메인을 설치하려고 하며, 도메인 설치에 실패하면 Apple과 함께 고객 지원 티켓을 만들어 고객을 대신하여 직접 추적할 수 있습니다.

>[!NOTE]
>
>참고: 도메인이 제대로 설치되지 않은 경우 사이트의 DNS를 AEM as a Cloud Service IP로 라우팅하지 마십시오.

## 사용자 지정 도메인 이름에 대한 기존 CDN 구성 {#pre-existing-cdn}

사용자 지정 도메인 이름에 대한 기존 CDN 구성이 있는 경우, **사용자 지정 도메인 이름** 및 **환경** 페이지를 사용하여 이러한 구성을 UI를 통해 추가하여 Cloud Manager에서 볼 수 있고 구성할 수 있도록 합니다.

UI를 사용하여 기존 환경 구성을 모두 마이그레이션하면 메시지가 사라집니다. 메시지가 사라지려면 영업일 기준으로 1~2일이 걸릴 수 있습니다.

문서를 참조하십시오 [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) 자세한 내용
