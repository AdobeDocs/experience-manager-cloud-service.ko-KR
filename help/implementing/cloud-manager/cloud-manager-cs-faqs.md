---
title: Cloud Manager - Cloud Services FAQ
seo-title: Cloud Manager FAQs
description: 문제 해결 팁은 Cloud Manager에서 Cloud Services FAQ 를 참조하십시오
seo-description: Follow this page to get answers on Cloud Manager - Cloud Services FAQs
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 1%

---

# Cloud Manager FAQ {#cloud-manager-faqs}

다음 섹션에서는 Cloud Services에 대한 Cloud Manager와 관련된 FAQ에 대한 답변을 제공합니다.

## Cloud Manager 빌드와 함께 Java 11을 사용할 수 있습니까? {#java-11-cloud-manager}

Java 8에서 11로 빌드를 전환하려고 할 때 AEM Cloud Manager 빌드가 실패합니다. 이 문제는 많은 원인을 가질 수 있으며, 가장 일반적인 원인은 아래에 설명되어 있습니다.

* 설명된 대로 Java 11에 대한 올바른 설정을 사용하여 maven-toolchain-plugin을 추가합니다 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started).  예를 들어 [wknd 샘플 프로젝트 코드](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* 아래 오류가 발생하면 을(를) 제거해야 합니다 `maven-scr-plugin` 모든 OSGi 주석을 OSGi R6 주석으로 변환합니다. 자세한 내용은 [여기](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Cloud Manager 빌드의 경우 maven enforcer 플러그인이 오류로 실패합니다 `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. 이 문제는 코드 컴파일과 비교하여 maven 명령을 실행하기 위해 다른 버전의 Java를 사용하는 Cloud Manager로 인해 알려진 문제입니다. 지금은 생략하세요 `requireJavaVersion` maven-enforcer-plugin 구성에서

## 코드 품질 검사가 실패하여 배포가 중단되었습니다. 이 수표를 우회할 수 있는 방법이 있나요? {#deployment-stuck}

다음을 제외한 모든 코드 품질 오류 *보안 등급* 는 중요하지 않은 지표이므로 결과 UI에서 항목을 확장하여 생략할 수 있습니다.

을 사용하는 사용자 [배포 관리자, 프로젝트 관리자 또는 비즈니스 소유자](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) 역할은 문제를 재정의할 수 있습니다. 이 경우 파이프라인이 진행되거나 해당 문제를 수락할 수 있습니다. 이 경우 파이프라인이 오류로 중지됩니다.  자세한 내용은 [파이프라인 실행 중 3계층 게이트](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use) 자세한 내용


## Maven 프로젝트 버전에서 SNAPSHOT을 사용할 수 있습니까? 패키지 및 번들 jar 파일의 버전 관리는 스테이지 및 프로덕션 배포에 대해 어떻게 작동합니까? {#snapshot-version}

스테이지 및 프로덕션 배포를 위한 패키지 및 번들 jar 파일의 버전 관리에 대해 알아보려면 다음 시나리오를 참조하십시오.

1. 개발자 배포의 경우 Git 분기 `pom.xml` 파일은 포함해야 합니다. `-SNAPSHOT` 의 끝 `<version>` 값. 이렇게 하면 버전이 변경되지 않고 여전히 설치되도록 후속 배포가 가능합니다. 개발자 배포에서 maven 빌드에 대한 자동 버전이 추가되거나 생성되지 않습니다.

1. 스테이지 및 프로덕션 배포에서는 설명된 대로 자동 버전이 생성됩니다 [여기](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=en#managing-code).

1. 스테이지 및 프로덕션 배포의 사용자 정의 버전 지정을 위해 다음과 같은 3가지 부분 적절한 maven 버전을 설정합니다. `1.0.0`. 프로덕션에 다른 배포를 수행해야 할 때마다 버전을 늘립니다.

1. Cloud Manager는 자동으로 해당 버전을 스테이지 및 프로덕션 빌드에 추가하고 Git 분기를 만듭니다. 특별한 구성이 필요하지 않습니다. 위의 3단계를 건너뛰면 배포가 계속 제대로 작동하며 버전이 자동으로 설정됩니다.

1. 버전을 `-SNAPSHOT` 스테이지 및 프로덕션 빌드 또는 배포용. Cloud Manager는 적절한 버전 번호를 자동으로 설정하고 Git에서 태그를 만듭니다. 필요한 경우 나중에 이 태그를 참조할 수 있습니다.

1. 개발 환경에서 몇 가지 실험적인 코드를 시도하려는 경우 새 Git 분기를 만들고 해당 다른 분기를 사용하도록 파이프라인을 설정할 수 있습니다. 이 기능은 배포가 실패하기 시작할 때 이전 버전의 코드로 테스트하여 배포가 언제 중단되었는지 확인하려는 경우에 유용합니다.

   아래의 Git 명령은 명명된 원격 분기를 만듭니다 *testbranch1* 특정 기존 커밋에 대해 `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  이 특수 분기는 다른 분기에 영향을 주지 않고 Cloud Manager에서 사용할 수 있습니다.

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   자세한 내용은 [Git 설명서](https://git-scm.com/book/en/v2/Git-Internals-Git-References) 자세한 내용

   나중에 테스트 분기를 삭제하려면 delete 명령을 사용합니다.

   `git push origin --delete testbranch1`

## Cloud Manager에서 Maven 빌드가 배포되지만 오류 없이 로컬에서 빌드됩니다. 디버그 방법 {#maven-build-fail}

자세한 내용은 [Git 리소스](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) 자세한 내용

## AEM as a Cloud Service 환경에서 Cloud Manager 배포가 배포 단계에서 실패하는 경우 어떻게 해야 합니까? {#cloud-manager-deployment-cloud-service}

배포가 실패하는 가장 일반적인 이유는 *sling-distribution-importer* 사용자.
문제, 원인 및 솔루션을 이해하려면 아래 예를 참조하십시오.

**문제**
AEM as a Cloud Service 환경에서 Cloud Manager 배포 중에 배포 단계가 실패하고 아래 오류와 같은 오류가 관찰됩니다.

`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10`
`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item`
`org.apache.sling.distribution.common.DistributionException: Error processing distribution package`
`dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.`
`Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.`
`Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.`

**원인**

sling-distribution-importer 사용자는 ui.content 패키지에 정의된 컨텐츠 경로에 따라 추가 권한이 필요합니다.  이는 일반적으로 /conf 및 /var 모두에 대한 권한을 추가해야 함을 의미합니다.

**솔루션**
이에 대한 해결 방법은 [RepositoryInitializer OSGi 구성](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#deploying) sling-distribution-importer 사용자에 대한 ACL을 추가하려면 앱 배포 패키지에 스크립트를 사용하십시오.
위의 예제 오류에서 패키지 myapp-base.ui.content-*.zip에 아래의 콘텐츠가 포함됩니다 `/conf` 및 `/var/workflow`. 배포가 실패하지 않도록 이러한 경로 아래에 sling-distribution-importer에 대한 권한을 추가해야 합니다.
다음은 한 예입니다 [org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) sling-distribution-importer 사용자에 대한 추가 권한을 추가하는 그러한 OSGi 구성 중 하나.  이 구성은 /var 아래에 권한을 추가합니다.  아래의 이 xml 파일 [1] 아래의 응용 프로그램 패키지에 추가해야 합니다. `/apps/myapp/config` 여기서 myapp 은 애플리케이션 코드가 저장되는 폴더입니다.
org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config

1. 만약 *sling-distribution-importer* 가 원인이 아닌 경우, 기본 서비스를 차단하는 잘못된 OSGi 구성으로 인해 배포가 실패할 수 있습니다. 배포 중에 명백한 오류가 있는지 확인하려면 로그를 확인하십시오.

1. 디스패처 또는 apache 구성이 잘못되어 배포가 실패할 수 있습니다. SDK에 포함된 Docker 이미지를 사용하여 로컬에서 Apache 구성 및 Dispatcher 구성을 테스트하십시오. 자세한 내용은 [클라우드의 디스패처](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#content-delivery) 간편한 로컬 테스트를 위해 dispatcher Docker 컨테이너를 설정하는 방법에 대해 설명합니다.

1. 작성자에서 게시 인스턴스로 컨텐츠 패키지(sling 배포)를 복제하는 동안 몇 가지 다른 오류로 인해 배포가 실패할 수 있습니다.

   로컬 설정에서 이를 시뮬레이션하려면 아래 단계를 참조하십시오.

   * 작성자 및 게시 인스턴스 설치(최신 AEM SDK jar 사용)
   * 작성자 인스턴스에 로그인합니다.
   * 이동 **도구** -> **배포** -> **배포**
   * 코드 베이스의 일부인 컨텐츠 패키지를 배포하고 오류가 발생하여 큐가 차단되는지 확인합니다

## aio cloud manager 설정 파이프라인 변수를 통해 변수를 설정할 수 없습니다. 이러한 문제를 디버깅하는 방법 {#set-variable}

만약 `403` 아래 명령과 유사한 명령을 통해 파이프라인 변수를 나열하거나 설정할 때 오류가 발생하면 을 로 추가해야 합니다 *배포 관리자* Admin Console에서 Cloud Manager 제품 역할.\
자세한 내용은 [API 권한](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) 자세한 내용

관련 명령 및 오류:

`$ aio cloudmanager:list-pipeline-variables 222`

*오류*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*오류*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1`

`setting variables... !`

*오류*: `Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)`
