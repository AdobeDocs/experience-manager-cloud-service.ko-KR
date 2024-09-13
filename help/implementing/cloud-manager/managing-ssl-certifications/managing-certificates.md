---
title: SSL 인증서 관리
description: Cloud Manager를 사용하여 SSL 인증서의 상태를 확인하는 방법과 SSL 인증서를 편집, 교체, 업데이트 및 삭제하는 방법을 알아봅니다.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: d2f05915c0bf0af073db7f070b83f13aeae55252
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 13%

---


# SSL 인증서 관리 {#managing-ssl-certificates}

Cloud Manager을 사용하여 Adobe 관리 및 고객 관리 SSL 인증서의 상태를 확인하는 방법과 이를 삭제하는 방법을 알아봅니다. 고객 관리 인증서의 경우 인증서를 편집하고 업데이트(대체)할 수도 있습니다.

## SSL 인증서 상태 확인 {#checking-status-an-ssl-certificate}

**SSL 인증서** 페이지에서 SSL 인증서의 상태를 한눈에 파악할 수 있습니다.

| SSL 인증서 상태 | 설명 |
| --- | --- |
| 녹색 | 인증서는 현재 날짜로부터 최소 14일 동안 유효합니다. |
| 주황색 | 인증서는 14일 이내에 만료됩니다.<br>· 가능한 사이트 액세스 또는 중단을 방지하기 위해 인증서를 갱신하고 Cloud Manager 사용자 인터페이스를 통해 인증서를 교체할 계획이 있는지 확인하십시오.<br>· Cloud Manager에서 인증서 만료가 임박했음을 알리기 위해 UI에 일반 알림을 보냅니다. |
| 빨간색 | SSL 인증서가 만료되었습니다.<br>만료된 고객 관리 SSL 인증서 업데이트](#update-ssl-certificate) 또는 [SSL 인증서 삭제](#deleting-an-ssl-certificate)를 참조하십시오.[ |

## 만료된 고객 관리 SSL 인증서 업데이트 {#update-ssl-certificate}

고객 관리 인증서가 만료되면 만료된 인증서와 함께 사용 중인 모든 도메인이 더 이상 작동하지 않습니다. 인증서를 업데이트하면 도메인이 계속해서 원하는 대로 작동할 수 있습니다.

이 작업을 완료하려면 사용자가 **비즈니스 소유자** 또는 **배포 관리자** 역할의 멤버여야 합니다.

**만료된 고객 관리 SSL 인증서를 업데이트하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직 선택
1. **[내 프로그램](/help/implementing/cloud-manager/navigation.md#my-programs)** 콘솔에서 프로그램을 선택합니다.
1. **개요** 페이지에서 **환경** 화면으로 이동합니다.
1. **환경** 화면에서 **SSL 인증서** 화면으로 이동합니다.
1. 업데이트하려는 만료된 고객 관리 인증서 행에서 맨 오른쪽에 있는 줄임표 버튼을 클릭한 다음 **보기 및 업데이트**&#x200B;를 선택합니다.

   ![만료된 고객 관리 SSL 인증 업데이트](/help/implementing/cloud-manager/assets/ssl/ssl-cert-update.png)

1. **SSL 인증서 보기 및 업데이트** 대화 상자에서 다음을 수행합니다.

   * (선택 사항) **인증서 이름** 필드에 새 이름을 입력합니다.
   * **인증서** 필드에 새 인증서 콘텐츠 키를 붙여 넣습니다.
   * **개인 키** 필드에서 인증서를 변경한 경우에만 이 필드를 업데이트하십시오.
   * **인증서 체인** 필드(또는 신뢰 체인)에 인증서 체인을 붙여 넣습니다.

1. 변경 내용을 저장하고 자동으로 적용하려면 **업데이트**&#x200B;를 클릭하십시오.

## 만료된 고객 관리 SSL 인증서 바꾸기 {#replace-ssl-certificate}

[만료된 SSL 인증서 업데이트](#update-ssl-certificate)에 설명된 것과 동일한 단계에 따라 만료된 고객 관리 SSL 인증서를 바꾸십시오.

## SSL 인증서 삭제 {#deleting-an-ssl-certificate}

Cloud Manager에서 Adobe 관리 또는 고객 관리 SSL 인증서를 삭제하는 것은 실행 취소할 수 없는 영구적인 작업입니다. Adobe Cloud Manager에서 SSL 파일을 삭제하기 전에 로컬에 저장하는 것이 좋습니다.

>[!NOTE]
>
>하나 이상의 활성 도메인이 연결된 Adobe 관리 SSL 인증서는 삭제할 수 없습니다. SSL 인증서를 삭제하기 전에 연결된 모든 활성 도메인을 삭제해야 합니다. 자세한 내용은 [사용자 지정 도메인 이름 관리](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)를 참조하십시오.

이 작업을 완료하려면 사용자가 **비즈니스 소유자** 또는 **배포 관리자** 역할의 멤버여야 합니다.

**SSL 인증서를 삭제하려면:**

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.
1. **개요** 페이지에서 **환경** 화면으로 이동합니다.
1. **환경** 화면에서 **SSL 인증서** 화면으로 이동합니다.
1. 삭제하려는 인증서 행에서 맨 오른쪽에 있는 줄임표 버튼을 클릭한 다음 **삭제**를 선택합니다.
삭제 버튼에 다음 이미지에 표시된 정보 아이콘이 있는 경우 위의 참고 사항을 참조하십시오.

   ![정보 아이콘이 있는 삭제 단추](/help/implementing/cloud-manager/assets/ssl/ssl-cert-delete-infoicon.png)

1. **SSL 인증서 삭제** 대화 상자에서 **삭제**&#x200B;를 클릭하여 삭제를 확인합니다.
1. 파이프라인을 실행하여 삭제된 인증서의 배포를 취소합니다.

## 기존 CDN 구성 {#pre-existing-cdn}

SSL 인증서에 대한 CDN 구성이 이미 있는 경우 **SSL 인증서** 페이지에 정보 메시지가 표시됩니다. Cloud Manager에서 보고 관리할 수 있도록 UI를 통해 이러한 구성을 추가하는 것이 좋습니다.

모든 기존 환경 구성이 UI를 사용하여 마이그레이션되면 메시지가 사라집니다. 메시지가 사라지는 데는 영업일 기준 1~2일이 소요될 수 있습니다.

자세한 내용은 [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)를 참조하십시오.

IP 허용 목록 또는 사용자 지정 허용 목록 이름에 대한 기존 CDN 구성이 있는 환경의 **IP 도메인** 및 **환경** 페이지에도 유사한 메시지가 제공됩니다.
