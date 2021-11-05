---
title: 사이트 테마 사용자 지정
description: 사이트 테마가 빌드되는 방법, 사용자 지정 방법 및 라이브 AEM 콘텐츠를 사용하여 테스트하는 방법을 알아봅니다.
source-git-commit: 348e26a9af260d89841d19d00ce4102c00ae34ed
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 0%

---


# 사이트 테마 사용자 지정 {#customize-the-site-theme}

사이트 테마가 빌드되는 방법, 사용자 지정 방법 및 라이브 AEM 콘텐츠를 사용하여 테스트하는 방법을 알아봅니다.

>[!CAUTION]
>
>빠른 사이트 만들기 도구는 현재 기술 미리 보기입니다. 테스트 및 평가 목적으로 사용할 수 있으며, Adobe 지원에 동의하지 않는 프로덕션 용도에는 사용할 수 없습니다.

## 지금까지 그 이야기 {#story-so-far}

AEM 빠른 사이트 만들기 여정의 이전 문서에서, [Git 리포지토리 액세스 정보 검색,](retrieve-access.md) 프런트 엔드 개발자 사용자 Cloud Manager가 git 리포지토리 정보에 액세스하는 방법을 알았고 이제 다음을 수행해야 합니다.

* Cloud Manager의 기능을 개략적으로 이해합니다.
* 사용자 지정 사항을 커밋할 수 있도록 자격 증명을 검색하여 AEM Git에 액세스했습니다.

여정의 이 부분에서는 다음 단계를 수행하여 사이트 테마를 검색하고 검색한 액세스 자격 증명을 사용하여 사용자 지정을 사용자 지정한 후 커밋하는 방법을 보여 줍니다.

## 목표 {#objective}

이 문서에서는 AEM 사이트 테마가 빌드되는 방법, 사이트 테마를 사용자 지정하는 방법 및 라이브 AEM 콘텐츠를 사용하여 테스트하는 방법을 설명합니다. 읽은 후에는 다음을 수행해야 합니다.

* 사이트 테마의 기본 구조 및 편집 방법을 이해합니다.
* 로컬 프록시를 통해 실제 AEM 콘텐츠를 사용하여 테마 사용자 지정을 테스트하는 방법을 참조하십시오.
* AEM Git 리포지토리에 변경 사항을 커밋하는 방법을 알아봅니다.

## 책임 역할 {#responsible-role}

이 여정 부분은 프런트 엔드 개발자에게 적용됩니다.

## 테마 구조 이해 {#understand-theme}

AEM 관리자가 제공하는 테마를 원하는 위치로 추출하여 기본 편집기에서 엽니다.

![테마 편집](assets/edit-theme.png)

주제는 전형적인 프런트 엔드 프로젝트입니다. 구조의 가장 중요한 부분은 다음과 같습니다.

* `src/main.ts`: JS 및 CSS 테마의 기본 시작 지점
* `src/site`: 전체 사이트에 적용되는 JS 및 CSS 파일
* `src/components`: AEM 구성 요소별 JS 및 CSS 파일
* `src/resources`: 아이콘, 로고 및 글꼴과 같은 정적 파일

