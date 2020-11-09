---
title: AEM as a Cloud Service에 배포
description: 'AEM as a Cloud Service에 배포 '
translation-type: tm+mt
source-git-commit: 450d78be9472c854a13ba35965ac10f806aba3d9
workflow-type: tm+mt
source-wordcount: '3210'
ht-degree: 0%

---


# AEM as a Cloud Service에 배포 {#deploying-to-aem-as-a-cloud-service}

## 소개 {#introduction}

코드 개발의 기본 사항은 AEM 온-프레미스 및 Managed Services 솔루션에 비해 AEM의 Cloud Service과 유사합니다. 개발자는 코드를 작성하고 로컬로 테스트한 다음 Cloud Service 환경으로 원격 AEM으로 푸시됩니다. Managed Services의 선택적 컨텐츠 전달 툴인 Cloud Manager가 필요합니다. 이제 Cloud Service 환경으로 AEM에 코드를 배포하는 유일한 메커니즘입니다.

AEM 버전 [업데이트는](/help/implementing/deploying/aem-version-updates.md) 사용자 지정 코드 [푸시와는 항상 별도의 배포 이벤트입니다](#customer-releases). 다른 방식으로 보면, 사용자 지정 코드 릴리스는 맨 위에 배포될 것이므로 제작 중인 AEM 버전에 대해 테스트되어야 합니다. AEM 버전 업데이트 이후 발생하는 업데이트로 자주 업데이트되며 자동으로 적용됩니다. 이미 배포된 고객 코드와 역호환되도록 설계되었습니다.

이 문서의 나머지 부분에서는 개발자가 Cloud Service 버전 업데이트 및 고객 업데이트로 AEM과 연동되도록 모범 사례를 적용하는 방법을 설명합니다.

>[!NOTE]
>기존 코드 베이스를 사용하는 고객은 [AEM 설명서에 설명된 저장소 구조 조정 연습을 수행하는 것이 좋습니다](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html).

## 고객 릴리스 {#customer-releases}

### 올바른 AEM 버전에 맞게 코딩 {#coding-against-the-right-aem-version}

이전 AEM 솔루션의 경우, 최신 AEM 버전은 가끔(약 분기별 서비스 팩이 있는 경우 대략 매년) 변경되었으며, 고객은 API Jar를 참조하여 프로덕션 인스턴스를 최신 빠른 시점으로 업데이트합니다. 그러나 Cloud Service 애플리케이션으로 AEM은 최신 버전의 AEM으로 자동 업데이트되므로 최신 AEM 버전에 대해 사용자 정의 코드를 작성해야 합니다.

기존의 비 클라우드 AEM 버전과 마찬가지로 특정 빠른 시작을 기반으로 한 로컬 오프라인 개발이 지원되며 대부분의 경우 디버깅을 위해 선택할 수 있는 도구가 될 것입니다.

>[!NOTE]
>애플리케이션이 로컬 시스템에서 작동하는 방식과 Adobe Cloud를 사용하는 방식 간에는 미묘한 차이가 있습니다. 이러한 아키텍처 차이는 로컬 개발 시 존중되어야 하며 클라우드 인프라에 배포할 때 다른 행동을 초래할 수 있습니다. 이러한 차이점 때문에 프로덕션에서 새로운 사용자 지정 코드를 롤아웃하기 전에 개발 및 준비 환경에서 철저한 테스트를 수행하는 것이 중요합니다.

내부 릴리스에 대한 사용자 정의 코드를 개발하려면 Cloud Service SDK로서 [AEM의 관련 버전을](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) 다운로드하여 설치해야 합니다. AEM을 Cloud Service 발송자 도구로 사용하는 방법에 대한 자세한 내용은 [이 페이지를 참조하십시오](/help/implementing/dispatcher/disp-overview.md).

다음 비디오에서는 코드를 Cloud Service으로 AEM에 배포하는 방법에 대한 고급 개요를 제공합니다.

>[!VIDEO](https://video.tv.adobe.com/v/30191?quality=9)

>[!NOTE]
>기존 코드 베이스를 사용하는 고객은 [AEM 설명서에 설명된 저장소 구조 조정 연습을 수행하는 것이 좋습니다](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html).

## Cloud Manager 및 Package Manager를 통해 콘텐츠 패키지 배포 {#deploying-content-packages-via-cloud-manager-and-package-manager}

### Cloud Manager를 통한 배포 {#deployments-via-cloud-manager}

고객은 Cloud Manager를 통해 클라우드 환경에 맞춤형 코드를 배포합니다. Cloud Manager는 로컬에 어셈블된 컨텐츠 패키지를 Sling Feature Model에 맞는 아티팩트로 변환한다는 점을 주의해야 합니다. 이 경우 AEM은 클라우드 환경에서 실행할 때 Cloud Service 애플리케이션으로 사용되는 방식입니다. 따라서 클라우드 환경의 패키지 관리자에서 패키지를 볼 때 이름이 &quot;cp2fm&quot;이고 변형된 패키지의 메타데이터가 모두 제거됩니다. 상호 작용을 할 수 없습니다. 즉, 다운로드, 복제 또는 열 수 없습니다. 변환기에 대한 자세한 설명은 여기에서 [확인할 수 있습니다](https://github.com/apache/sling-org-apache-sling-feature-cpconverter).

Cloud Service 애플리케이션으로 AEM용으로 작성된 컨텐츠 패키지는 변경할 수 없는 컨텐츠와 변경할 수 없는 컨텐츠 간의 완벽한 분리가 있어야 하며 Cloud Manager는 빌드하지 않고 다음과 같은 메시지를 게시함으로써 이를 적용합니다.

`Generated content-package <PACKAGE_ID> located in file <PATH> is of MIXED type`

이 섹션의 나머지 부분에서는 변경할 수 없고 변경할 수 없는 패키지의 구성 및 의미를 설명합니다.

### 변경할 수 없는 컨텐츠 패키지 {#immutabe-content-packages}

불변의 저장소에 남아 있는 모든 컨텐츠와 코드는 Cloud Manager를 통해 git에 체크 인하고 배포해야 합니다. 즉, 현재 AEM 솔루션과 달리 코드는 실행 중인 AEM 인스턴스에 직접 배포되지 않습니다. 이렇게 하면 모든 클라우드 환경에서 지정된 릴리스에 대해 실행되는 코드가 동일하므로 제작 시 의도하지 않은 코드 변형의 위험을 없앨 수 있습니다. 예를 들어 OSGI 구성은 런타임 시 AEM 웹 콘솔의 구성 관리자를 통해 관리되는 것이 아니라 소스 제어에 커밋되어야 합니다.

Blue-Green 배포 패턴으로 인한 애플리케이션 변경 사항은 스위치에서 사용할 수 있으므로 서비스 사용자, ACL, 노드 유형 및 색인 정의 변경을 제외하고 변경 가능한 저장소의 변경 사항에 따라 달라질 수 없습니다.

기존 코드 베이스를 사용하는 고객의 경우 AEM 설명서에 설명된 저장소 구조 조정 연습을 통해 이전에 /etc 아래에 있던 컨텐츠가 올바른 위치로 이동되도록 하는 것이 중요합니다.

## OSGI 구성 {#osgi-configuration}

위에서 언급한 바와 같이 OSGI 구성은 웹 콘솔을 통해 하는 것이 아니라 소스 제어에 커밋되어야 합니다. 이를 위한 기술은 다음과 같습니다.

* AEM 웹 콘솔의 구성 관리자를 사용하여 개발자의 로컬 AEM 환경에서 필요한 변경 작업을 수행한 다음 로컬 파일 시스템의 AEM 프로젝트로 결과 내보내기
* 로컬 파일 시스템의 AEM 프로젝트에서 속성 이름에 대한 AEM 콘솔의 구성 관리자를 참조하는 OSGI 구성을 수동으로 만듭니다.

AEM용 OSGi를 Cloud Service으로 [구성에서 OSGI 구성에 대한 자세한 내용을 참조하십시오](/help/implementing/deploying/configuring-osgi.md).

## 변경 가능한 컨텐츠 {#mutable-content}

경우에 따라 환경이 업데이트될 때마다 Cloud Manager에서 배포할 수 있도록 소스 제어에서 컨텐츠 변경 사항을 준비하는 것이 유용할 수 있습니다. 예를 들어, 특정 루트 폴더 구조를 시안하거나 편집 가능한 템플릿의 변경 사항을 줄여서 애플리케이션 배포로 업데이트된 구성 요소의 정책을 활성화하는 것이 적절할 수 있습니다.

Cloud Manager에서 제공하는 컨텐츠를 변경 가능한 저장소, 변경 가능한 컨텐츠 패키지 및 설명 문으로 설명하는 두 가지 전략이 있습니다.

### 변경 가능한 컨텐츠 패키지 {#mutable-content-packages}

폴더 경로 계층, 서비스 사용자 및 ACL(액세스 제어)과 같은 컨텐츠는 일반적으로 마웬 원형 기반 AEM 프로젝트에 커밋됩니다. 이러한 기술에는 AEM에서 내보내거나 XML로 직접 쓰기가 포함됩니다. 구축 및 배포 과정에서 Cloud Manager는 결과 변경 가능한 컨텐츠 패키지를 패키징합니다. 파이프라인의 배포 단계 동안 변경 가능한 컨텐츠가 3회에 서로 다르게 설치됩니다.

새로운 버전의 애플리케이션을 시작하기 전에

* 색인 정의(추가, 수정, 제거)

응용 프로그램의 새 버전을 시작하는 동안, 전환 전에 다음을 수행합니다.

* 서비스 사용자(추가)
* 서비스 사용자 ACL(추가)
* 노드 유형(추가)

응용 프로그램의 새 버전으로 전환 후:

* Jackrabbit Vault를 통해 정의할 수 있는 기타 모든 컨텐츠 예:
   * 폴더(추가, 수정, 제거)
   * 편집 가능한 템플릿(추가, 수정, 제거)
   * 컨텍스트 인식 구성(아래 `/conf`의 모든 것)(추가, 수정, 제거)
   * 스크립트(패키지 설치 과정에서 다양한 단계에 후크 설치 가능)

아래 install.author 또는 install.publish 폴더에 패키지를 포함하여 변경 가능한 컨텐츠 설치를 작성자 또는 게시로 제한할 수 있습니다 `/apps`. 권장 프로젝트 재조정 관련 [AEM 문서에서](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/restructuring/repository-restructuring.html) 자세히 살펴보십시오.

>[!NOTE]
>컨텐츠 패키지는 모든 환경 유형(dev, stage, prod)에 배포됩니다. 특정 환경으로 배포를 제한할 수 없습니다. 이 제한은 자동 실행의 테스트 실행 옵션을 보장하기 위해 적용됩니다. 환경에 적합한 컨텐츠를 사용하려면 패키지 관리자를 통해 수동으로 설치해야 합니다.

변경 가능한 컨텐츠 패키지 변경 사항을 적용한 후 롤백하는 메커니즘이 없습니다. 고객이 문제를 감지하면 다음 코드 릴리스나 마지막 방법으로 문제를 해결하도록 선택하여 배포 전 특정 시점으로 전체 시스템을 복구할 수 있습니다.

포함된 모든 타사 패키지는 Cloud Service 서비스 호환 시 AEM으로 확인되어야 하며, 그렇지 않은 경우 포함되면 배포 오류가 발생합니다.

위에서 언급한 바와 같이, 기존 코드 베이스를 사용하는 고객은 [AEM 설명서에 설명된 리포지토리 재조정 연습을 따라야 합니다](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/repository-restructuring.html).

## 리포인트 {#repoinit}

다음과 같은 경우 OSGI 공장 구성에서 명시적 컨텐츠 생성 `repoinit` 문을 직접 코딩하는 방법을 사용하는 것이 좋습니다.

* 서비스 사용자 만들기/삭제/비활성화
* 그룹 만들기/삭제
* 사용자 만들기/삭제
* ACL 추가

   >[!NOTE]
   >
   >ACL을 정의하려면 노드 구조가 이미 있어야 합니다. 따라서 앞서 경로 문을 만들어야 할 수도 있습니다.

* 경로 추가(예: 루트 폴더 구조)
* CND(Nodetype 정의) 추가

다음의 이점으로 인해 지원되는 컨텐츠 수정 사용 사례의 경우 이 권장 사항을 사용하는 것이 좋습니다.

* 리포인트는 시작 시 리소스를 생성하므로 로직은 이러한 리소스를 당연하게 활용할 수 있습니다. 변경할 수 있는 컨텐츠 패키지 방식에서는 시작 후 리소스가 생성되므로 이에 의존하는 애플리케이션 코드가 실패할 수 있습니다.
* 리포인트는 수행할 작업을 명시적으로 제어할 때 비교적 안전한 명령입니다. 또한, 지원되는 작업은 사용자, 서비스 사용자 및 그룹을 제거할 수 있는 몇 가지 보안 관련 사례를 제외하고 부가적입니다. 반대로 변경 가능한 컨텐츠 패키지 접근 방식에서는 어떤 것이 제거된다는 것은 명백하다. 필터를 정의하면 필터가 적용되는 모든 항목이 삭제됩니다. 그러나 새 컨텐츠가 있으면 애플리케이션의 동작을 변경할 수 있는 시나리오가 있으므로 주의해야 합니다.
* 리포인트는 빠르고 원자적인 작업을 수행합니다. 반대로 변경 가능한 컨텐츠 패키지는 필터에 의해 적용되는 구조에 따라 성능이 크게 달라질 수 있습니다. 단일 노드를 업데이트하더라도 큰 트리의 스냅샷이 생성될 수 있습니다.
* 로컬 개발 환경에서 OSGi 구성이 등록될 때 실행되므로 런타임 시 참조 문을 확인할 수 있습니다.
* repoinit 문은 원자적이고 명시적이며 상태가 이미 일치하는 경우 건너뜁니다.

Cloud Manager가 응용 프로그램을 배포하면 콘텐츠 패키지 설치와는 별도로 이러한 문을 실행합니다.

추천 문을 만들려면 아래 절차를 따르십시오.

1. 프로젝트의 구성 폴더에 공장 PID에 대한 OSGi 구성 `org.apache.sling.jcr.repoinit.RepositoryInitializer` 을 추가합니다. org.apache.sling.jcr.repoinit.RepositoryInitializer~initstructure와 같은 구성에 대해 **수사적 이름을 사용합니다**.
1. 구성의 스크립트 속성에 repoint 문을 추가합니다. 구문과 옵션은 Sling 설명서에 [설명되어 있습니다](https://sling.apache.org/documentation/bundles/repository-initialization.html). 하위 폴더 앞에 상위 폴더를 명시적으로 만들어야 합니다. 예를 들어, 이전 `/content` 의 명시적 작성 `/content/myfolder`전에 `/content/myfolder/mysubfolder`. 낮은 수준 구조에 설정된 ACL의 경우 높은 수준을 설정하고 `rep:glob` 제한을 사용하는 것이 좋습니다.  예 `(allow jcr:read on /apps restriction(rep:glob,/msm/wcm/rolloutconfigs))`.
1. 런타임 시 로컬 개발 환경에서 유효성을 확인합니다.

<!-- last statement in step 2 to be clarified with Brian -->

>[!WARNING]
>
>아래의 노드에 대해 정의된 ACL의 경우 `/apps` 또 `/libs` 는 리디렉션 실행이 빈 저장소에서 시작됩니다. 패키지가 설치된 후 문이 패키지에 정의된 내용을 사용할 수 없지만 아래의 상위 구조와 같은 전제 조건을 정의해야 합니다.

>[!TIP]
>
>ACL의 경우 심층 구조를 만드는 것이 번거로울 수 있으므로 ACL을 높은 수준에서 정의하고 rep:glob 제한을 통해 수행해야 하는 위치를 제한하는 것이 더 적절합니다.

리포인트에 대한 자세한 내용은 Sling [설명서에서 확인할 수 있습니다.](https://sling.apache.org/documentation/bundles/repository-initialization.html)

<!-- ### Packaging of Immutable and Mutable Packages {#packaging-of-immutable-and-mutable-packages}

above appears to be internal, to confirm with Brian -->

### 변경 가능한 컨텐츠 패키지에 대한 패키지 관리자 &quot;1%&quot; {#package-manager-oneoffs-for-mutable-content-packages}

컨텐츠 패키지를 &quot;일회성&quot;으로 설치해야 하는 경우도 있습니다. 예를 들어 프로덕션 문제를 디버깅하기 위해 프로덕션에서 스테이징으로 특정 컨텐츠를 가져오는 경우가 있습니다. 이러한 시나리오의 경우 Package Manager를 AEM에서 Cloud Service 환경으로 사용할 수 있습니다.

Package Manager는 런타임 개념이므로, 컨텐츠나 코드를 변경할 수 없는 저장소에 설치할 수 없으므로 이러한 컨텐츠 패키지는 변경할 수 있는 컨텐츠(주로 `/content` 또는 `/conf`)로만 구성되어야 합니다. 컨텐츠 패키지에 mutable 컨텐츠와 mutable 컨텐츠가 혼합되어 있는 컨텐츠가 포함되어 있는 경우 mutable 컨텐츠만 설치됩니다.

Cloud Manager를 통해 설치되는 모든 컨텐츠 패키지(mutable 및 mutable 모두)는 AEM Package Manager의 사용자 인터페이스에 고정된 상태로 나타납니다. 이러한 패키지는 다시 설치, 재구축 또는 다운로드할 수 없으며, **&quot;cp2fm&quot;** 접미어로 나열되며, 이는 해당 설치가 Cloud Manager에서 관리되었음을 나타냅니다.

### 타사 패키지 포함 {#including-third-party}

고객은 Adobe의 번역 파트너와 같은 소프트웨어 공급업체와 같은 제3자 소스에서 사전에 작성된 패키지를 포함하는 것이 일반적입니다. 원격 저장소에서 이러한 패키지를 호스팅하여 `pom.xml` 이 방법은 [암호로 보호된 다중 저장소에 설명된 것처럼 공용 저장소 및 암호 보호 전용 저장소에 대해서도 가능합니다](/help/onboarding/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repositories).

원격 저장소에 패키지를 저장할 수 없는 경우, 고객은 프로젝트의 일부로 SCM에 커밋되고 프로젝트에 종속되어 있는 어떤 항목에서도 참조되는 로컬 파일 시스템 기반의 Maven 저장소에 패키지를 저장할 수 있습니다. 리포지토리는 아래 그림과 같이 프로젝트 프롬프트에서 선언됩니다.


```
<repository>
    <id>project.local</id>
    <name>project</name>
    <url>file:${maven.multiModuleProjectDirectory}/repository</url>
</repository>
```

<!-- formatting appears broken in the code sample above, check how it appears on AEM -->

소프트웨어에 포함된 제3자 패키지는 본 문서에 설명된 Cloud Service 서비스 코딩 및 패키징 지침으로 AEM을 준수해야 하며, 그렇지 않은 경우 포함에 오류가 발생합니다.

다음 Maven POM XML 코드 조각은 **filevault-package-maven-plugin** Maven 플러그인 구성을 통해 일반적으로 &#39;all&#39;이라고 명명된 프로젝트의 &quot;Container&quot; 패키지에 타사 패키지를 어떻게 **** 포함할 수 있는지 보여줍니다.

```
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <subPackages>
           
          <!-- Include the application's ui.apps and ui.content packages -->
          ...
 
          <!-- Include any other extra packages such as AEM WCM Core Components -->
          <!-- Set the version for all dependencies, including 3rd party packages, in the project's Reactor POM -->
          <subPackage>
              <groupId>com.adobe.cq</groupId>
              <artifactId>core.wcm.components.all</artifactId>
              <filter>true</filter>
          </subPackage>
 
 
          <subPackage>
              <groupId>com.3rdparty.groupId</groupId>
              <artifactId>core.3rdparty.artifactId</artifactId>
              <filter>true</filter>
          </subPackage>
      <subPackages>
  </configuration>
</plugin>
...
```

## 롤링 배포의 작동 방식 {#how-rolling-deployments-work}

AEM 업데이트과 마찬가지로 고객 릴리스는 올바른 환경에서 작성자 클러스터 다운타임을 제거하기 위해 롤링 배포 전략을 사용하여 배포됩니다. 일반적인 이벤트 시퀀스는 아래에 설명되어 있습니다. 여기서 **파란색은** 이전 버전의 고객 코드이고 **녹색은** 새로운 버전입니다. Blue와 Green 모두 동일한 버전의 AEM 코드를 실행 중입니다.

* 블루 버전이 활성화되고 그린 출시 후보가 빌드되어 사용 가능합니다.
* 새로운 색인 정의나 업데이트된 색인 정의가 있으면 해당 인덱스가 처리됩니다. 파란색 배포에서는 항상 이전 색인을 사용하고 녹색에서는 항상 새 색인을 사용합니다.
* 블루가 여전히 서비스를 하고 있는 동안 그린이 시작됩니다
* 파란색은 실행 중이고, 그린은 건강검진을 통해 준비 상태를 확인 중이다
* 트래픽을 수락할 준비가 된 녹색 노드 및 작동 중단되는 파란색 노드 대체
* 시간이 지남에 따라 파란색 노드는 녹색이 남아 있을 때까지 녹색 노드로 대체되므로 배포가 완료됩니다
* 변경 가능한 모든 신규 또는 수정된 컨텐츠가 배포됩니다.

## 인덱스 {#indexes}

새 색인이나 수정된 색인은 새(녹색) 버전이 트래픽을 발생시키기 전에 추가적인 색인 또는 다시 색인 작업을 발생시킵니다. AEM의 Cloud Service 색인 관리에 대한 세부 사항은 [이 문서에서 확인할 수 있습니다](/help/operations/indexing.md). Cloud Manager 빌드 페이지에서 색인 작업의 상태를 확인할 수 있으며 새 버전이 트래픽을 받을 준비가 되면 알림을 받게 됩니다.

>[!NOTE]
>
>롤링 배포에 필요한 시간은 색인 크기에 따라 달라집니다. 녹색 버전은 새 색인이 생성될 때까지 트래픽을 허용할 수 없습니다.

현재 Cloud Service의 AEM은 ACS Commons Ensure Oak 색인 도구와 같은 색인 관리 도구로는 작동하지 않습니다.

## 복제 {#replication}

게시 메커니즘은 [AEM Replication Java API와 역호환됩니다](https://helpx.adobe.com/experience-manager/6-3/sites/developing/using/reference-materials/diff-previous/changes/com.day.cq.replication.Replicator.html).

Cloud Ready AEM quickstart를 사용하여 복제를 개발 및 테스트하려면, Author/Publish 설정과 함께 클래식 복제 기능을 사용해야 합니다. 클라우드에 대해 AEM 작성자의 UI 시작 지점이 제거된 경우 사용자가 구성을 위해 이동하게 `http://localhost:4502/etc/replication` 됩니다.

## 롤링 배포를 위한 이전 호환 코드 {#backwards-compatible-code-for-rolling-deployments}

위에서 설명한 바와 같이 Cloud Service의 롤링 배포 전략으로서 AEM은 이전 버전과 새 버전이 동시에 작동 중임을 의미합니다. 따라서 아직 작동 중인 이전 AEM 버전과 역호환하지 않는 코드 변경 사항은 주의하십시오.

또한 변경 가능한 컨텐츠는 제거되지 않으므로 롤백 시 새로운 릴리스에서 적용한 변경 가능한 컨텐츠 구조와 호환성이 있는지 테스트해야 합니다.

### 서비스 사용자 및 ACL 변경 사항 {#service-users-and-acl-changes}

컨텐츠나 코드에 액세스하기 위해 필요한 서비스 사용자 또는 ACL을 변경하면 이전 AEM 버전에서 오류가 발생하여 이전 서비스 사용자와 해당 컨텐츠나 코드에 액세스할 수 있습니다. 이 문제를 해결하기 위해 첫 번째 릴리스는 이후 릴리스에서 정리되기 전에 브리지 역할을 하면서 최소 2개 릴리스에 걸쳐 변경 사항이 분산되도록 하는 것이 좋습니다.

### 색인 변경 {#index-changes}

색인에 대한 변경 사항이 있는 경우 Blue 버전은 색인이 종료될 때까지 색인을 계속 사용하고 Green 버전은 자체 수정된 색인을 사용해야 합니다. 개발자는 이 문서에 설명된 색인 관리 기술 [을 따라야 합니다](/help/operations/indexing.md).

### 롤백 시 보수적인 코딩 {#conservative-coding-for-rollbacks}

배포 후 오류를 보고하거나 감지하는 경우 파란색 버전으로 롤백해야 할 수 있습니다. 새로운 구조(가변 컨텐츠 컨텐츠)가 롤백되지 않으므로 파란색 코드가 녹색 버전에서 만든 모든 새 구조와 호환되도록 하는 것이 좋습니다. 이전 코드가 호환되지 않으면 후속 고객 릴리스에 수정 사항이 적용되어야 합니다.

## 런타임 모드 {#runmodes}

기존 AEM 솔루션에서 고객은 임의 실행 모드로 인스턴스를 실행하고 OSGI 구성을 적용하거나 특정 인스턴스에 OSGI 번들을 설치할 수 있습니다. 일반적으로 정의된 실행 모드에는 *서비스* (작성자 및 게시)와 환경(dev, stage, prod)이 포함됩니다.

반면 AEM의 Cloud Service은 사용 가능한 실행 모드와 OSGI 번들 및 OSGI 구성을 매핑할 수 있는 방법에 대해 더 많은 의견을 가지고 있습니다.

* OSGI 구성 실행 모드는 개발, 준비, 환경 제품 또는 작성자를 참조하거나 서비스에 대해 게시해야 합니다. 이러한 조합 `<service>.<environment_type>` 은 지원되는 반면 이러한 조합은 이 특정 순서(예: `author.dev` 또는 `publish.prod`)에서 사용해야 합니다. OSGI 토큰은 런타임에 더 이상 포함되지 않는 메서드를 사용하지 않고 코드에서 직접 참조되어야 `getRunModes` `environment_type` 합니다. 자세한 내용은 AEM용 [OSGi를 Cloud Service으로 구성을 참조하십시오](/help/implementing/deploying/configuring-osgi.md).
* OSGI 번들 실행 모드는 서비스로 제한됩니다(작성자, 게시). 실행 모드별 OSGI 번들은 둘 중 하나 `install/author` 또는 아래의 컨텐츠 패키지에서 설치해야 합니다 `install/publish`.

기존 AEM 솔루션과 마찬가지로 실행 모드를 사용하여 특정 환경 또는 서비스에 맞는 컨텐츠만 설치할 수 있는 방법은 없습니다. 스테이지나 프로덕션에 없는 데이터 또는 HTML을 사용하여 개발 환경을 시드 하려는 경우 패키지 관리자를 사용할 수 있습니다.

지원되는 런타임 모드 구성은 다음과 같습니다.

* **config** (*기본값, 모든 AEM 서비스에 적용*)
* **config.author** (*모든 AEM 작성자 서비스에 적용*)
* **config.author.dev** (*AEM 개발자 작성자 서비스에 적용*)
* **config.author.stage** (*AEM 스테이징 작성자 서비스에 적용*)
* **config.author.prod** (*AEM Production Author 서비스에 적용*)
* **config.publish** (*AEM 게시 서비스에 적용*)
* **config.publish.dev** (*AEM 개발 게시 서비스에 적용*)
* **config.publish.stage** (*AEM 스테이징 게시 서비스에 적용*)
* **config.publish.prod** (*AEM Production Publish 서비스에 적용*)
* **config.dev** (*AEM 개발 서비스에 적용)
* **config.stage** (*AEM 스테이징 서비스에 적용)
* **config.prod** (*AEM Production 서비스에 적용)

가장 일치하는 실행 모드를 가진 OSGI 구성이 사용됩니다.

로컬에서 개발 시 런타임 모드 시작 매개 변수를 전달하여 어떤 런타임 모드 OSGI 구성을 사용할지 지정할 수 있습니다.

<!-- ### Performance Monitoring {#performance-monitoring}

Developers want to ensure that their custom code is performing well. For Cloud environments, performance reports can be viewed on Cloud Manager. -->

## 소스 제어에서 유지 관리 작업 구성 {#maintenance-tasks-configuration-in-source-control}

클라우드 환경에서 **도구 > 작업** 화면을 더 이상 사용할 수 없으므로 유지 관리 작업 구성은 소스 제어에서 유지되어야 합니다. 이는 변경 사항이 적극적으로 적용되거나 잊혀지는 것이 아니라 의도적으로 지속되도록 보장하는 이점이 있습니다. 자세한 내용은 [유지 관리 작업 문서를](/help/operations/maintenance.md) 참조하십시오.
