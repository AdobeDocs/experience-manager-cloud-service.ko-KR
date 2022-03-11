---
title: 맞춤형 도메인 이름 추가
description: 맞춤형 도메인 이름 추가
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
source-git-commit: 98c137645351c86da8680a31b4929c588863a981
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 4%

---

# 맞춤형 도메인 이름 추가 {#adding-cdn}

Cloud Manager에서 사용자 지정 도메인 이름을 추가하려면 사용자가 비즈니스 소유자 또는 배포 관리자여야 합니다.

아래 표에 표시된 대로 다음 단계를 완료해야 합니다.

| 단계 |  | 책임 | 추가 정보 |
|--- |--- |--- |---|
| SLL 인증서 추가 | SLL 인증서 추가 | 고객 | [SSL 인증서 추가](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-ssl-certificates/add-ssl-certificate.html?lang=en) |
| 도메인 확인 | TXT 레코드 추가 | 고객 | [TXT 레코드 추가](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/add-text-record.html?lang=en) |
| 도메인 확인 상태 검토 |  | 고객 |  |
|  | 상태: 도메인 확인 실패 | 고객 | [도메인 이름 상태 확인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-domain-name-status.html?lang=en) |
|  | 상태: 확인됨, 배포 실패 | Adobe 담당자에게 문의하십시오 | [도메인 이름 상태 확인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-domain-name-status.html?lang=en) |
| CNAME 또는 APEX 레코드를 추가하여 AEM as a Cloud Service을 가리키는 DNS 레코드를 추가합니다 | DNS 설정 구성 | 고객 | [DNS 설정 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/configure-dns-settings.html?lang=en) |
| DNS 레코드 상태 확인 |  | 고객 | [DNS 레코드 상태 확인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-dns-record-status.html?lang=en) |
|  | 상태: DNS 상태가 검색되지 않음 | 고객 | [DNS 레코드 상태 확인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-dns-record-status.html?lang=en) |
|  | 상태: DNS가 잘못 확인됨 | 고객 |  |


## 중요 고려 사항 {#important-considerations}

* 사용자 지정 도메인 이름을 추가하기 전에 사용자 지정 도메인 이름이 포함된 유효한 SSL 인증서를 프로그램에 설치해야 합니다. 을(를) 참조하십시오. [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) 추가 정보

* 해당 환경에 연결된 현재 실행 중인 파이프라인이 있는 동안에는 도메인 이름을 환경에 추가할 수 없습니다.

* 한 번에 하나의 도메인 이름만 추가할 수 있습니다. 작성자 측의 사용자 지정 도메인은 지원되지 않습니다.

* AEM as a Cloud Service은 와일드카드 도메인을 지원하지 않습니다.

* 각 Cloud Manager 환경은 환경당 최대 500개의 사용자 지정 도메인을 호스팅할 수 있습니다.

* 두 개 이상의 환경에서 동일한 도메인 이름을 사용할 수 없습니다.

## 도메인 설정 페이지에서 사용자 지정 도메인 이름 추가 {#adding-cdn-settings}

도메인 설정 페이지에서 사용자 지정 도메인 이름을 추가하려면 아래 단계를 따르십시오.

1. 다음으로 이동 **환경** 화면 **개요** 페이지.

1. 클릭 **도메인 설정** 를 클릭합니다.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. 클릭 **도메인 추가** 열기 단추 **도메인 이름 추가** 대화 상자

   ![](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. 에 사용자 지정 도메인 이름을 입력합니다. **도메인 이름**.

   >[!NOTE]
   >다음을 포함하지 않아야 합니다 `http://`, `https://`또는 도메인에 을 입력할 때 공백을 추가할 수 있습니다.

1. 을(를) 선택합니다 **환경** 의 게시 서비스가 도메인 이름과 연결됩니다.

1. 서비스를 다음 중 하나로 선택합니다. **게시** 또는 **미리 보기**.

   >[!NOTE]
   >이제 사용자 지정 도메인 이름이 게시 및 미리 보기 서비스 모두에 대한 사이트 프로그램의 Cloud Manager에서 지원됩니다. 각 Cloud Manager 환경은 환경당 최대 500개의 사용자 지정 도메인을 호스팅할 수 있습니다. 미리 보기 서비스에 대한 자세한 내용은 [서비스 미리 보기](/help/implementing/cloud-manager/manage-environments.md#preview-service).

1. 을(를) 선택합니다 **도메인 SSL 인증서** 드롭다운에서 을(를) 선택하고 을(를) 선택합니다. **계속**.

1. **도메인 이름 추가** 대화 상자가 나타납니다. 이렇게 하면 환경에 대한 도메인 이름 확인 화면이 표시됩니다. 을(를) 참조하십시오. [TXT 레코드 추가](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) 추가 정보

   제공된 지침에 따라 환경에 대한 도메인 소유권을 증명하십시오.

1. 클릭 **만들기**.
1. CDN 배포를 위해서는 유효한 SSL 인증서와 성공적인 TXT 확인이 필요합니다. 상태 표시입니다. **확인 및 배포**.
다음으로 이동 [사용자 지정 도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) 다양한 상태 및 해결 방법에 대해 자세히 알아보십시오.

   >[!NOTE]
   >DNS 전파 지연으로 인해 DNS 증명을 인식하는 데 최대 몇 시간이 걸릴 수 있습니다. Cloud Manager는 소유권을 확인하고 도메인 설정 테이블에서 볼 수 있는 상태를 업데이트합니다. 자세한 내용은 도메인 이름 상태 확인 을 참조하십시오.

## 환경 페이지에서 사용자 지정 도메인 이름 추가 {#adding-cdn-environments}

1. 관심 영역 환경에 대한 환경 세부 정보 페이지로 이동합니다.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. 도메인 이름 테이블의 맨 위에 있는 입력 필드를 사용하여 사용자 지정 도메인 이름을 제출하고 드롭다운 목록에서 SSL 인증서를 선택합니다. 클릭 **+ 추가**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. 에서 필드를 확인합니다. **도메인 이름 추가** 대화 상자를 열고 **계속**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >포함하지 않음 `http://`, `https://`또는 도메인에 을 입력할 때 공백을 추가할 수 있습니다.

1. Domain Name Verification for your Environment 화면이 표시됩니다.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

   을(를) 참조하십시오. [도메인 확인](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) 추가 정보 제공된 지침에 따라 환경에 대한 도메인 소유권을 증명하십시오.

1. 클릭 **만들기**.

1. 사용자 지정 도메인 이름 배포를 위해서는 유효한 SSL 인증서와 성공적인 TXT 확인이 필요합니다. 상태 표시입니다. **확인 및 배포**.

이때 사용자 지정 도메인 이름이 테스트용으로 준비되고 `CNAME` 그것을 가리키기 위해. 을(를) 참조하십시오. [도메인 이름 상태](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) 다양한 상태 및 해결 방법에 대해 자세히 알아보십시오.

>[!NOTE]
>DNS 전파 지연으로 인해 DNS 증명을 인식하는 데 최대 몇 시간이 걸릴 수 있습니다. Cloud Manager는 소유권을 확인하고 도메인 설정 테이블에서 볼 수 있는 상태를 업데이트합니다. 자세한 내용은 도메인 이름 상태 확인 을 참조하십시오.
