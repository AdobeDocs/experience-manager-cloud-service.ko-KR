---
title: Adobe Experience Manager (AEM) as a Cloud Service의 주요 변경 사항
description: Adobe Experience Manager (AEM) as a Cloud Service의 주요 변경 사항.
exl-id: fe11d779-66cd-45aa-aa6b-c819b88d2405
source-git-commit: 30edc83364dd9666b94f54048abc8b7f92ad6ce3
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 97%

---

# Adobe Experience Manager as a Cloud Service의 주요 변경 사항 {#notable-changes-aem-cloud}

AEM(Adobe Experience Manager) 클라우드 서비스는 AEM 프로젝트 관리를 위한 많은 새로운 기능과 가능성을 제공합니다. 그러나 온프레미스 또는 Adobe Managed Service의 AEM Sites에는 AEM Cloud Service와 비교하여 몇 가지 차이점이 있습니다. 이 문서에서는 중요한 차이점을 조명합니다.

>[!CONTEXTUALHELP]
>id="aem_cloud_notable_changes"
>title="AEM as a Cloud Service의 주요 변경 내용"
>abstract="이 탭에서는 AEM as a Cloud Service와 비교하여 AEM 온프레미스 또는 Adobe Managed Services 간의 차이점을 이해하는 데 도움이 되는 콘텐츠를 볼 수 있습니다."
>additional-url="https://video.tv.adobe.com/v/330543" text="AEM as a Cloud Service의 발전"


>[!NOTE]
>이 문서에서는 전반적인 AEM에 대한 주요 변경 사항을 조명합니다. 자세한 내용 및 솔루션별 변경 사항은 다음을 참조하십시오.
>
>* [Adobe Experience Manager as a Cloud Service 소개](/help/overview/introduction.md)
>* Adobe Experience Manager as a Cloud Service와 이전 버전 간의 [새로운 기능과 차이점](/help/overview/what-is-new-and-different.md)
>* Adobe Experience Manager as a Cloud Service [아키텍처](/help/overview/architecture.md)
>* [AEM Sites as a Cloud Service에 대한 주요 변경 사항](/help/sites-cloud/sites-cloud-changes.md)
>* [AEM Assets as a Cloud Service에 대한 주요 변경 사항](/help/assets/assets-cloud-changes.md)

주요 차이점은 다음 영역에서 찾을 수 있습니다.

