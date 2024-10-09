---
title: SSL 인증서 추가
description: Cloud Manager의 셀프서비스 도구를 사용하여 자체 SSL 인증서 또는 Adobe 관리 DV(도메인 유효성 검사) 인증서를 추가하는 방법을 알아봅니다.
exl-id: 104b5119-4a8b-4c13-99c6-f866b3c173b2
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 9cde6e63ec452161dbeb1e1bfb10c75f89e2692c
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 6%

---


# SSL 인증서 추가 {#add-ssl-cert}

Cloud를 사용하여 자체 SSL 인증서 또는 Adobe 관리 DV(도메인 유효성 검사) 인증서를 추가하는 방법을 알아봅니다

>[!TIP]
>
>인증서를 프로비저닝하는 데 며칠이 걸릴 수 있습니다. 따라서 Adobe은 자체 인증서를 제공하는 경우 기한 또는 Go-Live 날짜 이전에 충분히 프로비저닝할 것을 권장합니다.

## 사전 요구 사항 {#prerequisites}

* 인증서를 추가하려면 사용자는 **비즈니스 소유자** 또는 **배포 관리자** 역할의 멤버여야 합니다.
* 자체 인증서를 설치하는 경우 [SSL 인증서 관리 소개](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md#requirements)에서 **인증서 요구 사항**&#x200B;을 참조하십시오.

## SSL 인증서 추가 {#add-certificate}

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.
1. 페이지의 왼쪽 상단 모서리에서 ![메뉴 아이콘 표시](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭하여 사이드 메뉴를 표시합니다.
1. **서비스** 제목에서 ![닫힌 아이콘 잠금](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL 인증서 잠금**&#x200B;을 클릭합니다.

   ![SSL 인증서 추가](/help/implementing/cloud-manager/assets/ssl/ssl-cert-add.png)

1. SSL 인증서 페이지의 오른쪽 상단 모서리에서 **SSL 인증서 추가**&#x200B;를 클릭합니다.

1. **SSL 인증서 추가** 대화 상자에서 [특정 사용 사례](/help/implementing/cloud-manager/managing-ssl-certifications/introduction-to-ssl-certificates.md)를 기준으로 다음 중 하나를 수행합니다.

   | | 사용 사례 | 단계 |
   | --- | --- | --- |
   | 1 | **DV(Adobe 관리) 인증서 추가** | **DV(Adobe 관리) 인증서를 추가하려면:**<br> a. **SSL 인증서 추가** 대화 상자에서 인증서 유형 **Adobe 관리(DV)**&#x200B;를 선택합니다.<br>![DV 인증서를 추가합니다](/help/implementing/cloud-manager/assets/ssl/add-dv-certificate.png)<br>b. **인증서 이름** 필드에 인증서와 연결할 이름을 입력하십시오.<br>c입니다. **도메인 선택** 드롭다운 목록에서 DV 인증서와 연결할 도메인을 하나 이상 선택합니다.<br>선택할 도메인이 없습니까? 이 경우 사용자 정의 도메인을 추가해야 합니다. [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하십시오. 사용자 정의 도메인 이름을 모두 추가했으면 이 항목으로 돌아가서 1단계에서 다시 시작합니다.<br>일. 7단계로 진행합니다. |
   | 2 | **고객 관리(OV/EV) 인증서 추가** | **OV/EV(고객 관리) 인증서를 추가하려면:**<br> a. **SSL 인증서 추가** 대화 상자에서 인증서 유형 **고객 관리(OV/EV)**&#x200B;을(를) 선택합니다.<br>b. **인증서 이름** 필드에 인증서 이름을 입력합니다. 이 필드는 정보 제공용으로만 사용되며 인증서를 쉽게 참조하는 데 도움이 되는 모든 이름을 지정할 수 있습니다.<br>c입니다. **인증서**, **개인 키** 및 **인증서 체인** 필드에서 각 필드에 필요한 값을 붙여 넣습니다.<br>![SSL 인증서 추가 대화 상자](/help/implementing/cloud-manager/assets/ssl/ssl-cert-02.png)<br>값에서 발견된 오류가 표시됩니다. 인증서를 저장하려면 먼저 모든 오류를 해결해야 합니다. 일반적인 오류를 해결하는 방법에 대한 자세한 내용은 [인증서 오류](#certificate-errors)를 참조하세요.<br>일. 7단계로 진행합니다. |

1. 대화 상자의 오른쪽 하단에 있는 **저장**&#x200B;을 클릭합니다.

인증서가 발급되면 **SSL 인증서** 표에 녹색 확인 표시가 나타납니다.

이제 프로젝트에 대해 작동하는 SSL 인증서를 추가했습니다. 이 단계는 사용자 정의 도메인 이름을 처음 설정하는 경우가 많습니다.

* 사용자 지정 도메인 이름을 설정하려면 [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하십시오.
* Cloud Manager에서 SSL 인증서를 업데이트하고 관리하는 방법에 대한 자세한 내용은 [SSL 인증서 관리](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)를 참조하십시오.

>[!TIP]
>
>인증서를 추가하거나 관리하는 데 문제가 있는 경우 [SSL 인증서 오류 문제 해결](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md)을 참조하십시오.
