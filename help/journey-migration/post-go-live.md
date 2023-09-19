---
title: Go-Live 후
description: 문제 모니터링 및 성능 향상 방법 알아보기
exl-id: 487f0b51-501b-48fc-a796-3cb8a6d64462
source-git-commit: 1b9d49ce1ef8ad4b0a11400b41d8c9b880cbf884
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 28%

---

# Go-Live 후 {#post-go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_troubleshooting"
>title="AEM 문제 해결"
>abstract="지속적인 개발을 목적으로 모범 사례를 검토하고 개발자 콘솔 및 CRXDE Lite 등의 도구와 함께 로그를 관리하여 AEM 문제를 해결할 수 있습니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-logs.html?lang=ko-KR" text="로그 액세스 및 관리"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html?lang=ko-KR#aem-as-a-cloud-service-development-tools" text="AEM as a Cloud Service 개발 도구"

이 여정은 마지막 부분이므로 마이그레이션이 완료된 후 문제를 모니터링하고 성능을 향상시키는 방법에 대해 알아봅니다. 임시 파일을 정리하고, 지속적인 개발을 위한 우수 사례를 검토하고, 로그를 관리해야 합니다.

## 지금까지의 스토리 {#story-so-far}

여정의 이전 단계에서는 마이그레이션 및 [실행](/help/journey-migration/go-live.md) 코드와 콘텐츠를 AEM으로 as a Cloud Service으로 이동할 준비가 되었습니다.

## 목표 {#objective}

이 문서에서는 AEM as a Cloud Service 환경 문제를 해결하는 데 사용할 수 있는 도구에 대해 설명합니다.

* **개발자 콘솔**
* **CRXDE Lite**
* **로그 관리**

## 개발자 콘솔 {#developer-console}

AEM as a Cloud Service 개발자 환경 디버깅은 개발자 콘솔에서 개발, 스테이지 및 프로덕션 환경에 사용할 수 있습니다.

다음을 참조하십시오 [AEM용 구현 as a Cloud Service](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools) 개발 도구에 대해 자세히 알아보십시오.

## CRXDE Lite {#crxde-lite}

사용자는 개발 환경에서 CRXDE Lite에 액세스할 수 있지만, 스테이지나 프로덕션 환경에서는 액세스할 수 없습니다.

>[!IMPORTANT]
>다음과 같이 변경할 수 없는 저장소에 쓰기 `/libs` 및 `/apps` 런타임 시 오류가 발생합니다. 또한 스테이징 및 프로덕션 환경을 위한 개발자 도구에 대한 액세스 권한이 없습니다.

다음을 참조하십시오 [CRXDE Lite을 사용한 개발](/help/implementing/developing/tools/crxde.md) CRXDE Lite을 사용하여 AEM 애플리케이션을 개발하는 방법에 대한 자세한 내용을 보려면 .

## 로그 관리 {#managing-logs}

사용자는 선택한 환경에 사용할 수 있는 로그 파일 목록에 액세스할 수 있습니다.

다음을 참조하십시오 [로그 액세스 및 관리](/help/implementing/cloud-manager/manage-logs.md) 사용자 인터페이스를 통해 또는 Cloud Manager를 통해 API에서 로그에 액세스하고 관리하는 방법을 알아봅니다.

## 지원 문의 {#contacting-support}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_support"
>title="도움말 및 지원"
>abstract="자세한 설명이 필요하거나 문제를 해결하려면 Adobe의 AEM 지원 팀에 문의하십시오."
>additional-url="https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html" text="Experience Cloud 지원"

Cloud Service 액세스에 대한 질문이 있는 경우 Adobe 담당자에게 문의하거나 [Experience Cloud 지원](https://helpx.adobe.com/enterprise/using/support-for-experience-cloud.html) 을 참조하십시오.

## 문서 학습 {#document-learnings}

마이그레이션이 완료되면 이 프로세스 중에 얻은 지식을 문서화합니다. 설명서 프로세스에 도움이 될 수 있는 몇 가지 질문은 다음과 같습니다.

* 잘 작동한 것과 그렇지 않은 것은 무엇입니까?
* 주요 통증 사항은 무엇입니까?
* 향후 마이그레이션이 있는 경우 Recommendations으로 이동합니다.

이러한 마이그레이션 후 학습 내용을 조직 내의 관련자 및 팀과 공유합니다.

## 여정 종료 - 종료되었습니까? {#journey-ends}

축하합니다! AEM as a Cloud Service 마이그레이션 여정을 완료했습니다! 다음 방법을 이해할 수 있어야 합니다.

* AEM as a Cloud Service으로 이동 시작
* 배포를 AEM as a Cloud Service으로 이동할 준비가 되었는지 확인합니다.
* 코드 및 콘텐츠 클라우드 준비
* 마이그레이션 수행
* 문제 모니터링 및 성능 향상
