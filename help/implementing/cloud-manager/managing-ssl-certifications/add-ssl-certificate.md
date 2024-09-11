---
title: SSL 인증서 추가
description: Cloud Manager의 셀프서비스 도구를 사용하여 고유한 SSL 인증서 또는 DV(도메인 유효성 검사) 인증서를 추가하는 방법을 알아봅니다.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 6fb672e03fe28ae8af6dc873791c7d1ac1fb8fd7
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 9%

---


# SSL 인증서 추가

Cloud Manager의 셀프서비스 도구를 사용하여 고객 관리 SSL 인증서 또는 Adobe 생성 및 관리 DV(도메인 유효성 검사) 인증서를 추가하는 방법을 알아봅니다.

[SSL 인증서 오류 문제 해결](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md)도 참조하세요.


## SSL 인증서 추가 {#adding-an-ssl-certificate}

인증서를 프로비저닝하는 데 며칠이 걸릴 수 있습니다. 따라서 Adobe은 마감일이나 Go-Live 날짜 이전에 인증서를 프로비저닝할 것을 권장합니다.

[SSL 인증서 관리 소개](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md#requirements)에서 **인증서 요구 사항**&#x200B;을 검토하여 AEM as a Cloud Service에서 추가하려는 인증서를 지원하는지 확인하십시오.

이 작업을 완료하려면 사용자가 **비즈니스 소유자** 또는 **배포 관리자** 역할의 멤버여야 합니다.

>[!NOTE]
>
>고객은 DV(도메인 유효성 검사) 인증서를 업로드할 수 없습니다.

**SSL 인증서를 추가하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. **개요** 페이지에서 **환경** 화면으로 이동합니다.

1. 왼쪽 탐색 패널의 **서비스**&#x200B;에서 **SSL 인증서**&#x200B;를 클릭합니다. 다음 이미지에 표시된 대로 왼쪽 탐색 패널이 표시되지 않으면 왼쪽 위 모서리에 있는 햄버거 아이콘을 클릭해야 할 수 있습니다.

   ![SSL 인증서 추가](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. 페이지의 오른쪽 상단 모서리에서 **SSL 인증서 추가**&#x200B;를 클릭합니다.

1. **SSL 인증서 추가** 대화 상자에서 [특정 사용 사례](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)를 기준으로 다음 중 하나를 수행합니다.

   | | 사용 사례 | 단계 |
   | --- | --- | --- |
   | 1 | **Adobe 관리 인증서(DV) 추가** | **Adobe 관리 인증서(DV)를 추가하려면:**<br> a. 인증서 유형 **Adobe 관리(DV)**&#x200B;을(를) 선택합니다.<br>![DV 인증서를 추가합니다](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)<br>b. **도메인 선택** 드롭다운 목록에서 DV 인증서와 연결할 도메인을 하나 이상 선택합니다.<br>선택할 도메인이 없습니까? 이 경우 사용자 정의 도메인을 추가해야 합니다. [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하십시오. 사용자 정의 도메인 이름을 모두 추가했으면 이 항목으로 돌아가서 1단계에서 다시 시작합니다.<br>일. 7단계로 진행합니다. |
   | 2 | **고객 관리 인증서(OV/EV) 추가** | **고객 관리 인증서(OV/EV)를 추가하려면:**<br> a. 인증서 유형 **고객 관리(OV/EV)**&#x200B;을(를) 선택하십시오.<br>b. **인증서 이름** 필드에 인증서 이름을 입력합니다. 이 필드는 정보 제공용으로만 사용되며 인증서를 쉽게 참조하는 데 도움이 되는 모든 이름을 지정할 수 있습니다.<br>c입니다. **인증서**, **개인 키** 및 **인증서 체인** 필드에서 각 필드에 필요한 값을 붙여 넣습니다.<br>![SSL 인증서 추가 대화 상자](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)<br>값에서 발견된 오류가 표시됩니다. 인증서를 저장하려면 먼저 모든 오류를 해결해야 합니다. 일반적인 오류를 해결하는 방법에 대한 자세한 내용은 [인증서 오류](#certificate-errors)를 참조하세요.<br>일. 7단계로 진행합니다. |

<!--
    **Add an SSL certificate:**
    1. Select the certificate type **Customer managed (OV/EV)**.
    1. In **Certificate name** field, enter a name for your certificate. This field is for informational purposes only and can be any name that helps you reference your certificate easily.
    1. In the **Certificate**, **Private key**, and **Certificate chain** fields, paste the required values into their respective fields.

        ![Add SSL certificate dialog box](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)
  
    Any detected errors in values are displayed. Before you can save your certificate, you must address all errors. See [Certificate errors](#certificate-errors) to learn more about troubleshooting common errors.

    **Add a DV certificate:**
    1. Select the certificate type **Adobe managed (DV)**.

        ![Adding a DC certificate](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)

    1. In the **Select domains** drop-down list, select one or more domains that you want associated with the DV certificate.

        No domains to select? If so, it means that you must add a custom domain. See [Add a custom domain](#add-custom-domain). When you are finished, resume the steps from the beginning again. -->

1. 대화 상자의 오른쪽 하단에 있는 **저장**&#x200B;을 클릭합니다.

   인증서가 발급되면 **SSL 인증서** 표에 녹색 확인 표시가 나타납니다.

이제 프로젝트에 대해 작동하는 SSL 인증서를 추가했습니다. 이 단계는 사용자 정의 도메인 이름을 처음 설정하는 경우가 많습니다.

* 사용자 지정 도메인 이름을 설정하려면 [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하십시오.
* Cloud Manager에서 SSL 인증서를 업데이트하고 관리하는 방법에 대한 자세한 내용은 [SSL 인증서 관리](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)를 참조하십시오.

<!--
### Add a custom domain {#add-custom-domain}

Before you can add an Adobe generated and managed Domain Validated (DV) certificate, you must first add a custom domain. The process for doing so is nearly the same as detailed in [Introduction to custom domain names](/help/implementing/cloud-manager/custom-domain-names/introduction.md) and [Add a custom domain name](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md). However, that functionality is now slightly expanded, as described below.

1. When adding a custom domain name, in the **Verify domain** dialog box, select an **Adobe managed certificate**.

    ![Choose Adobe-managed](assets/verify-domain-dialog.png)

1. In the **Verify domain** dialog box, add a CNAME verification record to your DNS.

    ![Add CNAME entry](assets/verify-domain-dialog-adobe-managed.png)

1. After the domain is created, click the ellipsis button in the list of domains and select **Verify** to verify the domain.

    ![Verify domain](assets/verify-domain.png) 

1. Resume the task [Add a DV certificate](#adding-an-ssl-certificate). -->


