---
title: Cloud Manager FAQ
description: AEM as a Cloud Service에서 Cloud Manager에 대해 자주 묻는 질문에 대한 답변을 확인하십시오.
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
source-git-commit: 11ac22974524293ce3e4ceaa26e59fe75ea387e6
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 0%

---


# Cloud Manager FAQ {#cloud-manager-faqs}

이 문서는 AEM as a Cloud Service에서 Cloud Manager에 대해 자주 묻는 질문에 대한 답변을 제공합니다.

## Cloud Manager 빌드와 함께 Java 11을 사용할 수 있습니까? {#java-11-cloud-manager}

빌드를 Java 8에서 11로 전환하려고 할 때 AEM Cloud Manager 빌드가 실패할 수 있습니다. 이 섹션에는 많은 이유가 있을 수 있으며, 가장 일반적인 원인은 이 섹션에 설명되어 있습니다.

* 추가 `maven-toolchains-plugin` ( Java 11에 대한 적절한 설정 사용).
   * 이것은 문서화되었습니다 [여기](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/using-the-wizard.md#getting-started).
   * 예를 들어 [wknd 프로젝트 샘플 프로젝트 코드](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* 다음 오류가 발생하면 다음을 제거해야 합니다 `maven-scr-plugin` 모든 OSGi 주석을 OSGi R6 주석으로 변환합니다.
   * 자세한 내용은 [여기 있습니다.](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   ```text
   [main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
   ```

* Cloud Manager 빌드의 경우 `maven-enforcer-plugin` 오류 발생 `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. 이 문제는 코드 컴파일과 비교하여 maven 명령을 실행하기 위해 다른 버전의 Java를 사용하는 Cloud Manager로 인해 알려진 문제입니다. 지금은 생략하세요 `requireJavaVersion` 다음 `maven-enforcer-plugin` 구성.

## 코드 품질 검사에 실패하여 배포가 중단되었습니다. 이 수표를 우회할 수 있는 방법이 있나요? {#deployment-stuck}

보안 등급을 제외한 모든 코드 품질 확인 오류는 중요하지 않은 지표이므로 결과 UI에서 항목을 확장하여 생략할 수 있습니다.

의 사용자 [배포 관리자, 프로그램 관리자 또는 비즈니스 소유자](/help/onboarding/learn-concepts/aem-cs-team-product-profiles.md) 역할은 파이프라인이 진행되는 문제를 무시할 수 있습니다. 이러한 사용자도 문제를 허용할 수 있으며, 이 경우 파이프라인이 오류로 중지됩니다.

문서를 참조하십시오 [코드 품질 테스트](/help/implementing/cloud-manager/code-quality-testing.md) 자세한 내용

## Maven 프로젝트 버전에 SNAPSHOT을 사용할 수 있습니까? 패키지 및 번들 jar 파일의 버전 관리는 스테이지 및 프로덕션 배포에 대해 어떻게 작동합니까? {#snapshot-version}

다음 시나리오는 스테이지 및 프로덕션 배포를 위한 패키지 및 번들 jar 파일 버전 관리를 처리합니다.

* 개발자 배포의 경우 git 분기입니다 `pom.xml` 파일은 포함해야 합니다. `-SNAPSHOT` 의 끝 `<version>` 값.
   * 따라서 버전이 변경되지 않은 경우에도 후속 배포를 계속 설치할 수 있습니다. 개발자 배포에서 maven 빌드에 대한 자동 버전이 추가되거나 생성되지 않습니다.

* 스테이지 및 프로덕션 배포에서 자동 버전은 다음과 같이 생성됩니다. [여기에 설명되어 있습니다.](/help/implementing/cloud-manager/managing-code/project-version-handling.md)

* 스테이지 및 프로덕션 배포에서 사용자 정의 버전 지정을 위해 다음과 같은 적절한 3가지 부분 maven 버전을 설정합니다. `1.0.0`. 프로덕션에 배포할 때마다 버전을 늘립니다.

* Cloud Manager는 해당 버전을 스테이징 및 프로덕션 빌드에 자동으로 추가하고 Git 분기를 만듭니다. 특별한 구성이 필요하지 않습니다. 이전에 설명한 대로 maven 버전을 설정하지 않은 경우 배포는 계속 성공하며 버전이 자동으로 설정됩니다.

* 버전을 로 설정할 수 있습니다. `-SNAPSHOT` 문제 없이 스테이지 및 프로덕션 빌드 또는 배포의 경우. Cloud Manager는 적절한 버전 번호를 자동으로 설정하고 git에서 태그를 만듭니다. 필요한 경우 나중에 이 태그를 참조할 수 있습니다.

* 개발 환경에서 몇 가지 실험 코드를 시도하려는 경우 새 git 분기를 만들고 해당 분기를 사용하도록 파이프라인을 설정할 수 있습니다.
   * 이 기능은 배포가 실패하고 이전 버전의 코드로 테스트하여 실패의 원인이 된 변경 사항을 확인하려는 경우 유용합니다.

   * 아래 git 명령은 명명된 원격 분기를 만듭니다 `testbranch1` 기존 커밋 기반 `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  이 분기는 다른 분기에 영향을 주지 않고 Cloud Manager에서 사용할 수 있습니다.

   ```shell
   git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1
   ```

   * 자세한 내용은 [git 설명서](https://git-scm.com/book/en/v2/Git-Internals-Git-References) 자세한 내용

   * 나중에 테스트 분기를 삭제하려면 delete 명령을 사용합니다.

   ```shell
   git push origin --delete testbranch1
   ```

## Cloud Manager 배포에 대한 전문 빌드가 실패하지만 오류 없이 로컬에서 빌드됩니다. 뭐가 잘못됐나요? {#maven-build-fail}

자세한 내용은 [Git 리소스](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) 자세한 내용

## AEM as a Cloud Service의 배포 단계에서 Cloud Manager 배포가 실패하면 어떻게 해야 합니까? {#cloud-manager-deployment-cloud-service}

배포가 실패하는 가장 일반적인 이유는 `sling-distribution-importer` 사용자. 이 경우 Cloud Manager 배포 중에 배포 단계가 실패하고 다음과 같은 오류가 생성됩니다.

```text
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item
org.apache.sling.distribution.common.DistributionException: Error processing distribution package
dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.
Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.
Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.
```

이 경우 `sling-distribution-importer` 사용자에게는 `ui.content package`.  이는 일반적으로 두 작업 모두에 대한 권한을 추가해야 함을 의미합니다 `/conf` 및 `/var`.

해결 방법은 [RepositoryInitializer OSGi 구성](/help/implementing/deploying/overview.md#repoint) 앱 배포 패키지에 스크립팅하여 `sling-distribution-importer` 사용자.

이전 예제 오류에서 패키지는 `myapp-base.ui.content-*.zip` 다음 콘텐츠 포함 `/conf` 및 `/var/workflow`. 배포가 성공하려면 `sling-distribution-importer` 이 경로에는 다음이 필요합니다.

다음은 한 예입니다 [org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) 에 대한 추가 권한을 추가하는 그러한 OSGi 구성 중 하나 `sling-distribution-importer` 사용자.  이 구성은 다음에 권한을 추가합니다. `/var`.  아래의 이 xml 파일 [1] 아래의 응용 프로그램 패키지에 추가해야 합니다. `/apps/myapp/config` 여기서 myapp 은 애플리케이션 코드가 저장되는 폴더입니다.
org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config

RepositoryInitializer OSGi 구성을 추가해도 오류가 해결되지 않은 경우 이러한 추가 문제 중 하나가 원인일 수 있습니다.

* 기본 제공 서비스를 중단하는 잘못된 OSGi 구성으로 인해 배포가 실패할 수 있습니다.
   * 배포 중에 명백한 오류가 있는지 확인하려면 로그를 확인하십시오.

* 디스패처 또는 Apache 구성이 잘못되어 배포가 실패할 수 있습니다.
   * SDK에 포함된 Docker 이미지를 사용하여 로컬에서 Apache 및 Dispatcher 구성을 테스트하십시오.
   * 자세한 내용은 [클라우드의 디스패처](/help/implementing/dispatcher/disp-overview.md#content-delivery) 간편한 로컬 테스트를 위해 dispatcher Docker 컨테이너를 설정하는 방법에 대해 설명합니다.

* 작성자에서 게시 인스턴스로 컨텐츠 패키지(Sling 배포)를 복제하는 동안 몇 가지 다른 오류로 인해 배포가 실패할 수 있습니다.
   * 다음 단계에 따라 로컬 설정에서 문제를 시뮬레이션합니다.
      1. 최신 AEM SDK jar을 사용하여 로컬에서 작성자 및 게시 인스턴스를 설치합니다.
      1. 작성자 인스턴스에 로그인합니다.
      1. 이동 **도구** -> **배포** -> **배포**.
      1. 코드 베이스의 일부인 컨텐츠 패키지를 배포하고 오류가 발생하여 큐가 차단되는지 확인합니다.

## aio 명령을 사용하여 변수를 설정할 수 없습니다. 어떻게 해야 합니까? {#set-variable}

을(를) 받을 수 있습니다 `403` 를 통해 파이프라인 변수를 나열하거나 설정하려고 할 때 다음과 같은 오류가 발생합니다 `aio` 명령.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

이 경우 이러한 명령을 실행하는 사용자를 **배포 관리** Admin Console의 역할입니다.

자세한 내용은 [API 권한](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) 자세한 내용
