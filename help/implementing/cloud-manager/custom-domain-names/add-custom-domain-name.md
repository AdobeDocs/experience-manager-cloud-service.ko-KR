---
title: 사용자 정의 도메인 이름 추가
description: Cloud Manager를 사용하여 사용자 정의 도메인 이름을 추가하는 방법을 알아봅니다.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 4a369104ea8394989149541ee1a7b956383c8f12
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 27%

---


# 사용자 정의 도메인 이름 추가 {#adding-cdn}

Cloud Manager를 사용하여 사용자 정의 도메인 이름을 추가하는 방법을 알아봅니다.

## 요구 사항 {#requirements}

Cloud Manager에서 사용자 정의 도메인 이름을 추가하기 전에 이러한 요구 사항을 충족하십시오.

* [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) 문서에 설명된 대로 사용자 정의 도메인 이름을 추가하기 전에 추가하려는 도메인에 대한 도메인 SSL 인증서를 추가해야 합니다.
* Cloud Manager에서 사용자 정의 도메인 이름을 추가하려면 **비즈니스 소유자** 또는 **배포 관리자** 역할이 있어야 합니다.
* Fastly CDN을 사용하고 있습니다.

## 사용자 정의 도메인 이름을 추가할 위치 {#where}

Cloud Manager의 두 위치에서 사용자 정의 도메인 이름을 추가할 수 있습니다.

* [도메인 설정 페이지](#adding-cdn-settings)
* [환경 페이지](#adding-cdn-environments)

사용자 정의 도메인 이름을 추가하면 도메인이 가장 구체적이고 유효한 인증서를 사용하여 제공됩니다. 여러 인증서에 동일한 도메인이 있으면 가장 최근에 업데이트된 이 선택됩니다. Adobe은 도메인이 겹치지 않도록 인증서를 관리할 것을 권장합니다.

이 문서에 설명된 단계는 Fastly를 기반으로 합니다. 다른 CDN을 사용한 경우 사용하기로 선택한 CDN으로 도메인을 구성합니다.

## 도메인 설정 페이지에서 사용자 정의 도메인 이름 추가 {#adding-cdn-settings}

**도메인 설정** 페이지에서 사용자 정의 도메인 이름을 추가하려면 다음 단계를 따르십시오.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. 왼쪽 탐색 패널에서 **도메인 설정 선택** 탭으로 이동합니다.

   ![도메인 설정 창](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)으로 이동합니다.

1. 오른쪽 상단의 **도메인 추가** 단추를 클릭하여 **도메인 이름 추가** 대화 상자를 엽니다.

   ![도메인 추가 대화 상자](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. **도메인 이름** 탭에서 **도메인 이름** 필드에 사용자 지정 도메인 이름을 입력합니다.

   >[!NOTE]
   >
   >도메인을 입력할 때 `http://`, `https://` 또는 공백을 포함하지 마십시오.

1. 서비스를 도메인 이름과 연결할 **환경**&#x200B;을 선택합니다.

1. **게시** 또는 **미리보기** 서비스를 선택합니다.

1. 드롭다운에서 도메인 이름과 연결된 **도메인 SSL 인증서**&#x200B;를 선택하고 **계속**&#x200B;을 선택합니다.

1. **확인** 탭이 나타납니다.

   ![도메인 이름 확인](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

   * **확인** 탭에서는 필요한 TXT 레코드를 만드는 사용자 정의 도메인 이름을 구성하는 다음 단계에 대해 설명합니다.
   * 이 단계는 대화 상자에서 **만들기**&#x200B;를 클릭하기 전에 또는 대화 상자에서 **만들기**&#x200B;를 클릭한 후에 즉시 수행할 수 있습니다.
   * 옵션 및 다음 단계는 아래에 설명되어 있습니다.

1. **만들기**&#x200B;를 클릭하여 Cloud Manager에서 사용자 지정 도메인 이름을 저장합니다.

**사용자 정의 도메인 추가** 마법사에서 **만들기**&#x200B;을(를) 선택하면 Cloud Manager에서 TXT 확인을 트리거합니다. Cloud Manager에서 사용자 정의 도메인 이름을 설정할 때 TXT 레코드를 만듭니다. 그러나 이 단계는 필요하지 않습니다. 이후 확인을 위해 상태 옆에 있는 **다시 확인** 아이콘을 선택해야 합니다.

Cloud Manager에서 TXT 항목이 추가되고 확인될 때까지 이름이 활성화되지 않습니다. **확인 및 배포됨**&#x200B;의 상태는 TXT 확인에 성공했음을 나타냅니다.

* TXT 레코드에 대한 자세한 내용은 [TXT 레코드 추가](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md)를 참조하십시오.
* Cloud Manager에서 사용자 지정 도메인 이름과 TXT 항목을 확인하는 방법에 대한 자세한 내용은 [도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md)을 참조하십시오.

## 다음 단계 {#next-steps}

Cloud Manager에서 사용자 정의 도메인 이름을 만든 후 TXT 항목을 추가하여 도메인의 소유권을 확인합니다. 사용자 지정 도메인 이름을 계속 설정하려면 [TXT 레코드 추가](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) 문서를 계속 진행하십시오.

## 환경 페이지에서 사용자 정의 도메인 이름 추가 {#adding-cdn-environments}

**환경** 페이지에서 사용자 지정 도메인 이름을 추가하는 단계는 [도메인 설정 페이지에서 사용자 지정 도메인 이름을 추가](#adding-cdn-settings)하는 단계와 동일하지만 시작 지점이 다릅니다. **환경** 페이지에서 사용자 정의 도메인 이름을 추가하려면 다음 단계를 따르십시오.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 관심 환경의 **환경 세부 정보** 페이지로 이동합니다.

   ![환경 세부 정보 페이지에 도메인 이름 입력](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. **도메인 이름** 표를 사용하여 사용자 정의 도메인 이름을 제출합니다.

   1. 사용자 정의 도메인 이름을 입력합니다.
   1. 드롭다운 목록에서 이 이름과 연결된 SSL 인증서를 선택합니다.
   1. **+추가**&#x200B;를 클릭합니다.

   ![사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. **도메인 이름 추가** 대화 상자가 열리고 **도메인 이름** 탭이 표시됩니다. [도메인 설정 페이지에서 사용자 지정 도메인 이름을 추가](#adding-cdn-settings)하는 것처럼 계속합니다.
