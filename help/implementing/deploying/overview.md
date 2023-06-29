---
title: AEM as a Cloud Service에 배포
description: AEM as a Cloud Service에 배포
feature: Deploying
exl-id: 7fafd417-a53f-4909-8fa4-07bdb421484e
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '3462'
ht-degree: 49%

---

# AEM as a Cloud Service에 배포 {#deploying-to-aem-as-a-cloud-service}

## 소개 {#introduction}

코드 개발의 기본 사항은 AEM On Premise 및 Managed Services 솔루션과 비교할 경우 AEM as a Cloud Service의 기본 사항과 유사합니다. 개발자는 코드를 작성하고 로컬에서 테스트한 다음 AEM에서 원격 환경으로 as a Cloud Service으로 푸시합니다. Managed Services용 선택적 콘텐츠 게재 도구였던 Cloud Manager가 필요합니다. 이 게재 도구는 이제 AEM as a Cloud Service 개발, 스테이지 및 프로덕션 환경에 코드를 배포하는 유일한 메커니즘입니다. 앞에서 언급한 환경을 배포하기 전에 기능을 빠르게 확인하고 디버깅하기 위해 로컬 환경에서 로 코드를 동기화할 수 있습니다. [신속한 개발 환경](/help/implementing/developing/introduction/rapid-development-environments.md).

[AEM 버전](/help/implementing/deploying/aem-version-updates.md) 업데이트는 항상 [사용자 정의 코드](#customer-releases) 푸시와는 별도의 배포 이벤트입니다. 다른 관점에서 보면 사용자 정의 코드 릴리스는 상단에 배포되는 항목이므로 프로덕션에 있는 AEM 버전과 비교하여 테스트해야 합니다. 이후 발생하는 AEM 버전 업데이트는 자주 발생하고 자동으로 적용됩니다. 이미 배포된 사용자 정의 코드와 역으로 호환하기 위해 업데이트됩니다.

이 문서의 나머지 부분에서는 개발자가 AEM as a Cloud Service의 버전 업데이트 및 고객 업데이트 모두에서 작업할 수 있도록 모범 사례를 조정하는 방법을 설명합니다.

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html).
-->

## 고객 릴리스 {#customer-releases}

### 올바른 AEM 버전에 대한 코딩 {#coding-against-the-right-aem-version}

이전 AEM 솔루션의 경우 가장 최신 AEM 버전이 자주 변경되지 않고(분기별 서비스 팩으로 거의 매년 사용) 고객은 API Jar를 참조하여 프로덕션 인스턴스를 최신 빠른 시작으로 업데이트합니다. 그러나 AEMas a Cloud Service 의 응용 프로그램은 더 자주 AEM의 최신 버전으로 자동 업데이트되므로 내부 릴리스에 대한 사용자 지정 코드는 최신 AEM 버전에 대해 빌드해야 합니다.

기존 비 클라우드 AEM 버전과 마찬가지로 특정 빠른 시작을 기반으로 하는 로컬 오프라인 개발이 지원되며 일반적으로 디버깅을 위해 선택할 수 있는 도구가 될 것으로 예상됩니다.

>[!NOTE]
>애플리케이션이 로컬 시스템과 Adobe Cloud에서 동작하는 방식에는 운영상 미묘한 차이점이 있습니다. 이러한 구조적 차이는 로컬 개발 도중에 적용되어야 하고 이를 통해 클라우드 인프라에 배포 시 다른 비헤이비어가 발생할 수 있습니다. 이러한 차이점 때문에 프로덕션에서 새 사용자 지정 코드를 롤아웃하기 전에 개발 및 스테이징 환경에서 철저한 테스트를 수행하는 것이 중요합니다.

내부 릴리스용 사용자 정의 코드를 개발하려면 관련 버전의 [AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)를 다운로드하고 설치해야 합니다. AEM as a Cloud Service Dispatcher 도구로 AEM을 사용하는 방법에 대한 자세한 내용은 [이 페이지](/help/implementing/dispatcher/disp-overview.md)를 참조하십시오.

