---
title: Cloud Manager 2025.4.0 릴리스 정보
description: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.4.0 릴리스에 대해 알아봅니다.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: fcd9ead02ca5061778001d954ae9a9fc6088d5d1
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 48%

---

# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2025.4.0 릴리스 정보 {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.03.0+Release -->

AEM (Adobe Experience Manager) as a Cloud Service의 Cloud Manager 2025.4.0 릴리스에 대해 알아봅니다.


또한 [최신 Adobe Experience Manager as a Cloud Service 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)도 살펴보십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2025.4.0 릴리스 일자는 2025년 4월 10일 금요일입니다.

다음 릴리스는 2025년 5월 8일 금요일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* **(UI) 향상된 배포 가시성**

  이제 Cloud Manager의 파이프라인 실행 세부 정보 페이지에 배포가 다른 배포가 완료되기를 기다리는 동안 상태 메시지(&quot;*대기 중 - 다른 업데이트가 진행 중*&quot;)가 표시됩니다. 이 워크플로우를 통해 환경 배포 중 시퀀스를 보다 쉽게 이해할 수 있습니다.  <!-- CMGR-66890 -->

  ![세부 정보 및 분류를 표시하는 개발 배포 대화 상자](/help/implementing/cloud-manager/release-notes/assets/dev-deployment.png)

* **(UI) 도메인 유효성 검사 개선**

  이제 도메인을 추가할 때 도메인이 Fastly 계정에 이미 설치되어 있으면 Cloud Manager에 오류가 표시됩니다. &quot;*도메인이 Fastly 계정에 이미 설치되어 있습니다. Cloud Service에 추가하기 전에 먼저 여기에서 제거하십시오.*&quot;

## 얼리 어답터 프로그램 {#early-adoption}

Cloud Manager의 조기 채택 프로그램에 참여하여 일반 릴리스 전에 예정된 기능에 독점적으로 액세스할 수 있습니다.

현재 다음 조기 채택 기회를 사용할 수 있습니다.

### 자체 Git 가져오기 - GitLab 및 Bitbucket 지원 포함 {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

**자체 Git 가져오기** 기능이 확장되어 GitLab 및 Bitbucket과 같은 외부 저장소에 대한 지원이 포함되었습니다. 이 새로운 지원은 기존에 제공되던 개인 및 기업용 GitHub 저장소에 대한 지원에 추가됩니다. 이러한 새로운 저장소를 추가하면 이를 파이프라인에 직접 연결할 수도 있습니다. 이러한 저장소를 공개 클라우드 플랫폼이나 비공개 클라우드 또는 인프라 내에 호스팅할 수 있습니다. 또한 이 통합을 통해 Adobe 저장소와 지속적으로 코드를 동기화할 필요가 없으며 가져오기 요청을 메인 분기로 병합하기 전에 유효성 검사를 수행할 수 있는 기능이 제공됩니다.

이제 외부 저장소(GitHub 호스팅된 저장소 제외)와 **배포 트리거**&#x200B;를 **Git 변경 시**&#x200B;로 설정한 파이프라인이 자동으로 시작됩니다.

[Cloud Manager에서 외부 저장소 추가](/help/implementing/cloud-manager/managing-code/external-repositories.md)를 참조하십시오.

![저장소 추가 대화 상자](/help/implementing/cloud-manager/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>현재 기본 제공 가져오기 요청 코드 품질 검사는 GitHub 호스팅 저장소에만 적용되지만, 이 기능을 다른 Git 공급업체로 확장하기 위한 업데이트가 진행 중입니다.

이 새로운 기능을 테스트하고 피드백을 공유하는 데 관심이 있으시면 Adobe ID와 연결된 이메일 주소로 [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com)에 이메일을 보내 주십시오. 사용하려는 Git 플랫폼과 비공개/공개 또는 기업 저장소 구조인지 여부를 반드시 포함해야 합니다.

<!--
### AEM Home {#aem-home}

AEM Home introduces a centralized starting point for managing content, assets, and sites within Adobe Experience Manager. Designed to deliver a personalized experience, AEM Home lets you navigate the AEM ecosystem seamlessly according to your roles and goals. Acting as a guide, it provides key insights and recommended actions to help you achieve your objectives efficiently. With a clear, persona-driven layout, AEM Home ensures quick access to essential tools, supporting a streamlined and effective experience across all AEM features.

Available to early adopters, AEM Home offers an optimized experience focused on improving workflows, prioritizing goals, and delivering results. Opting in lets you influence AEM Home's development by providing feedback that helps shape its future and enhances its value for the entire AEM community.

If you are interested in testing this new capability and sharing your feedback, send an email to [Grp-AemHome@adobe.com](mailto:Grp-AemHome@adobe.com) from your email address associated with your Adobe ID. Be sure to include the following information:

* The role that best fits your profile: Content author, Developer, Business owner, Admin, or Other (provide a description).
* Your primary AEM access surface: AEM Sites, AEM Assets, AEM Forms, Cloud Manager, or Other (provide a description). -->

## 버그 수정

* **CN(일반 이름) 필드가 없는 인증서 문제**

  주체 필드에 일반 이름(CN)을 포함하지 않는 EV/OV 인증서를 처리할 때 Cloud Manager에서 더 이상 NPE(NullPointerException) 및 500 HTTP 응답을 throw하지 않습니다. 최신 인증서는 종종 CN을 생략하고 대신 SAN(주체 대체 이름)을 사용합니다. 이 수정 사항을 통해 SAN이 있을 때 구성 빌드 프로세스 중에 더 이상 CN이 없으므로 오류가 발생하지 않습니다. <!-- CMGR-67548 -->

* **인증서가 일치하지 않는 도메인 확인 문제**

  Cloud Manager은 더 이상 잘못된 인증서를 사용하여 도메인을 잘못 확인하지 않습니다. 이전에는 유효성 검사 논리에서 정확한 일치 대신 패턴 기반 일치를 사용했으며, 이로 인해 `should-not-be-verified.example.com`과(와) 같은 도메인이 `example.com`에 대해 유효한 인증서와 겹쳐서 확인된 것으로 표시되었습니다. 이 수정 사항을 사용하면 도메인 유효성 검사에서 정확한 일치 항목을 확인하여 잘못된 인증서 연결을 방지할 수 있습니다. <!-- CMGR-67225 -->

* **고급 네트워킹 포트 전달 이름에 적용된 고유성**

  이제 Cloud Manager은 고급 네트워킹 포트에 대해 고유한 이름을 적용합니다. 기존에는 중복 이름이 허용돼 갈등이 생길 수 있었다. 이 수정 사항을 통해 각 포트 전달 항목의 이름이 네트워크 구성 무결성에 대한 모범 사례와 일치하도록 합니다. <!-- CMGR-67082 -->


<!-- ## Known issues {#known-issues} -->

