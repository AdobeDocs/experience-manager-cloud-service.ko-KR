---
title: AEM as a Cloud Service에 배포
description: AEM as a Cloud Service에 배포
feature: Deploying
exl-id: 7fafd417-a53f-4909-8fa4-07bdb421484e
source-git-commit: 0481267958fe8ac4b28b2742924d2bc2c337eebc
workflow-type: tm+mt
source-wordcount: '3497'
ht-degree: 1%

---

# AEM as a Cloud Service에 배포 {#deploying-to-aem-as-a-cloud-service}

## 소개 {#introduction}

코드 개발의 기본 사항은 AEM On Premise 및 Managed Services 솔루션과 비교하여 AEM as a Cloud Service에서 유사합니다. 개발자가 코드를 작성하고 로컬로 테스트한 다음 원격 AEM as a Cloud Service 환경에 푸시됩니다. Managed Services용 선택적 콘텐츠 전달 도구인 Cloud Manager가 필요합니다. 이제 AEM as a Cloud Service 개발, 스테이지 및 프로덕션 환경에 코드를 배포하는 유일한 메커니즘입니다. 위의 환경을 배포하기 전에 빠른 기능 유효성 검사 및 디버깅을 위해 코드를 로컬 환경에서 로 동기화할 수 있습니다. [신속한 개발 환경](/help/implementing/developing/introduction/rapid-development-environments.md).

의 업데이트 [AEM 버전](/help/implementing/deploying/aem-version-updates.md) 는 푸싱에서 항상 별도의 배포 이벤트입니다 [사용자 지정 코드](#customer-releases). 다른 방식으로 보면, 사용자 지정 코드 릴리스는 맨 위에 배포되기 때문에 프로덕션 상태에 있는 AEM 버전에 대해 테스트해야 합니다. 이후 발생하는 AEM 버전 업데이트로, 자주 업데이트되며 자동으로 적용됩니다. 이미 배포된 고객 코드와 역호환되도록 하기 위한 것입니다.

이 문서의 나머지 부분에서는 개발자가 AEM as a Cloud Service의 버전 업데이트 및 고객 업데이트를 모두 사용하여 작동하도록 하는 방법을 설명합니다.

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html).
-->

## 고객 릴리스 {#customer-releases}

### 올바른 AEM 버전에 대해 코딩 {#coding-against-the-right-aem-version}

이전 AEM 솔루션의 경우, 가장 최신 AEM 버전이 자주(거의 매년 분기별 서비스 팩으로) 변경되었으며 고객은 API Jar을 참조하여 프로덕션 인스턴스를 자체 시간에 최신 빠른 시작으로 업데이트할 수 있습니다. 그러나 AEM as a Cloud Service 애플리케이션은 최신 AEM 버전으로 자동 업데이트됩니다. 따라서 내부 릴리스에 대한 사용자 지정 코드는 최신 AEM 버전에 대해 빌드해야 합니다.

기존의 비 클라우드 AEM 버전과 마찬가지로, 특정 빠른 시작을 기반으로 한 로컬 오프라인 개발이 지원되며, 대부분의 경우 디버깅을 위해 선택할 수 있는 도구가 될 것입니다.

>[!NOTE]
>로컬 시스템에서 애플리케이션이 동작하는 방식과 Adobe Cloud 간에 미묘한 운영 차이가 있습니다. 로컬 개발 중에 이러한 아키텍처 차이점을 존중해야 하며 클라우드 인프라에 배포할 때 다른 동작을 초래할 수 있습니다. 이러한 차이로 인해 프로덕션에서 새로운 사용자 지정 코드를 롤아웃하기 전에 개발 및 스테이지 환경에서 철저한 테스트를 수행하는 것이 중요합니다.

내부 릴리스에 대한 사용자 지정 코드를 개발하려면 적절한 버전의 [AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) 다운로드하여 설치해야 합니다. AEM as a Cloud Service Dispatcher 도구 사용에 대한 자세한 내용은 [이 페이지](/help/implementing/dispatcher/disp-overview.md).

