---
title: 맞춤형 도메인 이름 추가
description: Cloud Manager를 사용하여 사용자 지정 도메인 이름을 추가하는 방법을 알아봅니다.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
source-git-commit: 0febf4b4a59617e6cc4f8414963c4a91fcf8765e
workflow-type: tm+mt
source-wordcount: '570'
ht-degree: 2%

---

# 맞춤형 도메인 이름 추가 {#adding-cdn}

Cloud Manager의 두 위치에서 사용자 지정 도메인 이름을 추가할 수 있습니다.

* [도메인 설정 페이지에서](#adding-cdn-settings)
* [환경 페이지에서](#adding-cdn-environments)

>[!NOTE]
>
>사용자에게 **비즈니스 소유자** 또는 **배포 관리자** Cloud Manager에서 사용자 지정 도메인 이름을 추가하기 위한 역할

## 도메인 설정 페이지에서 사용자 지정 도메인 이름 추가 {#adding-cdn-settings}

다음 단계에 따라 **도메인 설정** 페이지.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 로 이동합니다 **환경** 화면 **개요** 페이지.

1. 클릭 **도메인 설정** 왼쪽 탐색 패널

   ![도메인 설정 창](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. 을(를) 클릭합니다. **도메인 추가** 오른쪽 상단의 단추를 클릭하여 **도메인 이름 추가** 대화 상자.

   ![도메인 추가 대화 상자](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. 에 사용자 지정 도메인 이름을 입력합니다. **도메인 이름** 필드.

   >[!NOTE]
   >
   >포함하지 않음 `http://`, `https://`또는 도메인에 을 입력할 때 공백을 추가할 수 있습니다.

1. 을(를) 선택합니다 **환경** 해당 서비스가 도메인 이름과 연결됩니다.

1. 다음 중 하나를 선택합니다 **게시** 또는 **미리 보기** 서비스.

1. 을(를) 선택합니다 **도메인 SSL 인증서** 드롭다운에서 도메인 이름과 연결된 다음 을 선택합니다. **계속**.

1. 다음 **도메인 이름 추가** 대화 상자가 나타나고 도메인 이름 확인 프로세스로 이동합니다. 제공된 지침에 따라 환경에 대한 도메인 소유권을 증명하십시오. 클릭 **만들기**.

   ![도메인 이름 확인](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

CDN 배포를 위해서는 유효한 SSL 인증서와 성공적인 TXT 확인이 필요합니다. 상태 표시입니다. **확인 및 배포**.

문서를 참조하십시오 [사용자 지정 도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) 다양한 상태 및 잠재적 문제를 해결하는 방법에 대해 자세히 알아보십시오.

>[!NOTE]
>
>DNS 전파 지연으로 인해 DNS 확인을 처리하는 데 몇 시간이 걸릴 수 있습니다.
>
>Cloud Manager는 소유권을 확인하고 도메인 설정 테이블에서 볼 수 있는 상태를 업데이트합니다. 문서를 참조하십시오 [사용자 지정 도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) 자세한 내용

>[!TIP]
>
>을(를) 참조하십시오. [TXT 레코드 추가](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) txt 레코드에 대한 자세한 내용을 살펴보십시오.

## 환경 페이지에서 사용자 지정 도메인 이름 추가 {#adding-cdn-environments}

다음 단계에 따라 **환경** 페이지.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.

1. 다음으로 이동 **환경 세부 사항** 관심 환경을 위한 페이지입니다.

   ![환경 세부 사항 페이지에 도메인 이름 입력](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. 를 사용하십시오 **도메인 이름** 사용자 지정 도메인 이름을 제출할 테이블입니다.

   1. 사용자 지정 도메인 이름을 입력합니다.
   1. 드롭다운 목록에서 이 이름과 연결된 SSL 인증서를 선택합니다.
   1. 클릭 **+추가**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. 에서 선택한 값을 확인합니다. **도메인 이름 추가** 대화 상자를 열고 **계속**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >
   >포함하지 않음 `http://`, `https://`도메인 이름에 을 입력할 때 또는 공백을 사용합니다.

1. 다음 **도메인 이름 추가** 대화 상자가 나타나고 도메인 이름 확인 프로세스로 이동합니다. 제공된 지침에 따라 환경에 대한 도메인 소유권을 증명하십시오. 클릭 **만들기**.

   ![도메인 이름 확인](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

CDN 배포를 위해서는 유효한 SSL 인증서와 성공적인 TXT 확인이 필요합니다. 상태 표시입니다. **확인 및 배포**.

문서를 참조하십시오 [사용자 지정 도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) 다양한 상태 및 잠재적 문제를 해결하는 방법에 대해 자세히 알아보십시오.

>[!NOTE]
>
>DNS 전파 지연으로 인해 DNS 확인을 처리하는 데 몇 시간이 걸릴 수 있습니다.
>
>Cloud Manager는 소유권을 확인하고 도메인 설정 테이블에서 볼 수 있는 상태를 업데이트합니다. 문서를 참조하십시오 [사용자 지정 도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) 자세한 내용

>[!TIP]
>
>을(를) 참조하십시오. [TXT 레코드 추가](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) txt 레코드에 대한 자세한 내용을 살펴보십시오.
