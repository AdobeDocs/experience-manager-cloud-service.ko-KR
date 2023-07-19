---
title: Cloud Manager FAQ
description: AEM as a Cloud Service의 Cloud Manager에 대해 가장 자주 묻는 질문에 대한 답변을 살펴보십시오.
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: ht
source-wordcount: '987'
ht-degree: 100%

---


# Cloud Manager FAQ {#cloud-manager-faqs}

이 문서에서는 AEM as a Cloud Service의 Cloud Manager에 대해 가장 자주 묻는 질문에 대한 답변을 살펴봅니다.

## Cloud Manager 빌드와 함께 Java™ 11을 사용할 수 있습니까? {#java-11-cloud-manager}

예. Java™ 11에 대한 적절한 설정과 함께 `maven-toolchains-plugin`을 추가합니다.

프로세스는 [여기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/using-the-wizard.md#getting-started)에 설명되어 있습니다.

예를 들어 [wknd 프로젝트 샘플 프로젝트 코드](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75)를 참조하십시오.

## Java™ 8에서 Java™ 11로 전환한 후 maven-scr-plugin에 대한 오류와 함께 빌드가 실패합니다. 어떻게 해야 합니까? {#build-fails-maven-scr-plugin}

빌드를 Java™ 8에서 11로 전환하려고 하면 AEM Cloud Manager 빌드가 실패할 수 있습니다. 다음 오류가 발생하면 `maven-scr-plugin`을 제거하고 모든 OSGi 주석을 OSGi R6 주석으로 전환해야 합니다.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

이 플러그인을 제거하는 방법에 대한 지침은 [여기](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/)를 참조하십시오.

## Java™ 8에서 Java™ 11로 전환한 후 RequireJavaVersion에 대한 오류와 함께 빌드가 실패합니다. 어떻게 해야 합니까? {#build-fails-requirejavaversion}

Cloud Manager 빌드의 경우 `maven-enforcer-plugin`이 실패하고 이러한 오류가 표시될 수 있습니다.

```text
"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion".
```

이 오류는 Cloud Manager가 다른 버전의 Java™를 사용하여 maven 명령을 실행하고 코드를 컴파일하기 때문에 알려진 문제입니다. `maven-enforcer-plugin` 구성에서 `requireJavaVersion`을 생략하기만 하면 됩니다.

## 코드 품질 검사에 실패하여 배포가 중단되었습니다. 이 검사를 우회하는 방법이 있습니까? {#deployment-stuck}

예. 보안 등급을 제외한 모든 코드 품질 검사 실패는 중요하지 않은 지표이므로 결과 UI의 항목을 확장하여 배포 파이프라인의 일부로 우회할 수 있습니다.

[배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자](/help/onboarding/aem-cs-team-product-profiles.md#cloud-manager-product-profiles) 역할을 가진 사용자는 문제를 재정의할 수 있습니다. 이 경우 파이프라인이 진행되거나 문제를 수락할 수 있으며 파이프라인이 실패와 함께 중지됩니다.

자세한 내용은 [코드 품질 테스트](/help/implementing/cloud-manager/code-quality-testing.md#three-tiered-gate) 및 [비프로덕션 파이프라인 구성](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#non-production-pipelines) 문서를 참조하십시오.

## Maven 프로젝트 버전에 SNAPSHOT을 사용할 수 있습니까? {#use-snapshot}

예. 개발자 배포의 경우 git 분기 `pom.xml` 파일의 `<version>` 값 끝에 `-SNAPSHOT`이 포함되어야 합니다.

버전이 변경되지 않은 경우에도 이 값을 사용하여 후속 배포를 계속 설치할 수 있습니다. 개발자 배포에서는 Maven 빌드에 대해 자동 버전이 추가되거나 생성되지 않습니다.

단계 및 프로덕션 빌드 또는 배포에 대해 버전을 `-SNAPSHOT`으로 설정할 수도 있습니다. Cloud Manager는 자동으로 적절한 버전 번호를 설정하고 git에 태그를 생성합니다. 필요한 경우 이 태그를 나중에 참조할 수 있습니다.

버전 처리에 대한 자세한 내용은 [여기에 문서화](/help/implementing/cloud-manager/managing-code/project-version-handling.md)되어 있습니다.

## 패키지 및 번들 버전 관리는 스테이지 및 프로덕션 배포에서 어떻게 작동합니까? {#snapshot-version}

스테이지 및 프로덕션 배포에서는 [여기에 설명](/help/implementing/cloud-manager/managing-code/project-version-handling.md)된 대로 자동 버전이 생성됩니다.

스테이지 및 프로덕션 배포에서 사용자 정의 버전을 사용하려면 `1.0.0`과 같이 적절한 3부분으로 구성된 Maven 버전을 설정합니다. 프로덕션에 배포할 때마다 버전을 늘립니다.

Cloud Manager는 스테이지 및 프로덕션 빌드에 해당 버전을 자동으로 추가하고 git 분기를 만듭니다. 특별한 구성은 필요하지 않습니다. 앞에서 설명한 대로 Maven 버전을 설정하지 않으면 배포가 계속 성공하고 버전이 자동 설정됩니다.

## Maven 빌드가 Cloud Manager 배포에 실패하지만 오류 없이 로컬로 빌드됩니다. 무엇이 문제입니까? {#maven-build-fail}

자세한 내용은 [이 git 리소스](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md)를 참조하십시오.

## AEM as a Cloud Service의 배포 단계에서 Cloud Manager 배포가 실패하면 어떻게 해야 합니까? {#cloud-manager-deployment-cloud-service}

배포가 실패하는 가장 일반적인 이유는 `sling-distribution-importer` 사용자에 대한 권한이 충분하지 않기 때문입니다. 이 경우 Cloud Manager 배포 중 배포 단계가 실패하고 다음과 같은 오류가 생성됩니다.

```text
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item
org.apache.sling.distribution.common.DistributionException: Error processing distribution package
dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.
Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.
Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.
```

`sling-distribution-importer` 사용자는 `ui.content package` 패키지에 정의된 콘텐츠 경로에 대한 추가 권한이 필요합니다. 이 규칙은 일반적으로 `/conf` 및 `/var` 모두에 대한 권한을 추가해야 함을 의미합니다.

해결 방법은 [RepositoryInitializer OSGi 구성](/help/implementing/deploying/overview.md#repoint) 스크립트를 앱 배포 패키지에 추가하여 `sling-distribution-importer` 사용자에 대한 ACL을 추가하는 것입니다.

이전 예의 오류에서 `myapp-base.ui.content-*.zip` 패키지에는 `/conf` 및 `/var/workflow` 아래에 콘텐츠가 포함되어 있습니다. 배포가 성공하려면 해당 경로 아래의 `sling-distribution-importer`에 대한 권한이 필요합니다.

다음은 `sling-distribution-importer` 사용자에 대한 추가 권한을 추가하는 [`org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config`](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) OSGi 구성의 예입니다. 이 구성은 `/var` 아래에 권한을 추가합니다. 이러한 구성은 `/apps/myapp/config` 아래의 애플리케이션 패키지에 추가되어야 합니다(여기서 myapp은 애플리케이션 코드가 저장된 폴더임).

## Cloud Manager 배포는 AEM as a Cloud Service의 배포 단계에서 실패하고 RepositoryInitializer OSGi 구성은 이미 추가했습니다. 그 밖에 어떤 작업을 할 수 있습니까? {#build-failures}

[RepositoryInitializer OSGi 구성을 추가](#cloud-manager-deployment-cloud-service)해도 오류가 해결되지 않으면 이러한 추가 문제 중 하나가 원인일 수 있습니다.

* 기본 제공 서비스를 중단시키는 잘못된 OSGi 구성으로 인해 배포가 실패할 수 있습니다.
   * 배포 중 로그를 확인하여 명백한 오류가 있는지 확인하십시오.

* 잘못된 Dispatcher 또는 Apache 구성으로 인해 배포가 실패할 수 있습니다.
   * SDK에 포함된 도커 이미지를 사용하여 로컬에서 Apache 및 Dispatcher 구성을 테스트해야 합니다.
   * 간편한 로컬 테스트를 위해 Dispatcher 도커 컨테이너를 설정하는 방법은 [클라우드의 Dispatcher](/help/implementing/dispatcher/disp-overview.md#content-delivery)를 참조하십시오.

* 작성자에서 게시 인스턴스로 콘텐츠 패키지를 복제(Sling 배포)하는 동안 다른 오류로 인해 배포가 실패할 수 있습니다.
   * 다음 단계에 따라 로컬 설정에서 문제를 시뮬레이션하십시오.
      1. 최신 AEM SDK jar를 사용하여 로컬로 작성자 및 게시 인스턴스를 설치합니다.
      1. 작성자 인스턴스에 로그온합니다.
      1. **도구** -> **배포** -> **배포**&#x200B;로 이동합니다.
      1. 코드베이스의 일부인 콘텐츠 패키지를 배포하고 대기열이 오류와 함께 차단되는지 확인합니다.

## aio 명령을 사용하여 변수를 설정할 수 없습니다. 어떻게 해야 합니까? {#set-variable}

`aio` 명령을 사용하여 파이프라인 변수를 나열하거나 설정하려고 하면 다음과 같은 `403` 오류가 나타날 수 있습니다.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

이 경우, 이러한 명령을 실행하는 사용자는 Admin Console에서 **배포 관리자** 역할에 추가되어야 합니다.

자세한 내용은 [API 권한](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/)을 참조하십시오.
