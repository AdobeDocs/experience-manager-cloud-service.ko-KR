---
title: Go-live 후 단계
description: Go-live 후 단계
exl-id: f9b0b2fa-e29c-4faa-a5e7-e5edd04b25ca
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 63%

---

# Go-live 후 {#post-go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_troubleshooting"
>title="AEM 문제 해결"
>abstract="개발자 콘솔 및 CRXDE Lite과 같은 도구와 함께 지속적인 개발에 대한 우수 사례를 검토하고 로그를 관리하여 AEM의 문제 해결을 지원합니다"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html" text="로그 액세스 및 관리"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools" text="AEM as a Cloud Service 개발 도구"


Go-live 후 단계에서는 임시 파일을 정리하고, 지속적인 개발을 위한 우수 사례를 검토하고, 로그를 관리해야 합니다.

다음 도구는 AEM as a Cloud Service 환경으로서 문제를 해결하는 데 사용할 수 있습니다.

* **개발자 콘솔**
* **CRX/DE Lite**
* **로그 관리**


## 개발자 콘솔 {#developer-console}

AEM as a Cloud Service 개발자 환경을 디버깅하는 방법은 개발자 콘솔에서 개발, 스테이지 및 프로덕션 환경에 사용할 수 있습니다.

개발 도구에 대한 자세한 내용은 [AEM as a Cloud Service 구현](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools)을 참조하십시오.

## CRX/DE Lite {#crxde-lite}

사용자는 개발 환경에서 CRX/DE Lite에 액세스할 수 있지만, 스테이지나 프로덕션 환경에서는 액세스할 수 없습니다.

>[!IMPORTANT]
>런타임 시 `/libs` 및 `/apps` 같은 변경할 수 없는 저장소에 쓸 경우 오류가 발생합니다. 또한 고객은 스테이징 및 프로덕션 환경을 위한 개발자 도구에 액세스할 수 없습니다.

CRX/DE Lite를 사용하여 AEM 애플리케이션을 개발하는 방법에 대해 알아보려면 [CRX/DE Lite를 사용한 개발](/help/implementing/developing/tools/crxde.md)을 참조하십시오.

## 로그 관리 {#managing-logs}

사용자는 선택한 환경에 사용할 수 있는 로그 파일 목록에 액세스할 수 있습니다.

UI를 통해 또는 Cloud Manager를 통해 API에서 로그에 액세스하고 관리하는 방법에 대해 알아보려면 [로그 액세스 및 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html)를 참조하십시오.

### 추가 지원 {#additional-support}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_support"
>title="도움말 및 지원"
>abstract="AEM 지원 팀에 문의하여 명확히 하거나 문제를 해결할 수 있습니다."
>additional-url="https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html" text="Experience Cloud 지원"

Cloud Service 액세스에 대한 질문이 있는 경우 Adobe 담당자 또는 [Experience Cloud 지원](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html)에 문의하여 자세한 내용을 확인하십시오.
