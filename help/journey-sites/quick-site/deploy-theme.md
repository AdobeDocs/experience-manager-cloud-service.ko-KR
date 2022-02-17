---
title: 사용자 지정 테마 배포
description: 파이프라인을 사용하여 사이트 테마를 배포하는 방법을 알아봅니다.
source-git-commit: 97c7590fd7b77e78cf2d465454fac80906d37803
workflow-type: tm+mt
source-wordcount: '1027'
ht-degree: 1%

---


# 사용자 지정 테마 배포 {#deploy-your-customized-theme}

파이프라인을 사용하여 사이트 테마를 배포하는 방법을 알아봅니다.

## 지금까지 그 이야기 {#story-so-far}

AEM 빠른 사이트 만들기 여정의 이전 문서에서, [사이트 테마 사용자 지정,](customize-theme.md) 테마를 만드는 방법, 테마를 사용자 지정하는 방법, 라이브 AEM 콘텐츠를 사용하여 테마를 테스트하는 방법을 배웠으며 이제 다음을 수행해야 합니다.

* 사이트 테마의 기본 구조 및 편집 방법을 이해합니다.
* 로컬 프록시를 통해 실제 AEM 콘텐츠를 사용하여 테마 사용자 지정을 테스트하는 방법을 참조하십시오.
* AEM Git 리포지토리에 변경 사항을 커밋하는 방법을 알아봅니다.

이제 마지막 단계를 수행한 다음 파이프라인을 사용하여 배포할 수 있습니다.

## 목표 {#objective}

이 문서에서는 파이프라인을 사용하여 테마를 배포하는 방법에 대해 설명합니다. 읽은 후에는 다음을 수행해야 합니다.

* 파이프라인 배포를 트리거하는 방법을 알아봅니다.
* 배포 상태를 확인하는 방법을 참조하십시오.

## 책임 역할 {#responsible-role}

이 여정 부분은 프런트 엔드 개발자에게 적용됩니다.

## 파이프라인 시작 {#start-pipeline}

테마 사용자 지정 변경 사항을 AEM Git 리포지토리에 커밋하면 다음을 실행할 수 있습니다 [관리자가 만든 파이프라인](pipeline-setup.md) 를 눌러 변경 사항을 배포합니다.

1. Cloud Manager에 로그인 [git 액세스 정보를 검색할 때](retrieve-access.md) 프로그램에 액세스합니다. 설정 **개요** 탭 다음에 대한 카드가 표시됩니다. **파이프라인**.

   ![Cloud Manager 개요](assets/cloud-manager-overview.png)

1. 시작할 파이프라인 옆에 있는 생략 부호를 탭하거나 클릭합니다. 드롭다운 메뉴에서 **실행**.

   ![파이프라인 실행](assets/run-pipeline.png)

1. 에서 **파이프라인 실행** 확인 대화 상자, 탭 또는 클릭 **예**.

   ![파이프라인 실행 확인](assets/pipeline-confirm.png)

1. 파이프라인 목록에서 상태 열은 현재 파이프라인이 실행 중임을 나타냅니다.

   ![파이프라인 실행 상태](assets/pipeline-running.png)

## 파이프라인 상태 확인 {#pipeline-status}

파이프라인의 상태를 확인하여 진행 상태를 언제든지 확인할 수 있습니다.

1. 파이프라인 옆에 있는 생략 부호를 탭하거나 클릭합니다.

   ![파이프라인 세부 사항 보기](assets/view-pipeline-details.png)

1. 파이프라인 세부 사항 창에는 파이프라인 진행 상태 분류가 표시됩니다.

   ![파이프라인 세부 사항](assets/pipeline-details.png)

