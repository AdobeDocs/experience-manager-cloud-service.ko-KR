---
title: 파이프라인 설정
description: 프런트 엔드 파이프라인을 만들어 사이트 테마의 사용자 지정을 관리합니다.
exl-id: 0d77d1a6-98f3-4961-9283-f52c1b5b2a7b
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '976'
ht-degree: 0%

---

# 파이프라인 설정 {#set-up-your-pipeline}

프런트 엔드 파이프라인을 만들어 사이트 테마의 사용자 지정을 관리합니다.

## 지금까지 그 이야기 {#story-so-far}

AEM 빠른 사이트 만들기 여정의 이전 문서에서, [템플릿에서 사이트 만들기,](create-site.md) 사이트 템플릿을 사용하여 프런트 엔드 도구를 사용하여 추가로 사용자 지정할 수 있는 AEM 사이트를 빠르게 만드는 방법을 배웠으며, 이제 다음을 수행해야 합니다.

* AEM 사이트 템플릿을 가져오는 방법을 이해합니다.
* 템플릿을 사용하여 새 사이트를 만드는 방법을 알아봅니다.
* 프런트엔드 개발자에게 제공하기 위해 새 사이트에서 템플릿을 다운로드하는 방법을 참조하십시오.

이 문서는 이러한 기본 사항을 기반으로 하여 프런트엔드 파이프라인을 설정할 수 있도록 합니다. 이 파이프라인은 나중에 여정에서 사용하여 프런트엔드 사용자 지정을 배포합니다.

## 목표 {#objective}

이 문서는 프런트 엔드 파이프라인을 이해하고 사이트 사용자 지정 테마의 배포를 관리하는 파이프라인을 만드는 방법을 관리하는 데 도움이 됩니다. 읽은 후에는 다음을 수행해야 합니다.

* 프런트엔드 파이프라인이 무엇인지 파악합니다.
* Cloud Manager에서 프런트엔드 파이프라인을 설정하는 방법을 알아봅니다.

## 책임 역할 {#responsible-role}

이 여정 부분은 Cloud Manager 관리자에게 적용됩니다.

## 요구 사항 {#requirements}

