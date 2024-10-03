---
title: 도메인 이름 상태 확인
description: Cloud Manager이 사용자 정의 도메인 이름을 성공적으로 확인했는지 확인하는 방법을 알아봅니다.
exl-id: 8fdc8dda-7dbf-46b6-9fc6-d304ed377197
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: ff8c7fb21b4d8bcf395d28c194a7351281eef45b
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 26%

---


# 도메인 이름 상태 확인 {#check-status}

Cloud Manager이 사용자 정의 도메인 이름을 성공적으로 확인했는지 확인하는 방법을 알아봅니다.

## 요구 사항 {#requirements}

Cloud Manager에서 도메인 이름 상태를 확인하기 전에 이러한 요구 사항을 충족하십시오.

* 먼저 [사용자 정의 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) 문서에 설명된 대로 사용자 정의 도메인에 대한 EV/OV 인증서를 추가합니다.

## 사용자 정의 도메인 이름의 상태 확인 {#how-to}

Cloud Manager 내에서 사용자 정의 도메인 이름의 상태를 확인할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직을 선택합니다.

1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.

1. **개요** 페이지에서 **환경** 화면으로 이동합니다.

1. 왼쪽 탐색 패널에서 **도메인 설정**&#x200B;을 클릭합니다.

1. 도메인 이름에 대한 **상태** 아이콘을 클릭합니다.

상태 세부 정보가 표시됩니다. **도메인 확인 및 배포됨** 상태가 표시되면 사용자 정의 도메인을 사용할 준비가 되었습니다. 다양한 상태와 그 의미에 대한 자세한 내용은 [다음 섹션](#statuses)을 참조하세요.

>[!NOTE]
>
>[Cloud Manager에 새 사용자 지정 도메인 이름을 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)할 때 **사용자 지정 도메인 추가** 마법사의 확인 단계에서 **만들기**&#x200B;을(를) 선택하면 Cloud Manager에서 자동으로 확인을 트리거합니다. 이후 확인 시 상태 옆에 있는 다시 확인 아이콘을 선택해야 합니다.

## 확인 상태 {#statuses}

Cloud Manager은 고객 관리 인증서를 통해 도메인 소유권을 확인합니다. 완료되면 다음 상태 메시지 중 하나가 표시됩니다.

| 상태 | 설명 |
| --- | --- |
| 도메인 확인 실패 | 고객 관리 EV/OV 인증서가 누락되었거나 오류가 감지되었습니다.<br> 상태 메시지에 제공된 지침에 따라 문제를 해결합니다. 준비가 되면 상태 옆에 있는 **다시 확인** 아이콘을 선택해야 합니다. |
| 도메인 확인 진행 중 | 확인이 진행 중입니다.<br>이 상태는 일반적으로 상태 옆에 있는 **다시 확인** 아이콘을 선택한 후에 표시됩니다. DNS 전파 지연으로 인해 DNS 확인을 처리하는 데 몇 시간이 걸릴 수 있습니다. |
| 확인됨 - 배포 실패 | EV/OV 인증서 확인에 성공했지만 CDN 배포에 실패했습니다.<br>이러한 경우 Adobe 담당자에게 문의하십시오. |
| 도메인 확인 및 배포됨 | 이 상태는 사용자 정의 도메인 이름을 사용할 준비가 되었음을 나타냅니다.<br>사용자 정의 도메인 이름이 테스트되고 Cloud Manager 도메인 이름을 가리킬 준비가 되었습니다. 자세한 내용은 [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하세요. |
| 삭제 중 | 사용자 정의 도메인 이름 삭제가 진행 중입니다. |
| 삭제 실패 | 사용자 정의 도메인 이름 삭제가 실패하여 다시 시도해야 합니다.<br>자세히 알아보려면 [사용자 지정 도메인 이름 관리](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)를 참조하세요. |


## 도메인 이름 오류 {#domain-error}

다음은 몇 가지 일반적인 도메인 이름 확인 오류와 일반적인 해결 방법입니다.

### 도메인이 설치되지 않음 오류 {#domain-not-installed}

인증서가 적절하게 업데이트되었는지 확인한 후에도 EV/OV 인증서의 도메인 유효성 검사 중에 이 오류가 발생할 수 있습니다.

#### 오류 원인 {#cause}

도메인을 처음 등록한 계정으로 빠르게 잠그고 다른 계정은 하위 도메인을 등록할 수 있는 권한을 요청해야 합니다. 또한 Fastly를 사용하면 하나의 Fastly 서비스 및 계정에 Apex 도메인 및 관련 하위 도메인만 할당할 수 있습니다. AEM Cloud Service 도메인에 사용되는 동일한 apex 및 하위 도메인을 연결하는 기존 Fastly 계정이 있는 경우 이 오류가 표시됩니다.

#### 오류 해결 {#resolution}

이 오류는 다음과 같이 수정됩니다.

* Cloud Manager에 도메인을 설치하기 전에 기존 계정에서 apex 및 하위 도메인을 제거합니다.

* 이 옵션을 사용하여 Apex 도메인과 모든 하위 도메인을 AEM as a Cloud Service Fastly 계정에 연결합니다. 자세한 내용은 [Fastly에서 도메인 작업 설명서](https://docs.fastly.com/en/guides/working-with-domains)를 참조하십시오.

* Apex 도메인에 여러 Fastly 계정에 연결해야 하는 AEM as a Cloud Service 및 비 AEM 사이트에 대한 여러 하위 도메인이 있는 경우 Cloud Manager에 도메인 설치를 시도합니다. 이 프로세스는 다양한 Fastly 계정에서 하위 도메인 연결을 관리하는 데 도움이 됩니다. Adobe 설치에 실패한 경우 Fastly를 사용하여 고객 지원 티켓을 만들어 도메인이 사용자를 대신하여 Fastly를 사용하여 후속 조치를 취할 수 있도록 합니다.

>[!TIP]
>
>Fastly로 도메인 위임 문제를 해결하는 데 일반적으로 영업일 기준 1~2일이 소요됩니다. 이러한 이유로 Go-Live 날짜 이전에 도메인을 설치하는 것이 좋습니다.

>[!NOTE]
>
>도메인이 정상적으로 설치되지 않은 경우, 사이트의 DNS를 AEM as a Cloud Service IP로 라우팅하지 마십시오.

## 사용자 정의 도메인 이름에 대한 기존 CDN 구성 {#pre-existing-cdn}

사용자 정의 도메인 이름에 대한 CDN 구성이 이미 있는 경우 **사용자 정의 도메인 이름** 및 **환경** 페이지에 정보 메시지가 표시됩니다. Cloud Manager 내에서 관리 및 볼 수 있도록 UI를 통해 이러한 구성을 추가하는 것이 좋습니다.

모든 기존 환경 구성이 UI를 사용하여 마이그레이션되면 메시지가 사라집니다. 메시지가 사라지는 데는 영업일 기준 1~2일이 소요될 수 있습니다.

자세한 내용은 [사용자 정의 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하십시오.

## 다음 단계 {#next-steps}

Cloud Manager에서 도메인 상태를 확인한 후 AEM as a Cloud Service을 가리키는 DNS, CNAME 또는 APEX 레코드를 추가하여 DNS 설정을 구성합니다. [사용자 정의 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) 문서로 이동하여 사용자 정의 도메인 이름을 계속 설정합니다.
