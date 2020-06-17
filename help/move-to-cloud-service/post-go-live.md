---
title: 게시 라이브 단계
description: 게시 라이브 단계
translation-type: tm+mt
source-git-commit: 0565d053b6040bc99ae79823711d56eb9aecdfb3
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---


# Post Go-live {#post-go-live}

Post Go-live 단계에서는 임시 파일을 정리하고, 연속적인 개발에 대한 우수 사례를 검토하고 로그를 관리해야 합니다.

Cloud Service 환경에서 AEM 문제를 해결하는 데 다음 도구를 사용할 수 있습니다.

* **개발자 콘솔**
* **CRX/DE Lite**
* **로그 관리**


## 개발자 콘솔 {#developer-console}

개발, 단계 및 프로덕션 환경을 위해 개발자 콘솔에서 AEM을 Cloud Service 개발자 환경으로 디버깅할 수 있습니다.

개발 도구 [에 대한 자세한 내용은 Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools) AEM용 구현을 참조하십시오.

## CRX/DE Lite {#crxde-lite}

사용자는 개발 환경에서 CRX/DE Lite에 액세스할 수 있지만 스테이지나 프로덕션은 액세스할 수 없습니다.

>[중요]
>런타임 시 `/libs` 및 같은 불변경 저장소에 쓰기 작업을 하면 오류가 `/apps` 발생합니다. 또한 고객은 스테이징 및 프로덕션 환경을 위한 개발자 도구에 액세스할 수 없습니다.

CRX/ [DE](https://docs.adobe.com/help/en/experience-manager-65/developing/devtools/developing-with-crxde-lite.html) Lite를 사용하여 AEM 애플리케이션을 개발하는 방법에 대해 알아보려면 CRX/DE Lite를 사용한 개발을 참조하십시오.

## 로그 관리 {#managing-logs}

사용자는 선택한 환경에 사용할 수 있는 로그 파일 목록에 액세스할 수 있습니다.

UI를 [통해 또는 Cloud](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html) Manager를 통해 API를 통해 로그에 액세스하고 관리하는 방법에 대해 알려면 로그 액세스 및 관리를 참조하십시오.

### 추가 지원 {#additional-support}

Cloud Service 액세스에 대한 질문이 있는 경우 Adobe 담당자 또는 Adobe AEM CQ 지원 포털에 문의하십시오.