* Cloud Manager에 액세스할 수 있어야 합니다.
* Adobe Analytics Mobile Apps 또는 Analytics Premium의 **배포 관리자** Cloud Manager의 역할.
* AEM 환경에 대한 Git 보고서는 Cloud Manager에서 설정해야 합니다.
   * 일반적으로 활성 프로젝트의 경우에는 이미 이러한 경우가 있습니다. 그러나 그렇지 않으면, 아래의 Cloud Manager 저장소 설명서를 참조하십시오 [추가 리소스](#additional-resources) 섹션을 참조하십시오.

## 프런트엔드 파이프라인이란? {#front-end-pipeline}

프런트 엔드 개발에는 AEM 사이트의 스타일을 정의하는 JavaScript, CSS 및 정적 리소스의 사용자 지정이 포함됩니다. 프런트 엔드 개발자는 고유한 로컬 환경에서 이러한 사용자 지정을 수행합니다. 준비가 되면 변경 사항이 AEM Git 리포지토리에 커밋됩니다. 그러나 소스 코드에만 커밋됩니다. 그들은 아직 살아 있지 않다.

프런트엔드 파이프라인은 이러한 커밋된 사용자 지정 사항을 가져와 AEM 환경, 일반적으로 프로덕션 또는 비프로덕션 환경에 배포합니다.

이러한 방식으로 프런트 엔드 개발은 자체 배포 파이프라인이 있는 AEM의 모든 전체 스택 백 엔드 개발과는 별도로 및 병렬로 작동할 수 있습니다.

>[!NOTE]
>
>프런트엔드 파이프라인은 JavaScript, CSS 및 정적 리소스만 배포하여 AEM 사이트를 스타일을 지정할 수 있습니다. 페이지 또는 자산과 같은 사이트 컨텐츠는 파이프라인에 배포할 수 없습니다.

## Cloud Manager 액세스 {#login}

1. Cloud Manager에 로그인 위치: [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).

1. Cloud Manager는 사용 가능한 다양한 프로그램을 나열합니다. 관리할 항목을 탭하거나 클릭합니다. AEM as a Cloud Service으로 시작하는 경우에는 하나의 프로그램만 사용할 수 있습니다.

   ![Cloud Manager에서 프로그램 선택](assets/cloud-manager-select-program.png)

이제 프로그램 개요가 표시됩니다. 페이지는 다르게 보이지만 이 예제와 비슷합니다.

![Cloud Manager 개요](assets/cloud-manager-overview.png)

액세스하거나 URL을 복사한 프로그램의 이름을 확인합니다. 이 기능은 나중에 프런트 엔드 개발자에게 제공해야 합니다.

## 프런트엔드 파이프라인 만들기 {#create-front-end-pipeline}

이제 Cloud Manager에 액세스했으므로 프런트 엔드 배포를 위한 파이프라인을 만들 수 있습니다.

1. 에서 **파이프라인** Cloud Manager 페이지의 섹션에서 **추가** 버튼을 클릭합니다.

   ![파이프라인](assets/pipelines-add.png)

1. 팝업 메뉴에서 **추가** 버튼 선택 **비프로덕션 파이프라인 추가** 참조하십시오.

1. 설정 **구성** 의 탭 **비프로덕션 파이프라인 추가** 대화 상자가 열립니다.
   * 선택 **배포 파이프라인**.
   * 에서 이름을 파이프라인에 제공합니다. **비프로덕션 파이프라인 이름** 필드.

   ![파이프라인 구성 추가](assets/add-pipeline-configuration.png)

1. 탭 또는 클릭 **계속**.

1. 설정 **소스 코드** 탭:
   * 선택 **프런트 엔드 코드** 를 배포할 코드 유형입니다.
   * 에서 올바른 환경을 선택했는지 확인합니다. **적합한 배포 환경**.
   * 올바른 을 선택합니다. **저장소**.
   * 정의 **Git 분기** 파이프라인과 연결해야 합니다.
   * 을(를) 정의합니다 **코드 위치** 프런트 엔드 개발이 선택한 저장소의 특정 경로 아래에 있는 경우 기본값은 저장소의 루트이지만 프런트 엔드 개발 및 백 엔드는 다른 경로에 있습니다.

   ![파이프라인을 추가하기 위한 소스 코드 정보](assets/add-pipeline-source-code.png)

1. **저장**&#x200B;을 탭하거나 클릭합니다.

새 파이프라인이 만들어지고 여기에서 표시됩니다 **파이프라인** 섹션을 참조하십시오. 파이프라인 이름 뒤에 생략 부호를 탭하면 필요에 따라 세부 사항을 편집하거나 볼 수 있는 옵션이 표시됩니다.

![파이프라인 옵션](assets/new-pipeline.png)

>[!TIP]
>
>이미 AEMaaCS의 파이프라인에 익숙하며, 프런트 엔드 파이프라인에 대한 세부 사항을 포함하여 서로 다른 유형 파이프라인 간의 차이에 대해 자세히 알려면 에 연결된 CI/CD 파이프라인 구성 - Cloud Services 을 참조하십시오 [추가 리소스](#additional-resources) 섹션을 참조하십시오.

## 다음은 무엇입니까? {#what-is-next}

이제 AEM 빠른 사이트 만들기 여정의 이 부분을 완료했으므로 다음을 수행해야 합니다.

* 프런트엔드 파이프라인이 무엇인지 파악합니다.
* Cloud Manager에서 프런트엔드 파이프라인을 설정하는 방법을 알아봅니다.

이 지식을 바탕으로 작성하고 다음 문서를 검토하여 AEM 빠른 사이트 만들기 여정을 계속 진행합니다 [프런트엔드 개발자에게 액세스 권한 부여,](grant-access.md) 여기서 프런트엔드 개발자를 Cloud Manager에 온보딩하여 AEM 사이트 git 리포지토리 및 파이프라인에 액세스할 수 있습니다.

## 추가 리소스 {#additional-resources}

문서를 검토하여 빠른 사이트 만들기 여정의 다음 부분으로 이동하는 것이 좋습니다 [사이트 테마 사용자 지정,](customize-theme.md) 다음은 이 문서에서 언급된 일부 개념을 자세히 설명하는 몇 가지 추가 선택적 리소스입니다. 여정을 계속 진행할 필요는 없습니다.

* [Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Cloud Manager의 기능에 대한 자세한 내용은 세부 기술 문서를 직접 참조하십시오.
* [Cloud Manager 저장소](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) - AEMaaCS 프로젝트용 Git 리포지토리를 설정 및 관리하는 방법에 대한 자세한 내용이 필요한 경우 이 문서를 참조하십시오.
* [CI/CD 파이프라인 구성 - Cloud Services](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) - 이 문서에서 전체 스택과 프런트 엔드 모두를 포함하는 파이프라인 설정에 대한 자세한 내용을 알아봅니다.
