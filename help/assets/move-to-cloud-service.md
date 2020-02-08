---
title: Adobe Experience Manager 6.x에서 클라우드 서비스로 마이그레이션
description: Adobe Experience Manager 6.x에서 클라우드 서비스로 마이그레이션
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Adobe Experience Manager Assets로 클라우드 서비스로 이동 {#move-to-assets-cloud-service}

<!-- About the need to move from previous AEM deployment to a cloud service deployment. And how does Adobe help do it OOTB?
-->

## 마이그레이션 도구 정보 {#migration-tool}

<!-- 
Link back to information about the tool in the Experience Manager as a Cloud Service docs if the tool works the same for Sites and Assets. Document the Assets-specific information here.

* What is the migration tool called? Is there a branding term for it?
* How much do we want to elaborate about the Pattern Detector rules? Is there a branding term for it?
* Before migrating using the tool, is any prepping required?
* See CQ-4271901

-->

마이그레이션 도구는 다음을 수행하는 데 도움이 됩니다.

* 기존 워크플로우 모델을 Assets Compute Service에서 작동하는 처리 프로필로 변환합니다.
* 워크플로우 모델에서 지원되지 않는 단계를 제거합니다.
* 워크플로우 런처를 비활성화합니다.
* 기존 소스 코드에 사용자 확인/확인 후 구성을 병합합니다.

마이그레이션 도구는 사용자가 다음 두 가지 방법으로 사용할 수 있는 처리 프로필을 Maven 모듈에 생성합니다.

* 기존 프로젝트로 병합
* 모듈을 새 하위 모듈로 추가합니다.

마이그레이션 도구는 변경 사항에 대한 보고서와 변경 사항에 대한 정보를 제공합니다.

<!--  

What is the output of the tool, besides migrated content.

Give details about reports and logs of the tool. 

* How to access the report, including required permissions.
* How to read/interpret the report.
* Location of logs. How to read the logs.
* What common errors to look for. Troubleshooting for these errors.

-->

## 컨텐츠를 새로운 배포로 마이그레이션 {#content-migration-across-deployments}