* [런타임 시 /apps 및 /libs를 변경할 수 없습니다](#apps-libs-immutable)

* [OSGi 번들 및 구성은 코드로 처리되어야 합니다.](#osgi)

* [게시 저장소에 대한 변경이 허용되지 않습니다](#changes-to-publish-repo)

* [맞춤형 실행 모드가 허용되지 않습니다](#custom-runmodes)

* [복제 에이전트 제거 및 관련 변경 사항](#replication-agents)

* [클래식 UI 제거](#classic-ui)

* [게시측 게재](#publish-side-delivery)

* [자산 처리 및 게재](#asset-handling)

## 런타임 시 /apps 및 /libs를 변경할 수 없습니다 {#apps-libs-immutable}

`/apps` 및 `/libs`의 모든 콘텐츠 및 하위 폴더는 읽기 전용입니다. 변경이 필요한 모든 기능 또는 사용자 정의 코드가 변경되지 않습니다. 해당 콘텐츠는 읽기 전용이고 쓰기 작업을 완료할 수 없다는 오류가 반환됩니다. 이는 AEM의 많은 영역에 영향을 줍니다.

* `/libs`의 변경 사항이 전혀 허용되지 않습니다.
   * 이는 새로운 규칙은 아니지만 AEM의 이전 온프레미스 버전에서는 강제 사항이 아니었습니다.
* 오버레이할 수 있는 `/libs`의 영역에 대한 오버레이가 여전히 `/apps`에서 허용됩니다.
   * 이러한 오버레이는 CI/CD 파이프라인을 통해 Git에서 가져와야 합니다.
* `/apps`에 저장된 정적 템플릿 디자인 정보는 UI를 통해 편집할 수 없습니다.
   * 대신 편집 가능한 템플릿을 사용하는 것이 좋습니다.
   * 정적 템플릿이 여전히 필요한 경우 구성 정보는 CI/CD 파이프라인을 통해 Git에서 가져와야 합니다.
* MSM 블루프린트 및 사용자 정의 MSM 롤아웃 구성은 CI/CD 파이프라인을 통해 Git에서 설치해야 합니다.
* I18n 번역 변경 사항은 CI/CD 파이프라인을 통해 Git에서 가져와야 합니다.

## OSGi 번들 및 구성은 코드로 처리되어야 합니다. {#osgi}

OSGi 번들 및 구성에 대한 변경 내용은 CI/CD 파이프라인을 통해 가져와야 합니다.

* 새로운 OSGi 번들이나 업데이트된 OSGi 번들은 CI/CD 파이프라인을 통해 Git을 통해 가져와야 합니다.
* OSGi 구성에 대한 변경 내용은 CI/CD 파이프라인을 통해서만 Git에서 가져올 수 있습니다.

이전 AEM 버전에서 OSGi 번들 및 구성을 변경하는 데 사용되는 웹 콘솔을 AEM Cloud Service에서는 사용할 수 없습니다.

## 게시 저장소에 대한 변경이 허용되지 않습니다 {#changes-to-publish-repo}

게시 계층의 `/home` 폴더 아래에 있는 변경 사항 외에 게시 저장소에 대한 직접 변경은 AEM Cloud Service에서 허용되지 않습니다. 이전 버전의 온프레미스 AEM 또는 AMS의 AEM에서는 게시 저장소에 직접 코드를 변경할 수 있었습니다. 다음과 같은 방법으로 일부 제한 사항을 완화할 수 있습니다.

* 콘텐츠 및 콘텐츠 기반 구성의 경우: 작성자 인스턴스에서 변경 작업을 수행한 다음 게시합니다.
* 코드 및 구성의 경우: GIT 저장소에서 변경 작업을 수행한 다음 CI/CD 파이프라인을 실행하여 롤아웃합니다.

## 맞춤형 실행 모드가 허용되지 않습니다 {#custom-runmodes}

추가적인 실행 모드나 사용자 정의 실행 모드는 AEM Cloud Service에서 사용할 수 없습니다. AEM Cloud Service에 대해 즉시 사용할 수 있도록 제공되는 실행 모드 목록에 대해서는 문서를 참조하십시오 [AEM에 as a Cloud Service 배포](/help/implementing/deploying/overview.md#runmodes)

## 복제 에이전트 제거 및 관련 변경 사항 {#replication-agents}

AEM Cloud Service에서는 콘텐츠가 [Sling 콘텐츠 배포](https://sling.apache.org/documentation/bundles/content-distribution.html)를 사용하여 게시됩니다. 이전 AEM 버전에서 사용된 복제 에이전트는 이제 사용되지 않거나 제공되지 않으며, 이는 기존 AEM 프로젝트의 다음 영역에 영향을 줄 수 있습니다.

* 예를 들어 미리보기 서버의 복제 에이전트에 콘텐츠를 푸시하는 사용자 정의 워크플로.
* 콘텐츠를 변환하기 위한 복제 에이전트에 대한 사용자 정의.
* 역복제를 사용하여 게시의 콘텐츠를 다시 작성으로 가져오기.

또한 일시 중지 및 비활성화 버튼이 복제 에이전트 관리 콘솔에서 제거됩니다.

## 클래식 UI 제거 {#classic-ui}

클래식 UI는 AEM Cloud Service에서 더 이상 사용할 수 없습니다.

## 게시측 게재 {#publish-side-delivery}

CDN과 작성 및 게시 서비스에 대한 트래픽 관리를 비롯한 HTTP 가속은 AEM Cloud Service에서 기본적으로 제공됩니다.

AMS 또는 온프레미스 설치에서 프로젝트 전환의 경우에는 AEM Cloud Service 내의 기능이 제공된 CDN에 맞게 최적화되므로 기본 CDN을 사용하는 것이 좋습니다.

## 자산 처리 및 게재 {#asset-handling}

자산 업로드, 처리 및 다운로드는 [!DNL Experience Manager Assets] as a [!DNL Cloud Service]에서 최적화됩니다. AEM [!DNL Assets]는 이제 더 효율적이고 더 많은 확장이 가능하며 더 빠른 속도로 업로드 및 다운로드할 수 있습니다. 또한 기존 맞춤형 코드 및 일부 작업에도 영향을 줍니다. 변경 사항 목록 및 [!DNL Experience Manager] 6.5 기능과의 패리티는 [ [!DNL Assets]](/help/assets/assets-cloud-changes.md) 변경 사항을 참조하십시오.
