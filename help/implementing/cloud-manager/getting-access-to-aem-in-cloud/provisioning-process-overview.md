---
title: 프로비저닝 프로세스 - 개요
description: 프로비저닝 프로세스 - 개요
source-git-commit: ffeda76f9c661117ddba50588ebea01d151ee8c3
workflow-type: ht
source-wordcount: '331'
ht-degree: 100%

---


# AEM as a Cloud Service: 온보딩 및 액세스

이 페이지에는 Experience Manager as a Cloud Service의 프로비저닝 프로세스에 대한 자가 진단 리소스들이 나열됩니다.

## AEM as a Cloud Service 프로비저닝 프로세스 개요

이 섹션에서는 다음 사항에 초점을 둔 주요 문서를 다룹니다.

* AEM as a Cloud Service 액세스
* Adobe Experience Manager as a Cloud Service 온보딩 및 프로비저닝 프로세스
* 도움말 및 리소스


### AEM as a Cloud Service 액세스

자동 프로비저닝이 완료되면 다음과 같은 작업을 수행할 수 있습니다.

* 액세스 권한 부여 – Adobe는 Adobe Identity Management System(IMS) 내에 조직을 만듭니다.
* 지정된 관리자는 기본적으로 관리자 권한을 갖습니다.
* 관리자는 Admin Console을 통해 추가 팀원에 대한 사용자 및 역할을 추가할 수 있습니다.
* Cloud Manager에서 권한 할당을 결정하기 위해 사용자에 대한 역할 기반 권한 검토

![processoverview.jpg](assets/processOverview.jpg)


자세한 내용은 [Experience League에서 Experience Manager as a Cloud Service 온보딩](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/home.html?lang=ko)을 참조하십시오.

### 리소스 및 링크

* [AEM as a Cloud Service에 대한 IMS 지원](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=ko)
* [Cloud Manager의 역할 기반 권한](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/what-is-required/role-based-permissions.html?lang=ko#what-is-required)
* [Experience Manager as a Cloud Service 액세스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=ko#getting-access)


## Adobe Experience Manager as a Cloud Service 온보딩 프로세스

### 1. 구매 주문 자동 프로비저닝을 트리거합니다.

### 2. Adobe Admin Console에 조직을 온보딩합니다.

![processoverview2.jpg](assets/processOverview2.jpg)

* 시스템 관리자:
   * AEM 프로그램 및 환경을 프로비저닝합니다.
   * 관리 작업을 위해 Admin Console로 이동합니다.
   * 각 도메인의 소유권을 확인하기 위해 도메인을 클레임합니다.
   * 사용자 디렉터리를 설정합니다.
   * IDP 구성.
* AEM 관리자:
   * 로컬 그룹, 권한 및 특권을 관리합니다.

### 3. Admin Console에서 사용자 온보딩 및 액세스를 관리합니다.

![processoverview3.jpg](assets/processOverview3.jpg)

크기와 선호도에 따라 다음 세 가지 방법으로 사용자를 온보딩할 수 있습니다.
* Admin Console에서 수동으로 사용자 만들기
* .csv 파일 업로드
* 기업 Active Directory의 사용자
동기화

### 4. 관리자가 조직을 구성하고 사용자 및 그룹에 환경에 대한 액세스 권한을 부여합니다.

## 도움말 및 리소스

* [최초 로그인 - Cloud Service](/help/journey-onboarding/sysadmin/learning-path-aem-users.md)
* [AEM as a Cloud Service 액세스 구성](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html?lang=ko#accessing)
