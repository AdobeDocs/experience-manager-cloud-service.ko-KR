---
title: 클라우드 서비스로 Adobe Experience Manager(AEM)의 주목할 만한 변경 사항
description: 클라우드 서비스로 Adobe Experience Manager(AEM)의 주목할 만한 변경 사항
translation-type: tm+mt
source-git-commit: e76de9b84931dced6383570e384ffdb6fb334daf

---


# 클라우드 서비스로 Adobe Experience Manager(AEM)의 주목할 만한 변경 사항 {#notable-changes-aem-cloud}

AEM Cloud 서비스는 AEM 프로젝트 관리에 대한 많은 새로운 기능과 가능성을 제공합니다. 그러나 AEM Cloud Service와 비교하여 온프레미스 또는 Adobe Managed Service에 있는 AEM Sites 간에는 많은 차이점이 있습니다. 이 문서에서는 중요한 차이점을 강조 표시합니다.

>[!NOTE]
>이 문서에서는 AEM 전체에 대한 주목할 만한 변경 사항을 강조 표시합니다. 솔루션별 변경 사항은 다음을 참조하십시오.
>
>* [AEM Cloud Service의 AEM Sites에 대한 주목할 만한 변경 사항](/help/sites-cloud/sites-cloud-changes.md)
>* [AEM Cloud Service의 AEM 자산에 대한 주목할 만한 변경 사항](/help/assets/assets-cloud-changes.md)


주요 차이점은 다음 영역에서 찾을 수 있습니다.

