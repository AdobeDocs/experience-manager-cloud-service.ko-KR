---
title: 사용자 정의 도메인 이름 추가
description: Cloud Manager를 사용하여 사용자 정의 도메인 이름을 추가하는 방법을 알아봅니다.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 73%

---


# 사용자 정의 도메인 이름 추가 {#adding-cdn}

Cloud Manager의 두 위치에서 사용자 정의 도메인 이름을 추가할 수 있습니다.

* [도메인 설정 페이지](#adding-cdn-settings)
* [환경 페이지](#adding-cdn-environments)

>[!NOTE]
>
>사용자에게 다음이 있어야 합니다. **비즈니스 소유자** 또는 **배포 관리자** cloud Manager에서 사용자 정의 도메인 이름을 추가할 역할이며 Fastly CDN을 사용해야 합니다.

## 도메인 설정 페이지에서 사용자 정의 도메인 이름 추가 {#adding-cdn-settings}

사용자 정의 도메인 이름을 추가하면 도메인이 가장 구체적이고 유효한 인증서를 사용하여 제공됩니다. 여러 인증서에 동일한 도메인이 있으면 가장 최근에 업데이트된 이 선택됩니다. Adobe은 도메인이 겹치지 않도록 인증서를 관리할 것을 권장합니다.

**도메인 설정** 페이지에서 사용자 정의 도메인 이름을 추가하려면 다음 단계를 따르십시오. 이러한 단계는 Fastly를 기반으로 합니다. 다른 CDN을 사용하는 경우 사용하기로 선택한 CDN으로 도메인을 구성해야 합니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. 다음으로 이동하여 **도메인 설정** 왼쪽 탐색 패널의 탭입니다.

   ![도메인 설정 창](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)으로 이동합니다.

1. 다음을 클릭합니다. **도메인 추가** 오른쪽 상단의 단추를 클릭하여 **도메인 이름 추가** 대화 상자.

   ![도메인 추가 대화 상자](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. **도메인 이름** 필드에 사용자 정의 도메인 이름을 입력합니다.

   >[!NOTE]
   >
   >도메인을 입력할 때 `http://`, `https://` 또는 공백을 포함하지 마십시오.

1. 서비스를 도메인 이름과 연결할 **환경**&#x200B;을 선택합니다.

1. **게시** 또는 **미리보기** 서비스를 선택합니다.

1. 드롭다운에서 도메인 이름과 연결된 **도메인 SSL 인증서**&#x200B;를 선택하고 **계속**&#x200B;을 선택합니다.

1. **도메인 이름 추가** 대화 상자가 나타나고 도메인 이름 확인 프로세스로 이동합니다. 제공된 지침에 따라 환경에 대한 도메인 소유권을 증명합니다. **만들기**&#x200B;를 클릭합니다.

   ![도메인 이름 확인](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

CDN 배포에는 유효한 SSL 인증서와 성공적인 TXT 확인이 필요합니다. 상태는 **확인 및 배포됨**&#x200B;으로 표시됩니다.

다양한 상태와 잠재적인 문제를 해결하는 방법에 대한 자세한 내용은 [사용자 정의 도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) 문서를 참조하십시오.

>[!TIP]
>
>의 필요성에 대한 다음 문서를 검토하십시오. [다음으로 CNAME 또는 A 레코드 추가](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) 사용자 정의 도메인에 DNS 레코드를 추가할 때 작업이 두 배로 증가하지 않도록 합니다. TXT 항목과 CNAME 또는 A 레코드를 관리 DNS 서버에서 동시에 설정할 수 있습니다.

>[!TIP]
>
>TXT 레코드에 대한 자세한 내용은 [TXT 레코드 추가](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md)를 참조하십시오.

>[!NOTE]
>
>DNS 전파 지연으로 인해 DNS 확인을 처리하는 데 몇 시간이 걸릴 수 있습니다.
>
>Cloud Manager는 소유권을 확인하고 도메인 설정 표에 표시되는 상태를 업데이트합니다. 자세한 내용은 [사용자 정의 도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md)을 참조하십시오.

## 환경 페이지에서 사용자 정의 도메인 이름 추가 {#adding-cdn-environments}

**환경** 페이지에서 사용자 정의 도메인 이름을 추가하려면 다음 단계를 따르십시오.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.

1. 원하는 환경의 **환경 세부 정보** 페이지로 이동합니다.

   ![환경 세부 정보 페이지에 도메인 이름 입력](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. **도메인 이름** 표를 사용하여 사용자 정의 도메인 이름을 제출합니다.

   1. 사용자 정의 도메인 이름을 입력합니다.
   1. 드롭다운 목록에서 이 이름과 연결된 SSL 인증서를 선택합니다.
   1. 클릭 **+추가**.

   ![사용자 정의 도메인 이름 추가](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. **도메인 이름 추가** 대화 상자에서 선택한 값을 확인하고 **계속**&#x200B;을 클릭합니다.

   ![도메인 이름 창](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >
   >도메인 이름을 입력할 때 `http://`, `https://` 또는 공백을 포함하지 마십시오.

1. **도메인 이름 추가** 대화 상자가 나타나고 도메인 이름 확인 프로세스로 이동합니다. 제공된 지침에 따라 환경에 대한 도메인 소유권을 증명합니다. **만들기**&#x200B;를 클릭합니다.

   ![도메인 이름 확인](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

CDN 배포에는 유효한 SSL 인증서와 성공적인 TXT 확인이 필요합니다. 상태는 **확인 및 배포됨**&#x200B;으로 표시됩니다.

다양한 상태와 잠재적인 문제를 해결하는 방법에 대한 자세한 내용은 [사용자 정의 도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) 문서를 참조하십시오.

>[!NOTE]
>
>DNS 전파 지연으로 인해 DNS 확인을 처리하는 데 몇 시간이 걸릴 수 있습니다.
>
>Cloud Manager는 소유권을 확인하고 도메인 설정 표에 표시되는 상태를 업데이트합니다. 자세한 내용은 [사용자 정의 도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md)을 참조하십시오.

>[!TIP]
>
>TXT 레코드에 대한 자세한 내용은 [TXT 레코드 추가](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md)를 참조하십시오.
