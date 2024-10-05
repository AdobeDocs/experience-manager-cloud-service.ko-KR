---
title: IP 허용 목록 소개
description: IP 허용 목록이 사용자가 AEM as a Cloud Service의 도메인에 액세스할 수 있는 주소를 제한하는 방법에 대해 알아봅니다.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 500e1b78fb9688601848fc17f312fc23be83bcb0
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 25%

---


# IP 허용 목록 소개 {#introduction}

IP 허용 목록이 사용자가 AEM as a Cloud Service의 도메인에 액세스할 수 있는 주소를 제한하는 방법에 대해 알아봅니다.

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="IP 허용 목록 관리"
>abstract="AEM as a Cloud Service는 인터넷을 통해 액세스할 수 있으며 사용자 인증 및 권한 부여를 통해 보호됩니다. Cloud Manager의 IP 허용 목록은 신뢰할 수 있는 IP 주소에 대한 액세스를 제한하고 제어하는 데만 사용할 수 있습니다. 적절한 권한이 있는 Cloud Manager 사용자는 사이트 사용자가 AEM 도메인에 액세스할 수 있는 신뢰할 수 있는 IP 주소의 허용 목록을 만들 수 있습니다."
>additional-url="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists" text="IP 허용 목록 추가"
>additional-url="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/managing-ip-allow-lists" text="IP 허용 목록 보기 및 업데이트"

## 개요 {#overview}

AEM as a cloud service는 기본적으로 인터넷을 통해 액세스할 수 있습니다. 보안은 사용자 인증 및 권한 부여를 통해 처리되지만, IP 허용 목록에 추가 기능은 신뢰할 수 있는 IP 주소로만 액세스를 제한하는 방법입니다.

Cloud Manager의 IP 허용 목록을 사용하여 이러한 신뢰할 수 있는 IP 주소에 대한 액세스를 제한하고 제어할 수 있습니다. 적절한 권한이 있는 Cloud Manager 사용자는 사이트 사용자가 AEM 도메인에 액세스할 수 있는 신뢰할 수 있는 IP 주소의 [IP 허용 목록을 만들고 추가](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md)할 수 있습니다.

추가한 후 [IP 허용 목록을 환경의 작성자 서비스나 게시자 서비스 또는 둘 다에 단위나 엔터티로 여러 번 적용 또는 적용 취소](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md)할 수 있습니다.

>[!NOTE]
>
>IP 허용 목록이 적용되지 않으면 기본적으로 모든 IP 주소가 허용됩니다. IP 허용 목록이 적용되면 IP 허용 목록의 주소 외에는 IP 주소가 허용되지 않습니다.

## 제한 사항 {#limitations}

IP 허용 목록을 사용하기 전에 다음 제한 사항의 기능, 사용 및 다른 기능에 미치는 영향을 파악하십시오.

### IP 허용 목록의 일반적인 제한 사항 {#general}

* 프로그램에 최대 50개의 IP 허용 목록을 추가할 수 있습니다.
* 각 IP 허용 목록에 최대 50개의 IP/CIDR 주소를 추가할 수 있습니다.
* IP 허용 목록 이름은 환경의 작성자 서비스용 Cloud Manager 또는 게시 서비스나 둘 다에서 지원됩니다.

### 프론트엔드 파이프라인 및 IP 허용 목록 {#front-end-pipeline}

[프론트엔드 파이프라인을 사용하여 사이트를 개발](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md)하려는 경우, 먼저 다음 Cloud Manager IP 허용 목록을 추가해야 합니다.

[IP 허용 목록을 추가](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md#add-cm-allowlist)할 때 이름을 *`Cloud Manager`*&#x200B;로 지정한 다음 아래 주소 목록을 복사하여 IP 허용 목록 대화 상자에 붙여 넣으십시오.

```text
52.254.106.192/28
20.186.185.181
52.254.106.240/28
52.254.107.128/28
52.254.105.192/28
52.254.106.176/28
20.186.185.227
52.254.106.144/28
52.254.107.64/28
20.186.185.239
20.22.83.112
52.254.107.80/28
52.254.107.144/28
52.254.106.224/28
20.14.241.153
52.254.107.0/28
52.254.107.32/28
52.254.106.208/28
40.70.154.136/29
52.254.106.160/28
52.254.107.16/28
52.254.106.0/28
4.152.211.251
```

프론트엔드 파이프라인 실행이 중단되지 않도록 하려면 이 Cloud Manager IP 허용 목록이 추가되었는지 확인하십시오. 그런 다음 목록을 작성자 환경 *이전*&#x200B;에 적용하여 파이프라인을 사용하도록 설정합니다.

자세한 내용은 [IP 허용 목록 적용](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) 및 [프론트엔드 파이프라인 사용](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md)을 참조하십시오.

### 범용 편집기 및 IP 허용 목록 {#universal-editor}

{{ip-allow-lists-ue}}