다음 비디오에서는 AEM as a Cloud Service에 코드를 배포하는 방법에 대한 높은 수준의 개요를 제공합니다.

>[!VIDEO](https://video.tv.adobe.com/v/30191?quality=9)

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html). 
-->

## Cloud Manager 및 패키지 관리자를 통해 컨텐츠 패키지 배포 {#deploying-content-packages-via-cloud-manager-and-package-manager}

### Cloud Manager를 통한 배포 {#deployments-via-cloud-manager}

고객은 Cloud Manager를 통해 클라우드 환경에 사용자 지정 코드를 배포합니다. Cloud Manager는 로컬에서 어셈블된 컨텐츠 패키지를 Sling 기능 모델을 따르는 아티팩트로 변환하며, 클라우드 환경에서 실행할 때 AEM as a Cloud Service 애플리케이션에 대해 설명합니다. 따라서 의 패키지를 볼 때 [패키지 관리자](/help/implementing/developing/tools/package-manager.md) 클라우드 환경에서 이름은 &quot;cp2fm&quot;을 포함하며, 변형된 패키지에는 모든 메타데이터가 제거됩니다. 상호 작용할 수 없으므로 다운로드, 복제 또는 열 수 없습니다. 변환기에 대한 자세한 설명서는 다음과 같습니다 [여기에서](https://github.com/apache/sling-org-apache-sling-feature-cpconverter).

AEM as a Cloud Service 애플리케이션용으로 작성된 컨텐츠 패키지는 변경할 수 없는 컨텐츠와 변경할 수 있는 컨텐츠 간에 완전히 구분되어 있어야 하며 Cloud Manager에서는 변경 가능한 컨텐츠만 설치하고 다음과 같은 메시지도 출력합니다.

`Generated content-package <PACKAGE_ID> located in file <PATH> is of MIXED type`

이 섹션의 나머지 부분에서는 변경할 수 없고 변경할 수 없는 패키지의 구성 및 의미에 대해 설명합니다.

### 변경할 수 없는 컨텐츠 패키지 {#immutabe-content-packages}

변경할 수 없는 저장소에 지속되는 모든 콘텐츠 및 코드는 Cloud Manager를 통해 git에 확인하고 배포해야 합니다. 즉, 현재 AEM 솔루션과 달리, 코드는 실행 중인 AEM 인스턴스에 직접 배포되지 않습니다. 따라서 클라우드 환경에서 지정된 릴리스에 대해 실행되는 코드가 동일하므로 프로덕션에 의도하지 않은 코드 변형이 발생할 위험이 없습니다. 예를 들어 OSGI 구성은 AEM 웹 콘솔의 구성 관리자를 통해 런타임 시 관리가 아닌 소스 제어에 커밋해야 합니다.

Blue-Green 배포 패턴으로 인한 응용 프로그램 변경 사항은 스위치에 의해 활성화되므로 서비스 사용자를 제외하고 변경 가능한 리포지토리의 변경 사항, ACL, 노드 유형 및 인덱스 정의가 변경되므로 달라질 수 없습니다.

기존 코드 베이스를 사용하는 고객의 경우 AEM 설명서에 설명된 저장소 구조 변경 연습을 통해 이전에 /etc 아래에 있던 컨텐츠가 올바른 위치로 이동되도록 하는 것이 중요합니다.

예를 들어, 이러한 코드 패키지에 일부 추가 제한이 적용됩니다 [후크 설치](https://jackrabbit.apache.org/filevault/installhooks.html) 지원되지 않습니다.

## OSGi 구성 {#osgi-configuration}

위에서 언급했듯이 OSGI 구성은 웹 콘솔을 통해서가 아니라 소스 제어에 커밋되어야 합니다. 다음과 같은 방법을 사용합니다.

* AEM 웹 콘솔의 구성 관리자를 사용하여 개발자의 로컬 AEM 환경에서 필요한 변경 작업을 수행한 다음 로컬 파일 시스템의 AEM 프로젝트로 결과를 내보냅니다
* 로컬 파일 시스템의 AEM 프로젝트에서 OSGI 구성을 수동으로 생성하여 속성 이름에 대한 AEM 콘솔의 구성 관리자를 참조합니다.

에서 OSGI 구성에 대해 자세히 알아보십시오 [AEM as a Cloud Service OSGi 구성](/help/implementing/deploying/configuring-osgi.md).

## 가변 콘텐츠 {#mutable-content}

경우에 따라 환경이 업데이트될 때마다 Cloud Manager에서 배포할 수 있도록 소스 제어에서 컨텐츠 변경 사항을 준비하는 것이 유용할 수 있습니다. 예를 들어, 특정 루트 폴더 구조를 시드하거나 편집 가능한 템플릿의 변경 사항을 정렬하여 응용 프로그램 배포로 업데이트된 구성 요소에 정책을 활성화하는 것이 합리적일 수 있습니다.

Cloud Manager에서 가변 저장소, 변경 가능한 컨텐츠 패키지 및 리포인트 문에 배포할 컨텐츠를 설명하는 두 가지 전략이 있습니다.

### 가변 콘텐츠 패키지 {#mutable-content-packages}

폴더 경로 계층, 서비스 사용자 및 액세스 제어(ACL)와 같은 컨텐츠는 일반적으로 maven 원형 기반 AEM 프로젝트에 커밋됩니다. 기법에는 AEM에서 내보내거나 XML로 직접 쓰는 작업이 포함됩니다. 빌드 및 배포 프로세스 중에 Cloud Manager는 결과 변경 가능한 컨텐츠 패키지를 패키지화합니다. 변경 가능한 컨텐츠는 파이프라인의 배포 단계 동안 3번 서로 다르게 설치됩니다.

새로운 버전의 응용 프로그램을 시작하기 전에:

* 인덱스 정의(추가, 수정, 제거)

새 버전의 응용 프로그램을 시작하는 동안 전환 전에

* 서비스 사용자(추가)
* 서비스 사용자 ACL(추가)
* 노드 유형(추가)

새 버전의 응용 프로그램으로 전환한 후:

* Jackrabbit Vault를 통해 정의할 수 있는 기타 모든 콘텐츠. 예:
   * 폴더(추가, 수정, 제거)
   * 편집 가능한 템플릿(추가, 수정, 제거)
   * 컨텍스트 인식 구성(아래에 있는 모든 것) `/conf`)(추가, 수정, 제거)
   * 스크립트(패키지)는 패키지 설치 프로세스의 다양한 단계에서 설치 후크를 트리거할 수 있습니다. <!-- MISDIRECTED REQUEST, 421 ERROR, CAN'T FIND CORRECT PATH See the [Jackrabbit filevault documentation](https://jackrabbit.incubator.apache.org/filevault/installhooks.html) about install hooks. --> AEM CS는 현재 Filerabault 버전 3.4.0을 사용하여 관리자 사용자, 시스템 사용자 및 관리자 그룹의 구성원에게 설치 후크를 제한합니다.)

아래의 install.author 또는 install.publish 폴더에 패키지를 포함하여 가변 컨텐츠 설치를 작성자 또는 게시로 제한할 수 있습니다 `/apps`. 이러한 분리를 반영하도록 재구성을 AEM 6.5에서 수행했으며 권장 프로젝트 재구성에 대한 세부 사항은 [AEM 6.5 설명서.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html)

>[!NOTE]
>컨텐츠 패키지는 모든 환경 유형(dev, stage, prod)에 배포됩니다. 배포를 특정 환경으로 제한할 수 없습니다. 이 제한은 자동 실행을 테스트하는 옵션을 보장하기 위해 적용됩니다. 환경에 고유한 컨텐츠는 [패키지 관리자.](/help/implementing/developing/tools/package-manager.md)

또한 적용된 변경 사항 컨텐츠 패키지 변경 사항을 롤백하는 메커니즘이 없습니다. 고객이 문제를 감지하면 다음 코드 릴리스에서 또는 마지막 수단으로 문제를 해결하도록 선택하고 전체 시스템을 배포 전 시점으로 복원할 수 있습니다.

포함된 모든 타사 패키지는 AEM as a Cloud Service 서비스 호환 여부에 대한 확인을 받아야 하며, 그렇지 않으면 배포 오류가 발생합니다.

위에서 언급했듯이 기존 코드 베이스를 사용하는 고객은 [AEM 6.5 설명서.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html)

## 포인트 {#repoinit}

다음과 같은 경우 명시적 콘텐츠 생성을 직접 코딩하는 방법을 사용하는 것이 좋습니다 `repoinit` OSGI 공장 구성의 문:

* 서비스 사용자 만들기/삭제/비활성화
* 그룹 만들기/삭제
* 사용자 만들기/삭제
* ACL 추가

   >[!NOTE]
   >
   >ACL을 정의하려면 노드 구조가 이미 있어야 합니다. 따라서 앞서 작성한 경로문이 필요할 수 있습니다.

* 경로 추가(예: 루트 폴더 구조)
* CND(nodetype 정의) 추가

다음과 같은 이점 때문에 지원되는 이러한 컨텐츠 수정 사용 사례에 대해 반복을 사용하는 것이 좋습니다.

* 리포인트는 시작 시 리소스를 만들어 로직이 그러한 리소스를 당연하게 사용할 수 있도록 합니다. 가변 컨텐츠 패키지 접근 방식에서는 시작 후 리소스가 생성되므로 여기에 의존하는 응용 프로그램 코드가 실패할 수 있습니다.
* 리포인트는 수행할 작업을 명시적으로 제어할 때 비교적 안전한 명령 세트입니다. 또한, 사용자, 서비스 사용자 및 그룹을 제거할 수 있는 몇 가지 보안 관련 사례를 제외하고 지원되는 유일한 작업은 추가 작업입니다. 반대로 변경 가능한 컨텐츠 패키지 접근 방식에서 무언가를 제거하는 것은 명시적 방식입니다. 필터를 정의하면 필터에 의해 적용되는 모든 항목이 삭제됩니다. 여전히 새 컨텐츠가 있으면 애플리케이션의 동작을 변경할 수 있는 시나리오가 있으므로 주의해야 합니다.
* 리포인트는 빠르고 원자적인 작업을 수행합니다. 반대로 변경할 수 있는 컨텐츠 패키지는 필터에 의해 적용되는 구조에 따라 성능이 크게 달라질 수 있습니다. 단일 노드를 업데이트하더라도 큰 트리의 스냅샷이 생성될 수 있습니다.
* OSGi 구성이 등록될 때 실행되므로 로컬 개발 환경에서 런타임 시 다시 점을 확인할 수 있습니다.
* repoinit 문은 원자적이고 명시적이며 상태가 이미 일치하는 경우 건너뜁니다.

Cloud Manager에서 애플리케이션을 배포하면 컨텐츠 패키지 설치와는 무관하게 이 문을 실행합니다.

지시 문을 만들려면 아래 절차를 따르십시오.

1. 출하 시 PID에 대한 OSGi 구성 추가 `org.apache.sling.jcr.repoinit.RepositoryInitializer` 를 클릭합니다. 구성을 설명하는 이름을 사용합니다. **org.apache.sling.jcr.repoinit.RepositoryInitializer~initstructure**.
1. 구성의 스크립트 속성에 repoint 문을 추가합니다. 구문 및 옵션은 [Sling 설명서](https://sling.apache.org/documentation/bundles/repository-initialization.html). 하위 폴더 앞에 상위 폴더를 명시적으로 만들어야 합니다. 예를 들어 `/content` 이전 `/content/myfolder`, 이전 `/content/myfolder/mysubfolder`. 낮은 수준 구조에서 설정되는 ACL의 경우 높은 수준에서 설정하고 `rep:glob` 제한 사항.  예 `(allow jcr:read on /apps restriction(rep:glob,/msm/wcm/rolloutconfigs))`.
1. 런타임 시 로컬 개발 환경에서 유효성을 확인합니다.

<!-- last statement in step 2 to be clarified with Brian -->

>[!WARNING]
>
>아래의 노드에 대해 정의된 ACL의 경우 `/apps` 또는 `/libs` 원격 실행은 빈 저장소에서 시작됩니다. 패키지는 응답 후 설치되므로 명령문은 패키지에 정의된 어떤 것도 사용할 수 없지만 아래의 상위 구조와 같은 전제 조건을 정의해야 합니다.

>[!TIP]
>
>ACL의 경우 딥 구조를 만드는 것이 번거로울 수 있으므로 상위 수준에서 ACL을 정의하고 rep:glob 제한을 통해 동작해야 하는 위치를 제한하는 것이 더 적합합니다.

리포인트에 대한 자세한 내용은 [Sling 설명서](https://sling.apache.org/documentation/bundles/repository-initialization.html)

<!-- ### Packaging of Immutable and Mutable Packages {#packaging-of-immutable-and-mutable-packages}

above appears to be internal, to confirm with Brian -->

### 가변 컨텐츠 패키지에 대한 패키지 관리자 &quot;일회성&quot; {#package-manager-oneoffs-for-mutable-content-packages}

>[!CONTEXTUALHELP]
>id="aemcloud_packagemanager"
>title="패키지 관리자 - 가변 컨텐츠 패키지 마이그레이션"
>abstract="프로덕션 문제를 디버깅하기 위해 프로덕션 환경에서 스테이징으로 특정 컨텐츠를 가져오는 작업을 포함하는 컨텐츠 패키지를 &#39;오프&#39;로 설치해야 하는 사용 사례와 온-프레미스 환경에서 AEM 클라우드 환경으로 작은 컨텐츠 패키지를 전송하는 사용 사례를 살펴보십시오."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=en#cloud-migration" text="콘텐츠 전송 도구"

컨텐츠 패키지를 &quot;일회성&quot;으로 설치해야 하는 사용 사례가 있습니다. 예를 들어 프로덕션 문제를 디버깅하기 위해 프로덕션에서 스테이징으로 특정 콘텐츠를 가져오는 경우가 있습니다. 이러한 시나리오에서는 [패키지 관리자](/help/implementing/developing/tools/package-manager.md) AEM as a Cloud Service 환경에서 사용할 수 있습니다.

패키지 관리자는 런타임 개념이므로 컨텐츠나 코드를 변경할 수 없는 저장소에 설치할 수 없으므로 이러한 컨텐츠 패키지는 주로 변경할 수 있는 컨텐츠(주로 `/content` 또는 `/conf`). 콘텐츠 패키지에 혼합(변경할 수 있는 콘텐츠와 변경할 수 없는 콘텐츠 모두)인 콘텐츠가 포함되어 있으면 가변 콘텐츠만 설치됩니다.

>[!IMPORTANT]
>
>패키지 관리자 UI는 **정의되지 않음** 패키지를 설치하는 데 10분 이상 걸리는 경우 오류 메시지가 표시됩니다.
>
>이것은 설치 오류가 아니라 Cloud Service이 모든 요청에 대해 갖는 시간 제한으로 인한 것입니다.
>
>이러한 오류가 표시되면 설치를 다시 시도하지 마십시오. 백그라운드에서 설치가 올바르게 진행 중입니다. 설치를 다시 시작하면 여러 동시 가져오기 프로세스에서 일부 충돌이 발생할 수 있습니다.

Cloud Manager를 통해 설치된 모든 컨텐츠 패키지(변경할 수 있고 변경할 수 없음)는 AEM Package Manager의 사용자 인터페이스에 고정된 상태로 표시됩니다. 이러한 패키지를 다시 설치하거나 다시 빌드하거나 다운로드할 수 없으며 **&quot;cp2fm&quot;** 접미사: 설치가 Cloud Manager에서 관리되었음을 나타냅니다.

### 타사 패키지 포함 {#including-third-party}

일반적으로 고객은 Adobe의 번역 파트너와 같은 소프트웨어 공급업체로부터 사전 빌드된 패키지를 포함합니다. 원격 리포지토리에서 이러한 패키지를 호스팅하고 `pom.xml`. 이 기능은 다음과 같이 암호를 보호하는 공용 저장소 및 개인 저장소에 사용할 수도 있습니다. [암호로 보호된 maven 저장소](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repositories).

원격 저장소에 패키지를 저장할 수 없는 경우, 고객은 프로젝트의 일부로 SCM에 커밋되고 이 패키지에 종속되는 모든 항목에서 참조하는 로컬 파일 시스템 기반 Maven 리포지토리에 배치할 수 있습니다. 리포지토리는 아래 그림과 같이 프로젝트 pom에서 선언됩니다.


```
<repository>
    <id>project.local</id>
    <name>project</name>
    <url>file:${maven.multiModuleProjectDirectory}/repository</url>
</repository>
```

<!-- formatting appears broken in the code sample above, check how it appears on AEM -->

포함된 타사 패키지는 이 문서에 설명된 AEM as a Cloud Service 서비스 코딩 및 패키징 지침을 따라야 하며, 그렇지 않으면 포함 시 배포 오류가 발생합니다.

다음 Maven `POM.xml` 코드 조각은 일반적으로 이름이 인 프로젝트의 &quot;컨테이너&quot; 패키지에 타사 패키지를 포함할 수 있는 방법을 보여 줍니다 **&#39;all&#39;**&#x200B;를 통해 **filervault-package-maven-plugin** Maven 플러그인 구성.

```
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <embeddeds>

          ...

          <!-- Include any other extra packages  -->
          <embedded>
              <groupId>com.vendor.x</groupId>
              <artifactId>vendor.plug-in.all</artifactId>
              <type>zip</type>
              <target>/apps/vendor-packages/container/install</target>
          </embedded>
      <embeddeds>
  </configuration>
</plugin>
...
```

## 롤링 배포 작동 방식 {#how-rolling-deployments-work}

AEM 업데이트과 마찬가지로, 고객 릴리스는 올바른 환경에서 작성 클러스터 다운타임을 제거하기 위해 롤링 배포 전략을 사용하여 배포됩니다. 이벤트의 일반 시퀀스는 아래에 설명되어 있습니다. 여기서 **파란색** 는 고객 코드의 이전 버전이며 **녹색** 는 새 버전입니다. 파란색과 녹색이 모두 동일한 버전의 AEM 코드를 실행하고 있습니다.

* 파란색 버전이 활성 상태이고 녹색의 릴리스 후보가 빌드되어 제공됩니다
* 새 인덱스 정의나 업데이트된 인덱스 정의가 있으면 해당 인덱스가 처리됩니다. 파란색 배포는 항상 이전 인덱스를 사용하는 반면 녹색은 항상 새 인덱스를 사용합니다.
* 블루가 아직 서비스를 하고 있는 동안 그린이 시작됩니다
* 블루(Blue)가 실행되고 있으며 제공 중, 그린(Green)이 상태 검사를 통해 준비 상태를 확인하는 중
* 준비가 된 녹색 노드는 트래픽을 수락하고 작동 중단되는 파란색 노드를 바꿉니다
* 시간이 지나면서 녹색만 남아 있을 때까지 파란색 노드는 녹색 노드로 대체되므로 배포를 완료합니다
* 새로운 콘텐츠 또는 수정된 변경 가능 콘텐츠가 배포됩니다

## 인덱스 {#indexes}

새 색인이나 수정된 색인은 새로운 (녹색) 버전에서 트래픽을 발생시키기 전에 추가적인 색인 지정 또는 재인덱싱 단계를 생성합니다. AEM as a Cloud Service의 색인 관리에 대한 자세한 내용은 [이 문서](/help/operations/indexing.md). Cloud Manager 빌드 페이지에서 색인 작업의 상태를 확인할 수 있으며 새 버전에서 트래픽을 받을 준비가 되면 알림을 받게 됩니다.

>[!NOTE]
>
>롤링 배포에 필요한 시간은 새 색인이 생성될 때까지 녹색 버전에서 트래픽을 허용할 수 없으므로 인덱스 크기에 따라 달라집니다.

현재 AEM as a Cloud Service은 ACS Commons Secure Oak Index 도구와 같은 인덱스 관리 도구에서 작동하지 않습니다.

## 복제 {#replication}

게시 메커니즘은 이전 버전과 호환됩니다 [AEM 복제 Java API](https://helpx.adobe.com/experience-manager/6-3/sites/developing/using/reference-materials/diff-previous/changes/com.day.cq.replication.Replicator.html).

Cloud Ready AEM 빠른 시작을 사용하여 복제를 개발하고 테스트하려면, 클래식 복제 기능을 작성자/게시 설정과 함께 사용해야 합니다. 클라우드에 대해 AEM 작성자 의 UI 시작 지점이 제거된 경우 사용자는 `http://localhost:4502/etc/replication` 참조하십시오.

## 롤링 배포를 위한 이전 호환 코드 {#backwards-compatible-code-for-rolling-deployments}

위에서 자세히 설명한 것처럼 AEM as a Cloud Service의 롤링 배포 전략은 이전 버전과 새 버전이 모두 동시에 작동할 수 있음을 의미합니다. 따라서 여전히 작동 중인 이전 AEM 버전과 이전 버전과 호환되지 않는 코드 변경 사항에 주의하십시오.

또한 변경 가능한 컨텐츠는 제거되지 않으므로 롤백 시 새로운 릴리스에서 적용한 새로운 가변 컨텐츠 구조와의 호환성을 테스트해야 합니다.

### 서비스 사용자 및 ACL 변경 사항 {#service-users-and-acl-changes}

컨텐츠나 코드에 액세스하는 데 필요한 서비스 사용자 또는 ACL을 변경하면 이전 AEM 버전에서 오류가 발생하여 이전 서비스 사용자가 해당 컨텐츠나 코드에 액세스할 수 있습니다. 이 동작을 해결하기 위해 첫 번째 릴리스가 후속 릴리스에서 정리되기 전에 브리지 역할을 하면서 최소 2개의 릴리스에 변경 사항을 분산하는 것이 좋습니다.

### 색인 변경 사항 {#index-changes}

인덱스에 대한 변경 사항이 수행된 경우 Blue 버전은 색인이 종료될 때까지 인덱스를 계속 사용하는 반면 Green 버전은 자체 수정된 인덱스 세트를 사용하는 것이 중요합니다. 개발자는 설명된 인덱스 관리 기술을 따라야 합니다 [이 문서](/help/operations/indexing.md).

### 롤백 시 보수적인 코딩 {#conservative-coding-for-rollbacks}

구축 후 오류를 보고하거나 감지하면 파란색 버전으로 롤백해야 할 수 있습니다. 새로운 구조(가변 컨텐츠 컨텐츠 컨텐츠)가 롤백되지 않으므로 파란색 코드가 녹색 버전에서 만든 모든 새 구조와 호환되는지 확인하는 것이 좋습니다. 이전 코드가 호환하지 않는 경우, 후속 고객 릴리스에서 수정 사항을 적용해야 합니다.

## 신속한 개발 환경(RDE) {#rde}

[신속한 개발 환경](/help/implementing/developing/introduction/rapid-development-environments.md) (또는 RDE 를 짧게 사용하면) 개발자가 변경 사항을 신속하게 배포하고 검토할 수 있으므로 로컬 개발 환경에서 이미 작동하는 것으로 입증된 기능을 테스트하는 데 필요한 시간을 최소화할 수 있습니다.

Cloud Manager 파이프라인을 통해 코드를 배포하는 일반적인 개발 환경과 달리 개발자는 명령줄 도구를 사용하여 로컬 개발 환경의 코드를 RDE에 동기화합니다. 변경 사항이 RDE에서 성공적으로 테스트되면 적절한 품질 게이트를 통해 코드를 지정하는 Cloud Manager 파이프라인을 통해 일반 클라우드 개발 환경에 배포해야 합니다.

## 실행 모드 {#runmodes}

기존 AEM 솔루션에서는 고객이 임의 실행 모드로 인스턴스를 실행하고 OSGI 구성을 적용하거나 특정 인스턴스에 OSGI 번들을 설치할 수 있습니다. 일반적으로 정의된 실행 모드에는 *서비스* (작성자 및 게시) 및 환경(rde, dev, stage, prod).

반면 AEM as a Cloud Service에서는 사용 가능한 실행 모드와 OSGI 번들 및 OSGI 구성을 매핑하는 방법에 대해 더 자세히 설명합니다.

* OSGI 구성 실행 모드는 RDE, dev, stage, prod for the environment 또는 author, publish for the service를 참조해야 합니다. 의 조합 `<service>.<environment_type>` 지원되지만 이 순서를 특정 순서로 사용해야 합니다(예: `author.dev` 또는 `publish.prod`). OSGI 토큰은 `getRunModes` 메서드를 포함할 필요가 없습니다. `environment_type` 런타임 시 자세한 내용은 [AEM as a Cloud Service OSGi 구성](/help/implementing/deploying/configuring-osgi.md).
* OSGI 번들 실행 모드는 서비스(작성자, 게시)로 제한됩니다. 실행 단위 모드 OSGI 번들은 다음 중 하나의 컨텐츠 패키지에 설치해야 합니다 `install/author` 또는 `install/publish`.

기존 AEM 솔루션과 마찬가지로 실행 모드를 사용하여 특정 환경 또는 서비스의 콘텐츠만 설치할 방법이 없습니다. 스테이지 또는 프로덕션에 없는 데이터 또는 HTML을 사용하여 개발 환경을 시드하려는 경우 패키지 관리자를 사용할 수 있습니다.

지원되는 실행 모드 구성은 다음과 같습니다.

* **config** (*기본값은 모든 AEM 서비스에 적용됩니다*)
* **config.author** (*모든 AEM 작성자 서비스에 적용됩니다*)
* **config.author.dev** (*AEM 개발 작성자 서비스에 적용됩니다*)
* **config.author.rde** (*AEM RDE 작성자 서비스에 적용됩니다*)
* **config.author.stage** (*AEM 스테이징 작성자 서비스에 적용됩니다*)
* **config.author.prod** (*AEM Production Author 서비스에 적용됩니다*)
* **config.publish** (*AEM 게시 서비스에 적용됩니다*)
* **config.publish.dev** (*AEM 개발 게시 서비스에 적용됩니다*)
* **config.publish.rde** (*AEM RDE 게시 서비스에 적용됩니다*)
* **config.publish.stage** (*AEM 스테이징 게시 서비스에 적용됩니다*)
* **config.publish.prod** (*AEM Production Publish 서비스에 적용됩니다*)
* **config.dev** (*AEM 개발 서비스에 적용됩니다*)
* **config.rde** (*RDE 서비스에 적용됩니다*)
* **config.stage** (*AEM 스테이징 서비스에 적용됩니다*)
* **config.prod** (*AEM Production Services에 적용됩니다*)

가장 일치하는 실행 모드가 있는 OSGI 구성이 사용됩니다.

로컬에서 개발할 때 실행 모드 시작 매개 변수 `-r`은 런타임 모드 OSGI 구성을 지정하는 데 사용됩니다.

```shell
$ java -jar aem-sdk-quickstart-xxxx.x.xxx.xxxx-xxxx.jar -r publish,dev
```

<!-- ### Performance Monitoring {#performance-monitoring}

Developers want to ensure that their custom code is performing well. For Cloud environments, performance reports can be viewed on Cloud Manager. -->

## 소스 제어에서 유지 관리 작업 구성 {#maintenance-tasks-configuration-in-source-control}

유지 관리 작업 구성은 **도구 > 작업** 화면은 더 이상 클라우드 환경에서 사용할 수 없습니다. 따라서 변경 사항이 적극적으로 적용되거나 잊혀지지 않고 의도적으로 유지되도록 하는 이점이 있습니다. 다음 문서를 참조하십시오 [유지 관리 작업 문서](/help/operations/maintenance.md) 추가 정보.
