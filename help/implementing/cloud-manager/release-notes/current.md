---
title: Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.8.0 릴리스 정보
description: AEM as a Cloud Service의 Cloud Manager 2023.8.0 릴리스 정보입니다.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 99772a1a3faa454a9b07dd92c9e7622ddb37ce2d
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 24%

---


# Adobe Experience Manager as a Cloud Service의 Cloud Manager 2023.8.0 릴리스 정보 {#release-notes}

이 페이지에서는 AEM as a Cloud Service의 Cloud Manager 2023.8.0 릴리스 정보에 대해 설명합니다.

>[!NOTE]
>
>Adobe Experience Manager as a Cloud Service의 최신 릴리스 정보는 [이 페이지](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

## 릴리스 일자 {#release-date}

AEM as a Cloud Service의 Cloud Manager 2023.8.0 릴리스 일자는 2023년 8월 10일입니다. 다음 릴리스는 2023년 7월 9일에 예정되어 있습니다.

## 새로운 기능 {#what-is-new}

* 콘텐츠 세트 구성 시 [콘텐츠 복사,](/help/implementing/developing/tools/content-copy.md) [컨텍스트 인식 구성](/help/implementing/developing/introduction/configurations.md) 는 이제 UI의 콘텐츠 세트에서 허용됩니다.
* Cloud Manager UI에서 오류 메시지의 이해도와 노출을 개선했습니다.

## 조기 채택 프로그램 {#early-adoption}

초기 채택 프로그램의 일부가 되어 예정된 기능을 테스트할 수 있습니다.

### 셀프서비스 콘텐츠 복원 {#content-restore}

[새로운 셀프서비스 콘텐츠 복원 기능](/help/operations/restore.md) 이제 최대 7일 동안 백업 복원을 제공하며 얼리 어답터가 평가 목적으로 사용할 수 있습니다. 평가 기능은 다음과 같습니다.

* 이전 24시간 동안의 시점 백업 복원
* 최대 7일 동안 고정 시간 복원

이 새로운 기능을 테스트하고 피드백을 공유하려면 (으)로 이메일을 보내십시오. `aemcs-restorefrombackup-adopter@adobe.com` Adobe ID과 연계된 이메일. 참고:

* 얼리 어답터 프로그램은 개발 환경으로만 제한됩니다.
* 이 기능의 얼리어답터 프로그램 가용성은 제한됩니다.
* 이 기능은 실수로 삭제된 콘텐츠를 복구하기 위한 것으로, 재해 복구용이 아닙니다.

### 경험 감사 대시보드 {#experience-audit-dashboard}

[Cloud Manager 경험 감사 대시보드](/help/implementing/cloud-manager/experience-audit-dashboard.md) 에는 페이지 성능 점수의 트렌드 보기와 이를 개선하는 데 도움이 되는 통찰력 및 권장 사항이 포함되어 있습니다. 경험 감사는 Cloud Manager 프로덕션 파이프라인의 한 단계로 포함됩니다.

대시보드는 웹 앱의 품질을 개선하기 위한 오픈 소스 자동 도구인 Google Lighthouse를 활용합니다. 공개 또는 인증이 필요한 웹 페이지에 대해 실행할 수 있습니다. 여기에는 성능, 접근성, 점진적 웹 앱, SEO 등에 대한 감사가 있습니다.

새로운 대시보드를 테스트하는 데 관심이 있으십니까? (으)로 이메일을 보내십시오. `aem-lighthouse-pilot@adobe.com` Adobe ID과 연결된 이메일을 통해 시작할 수 있습니다.

## 버그 수정 {#bug-fixes}

* 다음 **환경** 이제 를 트리거한 후 메뉴가 닫힙니다. **[콘텐츠 복사](/help/implementing/developing/tools/content-copy.md)** 모달
* [파이프라인 재실행](/help/implementing/cloud-manager/deploy-code.md#reexecute-deployment) 이전 실행에 가 없는 경우 이 더 이상 허용되지 않습니다. `commitId` 빌드 단계 상태를 설정합니다.
* 이제 사용자가 의 파이프라인을 클릭하면 드물게 발생하는 오류에 대해 보다 이해하기 쉬운 메시지가 표시됩니다. **활동** 또는 **파이프라인** screens.
* 다음 `contentSetName` 값이 더 이상 로그에 누락되지 않고 이제 를 시작할 때 입력에 제공됩니다. [콘텐츠 복사](/help/implementing/developing/tools/content-copy.md) 작업.
* 동일한 파이프라인에서 두 번의 실행을 시작하여 &quot;중단&quot; 상태로 이어지는 특정 드문 상황에서는 더 이상 이 작업을 수행할 수 없습니다.
* 인증서가 만료되면 인증서와 연결된 도메인 이름 및 IP 허용 목록이 더 이상 CDN에서 제거되지 않습니다.
   * 이러한 경우 사이트에 계속 연결할 수 있습니다.
   * [](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)Cloud Manager UI는 더 눈에 띄는 방식으로 SSL 인증서가 만료 예정이라는 사전 경고를 제공합니다.
* Sites가 Assets 전용 프로그램의 솔루션으로 추가되는 상황에서 AEM이 게시 끝점에 액세스할 수 없는 문제가 수정되었습니다.
