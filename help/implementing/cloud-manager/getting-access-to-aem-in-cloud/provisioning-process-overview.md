---
title: 프로비저닝 프로세스 - 개요
description: 프로비저닝 프로세스 - 개요
source-git-commit: 2f40b11a20a4ebb3ff7d9d2835bbe56e91ddf96d
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 8%

---


# AEM as a Cloud Service: 온보딩 및 액세스

이 페이지에는 Experience Manager as a Cloud Service의 프로비전 프로세스에 대한 자습 리소스들이 나열됩니다.

## AEM as a Cloud Service 프로비저닝 프로세스 개요

이 섹션에서는 다음 사항에 초점을 둔 주요 문서를 다룹니다.

* AEM as a Cloud Service 액세스
* Adobe Experience Manager as a Cloud Service 온보딩 및 프로비저닝 프로세스
* 도움말 및 리소스


### AEM as a Cloud Service 액세스

자동 프로비저닝이 완료되면

* 부여된 액세스 권한 - Adobe이 IMS(Adobe Identity Management System) 내에 조직을 만듭니다
* 지정된 관리자는 기본적으로 관리자 권한을 가집니다
* 관리자는 Admin Console을 통해 추가 팀 구성원의 사용자와 역할을 추가할 수 있습니다
* 사용자의 역할 기반 권한을 검토하여 Cloud Manager에서 권한 할당을 결정하십시오

> ![processoverview.jpg](./assets/processOverview.jpg)


자세한 내용은 [Experience League에서 Experience Manager as a Cloud Service으로 온보딩](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/home.html?lang=en)

### 리소스 및 링크

* [AEM as a Cloud Service를 위한 IMS 지원](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en)
* [Cloud Manager의 역할 기반 권한](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/what-is-required/role-based-permissions.html?lang=en#what-is-required)
* [Experience Manager as a Cloud Service 액세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=en#getting-access)


## Adobe Experience Manager as a Cloud Service 온보딩 프로세스

### 1. 구매 발주 자동 프로비전을 트리거합니다.

### 2. Adobe Admin Console에 온보드 조직

![processoverview2.jpg](./assets/processOverview2.jpg)

* 시스템 관리자:
   * AEM 프로그램 및 환경을 프로비저닝합니다.
   * 관리 작업을 위한 Admin Console으로 이동합니다.
   * 도메인을 요청하여 각 도메인의 소유권을 확인합니다.
   * 사용자 디렉토리를 설정합니다.
   * IDP 구성.
* AEM 관리자:
   * 로컬 그룹, 권한 및 권한을 관리합니다.

### 3. Admin Console에서 온보드 사용자 및 액세스 관리

![processoverview3.jpg](./assets/processOverview3.jpg)

크기 및 선호도에 따라 사용자를 온보딩하는 세 가지 방법:
* Admin Console에서 수동으로 사용자 만들기
* .csv 파일 업로드
* 엔터프라이즈 Active Directory에서 사용자 동기화

### 4. 관리자는 조직을 구성하고 사용자 및 그룹에 환경에 대한 액세스 권한을 부여합니다

## 도움말 및 리소스

* [처음 로그인 - Cloud Service](/help/journey-onboarding/sysadmin/learning-path-aem-users.md)
* [AEM as a Cloud Service 액세스 구성](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html?lang=en#accessing)
