---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.11.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2024.11.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 87293526ca9c10a142bc1d1d3a35562b171da385
workflow-type: tm+mt
source-wordcount: '784'
ht-degree: 30%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2024.11.0 릴리스 정보 {#release-notes}

AEM(Adobe Experience Manager as a Cloud Service)의 Cloud Manager 2024.11.0 릴리스에 대해 알아봅니다.

>[!NOTE]
>
>[최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 날짜 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2024.11.0 릴리스 날짜는 2024년 11월 7일입니다.

다음 예정 릴리스는 2024년 12월 5일입니다.

## 새로운 기능 {#what-is-new}

* 샌드박스 프로그램에서 살펴볼 수 있는 AEM Cloud Service-now를 통해 최신 Edge Delivery Services 혁신을 경험해 보십시오. [자세히 알아보기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-sandbox-programs.md#auto-creation) <!-- (CMGR-62319) -->
* 이제 AEM Cloud Manager의 도메인 설정 페이지에 이름별로 도메인을 빠르게 찾을 수 있는 검색 기능이 포함됩니다. 검색 필드에 키워드를 입력하여 일치하는 도메인을 필터링하고 표시할 수 있으므로 여러 도메인을 보다 쉽게 효율적으로 관리할 수 있습니다. 또한 페이지는 검색 결과를 더 세분화하기 위해 **확인됨** 및 **확인되지 않음**&#x200B;과 같은 상태 필터를 제공합니다. <!-- (CMGR-62615) -->

![도메인 설정의 검색 필드](/help/implementing/cloud-manager/assets/domain-settings-search.png)

## 얼리 어답터 프로그램 {#early-adoption}

Cloud Manager의 얼리 어답터 프로그램에 참여하여 향후 기능을 테스트할 기회를 얻으십시오.

### AEM 홈 {#aem-home}

AEM 홈에서는 Adobe Experience Manager 내의 콘텐츠, 에셋 및 사이트 관리를 위한 중앙 집중식 시작점을 제공합니다. 개인화된 경험을 제공하도록 설계된 AEM Home을 사용하면 역할과 목표에 따라 AEM 에코시스템을 원활하게 탐색할 수 있습니다. 가이드 역할을 하여 목표를 효율적으로 달성하는 데 도움이 되는 주요 인사이트 및 권장 작업을 제공합니다. 명확한 사용자 중심의 레이아웃을 통해 AEM Home은 필수 도구에 빠르게 액세스하여 모든 AEM 기능에 대해 간소화되고 효과적인 경험을 제공합니다.

얼리어답터가 사용할 수 있는 AEM 홈은 워크플로 개선, 목표 우선 순위 지정 및 결과 전달에 초점을 맞춘 최적화된 경험을 제공합니다. 옵트인을 사용하면 AEM Home의 미래를 설정하고 전체 AEM 커뮤니티에 대한 가치를 높이는 데 도움이 되는 피드백을 제공하여 Home의 개발에 영향을 줄 수 있습니다.

이 새로운 기능을 테스트하고 피드백을 공유하려면 Adobe ID과 연결된 전자 메일 주소에서 [Grp-AemHome@adobe.com](mailto:Grp-AemHome@adobe.com)(으)로 전자 메일을 보내세요. 다음 정보를 포함해야 합니다.

* 프로필에 가장 적합한 역할: 콘텐츠 작성자, 개발자, 비즈니스 소유자, 관리자 또는 기타(설명을 제공).
* 기본 AEM 액세스 표면: AEM Sites, AEM Assets, AEM Forms, Cloud Manager 또는 기타(설명을 제공).

### 자체 Git 가져오기 - GitLab 및 Bitbucket 지원 포함 {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**자체 Git 가져오기** 기능이 확장되어 GitLab 및 Bitbucket과 같은 외부 저장소에 대한 지원이 포함되었습니다. 이 새로운 지원은 기존에 제공되던 개인 및 기업용 GitHub 저장소에 대한 지원에 추가됩니다. 이러한 새로운 저장소를 추가하면 이를 파이프라인에 직접 연결할 수도 있습니다. 이러한 저장소를 공개 클라우드 플랫폼이나 비공개 클라우드 또는 인프라 내에 호스팅할 수 있습니다. 또한 이 통합을 통해 Adobe 저장소와 지속적으로 코드를 동기화할 필요 없으며 풀 요청을 메인 분기로 병합하기 전에 유효성 검사를 할 수 있는 기능이 제공됩니다.

[Cloud Manager에서 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)를 참조하십시오.

![저장소 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>현재 기본 제공 풀 요청 코드 품질 검사는 GitHub 호스팅 저장소에만 적용되지만, 이 기능을 다른 Git 공급업체로 확장하기 위한 업데이트가 진행 중입니다.

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com)에 이메일을 보내 주십시오. 사용할 Git 플랫폼과 개인/공용 또는 기업 저장소 구조를 포함해야 합니다. —>


## 버그 수정

* 최근 업데이트에서는 SonarQube에서 특정 경우에 하드 코딩된 암호가 검색되지 않는 문제를 해결했습니다. 이제 이 수정 사항에는 확장된 패턴 검사가 포함되어 있으며 SonarQube의 기본 감지 표준에 맞게 조정됩니다. <!-- CMGR-62682 -->
* Cloud Manager에서 SSL 인증서를 업데이트하려고 할 때 **[!UICONTROL SSL 인증서 보기 및 업데이트]** 대화 상자에서 **[!UICONTROL 업데이트]**&#x200B;를 클릭하면 알 수 없는 오류가 표시됩니다. <!-- CMGR-62848 -->
* Cloud Manager에서 도메인은 동일하지만 서신 대/소문자(대문자 또는 소문자)가 다른 경우에도 &quot;새 인증서가 기존 도메인과 일치하지 않습니다.&quot;라는 오류 메시지와 함께 SSL 인증서 업데이트가 실패합니다. 이제 업데이트는 도메인을 RFC 표준에 맞게 대소문자를 구분하지 않는 것으로 인식합니다. <!-- CMGR-62844 -->
* Cloud Manager허용 목록에 추가하다 에서 도메인 구성에 대한 외래 키 링크가 누락되었기 때문에 IP 도메인 바인딩이 실행 중 상태로 남아 있었습니다. 허용 목록에 추가하다 이제 이 수정은 IP 도메인 바인딩 링크를 관련 도메인 구성에 올바르게 연결합니다. <!-- CMGR-62838 -->
* Cloud Manager은 SSL 인증서의 OCSP(온라인 인증서 상태 프로토콜) 상태를 확인합니다. Adobe은 Cloud Manager을 통해 설치하기 전에 `openssl verify -untrusted intermediate.pem certificate.pem`과(와) 같은 도구를 사용하여 인증서의 무결성을 로컬에서 확인하는 것을 권장합니다. 자세한 내용은 [SSL 인증서 요구 사항 설명서](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/introduction-to-ssl-certificates#requirements)를 참조하세요. <!-- CMGR-62341  -->



<!-- ## Known issues {#known-issues} -->