>[!TIP]
>
>파이프라인 세부 사항 창에서 을 탭하거나 클릭할 수 있습니다 **다운로드 로그** 를 사용하면 디버깅을 위해 파이프라인의 모든 단계에서 단계가 실패합니다. 파이프라인을 디버깅하는 것이 이 여정 범위를 벗어납니다. 에서 Cloud Manager용 기술 문서 를 참조하십시오. [추가 리소스](#additional-resources) 섹션을 참조하십시오.

## 배포된 사용자 지정 확인 {#view-customizations}

파이프라인이 완료되면 관리자에게 변경 내용의 유효성을 확인할 것을 알릴 수 있습니다. 그러면 관리자가 다음을 수행합니다.

1. AEM 작성 환경을 엽니다.
1. 다음으로 이동 [관리자가 이전에 만든 사이트입니다.](create-site.md)
1. 컨텐츠 페이지 중 하나를 편집합니다.
1. 적용된 변경 사항을 참조하십시오.

![적용된 변경 사항](assets/changes-applied.png)

## 여정 종료? {#end-of-journey}

축하합니다! AEM 빠른 사이트 만들기 여정을 완료했습니다! 이제 다음을 수행해야 합니다.

* Cloud Manager와 프런트엔드 파이프라인이 프런트엔드 사용자 정의를 관리 및 배포하는 방법을 이해합니다.
* 템플릿을 기반으로 AEM 사이트를 만드는 방법과 사이트 테마를 다운로드하는 방법을 알아봅니다.
* AEM Git 리포지토리에 액세스할 수 있도록 프런트 엔드 개발자를 온보딩하는 방법입니다.
* 프록시된 AEM 콘텐츠를 사용하여 테마를 사용자 지정 및 테스트하고 이러한 변경 사항을 AEM Git에 커밋하는 방법입니다.
* 파이프라인을 사용하여 프런트 엔드 사용자 지정을 배포하는 방법입니다.

이제 자신만의 AEM 사이트의 테마를 사용자 지정할 준비가 되었습니다. 그러나 여러 프런트 엔드 파이프라인을 사용하여 서로 다른 작업 스트림을 만들기 전에 문서를 검토하십시오 [프런트엔드 파이프라인을 사용하여 사이트 개발](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) 이를 통해 다음과 같은 방법으로 프런트 엔드 개발을 최대한 활용할 수 있습니다.

* 한 가지 진실의 근원을 유지하는 것.
* 근심을 분리시키는 것.

AEM은 강력한 툴이며 다양한 추가 옵션을 사용할 수 있습니다. 에서 사용할 수 있는 추가 리소스 중 일부를 확인하십시오 [추가 리소스 섹션](#additional-resources) 추가 정보를 확인하십시오.

## 추가 리소스 {#additional-resources}

다음은 이 문서에서 언급된 몇 가지 개념을 자세히 설명하는 몇 가지 추가 리소스입니다.

* [사이트 레일을 사용하여 사이트 테마 관리](/help/sites-cloud/administering/site-creation/site-rail.md) - 사이트 레일의 강력한 기능을 학습하여 테마 소스 다운로드 및 테마 버전 관리 등 사이트 테마를 손쉽게 사용자 지정하고 관리할 수 있습니다.
* [AEM as a Cloud Service 기술 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html) - 이미 AEM에 대한 확고한 이해가 있는 경우 심층적인 기술 문서를 직접 참조할 수 있습니다.
* [Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Cloud Manager의 기능에 대한 자세한 내용은 세부 기술 문서를 직접 참조하십시오.
* [역할 기반 권한](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/role-based-permissions.html) - Cloud Manager에는 적절한 권한이 있는 미리 구성된 역할이 있습니다. 이러한 역할에 대한 자세한 내용 및 관리 방법은 이 문서를 참조하십시오.
* [Cloud Manager 저장소](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) - AEMaaCS 프로젝트용 Git 리포지토리를 설정 및 관리하는 방법에 대한 자세한 내용이 필요한 경우 이 문서를 참조하십시오.
* [CI/CD 파이프라인 구성 - Cloud Services](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) - 이 문서에서 전체 스택과 프런트 엔드 모두를 포함하는 파이프라인 설정에 대한 자세한 내용을 알아봅니다.
* [AEM Standard 사이트 템플릿](https://github.com/adobe/aem-site-template-standard) - AEM Standard Site 템플릿의 GitHub 리포지토리입니다.
* [AEM 사이트 테마](https://github.com/adobe/aem-site-template-standard-theme-e2e) - AEM 사이트 테마의 GitHub 리포지토리입니다.
* [npm](https://www.npmjs.com) - 사이트를 빠르게 구축하는 데 사용되는 AEM 테마는 npm을 기반으로 합니다.
* [웹 팩](https://webpack.js.org) - 사이트를 빠르게 구축하는 데 사용되는 AEM 테마는 웹 팩을 사용합니다.
* [페이지 생성 및 구성](/help/sites-cloud/authoring/fundamentals/organizing-pages.md) - 이 안내서에서는 템플릿에서 페이지를 만든 후 추가로 사용자 지정하려는 경우 AEM Site의 페이지를 관리하는 방법을 자세히 설명합니다.
* [패키지 작업 방법](/help/implementing/developing/tools/package-manager.md) - 패키지를 사용하면 저장소 컨텐츠를 가져오고 내보낼 수 있습니다. 이 문서에서는 AEMaaCS에도 적용되는 AEM 6.5에서 패키지를 사용하는 방법을 설명합니다.
* [온보딩 여정](/help/journey-onboarding/home.md) - 이 안내서는 AEM as a Cloud Service에 대한 액세스 및 팀 설정을 위한 시작점 역할을 합니다.
* [Adobe Experience Manager Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=ko-KR) - 기능에 대한 자세한 내용은 Cloud Manager 설명서를 참조하십시오.
* [사이트 관리 설명서](/help/sites-cloud/administering/site-creation/create-site.md) - 빠른 사이트 만들기 도구의 기능에 대한 자세한 내용은 사이트 작성 시 기술 문서를 참조하십시오.
* [프런트엔드 파이프라인을 사용한 사이트 개발](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) - 이 문서에서는 프런트 엔드 파이프라인을 사용하여 프런트 엔드 개발 프로세스에서 완전한 잠재성을 확보하기 위해 알아야 할 몇 가지 고려 사항에 대해 설명합니다.
