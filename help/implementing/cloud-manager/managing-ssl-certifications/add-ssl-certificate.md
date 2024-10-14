---
title: SSL 인증서 추가
description: Cloud Manager의 셀프서비스 도구를 사용하여 자체 SSL 인증서 또는 Adobe 관리 DV(도메인 유효성 검사) 인증서를 추가하는 방법을 알아봅니다.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f12392075b71b219bf449f585f63561167ddada9
workflow-type: tm+mt
source-wordcount: '1000'
ht-degree: 4%

---


# SSL 인증서 추가 {#add-ssl-cert}

Cloud를 사용하여 자체 SSL 인증서 또는 Adobe 관리 DV(도메인 유효성 검사) 인증서를 추가하는 방법을 알아봅니다

>[!NOTE]
>
>OV/EV(고객 관리) SSL 인증서와 고객 관리 CDN 공급자를 사용하는 경우 SSL 인증서 추가를 건너뛰고 준비가 되면 바로 [CDN 구성 추가](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md)(으)로 이동할 수 있습니다.

인증서를 프로비저닝하는 데 며칠이 걸릴 수 있습니다. 따라서 Adobe은 지연을 방지하기 위해 마감일이나 라이브 날짜 이전에 자체 인증서를 프로비저닝할 것을 권장합니다.

Cloud Manager에서 SSL 인증서를 업데이트하고 관리하는 방법에 대한 자세한 내용은 [SSL 인증서 관리](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)를 참조하십시오.

인증서를 추가하거나 관리하는 데 문제가 있는 경우 [SSL 인증서 오류 문제 해결](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md)을 참조하십시오.


## 사전 요구 사항 {#prerequisites}

* SSL 인증서를 추가하려면 사용자는 **비즈니스 소유자** 또는 **배포 관리자** 역할의 멤버여야 합니다.
* 자체 인증서를 설치하는 경우 [SSL 인증서 관리 소개](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements)에서 **인증서 요구 사항**&#x200B;을 참조하십시오.

## 추가할 SSL 인증서 선택 {#which-ssl-to-add}

[AEM Cloud Manager에서 사용자 정의 도메인 이름](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)을(를) 추가한 후 다음 단계는 DV(Adobe 관리) SSL 인증서(권장) 또는 OV/EV(고객 관리) SSL 인증서 사용 선택 여부에 따라 다릅니다.

