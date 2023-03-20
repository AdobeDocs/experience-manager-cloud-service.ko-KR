---
title: Go-Live 후
description: 문제를 모니터링하고 성능을 향상시키는 방법을 알아봅니다
exl-id: 487f0b51-501b-48fc-a796-3cb8a6d64462
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 25%

---

# Go-Live 후 {#post-go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_troubleshooting"
>title="AEM 문제 해결"
>abstract="개발자 콘솔 및 CRXDE Lite과 같은 도구와 함께 지속적인 개발에 대한 우수 사례를 검토하고 로그를 관리하여 AEM의 문제 해결을 지원합니다"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-logs.html" text="로그 액세스 및 관리"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html#aem-as-a-cloud-service-development-tools" text="AEM as a Cloud Service 개발 도구"

여정의 마지막 부분이므로 마이그레이션이 완료되면 문제를 모니터링하고 성능을 향상시키는 방법을 알아봅니다. 임시 파일을 정리하고, 지속적인 개발을 위한 우수 사례를 검토하고, 로그를 관리해야 합니다.

## 지금까지의 스토리 {#story-so-far}

여정의 이전 단계에서 마이그레이션 및 [Go-live](/help/journey-migration/go-live.md) 코드와 컨텐츠를 AEM as a Cloud Service으로 이동할 준비가 되면.

## 목표 {#objective}

이 문서에서는 AEM as a Cloud Service 환경 문제를 해결하는 데 사용할 수 있는 도구에 대해 설명합니다.

* **개발자 콘솔**
* **CRXDE Lite**
* **로그 관리**

## 개발자 콘솔 {#developer-console}

AEM as a Cloud Service 개발자 환경을 디버깅하는 방법은 개발자 콘솔에서 개발, 스테이지 및 프로덕션 환경에 사용할 수 있습니다.

개발 도구에 대한 자세한 내용은 [AEM as a Cloud Service 구현](/help/implementing/developing/introduction/development-guidelines.md#aem-as-a-cloud-service-development-tools)을 참조하십시오.

## CRXDE Lite {#crxde-lite}

사용자는 개발 환경에서 CRXDE Lite에 액세스할 수 있지만, 스테이지나 프로덕션 환경에서는 액세스할 수 없습니다.

>[!IMPORTANT]
>같은 변경할 수 없는 저장소에 쓰기 `/libs` 및 `/apps` 런타임 시 오류가 발생합니다. 또한 스테이징 및 프로덕션 환경을 위한 개발자 도구에 액세스할 수 없습니다.

CRXDE Lite를 사용하여 AEM 애플리케이션을 개발하는 방법에 대해 알아보려면 [CRXDE Lite를 사용한 개발](/help/implementing/developing/tools/crxde.md)을 참조하십시오.

## 로그 관리 {#managing-logs}

사용자는 선택한 환경에 사용할 수 있는 로그 파일 목록에 액세스할 수 있습니다.

UI를 통해 또는 Cloud Manager를 통해 API에서 로그에 액세스하고 관리하는 방법에 대해 알아보려면 [로그 액세스 및 관리](/help/implementing/cloud-manager/manage-logs.md)를 참조하십시오.

## 지원 문의 {#contacting-support}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_support"
>title="도움말 및 지원"
>abstract="AEM 지원 팀에 문의하여 명확히 하거나 문제를 해결할 수 있습니다."
>additional-url="https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html" text="Experience Cloud 지원"

Cloud Service 액세스에 대한 질문이 있는 경우 Adobe 담당자에게 문의하거나 [Experience Cloud 지원](https://helpx.adobe.com/kr/enterprise/using/support-for-experience-cloud.html) 자세한 내용

## 문서 학습 {#document-learnings}

마이그레이션이 완료되면 이 프로세스 동안 얻은 지식을 문서화해야 합니다. 설명서 프로세스에 도움이 될 수 있는 몇 가지 질문은 다음과 같습니다.

* 무엇이 잘 작동했고 무엇이 그렇지 않았습니까?
* 가장 큰 통증은 무엇이었습니까?
* 향후 마이그레이션의 경우 Recommendations.

그런 다음 이러한 마이그레이션 후 지식을 조직 내의 이해 관계자 및 팀과 공유해야 합니다.

## 여정 종료 - 종료되었습니까? {#journey-ends}

축하합니다! AEM as a Cloud Service 마이그레이션 여정을 완료했습니다! 다음 방법을 이해해야 합니다.

* AEM as a Cloud Service으로 이동 시작
* 배포가 AEM as a Cloud Service으로 이동할 준비가 되었는지 확인합니다.
* 코드 및 컨텐츠 클라우드를 준비합니다.
* 마이그레이션 수행
* 문제 모니터링 및 성능 향상
