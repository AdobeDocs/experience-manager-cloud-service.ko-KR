---
title: 클라우드 서비스로서의 Adobe Experience Manager(AEM)의 주요 변경 사항
description: 클라우드 서비스로서의 Adobe Experience Manager(AEM)의 주요 변경 사항
translation-type: ht
source-git-commit: e5e329f674f5e2817f6feb26e3a7720c8d26d333
workflow-type: ht
source-wordcount: '861'
ht-degree: 100%

---


# 클라우드 서비스로서의 Adobe Experience Manager(AEM)의 주요 변경 사항 {#notable-changes-aem-cloud}

AEM 클라우드 서비스는 AEM 프로젝트 관리를 위한 많은 새로운 기능과 가능성을 제공합니다. 그러나 온프레미스 또는 Adobe Managed Service의 AEM Sites에는 AEM 클라우드 서비스와 비교하여 많은 차이점이 있습니다. 이 문서에서는 중요한 차이점을 조명합니다.

>[!NOTE]
>이 문서에서는 전반적인 AEM에 대한 주요 변경 사항을 조명합니다. 자세한 내용 및 솔루션별 변경 사항은 다음을 참조하십시오.
>
>* [클라우드 서비스로서의 Adobe Experience Manager 소개](/help/overview/introduction.md)
>* 클라우드 서비스로서의 Adobe Experience Manager와 이전 버전 간의 [새로운 기능과 차이점](/help/overview/what-is-new-and-different.md)
>* 클라우드 서비스로서의 Adobe Experience Manager [아키텍처](/help/core-concepts/architecture.md)
>* [ 클라우드 서비스로서의 AEM Sites에 대한 주요 변경 사항](/help/sites-cloud/sites-cloud-changes.md)
>* [클라우드 서비스로서의 AEM Assets에 대한 주요 변경 사항](/help/assets/assets-cloud-changes.md)


기본 차이점은 다음 영역에서 찾을 수 있습니다.

