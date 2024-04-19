---
title: 게시 계층에 대한 사용자 정의 도메인 구성
description: Adobe Cloud Manager에서 게시 계층에 대한 사용자 정의 도메인을 구성하는 방법에 대해 알아봅니다.
role: null
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 1%

---


# 게시 계층에 대한 사용자 정의 도메인 구성{#configure-custom-domain}

Adobe Cloud Manager에서 사용자 정의 도메인을 추가하여 웹 사이트를 돋보이게 할 수 있습니다. AEM as a Cloud Service에는 기본 도메인이 제공되지만 필요에 따라 사용자 정의할 수 있습니다.
<!-- For example, AEM sites can use `sites.custom_domain.com`, and the AEM publish domain can be accessed via `assets.custom_domain.com`. Additionally, getting an SSL certificate for assets.pmi.com with a SAN entry for `delivery.custom_domain.com` improves security and trustworthiness. -->

## 시작하기에 앞서

* 다중 SAN(주체 대체 이름) TLS 또는 SSL 인증서가 있어야 합니다.
* SSL 인증서에는 동일한 도메인 내의 게시 계층에 대해 매핑된 인증서와 구별되는 SAN이 있어야 합니다.
* 인증서 정책은 DV(도메인 유효성 검사) 정책이 아닌 EV(확장 유효성 검사) 또는 OV(조직 유효성 검사) 정책을 준수해야 합니다.


## 사용자 정의 도메인 추가

게시 계층에 대한 사용자 정의 도메인을 구성하려면 다음 단계를 수행합니다.

1. 다음으로 이동 **[!UICONTROL Adobe Cloud Manager]** > **[!UICONTROL 프로그램 개요]** > **[!UICONTROL SSL 인증서]**을 클릭하고 SSL 인증서를 추가합니다.
   ![이미지](/help/assets/assets/ssl-certificate.png)
추가 방법 알아보기 [SSL 인증서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/add-ssl-certificate.html?lang=en) Adobe 클라우드 관리자.

1. SSL 인증서를 추가한 후 사용자 정의 도메인을 추가합니다. 클릭 **[!UICONTROL 도메인 설정]** 및에 대한 사용자 정의 도메인을 지정합니다. **[!UICONTROL 서비스 게시]** 옵션을 선택합니다.
   <br> 자세히 알아보기 [사용자 정의 도메인](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name.html?lang=en).

1. 게시 도메인에 해당하는 DNS 레코드에 CNAME 레코드 2개를 추가합니다.
   <br> DNS 전파 지연으로 인해 DNS 확인을 처리하는 데 몇 시간이 걸릴 수 있습니다.

1. 지원 사례를 기록하여 사용자 정의 도메인을 쉽게 구성하여 게재 계층으로 전달합니다.

>[!NOTE]
>
> 자산 선택기에 대해 IMS 클라이언트에서 허용된 리디렉션 URL 목록에 사용자 지정 도메인을 추가해야 합니다.<br>사용자 정의 Adobe 문자열을 제공하여 해당 도메인 팀과 조정하여 이 작업을 실행합니다.