>[!TIP]
>
>표준 AEM 사이트 테마에 대한 자세한 내용은 [추가 리소스](#additional-resources) 섹션을 참조하십시오.

테마 프로젝트의 구조에 익숙해지면 로컬 프록시를 시작하여 실제 AEM 콘텐츠를 기반으로 모든 테마 사용자 지정을 실시간으로 볼 수 있습니다.

## 로컬 프록시 시작 {#starting-proxy}

1. 명령줄에서 로컬 컴퓨터의 테마 루트로 이동합니다.
1. 실행 `npm install` 및 npm은 종속성을 검색하고 프로젝트를 설치합니다.

   ![npm 설치](assets/npm-install.png)

1. 실행 `npm run live` 프록시 서버가 시작됩니다.

   ![npm 실행 라이브](assets/npm-run-live.png)

1. 프록시 서버가 시작되면 브라우저가 자동으로 `http://localhost:7001/`. 탭 또는 클릭 **로컬로 로그인(관리 작업만 해당)** AEM 관리자가 제공한 프록시 사용자 자격 증명으로 로그온합니다.

   ![로컬로 로그인](assets/sign-in-locally.png)

1. 로그인하고 나면 AEM 관리자가 제공한 샘플 컨텐츠 경로를 가리키도록 브라우저의 URL을 변경합니다.

   * 예를 들어, 제공된 경로가 `/content/<your-site>/en/home.html?wcmmode=disabled`
   * URL을 `http://localhost:7001/content/<your-site>/en/home.html?wcmmode=disabled`

   ![프록시된 샘플 컨텐츠](assets/proxied-sample-content.png)

사이트를 탐색하여 컨텐츠를 탐색할 수 있습니다. 실제 컨텐츠에 대한 테마 사용자 지정을 만들 수 있도록 라이브 AEM 인스턴스에서 사이트를 라이브로 가져옵니다.

## 테마 사용자 지정 {#customize-theme}

이제 테마 사용자 지정을 시작할 수 있습니다. 다음은 프록시를 통해 변경 사항을 실시간으로 볼 수 있는 방법을 보여주는 간단한 예입니다.

1. 편집기에서 파일을 엽니다 `<your-theme-sources>/src/site/_variables.scss`

   ![테마 편집](assets/edit-theme.png)

1. 변수 편집 `$color-background` 그리고 흰색이 아닌 값으로 설정합니다. 이 예제에서는 `orange` 이 사용됩니다.

   ![편집된 테마](assets/edited-theme.png)

1. 파일을 저장하면 프록시 서버가 줄을 통해 변경 사항을 인식한다는 것을 알 수 있습니다 `[Browsersync] File event [change]`.

   ![프록시 브라우저 동기화](assets/proxy-browsersync.png)

1. 프록시 서버의 브라우저로 다시 전환하면 변경 사항이 즉시 표시됩니다.

   ![주황색 테마](assets/orange-theme.png)

AEM 관리자가 제공한 요구 사항에 따라 테마를 계속 사용자 지정할 수 있습니다.

## 변경 내용 커밋 {#committing-changes}

사용자 지정 사항이 완료되면 AEM Git 리포지토리에 커밋할 수 있습니다. 먼저 리포지토리를 로컬 시스템에 복제해야 합니다.

1. 명령줄에서 보고서를 복제할 위치로 이동합니다.
1. 명령을 실행합니다 [이전에 Cloud Manager에서 검색됨.](retrieve-access.md) 비슷해야 합니다 `git clone https://git.cloudmanager.adobe.com/<my-org>/<my-program>/`. 다음 Git 사용자 이름 및 암호를 사용합니다 [이 여정의 이전 부분에서 읽어들입니다.](retrieve-access.md)

   ![리포지토리 복제](assets/clone-repo.png)

1. 편집 중인 테마 프로젝트를 다음과 유사한 명령을 사용하여 복제된 보고서로 이동합니다. `mv <site-theme-sources> <cloned-repo>`
1. 복제된 리포지토리의 디렉토리에서 다음 명령을 사용하여 방금 이동한 테마 파일을 커밋합니다.

   ```text
   git add .
   git commit -m "Adding theme sources"
   git push
   ```

1. 사용자 지정 항목이 AEM Git 리포지토리에 푸시됩니다.

   ![커밋된 변경 사항](assets/changes-committed.png)

사용자 지정 사항도 이제 AEM Git 리포지토리에 안전하게 저장됩니다.

## 다음은 무엇입니까? {#what-is-next}

이제 AEM 빠른 사이트 만들기 여정의 이 부분을 완료했으므로 다음을 수행해야 합니다.

* 사이트 테마의 기본 구조 및 편집 방법을 이해합니다.
* 로컬 프록시를 통해 실제 AEM 콘텐츠를 사용하여 테마 사용자 지정을 테스트하는 방법을 참조하십시오.
* AEM Git 리포지토리에 변경 사항을 커밋하는 방법을 알아봅니다.

이 지식을 바탕으로 작성하고 다음 문서를 검토하여 AEM 빠른 사이트 만들기 여정을 계속 진행합니다 [맞춤형 테마 배포,](deploy-theme.md) 여기서 프런트 엔드 파이프라인을 사용하여 테마를 배포하는 방법을 배웁니다.

## 추가 리소스 {#additional-resources}

문서를 검토하여 빠른 사이트 만들기 여정의 다음 부분으로 이동하는 것이 좋습니다 [맞춤형 테마 배포,](deploy-theme.md) 다음은 이 문서에서 언급된 일부 개념을 자세히 설명하는 몇 가지 추가 선택적 리소스입니다. 여정을 계속 진행할 필요는 없습니다.

* [AEM 사이트 테마](https://github.com/adobe/aem-site-template-standard-theme-e2e) - AEM 사이트 테마의 GitHub 리포지토리입니다.
* [npm](https://www.npmjs.com) - 사이트를 빠르게 구축하는 데 사용되는 AEM 테마는 npm을 기반으로 합니다.
* [웹 팩](https://webpack.js.org) - 사이트를 빠르게 구축하는 데 사용되는 AEM 테마는 웹 팩을 사용합니다.