* [런타임 시 /apps 및 /libs를 변경할 수 없습니다](#apps-libs-immutable)

* [OSGi 번들 및 설정은 리포지토리 기반이어야 합니다](#osgi)

* [게시 리포지토리에 대한 변경이 허용되지 않습니다](#changes-to-publish-repo)

* [사용자 지정 실행 모드가 허용되지 않습니다](#custom-runmodes)

* [복제 에이전트 제거](#replication-agents)

* [클래식 UI 제거](#classic-ui)

* [게시 측 제공](#publish-side-delivery)

* [자산 처리 및 제공](#asset-handling)

## 런타임 시 /apps 및 /libs를 변경할 수 없습니다 {#apps-libs-immutable}

`/apps` 및 `/libs`의 모든 컨텐츠 및 하위 폴더는 읽기 전용입니다. 변경이 필요한 모든 기능 또는 사용자 지정 코드가 변경되지 않습니다. 해당 컨텐츠는 읽기 전용이고 쓰기 작업을 완료할 수 없다는 오류가 반환됩니다. 이것은 AEM의 많은 영역에 영향을 줍니다.

* `/libs`의 변경 사항이 전혀 허용되지 않습니다.
   * 이것이 새로운 규칙은 아니지만, AEM의 이전 온프레미스 버전에서는 강제 사항이 아니었습니다.
* 오버레이가 허용된 `/libs`의 영역에 대한 오버레이가 여전히 `/apps` 내에서 허용됩니다.
   * 이러한 오버레이는 CI/CD 파이프라인을 통해 Git에서 가져와야 합니다.
* `/apps`에 저장된 정적 템플릿 디자인 정보는 UI를 통해 편집할 수 없습니다.
   * 대신 편집 가능한 템플릿을 사용하는 것이 좋습니다.
   * 정적 템플릿이 여전히 필요한 경우 구성 정보는 CI/CD 파이프라인을 통해 Git에서 가져와야 합니다.
* MSM 블루프린트 및 사용자 지정 MSM 롤아웃 구성은 CI/CD 파이프라인을 통해 Git에서 설치해야 합니다.
* I18n 번역 변경 사항은 CI/CD 파이프라인을 통해 Git에서 가져와야 합니다.

## OSGi 번들 및 설정은 리포지토리 기반이어야 합니다. {#osgi}

이전 AEM 버전에서 OSGi 설정을 변경하는 데 사용되는 웹 콘솔을 AEM 클라우드 서비스에서는 사용할 수 없습니다. 따라서 OSGi에 대한 변경 사항은 CI/CD 파이프라인을 통해 가져와야 합니다.

* OSGi 설정에 대한 변경은 JCR 기반 OSGi 설정으로서 Git 지속성을 통해서만 가능합니다.
* 새로운 OSGi 번들이나 업데이트된 OSGi 번들은 CI/CD 파이프라인 빌드 프로세스의 일부로서 Git을 통해 가져와야 합니다.

## 게시 리포지토리에 대한 변경이 허용되지 않습니다 {#changes-to-publish-repo}

AEM 클라우드 서비스에서는 게시 리포지토리에 대한 직접 변경을 수행할 수 없습니다. 이전 버전의 온프레미스 AEM 또는 AMS의 AEM에서는 사용자를 생성하고 사용자 프로필을 업데이트하며 노드를 만드는 등의 작업을 위해 게시 리포지토리에서 바로 코드를 변경할 수 있었습니다. 이러한 작업은 이제 불가능하고 다음 방법으로 보완할 수 있습니다.

* 컨텐츠 및 컨텐츠 기반 구성의 경우: 작성 인스턴스에서 변경 작업을 수행한 다음 게시합니다.
* 코드 및 구성의 경우: GIT 리포지토리에서 변경 작업을 수행한 다음, CI/CD 파이프라인을 실행하여 롤아웃합니다.
* 양식 제출 또는 프로필 데이터와 같은 사용자 관련 데이터의 경우: Experience Cloud Platform이나 기타 타사 세션 인식 스토어의 통합 프로필 서비스를 사용합니다.

## 사용자 지정 실행 모드가 허용되지 않습니다 {#custom-runmodes}

AEM 클라우드 서비스에 대해 즉시 사용할 수 있도록 다음 실행 모드가 제공됩니다.

* `author`
* `publish`
* `prod`
* `author.prod`
* `publish.prod`
* `stage`
* `author.stage`
* `publish.stage`
* `dev`
* `author.dev`
* `publish.dev`

추가적인 실행 모드나 사용자 지정 실행 모드는 AEM 클라우드 서비스에서 사용할 수 없습니다.

## 복제 에이전트 제거 {#replication-agents}

AEM 클라우드 서비스에서는 컨텐츠가 [Sling 컨텐츠 배포](https://sling.apache.org/documentation/bundles/content-distribution.html)를 사용하여 게시됩니다. 이전 AEM 버전에서 사용된 복제 에이전트는 이제 사용되지 않거나 제공되지 않으며, 이것은 기존 AEM 프로젝트의 다음 영역에 영향을 줄 수 있습니다.

* 예를 들어 미리 보기 서버의 복제 에이전트에 컨텐츠를 푸시하는 사용자 지정 워크플로우.
* 컨텐츠를 변환하기 위한 복제 에이전트에 대한 사용자 지정
* 역복제를 사용하여 게시의 컨텐츠를 다시 작성으로 가져오기

## 클래식 UI 제거 {#classic-ui}

클래식 UI는 AEM 클라우드 서비스에서 이제 사용할 수 없습니다.

## 게시 측 제공 {#publish-side-delivery}

CDN과 작성 및 게시 서비스에 대한 트래픽 관리를 비롯한 HTTP 가속은 AEM 클라우드 서비스에서 기본적으로 제공됩니다.

AMS 또는 온프레미스 설치에서 프로젝트 전환의 경우에는 AEM 클라우드 서비스 내의 기능이 제공된 CDN에 맞게 최적화되므로 기본 CDN을 활용하는 것이 좋습니다.

## 자산 처리 및 제공 {#asset-handling}

자산 업로드, 처리 및 다운로드가 보다 효율적으로 수행되도록 AEM 클라우드 서비스에서 최적화되었기 때문에 더욱 효율적인 크기 조절과 더 빠른 업로드 및 다운로드가 가능합니다. 그러나 이는 일부 기존 사용자 지정 코드에 영향을 줄 수 있습니다.

* 이전 AEM 버전의 기본 워크플로우 **DAM 자산 업데이트**&#x200B;는 이제 사용할 수 없습니다.
* **변환하지 않은** 바이너리를 제공하는 웹 사이트 구성 요소는 직접 다운로드를 사용해야 합니다.
   * Sling GET 서블릿은 기본적으로 이를 수행하도록 변경되었습니다.
* **변환한** 바이너리를 전달하는 웹 사이트 구성 요소(예: 서블릿을 통한 크기 조정)는 계속 이전처럼 수행할 수 있습니다.
* 패키지 관리자를 통해 들어오는 자산은 Assets 인터페이스의 **자산 재처리** 작업을 사용하여 수동으로 다시 처리해야 합니다.