AEM 다음 비디오는 as a Cloud Service으로 코드를 배포하는 방법에 대한 높은 수준의 개요를 제공합니다.

>[!VIDEO](https://video.tv.adobe.com/v/30191?quality=9)

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html). 
-->

## Cloud Manager 및 Package Manager를 통해 콘텐츠 패키지 배포 {#deploying-content-packages-via-cloud-manager-and-package-manager}

### Cloud Manager를 통한 배포 {#deployments-via-cloud-manager}

<!-- Alexandru: temporarily commenting this out, until I get some clarification from Brian 

![image](https://git.corp.adobe.com/storage/user/9001/files/e91b880e-226c-4d5a-93e0-ae5c3d6685c8) -->

고객은 Cloud Manager를 통해 클라우드 환경에 사용자 정의 코드를 배포합니다. Cloud Manager는 로컬로 조립된 콘텐츠 패키지를 Sling 기능 모델에 따라 아티팩트로 변환합니다. 이 모델은 클라우드 환경에서 실행할 때 AEM as a Cloud Service의 애플리케이션을 설명하는 방법입니다. 따라서 의 패키지를 볼 때 [패키지 관리자](/help/implementing/developing/tools/package-manager.md) 클라우드 환경에서 이름에는 &quot;cp2fm&quot;이 포함되며 변환된 패키지에는 모든 메타데이터가 제거됩니다. 상호 작용할 수 없다는 것은 다운로드, 복제 또는 열 수 없다는 의미입니다. 변환기에 대한 세부 문서는 [여기](https://github.com/apache/sling-org-apache-sling-feature-cpconverter)에서 확인할 수 있습니다.

AEMas a Cloud Service 의 애플리케이션용으로 작성된 콘텐츠 패키지는 변경할 수 없는 콘텐츠와 변경할 수 있는 콘텐츠를 완전히 구분해야 하며 Cloud Manager는 변경 가능한 콘텐츠만 설치하고 다음과 같은 메시지를 출력합니다.

`Generated content-package <PACKAGE_ID> located in file <PATH> is of MIXED type`

이 섹션의 나머지 부분에서는 변경 불가능한 패키지와 변경 가능한 패키지의 구성 및 의미에 대해 설명합니다.

### 변경 불가능한 콘텐츠 패키지 {#immutabe-content-packages}

변경 불가능한 저장소에서 지속되는 모든 콘텐츠는 Git에 체크인하고 Cloud Manager를 통해 배포해야 합니다. 즉, 현재 AEM 솔루션과 달리 코드는 실행 중인 AEM 인스턴스에 직접 배포하지 않습니다. 이 워크플로우는 모든 클라우드 환경에서 주어진 릴리스에 대해 실행되는 코드가 동일하도록 하여 프로덕션에 의도하지 않은 코드 변형이 발생할 위험을 제거합니다. 예를 들어 OSGI 구성은 AEM 웹 콘솔의 구성 관리자를 통해 런타임에 관리되지 않고 소스 제어에 커밋되어야 합니다.

배포 패턴으로 인한 애플리케이션 변경은 스위치에 의해 활성화되므로 서비스 사용자, 해당 ACL, 노드 유형 및 색인 정의 변경을 제외한 변경 가능한 저장소의 변경 사항에 따라 달라질 수 없습니다.

고객이 기존 코드 베이스를 보유하고 있는 경우 AEM 설명서에 설명된 저장소 재구성 연습을 살펴보면서 /etc 아래의 이전 콘텐츠가 올바른 위치로 이동했는지 확인해야 합니다.

추가적인 제한이 해당 코드 패키지에 일부 적용됩니다. 예를 들어 [설치 후크](https://jackrabbit.apache.org/filevault/installhooks.html)는 지원되지 않습니다.

## OSGi 구성 {#osgi-configuration}

앞서 언급한 바와 같이 OSGI 구성은 웹 콘솔을 통해서가 아니라 소스 제어에 커밋해야 합니다. 이에 필요한 기술에는 다음이 포함됩니다.

* AEM 웹 콘솔의 구성 관리자를 통해 개발자의 로컬 AEM 환경에 필요한 변경 작업을 수행하고 로컬 파일 시스템의 AEM 프로젝트로 결과 내보내기
* 로컬 파일 시스템의 AEM 프로젝트에서 OSGI 구성을 수동으로 만들기, 속성 이름은 AEM 콘솔의 구성 관리자 참조.

[AEM as a Cloud Service용 OSGi 구성](/help/implementing/deploying/configuring-osgi.md)에서 OSGI 구성에 대해 자세히 살펴봅니다.

## 변경 가능한 콘텐츠 {#mutable-content}

환경이 업데이트될 때마다 Cloud Manager에서 배포할 수 있도록 소스 제어에서 콘텐츠 변경 사항을 준비하는 것이 유용할 수 있습니다. 예를 들어 특정 루트 폴더 구조를 시드하는 것이 적절할 수 있습니다. 또는 편집 가능한 템플릿에 변경 내용을 표시하여 애플리케이션 배포에 의해 업데이트된 정책 구성 요소를 활성화할 수 있습니다.

Cloud Manager에서 변경 가능한 저장소, 변경 가능한 콘텐츠 패키지 및 로 배포하는 콘텐츠를 설명하는 두 가지 전략이 있습니다 `repoinit` 명령문입니다.

### 변경 가능한 콘텐츠 패키지 {#mutable-content-packages}

일반적으로 폴더 경로 계층, 서비스 사용자와 액세스 제어(ACL) 등 콘텐츠는 Maven Archetype 기반 AEM 프로젝트에 커밋합니다. 기법에는 AEM에서 내보내기 또는 직접 XML로 작성하기가 포함됩니다. 빌드 및 배포 프로세스 도중 Cloud Manager는 최종 변경 가능한 콘텐츠 패키지를 패키지화합니다. 변경 가능한 콘텐츠는 파이프라인의 배포 단계 동안 세 번 서로 다른 시점에 설치됩니다.

새 애플리케이션 버전 시작에 앞서:

* 색인 정의 (추가, 수정, 제거)

새 애플리케이션 버전 시작 도중(단, 전환에 앞서):

* 서비스 사용자 (추가)
* 서비스 사용자 ACL (추가)
* 노드 유형 (추가)

새 애플리케이션 버전으로 전환하고 나서:

* Jackrabbit vault를 통해 정의할 수 있는 기타 모든 콘텐츠. 예:
   * 폴더 (추가, 수정, 제거)
   * 편집 가능한 템플릿 (추가, 수정, 제거)
   * 컨텍스트 인식 구성 (`/conf` 아래의 모든 항목) (추가, 수정, 제거)
   * 스크립트 (패키지는 패키지 설치의 여러 설치 프로세스 단계에서 설치 후크를 트리거할 수 있습니다. 다음을 참조하십시오 [Jackrabbit filevault 설명서](https://jackrabbit.apache.org/filevault/installhooks.html) 설치 후크 정보. AEM CS는 현재 설치 후크를 관리자 사용자, 시스템 사용자 및 관리자 그룹의 구성원으로 제한하는 Filevault 버전 3.4.0을 사용합니다.)

`/apps` 아래의 install.author 또는 install.publish 폴더에 패키지를 임베드하여 변경 가능한 콘텐츠 설치를 작성자 또는 게시로 제한할 수 있습니다. AEM 6.5에서 재구성을 수행하여 이 분리를 반영합니다. 권장되는 프로젝트 재구성에 대한 자세한 내용은 [AEM 6.5 설명서](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html)에서 확인할 수 있습니다.

>[!NOTE]
>모든 환경 유형(개발/단계/프로덕션)에 콘텐츠 패키지를 배포합니다. 배포를 특정 환경으로 제한할 수 없습니다. 이 제한은 자동화된 실행의 테스트 실행 옵션을 보장하기 위해 적용됩니다. 특정 환경에 해당하는 컨텐츠는 다음을 통해 수동으로 설치해야 합니다. [패키지 관리자](/help/implementing/developing/tools/package-manager.md).

또한 변경 가능한 콘텐츠 패키지 변경 사항을 적용하고 나서 롤백할 수 있는 메커니즘은 없습니다. 고객이 문제를 감지하는 경우 다음 코드 릴리스에서 문제를 해결하거나 마지막 수단으로 전체 시스템을 배포하기 전 시점으로 복원하도록 선택할 수 있습니다.

AEM 포함된 모든 서드파티 패키지는 as a Cloud Service 호환되는지 확인해야 합니다. 그렇지 않으면 배포가 실패합니다.

위에서 언급했듯이 기존 코드 베이스를 사용하는 고객은 의 6.5 저장소 변경 사항에 필요한 저장소 재구성 연습을 따라야 합니다 [AEM 6.5 설명서.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html)

## Repoinit {#repoinit}

다음 경우에는 OSGI 팩토리 구성에서 명시적 콘텐츠 생성 `repoinit` 명령문을 직접 코딩하는 방식을 사용하는 것이 좋습니다.

* 서비스 사용자 만들기/삭제/비활성화
* 그룹 만들기/삭제
* 사용자 만들기/삭제
* ACL 추가

  >[!NOTE]
  >
  >ACL을 정의하려면 노드 구조가 이미 있어야 합니다. 따라서 선행하는 경로 만들기 명령문이 필요할 수 있습니다.

* 경로 추가 (예: 루트 폴더 구조)
* CND 추가 (노드 유형 정의)

다음과 같은 이점으로 인해 지원되는 이 콘텐츠 수정 사용 사례에 대해 Repoinit가 권장됩니다.

* `Repoinit` 는 시작 시 리소스를 생성하므로 로직은 해당 리소스의 존재를 당연한 것으로 간주할 수 있습니다. 변경 가능한 콘텐츠 패키지 방식에서는 시작 후 리소스가 생성되므로 리소스를 사용하는 애플리케이션 코드가 실패할 수 있습니다.
* `Repoinit` 는 수행할 작업을 명시적으로 제어할 때 상대적으로 안전한 명령 집합입니다. 또한 사용자, 서비스 사용자 및 그룹을 제거할 수 있는 몇 가지 보안 관련 경우를 제외하고 유일하게 지원되는 작업은 부가적입니다. 반면에 필터를 정의하면 필터에 포함된 모든 항목이 삭제되므로 변경 가능한 콘텐츠 패키지 방식으로 항목을 명시적으로 제거할 수 있습니다. 단, 새 콘텐츠의 존재 여부에 따라 애플리케이션 비헤이비어를 변경할 수 있는 시나리오가 모든 콘텐츠에 있으므로 주의해야 합니다.
* `Repoinit` 빠르고 작은 연산을 수행합니다. 반면, 변경 가능한 콘텐츠 패키지의 성능은 필터에 포함된 구조에 따라 상당히 달라질 수 있습니다. 단일 노드를 업데이트하더라도 대형 트리의 스냅샷이 생성될 수 있습니다.
* 유효성을 검사할 수 있습니다 `repoinit` 문은 OSGi 구성이 등록될 때 실행되므로 런타임에 로컬 개발 환경에서 실행됩니다.
* `Repoinit` 문은 원자적이며 명시적이며 상태가 이미 일치하는 경우 건너뜁니다.

Cloud Manager가 애플리케이션을 배포하는 경우 콘텐츠 패키지 설치와 별도로 해당 명령문을 실행합니다.

만들려면 `repoinit` 명령문을 보려면 아래 절차를 따르십시오.

1. 프로젝트 구성 폴더의 공장 PID `org.apache.sling.jcr.repoinit.RepositoryInitializer`에 대한 OSGi 구성을 추가합니다. **org.apache.sling.jcr.repoinit.RepositoryInitializer~initstructure** 등 구성을 설명하는 이름을 사용합니다.
1. 추가 `repoinit` 구문을 구성의 스크립트 속성에 추가합니다. 구문 및 옵션은 [Sling 설명서](https://sling.apache.org/documentation/bundles/repository-initialization.html)에 문서화되어 있습니다. 하위 폴더 앞에 상위 폴더를 명시적으로 만들어야 합니다. 예: `/content/myfolder` 이전, `/content/myfolder/mysubfolder`이전에 `/content` 명시적으로 생성. ACL을 낮은 수준 구조로 설정하려면 상위 수준으로 설정하고 를 사용하는 것이 좋습니다 `rep:glob` 제한. (예: `(allow jcr:read on /apps restriction(rep:glob,/msm/wcm/rolloutconfigs))`)
1. 런타임 시 로컬 개발 환경의 유효성을 확인합니다.

<!-- last statement in step 2 to be clarified with Brian -->

>[!WARNING]
>
>아래의 노드에 대해 정의된 ACL의 경우 `/apps` 또는 `/libs` 다음 `repoinit`빈 저장소에서 실행이 시작됩니다. 다음 이후 패키지가 설치됩니다. `repoinit` 따라서 문은 패키지에 정의된 어떤 것도 사용할 수 없지만 아래의 상위 구조와 같은 전제 조건을 정의해야 합니다.

>[!TIP]
>
>ACL의 경우 깊은 구조를 만드는 것이 번거로울 수 있습니다. 따라서 상위 수준에서 ACL을 정의하고 를 통해 수행할 위치를 제한하는 것이 더 합리적입니다. `rep:glob` 제한.

에 대한 추가 세부 정보 `repoinit` 에서 찾을 수 있음 [Sling 설명서](https://sling.apache.org/documentation/bundles/repository-initialization.html)

<!-- ### Packaging of Immutable and Mutable Packages {#packaging-of-immutable-and-mutable-packages}

above appears to be internal, to confirm with Brian -->

### 변경 가능한 콘텐츠 패키지에 대한“일회성” 패키지 관리자 {#package-manager-oneoffs-for-mutable-content-packages}

>[!CONTEXTUALHELP]
>id="aemcloud_packagemanager"
>title="패키지 관리자 - 변경 가능한 콘텐츠 패키지 마이그레이션"
>abstract="콘텐츠 패키지를 “일회성”으로 설치해야 하는 사용 사례에서 패키지 관리자 사용에 대해 알아봅니다. 설치에는 프로덕션 문제를 디버깅하기 위해 프로덕션에서 스테이징으로 특정 콘텐츠를 가져오고 온프레미스 환경에서 AEM Cloud 환경 등으로 소형 콘텐츠 패키지를 이전하는 등의 작업이 포함됩니다."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=en" text="콘텐츠 전송 도구"

콘텐츠 패키지를 “일회성”으로 설치해야 하는 사용 사례가 있습니다. 예를 들어 프로덕션 문제를 디버깅하기 위해 프로덕션에서 스테이징으로 특정 콘텐츠를 가져옵니다. 이러한 시나리오의 경우 [패키지 관리자](/help/implementing/developing/tools/package-manager.md) AEM의 환경에서 as a Cloud Service으로 사용할 수 있습니다.

패키지 관리자는 런타임 개념입니다. 변경 불가능한 저장소에 콘텐츠나 코드를 설치할 수 없으므로 해당 콘텐츠 패키지는 변경 가능한 콘텐츠로만 구성되어야 합니다(주로 `/content` 또는 `/conf`). 콘텐츠 패키지에 혼합된 콘텐츠(변경 가능한 콘텐츠와 변경 불가능한 콘텐츠 모두)가 포함된 경우, 변경 가능한 콘텐츠만 설치합니다.

>[!IMPORTANT]
>
>패키지 관리자 사용자 인터페이스는 다음을 반환할 수 있습니다. **정의되지 않음** 패키지를 설치하는 데 10분 이상 걸리는 경우 오류 메시지가 표시됩니다.
>
>이 시간은 설치 오류가 아니라 Cloud Service이 모든 요청에 대해 갖는 시간 초과로 인한 것입니다.
>
>해당 오류가 표시되면 설치를 재시도하지 마십시오. 설치가 배경에서 제대로 진행되고 있습니다. 설치를 다시 시작하면 여러 동시 가져오기 프로세스에서 일부 충돌이 발생할 수 있습니다.

Cloud Manager를 통해 설치된 모든 콘텐츠 패키지(변경 가능 및 변경 불가 모두)는 AEM Package Manager의 사용자 인터페이스에 고정된 상태로 표시됩니다. 이러한 패키지는 재설치, 재구축 또는 다운로드할 수 없으며 **&quot;cp2fm&quot;** cloud Manager에서 설치를 관리했음을 나타내는 접미사.

### 서드파티 패키지 포함 {#including-third-party}

고객은 일반적으로 Adobe의 번역 파트너와 같은 소프트웨어 공급업체와 같은 서드파티 소스의 사전 설치된 패키지를 포함합니다. 원격 저장소에서 해당 패키지를 호스팅하고 `pom.xml`에서 참조하는 것이 좋습니다. 이 방법은에 설명된 대로 공용 저장소 및 암호 보호가 있는 개인 저장소에 대해 가능합니다. [암호로 보호된 maven 저장소](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repositories).

패키지를 원격 저장소에 저장할 수 없는 경우 고객은 프로젝트의 일부로 SCM에 커밋되는 로컬 파일 시스템 기반 Maven 저장소에 배치할 수 있습니다. 이것은 무엇이든지 그것에 의존하는 것에 의해 참조된다. 저장소는 아래 그림과 같이 프로젝트 pom에서 선언됩니다.


```
<repository>
    <id>project.local</id>
    <name>project</name>
    <url>file:${maven.multiModuleProjectDirectory}/repository</url>
</repository>
```

<!-- formatting appears broken in the code sample above, check how it appears on AEM -->

포함된 모든 서드파티 패키지는 이 문서에 설명된 AEM as a Cloud Service 코딩 및 패키징 지침을 준수해야 합니다. 그렇지 않으면 포함 시 배포가 실패합니다.

다음 Maven `POM.xml` 코드 조각은 일반적으로 이라는 프로젝트의 &quot;컨테이너&quot; 패키지에 타사 패키지를 임베드할 수 있는 방법을 보여 줍니다. **&#39;all&#39;**, **filevault-package-maven-plugin** Maven 플러그인 구성

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

AEM 업데이트와 마찬가지로 적절한 상황에서 작성 클러스터 중단 시간을 없애려면 롤링 배치 전략을 사용하여 고객 릴리스를 배포합니다. 일반적인 이벤트 순서는 아래에 설명되어 있습니다. 여기서 고객 코드의 이전 버전 및 새 버전의 노드는 동일한 버전의 AEM 코드를 실행 중입니다.

* 이전 버전의 노드는 활성 상태이고 새 버전의 릴리스 후보는 빌드되고 사용할 수 있습니다.
* 신규 또는 업데이트된 색인 정의가 있는 경우 해당 색인이 처리됩니다. 이전 버전의 노드는 항상 이전 색인을 사용하는 반면, 새 버전의 노드는 항상 새 색인을 사용합니다.
* 이전 버전은 여전히 트래픽을 제공하는 반면 새 버전이 있는 노드는 시작됩니다.
* 이전 버전의 노드가 실행 중이며 새 버전의 노드가 상태 검사를 통해 준비 여부를 확인하는 동안 계속 제공됩니다.
* 준비가 완료된 새 버전의 노드는 트래픽을 수락하고 노드가 오래된 버전으로 교체됩니다.
* 시간이 지남에 따라 이전 버전의 노드는 새 버전의 노드만 남아 있을 때까지 새 버전의 노드로 바뀌고 배포가 완료됩니다.
* 그러면 신규 또는 수정된 가변 콘텐츠가 배포됩니다.

## 색인 {#indexes}

새 색인이나 수정된 색인으로 인해 새 버전이 트래픽을 가져오기 전에 색인화 또는 색인 재지정 단계가 추가로 발생합니다. AEM as a Cloud Service의 색인 관리에 대한 자세한 내용은 [이 문서](/help/operations/indexing.md)에서 확인할 수 있습니다. Cloud Manager에서 빌드 페이지의 색인화 상태를 확인하고 새 버전이 트래픽을 가져올 수 있게 되면 알림을 받을 수 있습니다.

>[!NOTE]
>
>롤링 배포에 필요한 시간은 인덱스 크기에 따라 다릅니다. 그 이유는 새 색인이 생성될 때까지 새 버전이 트래픽을 허용할 수 없기 때문입니다.

현재 AEM as a Cloud Service은 ACS Commons Ensure Oak Index 도구와 같은 인덱스 관리 도구에서는 작동하지 않습니다.

## 복제 {#replication}

게시 메커니즘은 과 하위 호환됩니다. [AEM Replication Java™ API](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html).

Cloud ready AEM 빠른 시작을 사용하여 복제를 개발하고 테스트하려면 작성자/게시 설정과 함께 클래식 복제 기능을 사용해야 합니다. 클라우드에 대해 AEM 작성자의 사용자 인터페이스 진입점이 제거되면 사용자는 `http://localhost:4502/etc/replication` 구성.

## 롤링 배포에 대한 역으로 호환 가능한 코드 {#backwards-compatible-code-for-rolling-deployments}

위에서 설명한 AEM as a Cloud Service의 롤링 배포 전략은 이전 버전과 새 버전이 동시에 작동할 수 있음을 의미합니다. 따라서 계속 작동 중인 이전 AEM 버전과 역으로 호환되지 않는 코드 변경에 주의합니다.

또한 변경 가능한 콘텐츠는 제거되지 않으므로 롤백이 있는 경우 이전 릴리스에서 새 릴리스에 의해 적용된 변경 가능한 콘텐츠 구조와의 호환성을 테스트해야 합니다.

### 서비스 사용자 및 ACL 변경 사항 {#service-users-and-acl-changes}

콘텐츠 또는 코드에 액세스하는 서비스 사용자 또는 ACL을 변경하면 이전 AEM 버전에서 오류가 발생하여 오래된 서비스 사용자가 해당 콘텐츠 또는 코드에 액세스할 수 있습니다. 이 비헤이비어를 해결하려면 변경 사항을 최소 두 개 이상의 릴리스에 분산하는 것이 좋습니다. 첫 번째 릴리스는 후속 릴리스에서 정리하기 전에 링크 역할을 합니다.

### 색인 변경 {#index-changes}

색인이 변경되면 새 버전은 종료될 때까지 색인을 계속 사용하고 이전 버전은 자체 수정된 색인 세트를 사용해야 합니다. 개발자는 [이 문서](/help/operations/indexing.md)에 설명된 색인 관리 기법을 따라야 합니다.

### 롤백에 필요한 일반적인 코딩 {#conservative-coding-for-rollbacks}

배포 후 오류를 보고하거나 감지하는 경우, 이전 버전으로 롤백해야 합니다. 새 구조(변경 가능한 콘텐츠)가 롤백되지 않으므로 새 코드가 새 버전에서 만든 새 구조와 호환되는지 확인하십시오. 이전 코드가 호환되지 않는 경우, 후속 고객 릴리스에 수정 사항을 적용해야 합니다.

## 신속한 개발 환경 (RDE) {#rde}

[신속한 개발 환경](/help/implementing/developing/introduction/rapid-development-environments.md) (또는 간단히 RDE) 개발자는 변경 사항을 신속하게 배포하고 검토할 수 있으므로 이미 로컬 개발 환경에서 작동하는 것으로 입증된 기능을 테스트하는 데 필요한 시간을 최소화할 수 있습니다.

Cloud Manager 파이프라인을 통해 코드를 배포하는 일반 개발 환경과 달리 개발자는 명령줄 도구를 사용하여 로컬 개발 환경에서 RDE로 코드를 동기화합니다. 변경 사항이 RDE에서 성공적으로 테스트되면 Cloud Manager 파이프라인을 통해 일반 클라우드 개발 환경에 배포하고 이를 통해 적절한 품질 게이트를 통해 코드를 배치합니다.

## 실행 모드 {#runmodes}

기존 AEM 솔루션에서 고객은 임의의 실행 모드로 인스턴스를 실행하고, OSGI 구성을 적용하거나 해당 특정 인스턴스에 OSGI 번들을 설치할 수 있습니다. 일반적으로 정의된 실행 모드에는 *서비스*(작성자 및 게시) 및 환경(RDE, 개발, 스테이지, 프로덕션)이 포함됩니다.

반면에 AEM as a Cloud Service는 사용 가능한 실행 모드와 OSGI 번들 및 OSGI 구성을 매핑할 수 있는 방법에 있어 보다 독창적입니다.

* OSGI 구성 실행 모드는 환경에 대한 RDE, 개발, 스테이지, 프로덕션 또는 서비스에 대한 작성자, 게시를 참조해야 합니다. 의 조합 `<service>.<environment_type>` 는 지원되지만 이러한 환경은 다음과 같은 특정 순서로 사용해야 합니다 `author.dev` 또는 `publish.prod`). OSGI 토큰은 를 사용하지 않고 코드에서 직접 참조해야 합니다. `getRunModes` 메서드, 더 이상 `environment_type` 런타임 시. 자세한 내용은 [AEM as a Cloud Service용 OSGi 구성](/help/implementing/deploying/configuring-osgi.md)을 참조하십시오.
* OSGI 번들 실행 모드는 서비스(작성자, 게시)로 제한됩니다. 실행별 모드 OSGI 번들은 `install.author` 또는 `install.publish` 아래의 콘텐츠 패키지에 설치해야 합니다.

AEM as a Cloud Service에서는 실행 모드를 사용하여 특정 환경 또는 서비스에 대한 콘텐츠를 설치할 수 없습니다. 스테이징 또는 프로덕션 환경에 없는 데이터 또는 HTML으로 개발 환경을 시드해야 하는 경우 패키지 관리자 를 사용할 수 있습니다.

지원되는 실행 모드 구성은

* **config** (*기본값, 모든 AEM 서비스*&#x200B;에 적용됨)
* **config.author** (*모든 AEM 작성자 서비스에 적용됨*)
* **config.author.dev** (*모든 AEM 개발 작성자 서비스에 적용됨*)
* **config.author.rde** (*모든 AEM RDE 작성자 서비스에 적용됨*)
* **config.author.stag** (*모든 AEM 스테이징 작성자 서비스에 적용됨*)
* **config.author.prod** (*모든 AEM 프로덕션 작성자 서비스에 적용됨*)
* **config.publish** (*AEM 게시 서비스에 적용됨*)
* **config.publish.dev** (*AEM 개발 게시 서비스에 적용됨*)
* **config.publish.rde** (*AEM RDE 게시 서비스에 적용됨*)
* **config.publish.stage** (*모든 AEM 스테이징 게시 서비스에 적용됨*)
* **config.publish.prod** (*모든 AEM 프로덕션 게시 서비스에 적용됨*)
* **config.dev** (*AEM 개발 서비스에 적용됨*)
* **config.rde** (*RDE 서비스에 적용됨*)
* **config.stage** (*AEM 스테이징 서비스에 적용됨*)
* **config.prod** (*AEM 프로덕션 서비스에 적용됨*)

가장 일치하는 실행 모드가 있는 OSGI 구성이 사용됩니다.

로컬에서 개발할 때 실행 모드 시작 매개 변수 `-r`는 실행 모드 OSGI 구성을 지정하는 데 사용됩니다.

```shell
$ java -jar aem-sdk-quickstart-xxxx.x.xxx.xxxx-xxxx.jar -r publish,dev
```

<!-- ### Performance Monitoring {#performance-monitoring}

Developers want to ensure that their custom code is performing well. For Cloud environments, performance reports can be viewed on Cloud Manager. -->

## 소스 제어의 유지 관리 작업 구성 {#maintenance-tasks-configuration-in-source-control}

유지 관리 작업 구성은 소스 제어에서 유지되어야 합니다. **도구 > 작업** 클라우드 환경에서는 화면을 사용할 수 없습니다. 이러한 이점은 변화들이 반응적으로 적용되고 잊혀지지 않고 의도적으로 지속되도록 한다. 다음을 참조하십시오 [유지 관리 작업 문서](/help/operations/maintenance.md) 추가 정보.
