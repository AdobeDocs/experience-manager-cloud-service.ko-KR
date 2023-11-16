---
title: SSL 인증서 관리
description: Cloud Manager를 사용하여 SSL 인증서의 상태를 확인하는 방법과 SSL 인증서를 편집, 교체, 업데이트 및 삭제하는 방법을 알아봅니다.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 84%

---


# SSL 인증서 관리 {#managing-ssl-certificates}

Cloud Manager를 사용하여 SSL 인증서의 상태를 확인하는 방법과 SSL 인증서를 편집, 교체, 업데이트 및 삭제하는 방법을 알아봅니다.

## SSL 인증서 상태 확인 {#checking-status-an-ssl-certificate}

SSL 인증서 페이지에서 SSL 인증서의 상태에 대한 개요를 파악할 수 있습니다.

* **녹색** - 이 상태는 인증서가 현재 날짜로부터 최소 60일 동안 유효함을 나타냅니다.

* **주황색** - 이 상태는 인증서가 60일 이내에 만료될 예정임을 나타냅니다.
   * 가능한 사이트 액세스 또는 중단을 방지하기 위해 인증서를 갱신하고 Cloud Manager 사용자 인터페이스를 사용하여 인증서를 교체할 계획이 있는지 확인해야 합니다.
   * Cloud Manager는 인증서 만료가 임박했음을 알리기 위해 UI에서 정기적인 알림을 보냅니다.

* **빨간색** - 이 상태는 SSL 인증서가 만료되었음을 나타냅니다.

## SSL 인증서 업데이트 {#update-ssl-certificate}

인증서가 만료되면 만료된 인증서와 함께 사용 중인 모든 도메인이 더 이상 작동하지 않습니다. 다음 단계를 통해 인증서를 업데이트하면 도메인이 계속해서 원하는 대로 작동할 수 있습니다.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.
1. **개요** 페이지에서 **환경** 화면으로 이동합니다.
1. **환경** 화면에서 **SSL 인증서** 화면으로 이동합니다.
1. 프로그램에 성공적으로 설치된 각 SSL 인증서에 대한 행이 있는 표를 볼 수 있습니다. 업데이트하려는 인증서 행의 맨 오른쪽 끝에 있는 줄임표 버튼을 클릭하고 을 선택합니다 **보기 및 업데이트**.
1. 인증서 세부 정보가 표시되고 업데이트할 수 있습니다.
1. 파이프라인을 실행하여 업데이트된 인증서를 배포합니다.

>[!NOTE]
>
>Cloud Manager에서 SSL 인증서를 업데이트하려면 사용자가 **비즈니스 소유자** 또는 **배포 관리자** 역할의 멤버여야 합니다.

## SSL 인증서 교체 {#replace-ssl-certificate}

[SSL 인증서 업데이트](#update-ssl-certificate) 섹션에 설명된 것과 동일한 단계에 따라 SSL 인증서를 교체할 수 있습니다.

## SSL 인증서 삭제 {#deleting-an-ssl-certificate}

Cloud Manager에서 인증서 제거는 취소할 수 없는 영구적인 작업입니다. Cloud Manager에서 SSL 파일을 삭제하기 전에 로컬에 저장하는 것이 좋습니다.

Cloud Manager에서는 하나 이상의 도메인이 연결된 SSL 인증서를 삭제할 수 없습니다. SSL 인증서를 삭제하기 전에 연결된 모든 도메인을 삭제해야 합니다. 자세한 내용은 [사용자 정의 도메인 이름 관리](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)을 참조하십시오.

SSL 인증서를 삭제하려면 다음 단계를 따르십시오.

1. [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)에서 Cloud Manager에 로그인한 다음 적절한 조직과 프로그램을 선택합니다.
1. **개요** 페이지에서 **환경** 화면으로 이동합니다.
1. **환경** 화면에서 **SSL 인증서** 화면으로 이동합니다.
1. 프로그램에 성공적으로 설치된 각 SSL 인증서에 대한 행이 있는 표를 볼 수 있습니다. 삭제하려는 인증서 행의 맨 오른쪽 끝에 있는 줄임표를 클릭하고 을 선택합니다 **삭제**.
1. **SSL 인증서 삭제** 대화 상자에서 삭제를 확인합니다.
1. 파이프라인을 실행하여 삭제된 인증서의 배포를 취소합니다.

>[!NOTE]
>
>Cloud Manager에서 SSL 인증서를 삭제하려면 사용자가 **비즈니스 소유자** 또는 **배포 관리자** 역할의 멤버여야 합니다.

## 기존 CDN 구성 {#pre-existing-cdn}

SSL 인증서에 대한 기존 CDN 구성이 있는 경우, **SSL 인증서** 페이지에는 이러한 구성을 Cloud Manager에서 보고 구성할 수 있도록 UI를 통해 추가하도록 권장하는 정보 메시지가 표시됩니다.

UI를 사용하여 모든 기존 환경 구성이 마이그레이션되면 메시지가 사라집니다. 메시지가 사라지는 데는 영업일 기준 1~2일이 소요될 수 있습니다.

자세한 내용은 [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md)를 참조하십시오.

IP 허용 목록 또는 사용자 정의 도메인 이름에 대한 기존 CDN 구성이 있는 환경의 **IP 허용 목록** 및 **환경** 페이지에도 유사한 메시지가 제공됩니다.
