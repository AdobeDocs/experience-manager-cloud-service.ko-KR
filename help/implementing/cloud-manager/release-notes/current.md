---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.10.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2024.10.0 릴리스 정보에 대해 알아봅니다.
feature: Release Information
role: Admin
source-git-commit: aa8d4c8c69a96054492b886893414c3e82b2f4ad
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 13%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.10.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2024.10.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>[최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 릴리스 2024.10.0의 릴리스 날짜는 2024년 10월 3일입니다.

다음 릴리스는 2024년 11월 14일 금요일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* <!-- BOTH CS & AMS --> Cloud Manager에 사용된 AEM Archetype 버전이 이제 버전 26으로 업데이트되었습니다. [https://github.com/adobe/aem-project-archetype/releases](https://github.com/adobe/aem-project-archetype/releases) 보기

<!-- (CMGR-59817) -->

* <!-- CS ONLY --> 새 사용자 정의 도메인을 추가할 때 이전 확인 방법에는 긴 DNS 유효성 검사 프로세스가 포함되었습니다. Adobe은 고객을 위해 이 프로세스를 간소화했습니다. 이제 소유권 증명 역할을 하는 유효한 SSL 인증서(EV 또는 OV)만 제공하면 됩니다. 더 이상 DNS에서 TXT 레코드를 업데이트할 필요가 없습니다.

  >[!NOTE]
  >
  >이 기능은 고객이 관리하는 EV 및 OV 인증서에만 적용할 수 있습니다. Adobe에서 관리하는 DV 인증서에는 CNAME 레코드가 있어야 합니다.

  [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하십시오.

  ![고객 관리 EV/OV 인증서의 도메인 확인](/help/implementing/cloud-manager/assets/verify-domain-customer-managed-step.png)

* <!-- CS ONLY --> 네트워크 인프라를 추가하거나 편집할 때 IP 주소 및 네트워크 마스크 필드의 값은 다음 규칙에 따라 검증됩니다.

   * 주소 공간은 연결 주소 공간에 정의된 주소와 겹치지 않아야 합니다.
   * DNS 주소는 연결 주소 공간에 정의된 네트워크 마스크에 속하거나 공용이어야 합니다.

  ![네트워크 인프라 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/network-infrastructure-add.png)

* <!-- CS ONLY --> 색인화, 변경 가능한 콘텐츠 설치 및 작업 변형을 위한 환경 배포 로그 형식이 변경되었습니다.

  >[!NOTE]
  >
  >이 변경 사항은 2024년 12월 완료 예정일에 따라 단계적으로 롤아웃할 예정입니다.

  ![프로덕션 카드에 배포](/help/implementing/cloud-manager/release-notes/assets/deploy-to-production-card.png)

  로그 형식은 다음에 표시되는 간단한 항목에서 변경됩니다.

  ![단순 항목을 표시하는 로그 파일](/help/implementing/cloud-manager/release-notes/assets/log-file-simple-entry.png)

  다음에 표시되는 JSON 항목으로:

  ![json 항목을 표시하는 로그 파일](/help/implementing/cloud-manager/release-notes/assets/log-file-json-entry.png)


## 얼리 어답터 프로그램 {#early-adoption}

Cloud Manager의 초기 채택 프로그램의 일부가 되어 향후 출시될 기능을 테스트할 수 있습니다.

### 자신만의 Git을 가져와 - 이제 GitLab 및 Bitbucket에 대한 지원 {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**고유한 Git 가져오기** 기능이 GitLab 및 Bitbucket과 같은 외부 저장소에 대한 지원을 포함하도록 확장되었습니다. 이 새로운 지원은 개인 및 엔터프라이즈 GitHub 저장소에 대한 기존 지원에 추가됩니다. 이러한 새 저장소를 추가할 때 파이프라인에 직접 연결할 수도 있습니다. 이러한 저장소를 공용 클라우드 플랫폼 또는 개인 클라우드 또는 인프라 내에서 호스팅할 수 있습니다. 또한 이 통합은 Adobe 저장소와 상수 코드 동기화를 필요로 하지 않고 가져오기 요청을 주 분기로 병합하기 전에 유효성을 검사하는 기능을 제공합니다.

[Cloud Manager에 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)를 참조하십시오.

![저장소 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>현재 기본 가져오기 요청 코드 품질 검사는 GitHub 호스팅 저장소에 대해서만 적용되지만 이 기능을 다른 Git 공급업체에 확장하는 업데이트가 진행 중입니다.

이 새로운 기능을 테스트하고 피드백을 공유하려면 Adobe ID과 연결된 전자 메일 주소에서 [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com)(으)로 전자 메일을 보내세요. 사용할 Git 플랫폼과 개인/공용 또는 기업 저장소 구조를 포함해야 합니다.


<!-- ## Bug fixes




## Known Issues {#known-issues} -->
