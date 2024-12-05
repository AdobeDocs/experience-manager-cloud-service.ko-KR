---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.12.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2024.12.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
source-git-commit: ea1aa471a4fcb2ace6e4079715ac88af2d296e18
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.12.0 릴리스 정보 {#release-notes}

AEM (Adobe Experience Manager) as a Cloud Service의 Cloud Manager 2024.12.0 릴리스에 대해 알아봅니다.

>[!NOTE]
>
>[최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2024.12.0 릴리스 날짜는 2024년 12월 5일 목요일입니다.

다음 예정 릴리스는 2024년 1월입니다.

## 새로운 기능 {#what-is-new}

* **Java 21 지원:** 고객은 이제 선택적으로 Java 17 또는 Java 21을 사용하여 빌드할 수 있으므로 성능이 향상되고 새로운 언어 기능이 제공됩니다. Maven 프로젝트 설명 및 특정 라이브러리 버전 업데이트를 포함한 구성 단계는 [빌드 환경](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md)을 참조하십시오. 빌드 버전이 Java 17 또는 Java 21로 설정된 경우 런타임은 기본적으로 Java 21로 설정됩니다.

  2025년 2월부터 샌드박스 및 개발 환경은 빌드 버전(Java 8, 11, 17 또는 21)에 관계없이 Java 21 런타임으로 업그레이드됩니다. 프로덕션 환경은 2025년 4월 업그레이드 이후 운영됩니다.

* **레코드 종류:** AEM Cloud Manager에서 CDN 구성을 사용하는 도메인에 대한 Go-Live 준비를 개선하기 위해 레코드 종류 지원이 추가되었습니다. 이제 Fastly의 IP를 나타내는 CNAME 레코드 유형 또는 A 레코드 유형을 추가하여 라이브로 전환하여 도메인 라우팅을 간소화할 수 있습니다. 이 향상된 기능을 통해 Fastly를 통해 도메인 설정을 위해 CNAME 레코드에만 의존하는 제한을 없앨 수 있습니다.

  [사용자 지정 도메인 이름 추가](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)를 참조하십시오. <!-- CMGR-63076 -->

* **Edge Delivery 사이트에 여러 도메인 추가:** 이제 apex 및 비 apex 도메인을 포함한 여러 도메인을 AEM Cloud Manager의 Edge Delivery EDS(사이트)에 추가할 수 있습니다. 이 향상된 기능은 여러 도메인을 EDS 원본과 연결하는 기능을 제한했던 이전 제한 사항을 해결했습니다. 업데이트는 도메인 구성을 보다 유연하게 관리할 수 있도록 하며 복잡한 도메인 설정이 있는 사이트의 라이브 프로세스를 간소화합니다. <!-- CMGR-63007 -->

* **고급 필터링 옵션:** AEM Cloud Manager의 파이프라인 실행 페이지 및 SSL 인증서 페이지에 고급 필터링 옵션이 도입되었습니다. 이제 여러 기준으로 필터링하여 관련 데이터에 보다 빠르게 액세스하고 배포 효율성을 향상시킬 수 있습니다. <!-- CMGR-26263 -->

   * **파이프라인 활동 필터링:** 파이프라인 활동 필터링을 포함하여 특정 파이프라인 활동에 대한 검색 결과를 구체화할 수 있습니다. 사용 가능한 필터에는 파이프라인, 작업 및 상태가 포함됩니다.
     ![파이프라인 활동 필터링](/help/implementing/cloud-manager/assets/filters-pipeline.png)


   * **SSL 인증서 필터링:** 특정 인증서에 대한 검색 결과를 구체화할 수 있는 SSL 인증서 필터링을 포함합니다. 사용 가능한 필터에는 SSL 인증서 이름, 소유권 및 상태가 포함됩니다.
     ![SSL 인증서 필터링](/help/implementing/cloud-manager/assets/filters-ssl-certificates.png)

## 얼리 어답터 프로그램 {#early-adoption}

Cloud Manager의 얼리 어답터 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### 자체 Git 가져오기 - GitLab 및 Bitbucket 지원 포함 {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**고유한 Git 가져오기** 기능이 GitLab 및 Bitbucket과 같은 외부 저장소에 대한 지원을 포함하도록 확장되었습니다. 이 새로운 지원은 기존에 제공되던 개인 및 기업용 GitHub 저장소에 대한 지원에 추가됩니다. 이러한 새로운 저장소를 추가하면 이를 파이프라인에 직접 연결할 수도 있습니다. 이러한 저장소를 공개 클라우드 플랫폼이나 비공개 클라우드 또는 인프라 내에 호스팅할 수 있습니다. 또한 이 통합을 통해 Adobe 저장소와 지속적으로 코드를 동기화할 필요가 없으며 가져오기 요청을 메인 분기로 병합하기 전에 유효성 검사를 수행할 수 있는 기능이 제공됩니다.

이제 외부 저장소(GitHub 호스팅 저장소 제외) 및 **배포 트리거**&#x200B;을(를) 사용하여 **Git 변경 시**(으)로 설정된 파이프라인이 자동으로 시작됩니다.

[Cloud Manager에서 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)를 참조하십시오.

![저장소 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>현재 기본 제공 가져오기 요청 코드 품질 검사는 GitHub 호스팅 저장소에만 적용되지만, 이 기능을 다른 Git 공급업체로 확장하기 위한 업데이트가 진행 중입니다.

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com)에 이메일을 보내 주십시오. 사용하려는 Git 플랫폼과 비공개/공개 또는 기업 저장소 구조인지 여부를 반드시 포함해야 합니다.

## 버그 수정

* AEM Cloud Manager에서 활성 도메인 매핑이 있는 도메인이 삭제되지 않도록 하는 보호 기능이 추가되었습니다. 이제 이러한 도메인을 삭제하려는 사용자에게 도메인 삭제를 진행하기 전에 먼저 도메인 매핑을 삭제하라는 오류 메시지가 표시됩니다. 이 워크플로우에서는 도메인 무결성을 보장하고 실수로 잘못 구성되는 것을 방지합니다. <!-- CMGR-63033 -->
* 드물게 각 경우에 연결된 상태가 잘못되어 사용자가 도메인 이름을 추가하거나 SSL 인증서를 업데이트할 수 없습니다. <!-- CMGR-62816 -->


<!-- ## Known issues {#known-issues} -->