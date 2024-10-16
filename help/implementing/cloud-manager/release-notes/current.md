---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.10.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2024.10.0 릴리스 정보에 대해 알아봅니다.
feature: Release Information
role: Admin
source-git-commit: 9cde6e63ec452161dbeb1e1bfb10c75f89e2692c
workflow-type: ht
source-wordcount: '569'
ht-degree: 100%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.10.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2024.10.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>[최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2024.10.0 릴리스 일자는 2024년 10월 3일입니다.

다음 릴리스는 2024년 11월 14일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* <!-- BOTH CS & AMS --> Cloud Manager에서 사용하는 AEM Archetype 버전은 이제 버전 26으로 업데이트되었습니다. [https://github.com/adobe/aem-project-archetype/releases](https://github.com/adobe/aem-project-archetype/releases) 참조

<!-- (CMGR-59817) -->

* <!-- CS ONLY --> 새로운 사용자 정의 도메인을 추가할 때 이전의 확인 메서드에는 긴 DNS 확인 과정이 포함되었습니다. Adobe는 고객을 위해 이 과정을 단순화했습니다. 이제 소유권을 증명하는 유효한 SSL 인증서(EV 또는 OV)만 제공하면 됩니다. 더 이상 DNS에서 TXT 레코드를 업데이트할 필요가 없습니다.

  >[!NOTE]
  >
  >이 기능은 고객이 관리하는 EV 및 OV 인증서에만 적용됩니다. Adobe에서 관리하는 DV 인증서에는 여전히 CNAME 레코드가 있어야 합니다.

  [사용자 정의 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하십시오.

  ![고객 관리 EV/OV 인증서에 대한 도메인 확인](/help/implementing/cloud-manager/assets/verify-domain-customer-managed-step.png)

* <!-- CS ONLY --> 네트워크 인프라를 추가하거나 편집할 때 IP 주소 및 네트워크 마스크 필드의 값은 다음 규칙에 따라 확인됩니다.

   * 주소 공간은 연결 주소 공간에 정의된 주소와 겹치면 안 됩니다.
   * DNS 주소는 연결 주소 공간에 정의된 네트워크 마스크에 속해야 하거나 공개 주소여야 합니다.

  ![네트워크 인프라 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/network-infrastructure-add.png)

* <!-- CS ONLY --> 색인화, 변경 가능한 콘텐츠 설치 및 변환 작업에 대한 환경 배포 로그 포맷이 변경되고 있습니다.

  >[!NOTE]
  >
  >이러한 변경 사항은 단계적으로 도입되어 2024년 12월에 완료될 예정입니다.

  ![프로덕션에 배포 카드](/help/implementing/cloud-manager/release-notes/assets/deploy-to-production-card.png)

  기록 포맷은 다음과 같은 간단한 항목으로 변경됩니다.

  ![간단한 항목을 보여 주는 로그 파일](/help/implementing/cloud-manager/release-notes/assets/log-file-simple-entry.png)

  다음에서 볼 수 있는 JSON 항목에 대해:

  ![JSON 항목을 보여 주는 로그 파일](/help/implementing/cloud-manager/release-notes/assets/log-file-json-entry.png)


## 얼리 어답터 프로그램 {#early-adoption}

Cloud Manager의 얼리 어답터 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### 자체 Git 가져오기 - GitLab 및 Bitbucket 지원 포함 {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**자체 Git 가져오기** 기능이 확장되어 GitLab 및 Bitbucket과 같은 외부 저장소에 대한 지원이 포함되었습니다. 이 새로운 지원은 기존에 제공되던 개인 및 기업용 GitHub 저장소에 대한 지원에 추가됩니다. 이러한 새로운 저장소를 추가하면 이를 파이프라인에 직접 연결할 수도 있습니다. 이러한 저장소를 공개 클라우드 플랫폼이나 비공개 클라우드 또는 인프라 내에 호스팅할 수 있습니다. 또한 이 통합을 통해 Adobe 저장소와 지속적으로 코드를 동기화할 필요 없으며 풀 요청을 메인 분기로 병합하기 전에 유효성 검사를 할 수 있는 기능이 제공됩니다.

[Cloud Manager에서 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)를 참조하십시오.

![저장소 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>현재 기본 제공 풀 요청 코드 품질 검사는 GitHub 호스팅 저장소에만 적용되지만, 이 기능을 다른 Git 공급업체로 확장하기 위한 업데이트가 진행 중입니다.

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com)에 이메일을 보내 주십시오. 사용하려는 Git 플랫폼과 비공개/공개 또는 기업 저장소 구조인지 여부를 반드시 포함해야 합니다.


<!-- ## Bug fixes




## Known issues {#known-issues} -->
