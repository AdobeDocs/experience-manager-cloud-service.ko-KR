---
title: Git 리포지토리 액세스 정보 검색
description: 프런트 엔드 개발자가 Cloud Manager를 사용하여 git 리포지토리 정보에 액세스하는 방법을 알아봅니다.
exl-id: 3ef1cf86-6da4-4c09-9cfc-acafc8f6dd5c
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 4%

---

# Git 리포지토리 액세스 정보 검색 {#retrieve-access}

프런트 엔드 개발자가 Cloud Manager를 사용하여 git 리포지토리 정보에 액세스하는 방법을 알아봅니다.

## 지금까지 그 이야기 {#story-so-far}

사이트 테마의 사용자 지정을 담당하는 프런트엔드 개발자인 경우, AEM 설정 방법에 대한 지식이 필요하지 않으며, 로 건너뛸 수 있습니다 [목표](#objective) 섹션을 참조하십시오.

Cloud Manager 또는 AEM 관리자 및 프런트 엔드 개발자의 역할을 수행하는 경우 AEM 빠른 사이트 작성 여정의 이전 문서에서 다음을 배웠습니다. [프런트엔드 개발자에게 액세스 권한 부여,](grant-access.md) 프런트엔드 개발자가 git 리포지토리에 액세스할 수 있도록 온보딩하는 방법, 이제 다음을 알아야 합니다.

* 프런트엔드 개발자를 사용자로 추가하는 방법
* 프런트 엔드 개발자에게 필요한 역할을 부여하는 방법입니다.

이 문서는 프런트 엔드 개발자가 Cloud Manager 액세스를 사용하여 AEM Git 저장소에 액세스하기 위해 자격 증명을 검색하는 방법을 보여주는 다음 단계를 수행합니다.

템플릿을 기반으로 만든 사이트가 있고 파이프라인 설정이 있으며 프런트 엔드 개발자는 온보딩되며 필요한 모든 정보를 가지고 있으므로 이 문서는 관리자로부터 멀리 떨어진 동시에 프런트 엔드 개발자 역할으로만 전환됩니다.

## 목표 {#objective}

이 문서에서는 프런트 엔드 개발자 역할에서 Cloud Manager에 액세스하고 AEM Git 리포지토리에 대한 액세스 자격 증명을 검색하는 방법에 대해 설명합니다. 읽는 동안 다음을 수행합니다.

* Cloud Manager의 기능을 개략적으로 이해합니다.
* 사용자 지정 사항을 커밋할 수 있도록 자격 증명을 검색하여 AEM Git에 액세스했습니다.

## 책임 역할 {#responsible-role}

이 여정 부분은 프런트 엔드 개발자에게 적용됩니다.

## 요구 사항 {#requirements}

프런트 엔드 개발자는 빠른 사이트 작성 도구를 사용하여 AEM의 설정 방법이나 설정에 대한 지식이 없어도 독립적으로 작업할 수 있습니다. 그러나 Cloud Manager 관리자는 프런트 엔드 개발자를 프로젝트 팀에 온보딩해야 하며, AEM 관리자는 필요한 정보를 제공해야 합니다. 계속하기 전에 다음 정보가 있는지 확인하십시오.

* AEM 관리자로부터 다음을 수행합니다.
   * 사용자 지정할 테마 원본 파일
   * 참조 기반으로 사용할 예제 페이지의 경로
   * 라이브 AEM 컨텐츠에 대한 사용자 지정을 테스트하는 프록시 사용자 자격 증명
   * 프런트엔드 설계 요구 사항
* Cloud Manager 관리자로부터 다음을 수행합니다.
   * 액세스 권한을 알려주는 Cloud Manager의 환영 이메일.
   * Cloud Manager 내에서 프로그램의 이름 또는 URL입니다

이러한 항목이 누락된 경우 AEM 관리자 또는 Cloud Manager 관리자에게 문의하십시오.

프런트 엔드 개발자는 다음과 같은 일반적인 도구와 함께 프런트 엔드 개발 워크플로우에 대한 광범위한 경험을 가지고 있다고 가정합니다.

* git
* npm
* 웹 팩
* 기본 설정 편집기

## Cloud Manager 이해 {#understanding-cloud-manager}

조직에서 Cloud Manager를 사용하여 클라우드에서 AEM을 자체 관리할 수 있습니다. IT팀 및 구현 파트너가 성능 또는 보안을 손상하지 않고 사용자 지정 내용 또는 업데이트를 신속하게 전달할 수 있는 CI/CD(지속적 통합 및 지속적 배포) 프레임워크가 포함되어 있습니다.

프런트엔드 개발자의 경우,

* 프런트엔드 사용자 지정을 커밋할 수 있도록 AEM Git 리포지토리 정보에 액세스합니다.
* 배포 파이프라인을 시작하여 사용자 지정을 배포합니다.

Cloud Manager 관리자는 Cloud Manager 사용자로 온보딩합니다. 다음과 유사한 환영 이메일을 받았어야 합니다.

![환영 이메일](assets/welcome-email.png)

이 이메일을 받지 못한 경우 Cloud Manager 관리자에게 문의하십시오.

## Cloud Manager 액세스 {#access-cloud-manager}

1. Adobe Experience Cloud에 로그인 위치 [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) 또는 환영 이메일에 제공된 링크를 클릭합니다.

1. Cloud Manager는 사용 가능한 다양한 프로그램을 나열합니다. Cloud Manager 관리자가 제공하는 대로 액세스해야 하는 아이콘을 탭하거나 클릭합니다. AEMaaCS의 첫 번째 프런트 엔드 프로젝트인 경우 하나의 프로그램만 사용할 수 있습니다.

   ![Cloud Manager에서 프로그램 선택](assets/cloud-manager-select-program.png)

이제 프로그램 개요가 표시됩니다. 페이지는 다르게 보이지만 이 예제와 비슷합니다.

![Cloud Manager 개요](assets/cloud-manager-overview.png)

## 저장소 액세스 정보 검색 {#repo-access}

1. 에서 **파이프라인** Cloud Manager 페이지의 섹션에서 **보고서 정보에 액세스** 버튼을 클릭합니다.

   ![파이프라인](assets/pipelines-repo-info.png)

1. 다음 **저장소 정보** 대화 상자가 열립니다.

   ![보고서 정보](assets/repo-info.png)

1. 을(를) 탭하거나 클릭합니다 **암호 생성** 직접 암호를 만드는 단추입니다.

1. 보안 암호 관리자에 생성된 암호를 저장합니다. 암호가 다시 표시되지 않습니다.

1. 또한 **사용자 이름** 및 **Git 명령줄** 필드. 나중에 이 정보를 사용하여 보고서에 액세스합니다.

1. 탭 또는 클릭 **닫기**.

## 다음은 무엇입니까? {#what-is-next}

이제 AEM 빠른 사이트 만들기 여정의 이 부분을 완료했으므로 다음을 수행해야 합니다.

* Cloud Manager의 기능을 개략적으로 이해합니다.
* 사용자 지정 사항을 커밋할 수 있도록 자격 증명을 검색하여 AEM Git에 액세스했습니다.

이 지식을 바탕으로 작성하고 다음 문서를 검토하여 AEM 빠른 사이트 만들기 여정을 계속 진행합니다 [사이트 테마 사용자 지정,](customize-theme.md) 사이트 테마가 빌드되는 방법, 사용자 지정 방법 및 라이브 AEM 콘텐츠를 사용하여 테스트하는 방법을 알아봅니다.

## 추가 리소스 {#additional-resources}

문서를 검토하여 빠른 사이트 만들기 여정의 다음 부분으로 이동하는 것이 좋습니다 [사이트 테마 사용자 지정,](customize-theme.md) 다음은 이 문서에서 언급된 일부 개념을 자세히 설명하는 몇 가지 추가 선택적 리소스입니다. 여정을 계속 진행할 필요는 없습니다.

* [Adobe Experience Manager Cloud Manager 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=ko-KR) - 기능에 대한 자세한 내용은 Cloud Manager 설명서를 참조하십시오.
