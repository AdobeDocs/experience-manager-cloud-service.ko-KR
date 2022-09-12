---
title: SSL 인증서 관리
description: Cloud Manager를 사용하여 SSL 인증서의 상태를 확인하고, 인증서를 편집, 바꾸기, 업데이트 및 삭제하는 방법을 알아봅니다.
exl-id: ad6170f4-93bd-4bac-9c54-63c35a0d4f06
source-git-commit: 878381f9c5780864f218a00a272b1600d578dcca
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 2%

---

# SSL 인증서 관리 {#managing-ssl-certificates}

Cloud Manager를 사용하여 SSL 인증서의 상태를 확인하고, 인증서를 편집, 바꾸기, 업데이트 및 삭제하는 방법을 알아봅니다.

## SSL 인증서 상태 확인 {#checking-status-an-ssl-certificate}

SSL 인증서 상태는 SSL 인증서 페이지에서 한 눈에 알 수 있습니다.

* **녹색** - 이 상태는 현재 날짜로부터 최소 60일 동안 인증서가 유효함을 나타냅니다.

* **주황** - 이 상태는 인증서가 60일 이내에 만료됨을 나타냅니다.
   * 가능한 사이트 액세스 또는 정전을 방지하기 위해 인증서를 갱신하고 Cloud Manager UI를 통해 교체할 계획이 있는지 확인해야 합니다.
   * Cloud Manager는 UI에서 정기적인 알림을 전송하여 임박한 인증서 만료를 알려줍니다.

* **빨간색** - 이 상태는 SSL 인증서가 만료되었음을 나타냅니다.

## SSL 인증서 업데이트 {#update-ssl-certificate}

인증서가 만료되면 만료된 인증서와 함께 사용 중인 모든 도메인이 더 이상 작동하지 않습니다. 다음 단계를 통해 인증서를 업데이트하면 도메인이 원하는 대로 계속 작동합니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.
1. 다음으로 이동 **환경** 화면 **개요** 페이지.
1. 로 이동합니다 **SSL 인증서** 화면 **환경** 화면.
1. 프로그램에 성공적으로 설치된 각 SSL 인증서에 대한 행이 포함된 테이블이 표시됩니다. 업데이트할 인증서 행의 맨 오른쪽에 있는 줄임표 단추를 클릭하고 선택합니다 **보기 및 업데이트**.
1. 인증서 세부 사항이 표시되고 업데이트할 수 있습니다.

>[!NOTE]
>
>사용자는 **비즈니스 소유자** 또는 **배포 관리자** cloud Manager에서 SSL 인증서를 업데이트하는 역할.

## SSL 인증서 바꾸기 {#replace-ssl-certificate}

섹션에 설명된 것과 동일한 단계에 따라 SSL 인증서를 대체할 수 있습니다 [SSL 인증서 업데이트.](#update-ssl-certificate)

## SSL 인증서 삭제 {#deleting-an-ssl-certificate}

Cloud Manager에서 인증서를 제거하는 것은 실행 취소할 수 없는 영구 작업입니다. 가장 좋은 방법은 Cloud Manager에서 SSL 파일을 삭제하기 전에 로컬에 저장하는 것입니다.

Cloud Manager에서는 연결된 도메인이 하나 이상 있는 SSL 인증서를 삭제할 수 없습니다. 연관된 모든 도메인은 SSL 인증서를 삭제하기 전에 삭제해야 합니다. 문서를 참조하십시오 [사용자 지정 도메인 이름 관리](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) 추가 정보

다음 단계에 따라 SSL 인증서를 삭제합니다.

1. Cloud Manager에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 적절한 조직과 프로그램을 선택합니다.
1. 다음으로 이동 **환경** 화면 **개요** 페이지.
1. 로 이동합니다 **SSL 인증서** 화면 **환경** 화면.
1. 프로그램에 성공적으로 설치된 각 SSL 인증서에 대한 행이 포함된 테이블이 표시됩니다. 삭제할 인증서 행의 맨 오른쪽에 있는 줄임표 단추를 클릭하고 선택합니다 **삭제**.
1. 에서 삭제를 확인합니다. **SSL 인증서 삭제** 대화 상자.

>[!NOTE]
>
>사용자는 **비즈니스 소유자** 또는 **배포 관리자** 클라우드 관리자에서 SSL 인증서를 삭제하는 역할입니다.

## 기존 CDN 구성 {#pre-existing-cdn}

SSL 인증서에 대한 기존 CDN 구성이 있는 경우, **SSL 인증서** 페이지에 이러한 구성을 UI를 통해 추가하여 Cloud Manager에서 볼 수 있고 구성할 수 있도록 합니다.

UI를 사용하여 기존 환경 구성을 모두 마이그레이션하면 메시지가 사라집니다. 메시지가 사라지려면 영업일 기준으로 1~2일이 걸릴 수 있습니다.

문서를 참조하십시오 [SSL 인증서 추가](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) 자세한 내용

또한 **IP 허용 목록** 그리고 **환경** IP 허용 목록 또는 사용자 지정 도메인 이름에 대한 기존 CDN 구성이 있는 환경의 페이지입니다.