* [런타임 시 /apps 및 /libs를 변경할 수 없습니다.](#apps-libs-immutable)
* [OSGi 번들 및 설정은 저장소 기반이어야 합니다.](#osgi)
* [게시 보관소에 대한 변경 사항은 허용되지 않습니다.](#changes-to-publish-repo)
* [사용자 정의 실행 모드는 허용되지 않습니다.](#custom-runmodes)
* [복제 에이전트 제거](#replication-agents)
* [클래식 UI 제거](#classic-ui)
* [게시 측 배달](#publish-side-delivery)
* [자산 처리 및 배달](#asset-handling)

## 런타임 시 /apps 및 /libs를 변경할 수 없습니다. {#apps-libs-immutable}

의 모든 콘텐트 및 하위 `/apps` 폴더는 읽기 `/libs` 전용입니다. 변경이 필요한 모든 기능 또는 사용자 지정 코드는 변경되지 않습니다. 해당 컨텐츠가 읽기 전용이고 쓰기 작업을 완료할 수 없다는 오류가 반환됩니다. 이는 AEM의 여러 영역에 영향을 줍니다.

* 의 변경은 전혀 허용되지 `/libs` 않습니다.
   * 이것은 새로운 규칙이 아니지만, AEM의 이전 온-프레미스 버전에서 적용되지 않았습니다.
* 오버레이가 허용된 영역에 `/libs` 대한 오버레이는 여전히 내에서 허용됩니다 `/apps`.
   * 이러한 오버레이는 CI/CD 파이프라인을 통해 Git에서 가져와야 합니다.
* 에 저장된 정적 템플릿 디자인 정보는 UI를 통해 편집할 `/apps` 수 없습니다.
   * 편집 가능한 템플릿을 대신 사용하는 것이 좋습니다.
   * 정적 템플릿이 여전히 필요한 경우 구성 정보는 CI/CD 파이프라인을 통해 Git에서 가져와야 합니다.
* MSM Blueprint 및 사용자 정의 MSM 롤아웃 구성은 CI/CD 파이프라인을 통해 Git에서 설치해야 합니다.
* I18n 변환 변경 사항은 CI/CD 파이프라인을 통해 Git에서 가져와야 합니다.

## OSGi 번들 및 설정은 저장소 기반이어야 합니다. {#osgi}

AEM의 이전 버전에서 OSGi 설정을 변경하는 데 사용되는 웹 콘솔은 AEM Cloud 서비스에서 사용할 수 없습니다. 따라서 OSGi에 대한 변경 사항은 CI/CD 파이프라인을 통해 도입해야 합니다.

* OSGi 설정에 대한 변경 사항은 JCR 기반 OSGi 설정으로 Git 지속성을 통해서만 가능합니다.
* CI/CD 파이프라인 빌드 프로세스의 일부로 새로운 OSGi 번이나 업데이트된 OSGi 번들을 Git을 통해 도입해야 합니다.

## 게시 보관소에 대한 변경 사항은 허용되지 않습니다. {#changes-to-publish-repo}

AEM Cloud Service에서는 게시 리포지토리에 직접 변경을 수행할 수 없습니다. AMS에 있는 온프레미스 AEM 또는 AEM의 이전 버전에서는 사용자를 만들고 사용자 프로필을 업데이트하며 노드를 만들기 위해 코드를 직접 게시 리포지토리로 변경할 수 있습니다. 더 이상 이 작업을 수행할 수 없으며 다음과 같은 방법으로 수정할 수 있습니다.

* 컨텐츠 및 컨텐츠 기반 구성의 경우:작성 인스턴스에서 변경 사항을 적용하고 게시합니다.
* 코드 및 구성:git 리포지토리에서 변경 사항을 적용하고 CI/CD 파이프라인을 실행하여 롤아웃합니다.
* 양식 제출 또는 프로필 데이터와 같은 사용자 관련 데이터의 경우:experience Cloud Platform 또는 기타 타사 세션 인식 스토어에서 통합 프로필 서비스를 사용하십시오.

## 사용자 정의 실행 모드는 허용되지 않습니다. {#custom-runmodes}

AEM Cloud Service에 대해 즉시 사용 가능한 실행 모드는 다음과 같습니다.

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

AEM Cloud Service에서는 추가 또는 사용자 정의 실행 모드를 사용할 수 없습니다.

## 복제 에이전트 제거 {#replication-agents}

AEM Cloud Service에서 컨텐츠는 Sling 콘텐츠 [배포를 사용하여 게시됩니다](https://sling.apache.org/documentation/bundles/content-distribution.html). 이전 버전의 AEM에서 사용된 복제 에이전트가 더 이상 사용되지 않거나 제공되지 않으므로 기존 AEM 프로젝트의 다음 영역에 영향을 줄 수 있습니다.

* 예를 들어 미리 보기 서버의 복제 에이전트로 컨텐츠를 전달하는 사용자 정의 워크플로우입니다.
* 복제 에이전트를 사용자 정의하여 컨텐츠 변환
* 역방향 복제를 사용하여 게시에서 작성자로 컨텐츠 다시 가져오기

## 클래식 UI 제거 {#classic-ui}

AEM Cloud 서비스에서 클래식 UI를 더 이상 사용할 수 없습니다.

## 게시 측 배달 {#publish-side-delivery}

CDN 및 작성자 및 게시 서비스에 대한 트래픽 관리를 비롯한 HTTP 가속은 기본적으로 AEM Cloud Service에서 제공됩니다.

AMS 또는 온-프레미스 설치에서 프로젝트를 전환하는 경우 AEM Cloud Service 내의 기능이 제공된 CDN에 맞게 최적화되므로 내장 CDN을 적극 활용하는 것이 좋습니다.

## 자산 처리 및 배달 {#asset-handling}

자산 업로드, 처리 및 다운로드는 AEM Cloud Service에서 보다 효율적으로 크기 조정 및 보다 빠른 업로드 및 다운로드를 할 수 있도록 최적화되었습니다. 그러나 이는 일부 기존 사용자 지정 코드에 영향을 줄 수 있습니다.

* 이전 버전의 **AEM에서** 기본 워크플로 DAM 자산 업데이트를 더 이상 사용할 수 없습니다.
* 변형 **없이 바이너리를** 제공하는 웹 사이트 구성 요소는 직접 다운로드를 사용해야 합니다.
   * Sling GET 서블릿이 기본적으로 이렇게 변경되었습니다.
* 변형 **(예: servlet을 통한 크기 조정)을** 통해 바이너리를 전달하는 웹 사이트 구성 요소는 계속 작업할 수 있습니다.
* 패키지 관리자를 통해 들어오는 자산은 자산 인터페이스의 자산 재처리 **작업을 사용하여** 수동으로 다시 처리해야 합니다.