* **DV(Adobe 관리) SSL 인증서의 경우:**
   * Cloud Manager에서 사용자 정의 도메인을 추가하고 확인하면 도메인 유효성 검사 프로세스가 수행됩니다.
   * 이제 [DV(Adobe 관리) SSL 인증서를 추가](#add-adobe-managed-ssl-cert)해야 합니다.
Cloud Manager에 추가되면 Adobe이 발급될 때까지 기다렸다가 사용자를 대신하여 DV SSL 인증서를 설치합니다.
   * 인증서가 활성화되면 사용자 정의 도메인을 사용할 수 있습니다.

* **고객 관리(OV/EV) SSL 인증서:**

   * 인증 기관에서 OV/EV SSL 인증서를 받습니다. 자세한 내용은 [고객 관리 OV/EV SSL 인증서에 대한 요구 사항](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements)을 검토하십시오.
   * 인증서를 얻은 후 [고객 관리(OV/EV) SSL 인증서의 ](#add-customer-manage-ssl-cert) 세부 정보를 Cloud Manager에 추가합니다.
   * 추가되면 사용자 정의 도메인 이름이 확인된 것으로 표시되고 SSL 인증서가 적용됩니다.

두 경우 모두 인증서를 확인하고 설치한 후 사용자 정의 도메인을 환경에서 안전하게 사용할 수 있습니다. 모든 것이 예상대로 작동하는지 확인하려면 Cloud Manager 인터페이스에서 [정기적으로 도메인의 상태를 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md)하십시오.

[SSL 인증서 소개](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md)도 참조하세요.

## DV(Adobe 관리) SSL 인증서 추가 {#add-adobe-managed-ssl-cert}

도메인에서 Adobe 관리 SSL 인증서(권장) 또는 고객 관리 SSL 인증서를 사용할지 선택하는 데 도움이 필요하십니까? [추가할 SSL 인증서 선택](#which-ssl-to-add)을 참조하세요.

**DV(Adobe 관리) SSL 인증서를 추가하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.
1. 페이지의 왼쪽 상단 모서리에서 ![메뉴 아이콘 표시](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭하여 사이드 메뉴를 표시합니다.

1. **서비스** 제목에서 ![닫힌 아이콘 잠금](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL 인증서 잠금**&#x200B;을 클릭합니다.

   ![SSL 인증서 추가](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. SSL 인증서 페이지의 오른쪽 상단 모서리에서 **SSL 인증서 추가**&#x200B;를 클릭합니다.

1. **SSL 인증서 추가** 대화 상자에서 [특정 사용 사례](#which-ssl-to-add)에 따라 **Adobe 관리(DV)**&#x200B;를 선택합니다.

   ![DV 인증서 추가](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)

1. **인증서 이름** 필드에 DV SSL 인증서와 연결할 이름을 입력합니다.

1. **도메인 선택** 드롭다운 목록에서 DV SSL 인증서와 연결하려는 확인된 도메인을 하나 이상 선택합니다.
   * 선택할 도메인이 없습니까? 이 경우 SSL 인증서를 추가하려면 먼저 사용자 정의 도메인 이름을 추가하고 인증되었는지 확인해야 합니다.
   * [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하십시오.
   * 사용자 정의 도메인 이름을 모두 추가했으면 이 항목으로 돌아가서 1단계에서 다시 시작합니다.

1. 대화 상자의 오른쪽 하단에 있는 **저장**&#x200B;을 클릭합니다.

   SSL 인증서가 발급되면 **SSL 인증서** 표에 녹색 Valid 확인 표시가 나타납니다.

이제 프로젝트에 대한 작업 Adobe 관리 DV SSL 인증서를 추가했습니다. 이 단계는 사용자 정의 도메인 이름을 처음 설정하는 경우가 많습니다.

이제 [CDN 구성](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md)을 추가할 준비가 되었습니다.

## OV/ED(고객 관리) SSL 인증서 추가 {#add-customer-managed-ssl-cert}

<!-- IF THIS TOPIC GET UPDATED, REMEMBER TO UPDATE THE STEPS ALSO IN THE "MANAGE SSL CERTIFICATES TOPIC TOO -->

도메인에서 Adobe 관리 SSL 인증서(권장) 또는 고객 관리 SSL 인증서를 사용할지 선택하는 데 도움이 필요하십니까? [추가할 SSL 인증서 선택](#which-ssl-to-add)을 참조하세요.

**고객 관리(OV/EV) SSL 인증서를 추가하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. 페이지의 왼쪽 상단 모서리에서 ![메뉴 아이콘 표시](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭하여 사이드 메뉴를 표시합니다.

1. **서비스** 제목에서 ![닫힌 아이콘 잠금](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL 인증서 잠금**&#x200B;을 클릭합니다.

   ![SSL 인증서 추가](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. SSL 인증서 페이지의 오른쪽 상단 모서리에서 **SSL 인증서 추가**&#x200B;를 클릭합니다.

1. **SSL 인증서 추가** 대화 상자에서 [특정 사용 사례](#which-ssl-to-add)에 따라 **고객 관리(OV/EV)**&#x200B;를 선택합니다.

1. **인증서 이름** 필드에 인증서 이름을 입력합니다.
이 필드는 정보 제공용으로만 사용되며 SSL 인증서를 쉽게 참조하는 데 도움이 되는 모든 이름이 될 수 있습니다.

1. **인증서**, **개인 키** 및 **인증서 체인** 필드에서 OV 또는 EV SSL 인증서의 필수 값을 복사하여 대화 상자의 해당 필드에 붙여넣습니다.

   값에서 감지된 모든 오류가 표시됩니다. 인증서를 저장하려면 먼저 모든 오류를 해결해야 합니다. 일반적인 오류를 해결하는 방법에 대한 자세한 내용은 [인증서 오류](#certificate-errors)를 참조하세요.

   ![SSL 인증서 추가 대화 상자](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)|

1. 대화 상자의 오른쪽 하단에 있는 **저장**&#x200B;을 클릭합니다.

   >[!NOTE]
   >
   >* [사용자 지정 도메인 이름을 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)하는 동안 **고객 관리 인증서**&#x200B;을(를) 선택한 경우 ***이후***&#x200B;에 고객 관리(OV/EV) SSL 인증서가 추가 및 저장되며 도메인이 확인됩니다. [사용자 지정 도메인 이름 상태 확인](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#how-to)도 참조하세요.

   SSL 인증서가 발급되면 **SSL 인증서** 표에 녹색 확인 확인 확인 표시가 나타납니다.

이제 프로젝트에 대해 작동하는 SSL 인증서를 추가했습니다. 이 단계는 사용자 정의 도메인 이름을 처음 설정하는 경우가 많습니다.

이제 [CDN 구성](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md)을 추가할 준비가 되었습니다.























<!--
## Add an SSL certificate {#add-ssl-cert}

1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate program.
1. On the **[My Programs](/help/implementing/cloud-manager/navigation.md#my-programs)** console, select the program.
1. In the upper-left corner of the page, click ![Show menu icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) to reveal the side menu. 
1. Under the **Services** heading, click ![Lock closed icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL Certificates**. 

   ![Adding an SSL certificate](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. Near the upper-right corner of the SSL Certificates page, click **Add SSL Certificate**.

1. In the **Add SSL certificate** dialog box, based on [your particular use case](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md), do one of the following:

    | | Use case | Steps |
    | --- | --- | --- |
    | 1 | **Add an Adobe managed (DV) certificate** | **To add an Adobe managed (DV) SSL certificate:**<br>a. In the **Add SSL Certificate** dialog box, select the certificate type **Adobe managed (DV)**.<br>![Add a DV certificate](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)<br>b. In the **Certificate name** field, enter a name you want associated with the certificate.<br>c. In the **Select domains** drop-down list, select one or more domains that you want associated with the DV SSL certificate.<br>No domains to select? If so, it means that you must first add a custom domain name and ensure it is verified before you can add an SSL certificate. See [Add a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). When you are finished adding a custom domain name, return to this topic and begin at step 1 again.<br>d. Continue to step 7. |
    | 2 | **Add a customer managed (OV/EV) certificate** | **To add a customer managed (OV/EV) SSL certificate:**<br>a. In the **Add SSL Certificate** dialog box, select the certificate type **Customer managed (OV/EV)**.<br>b. In the **Certificate name** field, enter a name for your certificate. This field is for informational purposes only and can be any name that helps you reference your SSL certificate easily.<br>c. In the **Certificate**, **Private key**, and **Certificate chain** fields, paste the required values into their respective fields.<br>![Add SSL certificate dialog box](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)<br>Any detected errors in values are displayed. Before you can save your certificate, you must address all errors. See [Certificate Errors](#certificate-errors) to learn more about troubleshooting common errors.<br>d. Continue to step 7. | 

1. In the lower-right corner of the dialog box, click **Save**.

    >[!NOTE]
    >
    >* If you selected **Adobe managed certificate** while [adding a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md), the domain is verified with the added certificate when the custom domain is added. 
    >
    >* If you selected **Customer managed certificate** while [adding a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md), the domain is verified ***after*** the customer managed (OV/EV) SSL certificate is added and saved. See also [Check the status of a custom domain name](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md#how-to).

    After the SSL certificate is successfully issued, it is displayed with a green verified check mark in the **SSL Certificates** table. 

    You now have added a working SSL certificate for your project. This step is often the first to set up a custom domain name. 
    

* To learn about updating and managing your SSL certificates in Cloud Manager, see [Manage SSL certificates](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md).

* If you are having issues adding or managing your certificates, see [Troubleshoot SSL certificate errors](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md). -->
