---
title: SSL 인증서 관리
description: Cloud Manager를 사용하여 SSL 인증서의 상태를 확인하는 방법과 SSL 인증서를 편집, 교체, 업데이트 및 삭제하는 방법을 알아봅니다.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b735c724bd8d68273b3c09a2dc53a13f5f6095ae
workflow-type: tm+mt
source-wordcount: '1038'
ht-degree: 9%

---


# SSL 인증서 관리 {#managing-ssl-certificates}

Cloud Manager를 사용하여 SSL 인증서의 상태를 확인하는 방법과 SSL 인증서를 편집, 교체, 업데이트 및 삭제하는 방법을 알아봅니다.

## SSL 인증서 상태 확인 {#checking-status-an-ssl-certificate}

Cloud Manager은 프로그램의 모든 인증서 상태에 대한 개요를 제공합니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.
1. 페이지의 왼쪽 상단 모서리에서 ![메뉴 아이콘 표시](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭하여 사이드 메뉴를 표시합니다.
1. **서비스** 제목에서 ![닫힌 아이콘 잠금](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL 인증서 잠금**&#x200B;을 클릭합니다.

**SSL 인증서** 페이지에서 SSL 인증서의 상태를 확인할 수 있습니다.

| SSL 인증서 상태 | 설명 |
| --- | --- |
| 녹색 | 인증서는 현재 날짜로부터 최소 14일 동안 유효합니다. |
| 주황색 | 인증서는 14일 이내에 만료됩니다.<br>· 가능한 사이트 액세스 또는 중단을 방지하기 위해 인증서를 갱신하고 Cloud Manager 사용자 인터페이스를 통해 인증서를 교체할 계획이 있는지 확인하십시오.<br>· Cloud Manager에서 인증서 만료가 임박했음을 알리기 위해 UI에 일반 알림을 보냅니다. |
| 빨간색 | SSL 인증서가 만료되었습니다.<br>만료된 고객 관리 SSL 인증서 업데이트](#update-ssl-certificate) 또는 [SSL 인증서 삭제](#deleting-an-ssl-certificate)를 참조하십시오.[ |

## 만료된 고객 관리 SSL 인증서 업데이트 {#update-ssl-certificate}

고객 관리 인증서가 만료되면 만료된 인증서와 함께 사용 중인 모든 도메인이 더 이상 작동하지 않습니다. 인증서를 업데이트하면 도메인이 계속해서 원하는 대로 작동할 수 있습니다.

이 작업을 완료하려면 사용자가 **비즈니스 소유자** 또는 **배포 관리자** 역할의 멤버여야 합니다.

**만료된 고객 관리 SSL 인증서를 업데이트하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.
1. 페이지의 왼쪽 상단 모서리에서 ![메뉴 아이콘 표시](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭하여 사이드 메뉴를 표시합니다.
1. **서비스** 제목에서 ![닫힌 아이콘 잠금](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL 인증서 잠금**&#x200B;을 클릭합니다.
1. 업데이트하려는 만료된 고객 관리 인증서 행에서 맨 오른쪽에 있는 줄임표 버튼을 클릭한 다음 **보기 및 업데이트**&#x200B;를 선택합니다.

   ![만료된 고객 관리 SSL 인증 업데이트](/help/implementing/cloud-manager/assets/ssl/ssl-cert-update.png)

1. **SSL 인증서 보기 및 업데이트** 대화 상자에서 다음을 수행합니다.

   * (선택 사항) **인증서 이름** 필드에 새 이름을 입력합니다.
   * **인증서** 필드에 새 인증서 콘텐츠 키를 붙여 넣습니다.
   * **개인 키** 필드에서 인증서를 변경한 경우에만 이 필드를 업데이트하십시오.
   * **인증서 체인** 필드(또는 신뢰 체인)에 인증서 체인을 붙여 넣습니다.

1. 변경 내용을 저장하고 자동으로 적용하려면 **업데이트**&#x200B;를 클릭하십시오.

>[!NOTE]
>
>동일한 SAN 도메인 항목을 포함하는 SAN 인증서가 두 개 이상 있는 경우, 해당 도메인에 한 개의 인증서가 포함되고 다른 인증서가 업데이트되면 이제 도메인에 대해 후자가 설치됩니다.
>
>자세한 내용은 [SSL 인증서 문제 해결](/help/implementing/cloud-manager/managing-ssl-certifications/troubleshoot-ssl-cert.md#wrong-san-cert)을 참조하십시오.

## 만료된 고객 관리 SSL 인증서 바꾸기 {#replace-ssl-certificate}

[만료된 SSL 인증서 업데이트](#update-ssl-certificate)에 설명된 것과 동일한 단계에 따라 만료된 고객 관리 SSL 인증서를 바꾸십시오.

## Adobe 관리 SSL 인증서(#rename-an-ssl-certificate) 이름 바꾸기

다음은 SSL 인증서의 이름을 변경할 수 있는 몇 가지 이유입니다.

* **개선된 조직**: 인증서의 이름을 바꾸면 해당 환경(예: 스테이징, 프로덕션) 또는 도메인을 식별하는 등 용도를 명확하게 하는 데 도움이 될 수 있습니다.
* **혼동 방지**: 여러 인증서를 관리하는 경우 명확하고 설명적인 이름을 사용하면 잘못된 도메인에 잘못된 인증서를 적용하는 것과 같은 실수를 방지할 수 있습니다.
* **준수 및 감사**: 올바른 이름의 인증서를 보안 및 감사 목적으로 추적하기가 더 쉬울 수 있습니다.

**Adobe 관리 SSL 인증서의 이름을 바꾸려면**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.
1. 페이지의 왼쪽 상단 모서리에서 ![메뉴 아이콘 표시](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭하여 사이드 메뉴를 표시합니다.
1. **서비스** 제목에서 ![닫힌 아이콘 잠금](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL 인증서 잠금**&#x200B;을 클릭합니다.
1. **SSL 인증서** 페이지에서 이름을 바꿀 *Adobe 관리* 인증서가 있는 행 끝에 있는 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다.
1. 드롭다운 메뉴에서 **이름 바꾸기**&#x200B;를 클릭합니다.
1. **DV 인증서 이름 바꾸기** 대화 상자의 **인증서 이름** 텍스트 필드에 새 인증서 이름을 입력합니다.
1. **이름 바꾸기**&#x200B;를 클릭합니다.

## SSL 인증서 삭제 {#deleting-an-ssl-certificate}

Cloud Manager에서 Adobe 관리 또는 고객 관리 SSL 인증서를 삭제하는 것은 실행 취소할 수 없는 영구적인 작업입니다. Adobe Cloud Manager에서 SSL 파일을 삭제하기 전에 로컬에 저장하는 것이 좋습니다.

>[!NOTE]
>
>하나 이상의 활성 도메인이 연결된 Adobe 관리 SSL 인증서는 삭제할 수 없습니다. SSL 인증서를 삭제하기 전에 연결된 모든 활성 도메인을 삭제해야 합니다. 자세한 내용은 [사용자 지정 도메인 이름 관리](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)를 참조하십시오.

이 작업을 완료하려면 사용자가 **비즈니스 소유자** 또는 **배포 관리자** 역할의 멤버여야 합니다.

**SSL 인증서를 삭제하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 프로그램을 선택합니다.
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.
1. 페이지의 왼쪽 상단 모서리에서 ![메뉴 아이콘 표시](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg)를 클릭하여 사이드 메뉴를 표시합니다.
1. **서비스** 제목에서 ![닫힌 아이콘 잠금](https://spectrum.adobe.com/static/icons/workflow_18/Smock_LockClosed_18_N.svg) **SSL 인증서 잠금**&#x200B;을 클릭합니다.
1. SSL 인증서 페이지의 삭제하려는 인증서의 테이블 행에서 맨 오른쪽에 있는 ![추가 아이콘](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)을 클릭합니다
1. 드롭다운 메뉴에서 **삭제**를 클릭합니다.
삭제 버튼에 다음 이미지에 표시된 정보 아이콘이 있는 경우 위의 참고 사항을 참조하십시오.

   ![정보 아이콘이 있는 삭제 단추](/help/implementing/cloud-manager/assets/ssl/ssl-cert-delete-infoicon.png)

1. **SSL 인증서 삭제** 대화 상자에서 **삭제**&#x200B;를 클릭하여 삭제를 확인합니다.
1. 파이프라인을 실행하여 삭제된 인증서의 배포를 취소합니다.

## 기존 CDN 구성 {#pre-existing-cdn}

SSL 인증서에 대한 CDN 구성이 이미 있는 경우 **SSL 인증서** 페이지에 정보 메시지가 표시됩니다. Cloud Manager에서 보고 관리할 수 있도록 UI를 통해 이러한 구성을 추가하는 것이 좋습니다.

모든 기존 환경 구성이 UI를 사용하여 마이그레이션되면 메시지가 사라집니다. 메시지가 사라지는 데는 영업일 기준 1~2일이 소요될 수 있습니다.

자세한 내용은 [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)를 참조하십시오.

IP 허용 목록 또는 사용자 지정 허용 목록 이름에 대한 기존 CDN 구성이 있는 환경의 **IP 도메인** 및 **환경** 페이지에도 유사한 메시지가 제공됩니다.
