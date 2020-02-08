---
title: AEM Connector 제출
description: AEM Connector 제출
translation-type: tm+mt
source-git-commit: 629de3a9f55d2e4c52ef91c9e0bb5d439aebe84f

---


AEM Connector 제출
===========================

아래에 제공된 정보는 AEM Connectors 제출에 유용하며 커넥터 [구현](implement.md) 및 [유지 관리에](maintain.md) 대한 문서와 함께 읽어야 합니다.

AEM Connectors는 Adobe Exchange에 [나열됩니다](https://marketing.adobe.com/resources/content/resources/en/exchange/marketplace.html).

이전 AEM 솔루션에서 패키지 관리자는 다양한 AEM 인스턴스에 커넥터를 설치하는 데 사용되었습니다. 그러나 AEM을 클라우드 서비스로 사용하는 경우 Cloud Manager의 CI/CD 프로세스 동안 커넥터가 배포됩니다. 커넥터를 배포하려면 멀티캠 프로젝트의 pom.xml에서 커넥터를 참조해야 합니다.

프로젝트에 패키지를 포함할 수 있는 방법에는 다양한 옵션이 있습니다.

1. 파트너의 공개 저장소 - 파트너가 공개적으로 액세스 가능한 마스터 저장소에서 컨텐츠 패키지를 호스트합니다.
1. 번들 아티팩트 - 이 경우 커넥터 패키지는 고객의 고급 프로젝트에 로컬로 포함됩니다.

호스팅되는 위치에 관계없이 패키지는 공급업체에서 제공하는 것처럼 pom.xml에서 종속성으로 참조되어야 합니다.

```xml
<!-- UberJAR Dependency to be added to the project's Reactor pom.xml -->
<dependency>
  <groupId>com.partnername</groupId>
  <artifactId>my-artifact</artifactId>
  <version>V123</version> <!-- use the latest! -->
  <scope>provided</scope>
  <classifier>my_classifier</classifier>
</dependency>
```

ISV 파트너가 액세스 가능한 인터넷(예: 액세스 가능한 Cloud Manager)의 확장 저장소에 커넥터를 호스팅하는 경우, ISV는 pom.xml을 배치할 수 있는 저장소 구성을 제공해야 하며, 따라서 빌드 시(위) 커넥터 종속성(위)을(를) 로컬 및 클라우드 관리자 둘 다에 의해 해결할 수 있습니다.

```xml
<repository>
    <id>the-repository</id>
    <name>The Repository Where the Connector is Hosted</name>
    <url>https://repo.partnername.com/repositories/aem_connector_repo</url>
    <releases>
        <enabled>true</enabled>
        <updatePolicy>never</updatePolicy>
    </releases>
    <snapshots>
        <enabled>false</enabled>
    </snapshots>
</repository>
```

ISV 파트너가 커넥터를 다운로드 가능한 파일로 배포하기로 선택한 경우, ISV는 Cloud Manager가 이러한 종속성을 해결할 수 있도록 파일을 AEM 프로젝트의 일부로 Git에 체크 인해야 하는 로컬-파일 시스템 마비소에 배포하는 방법에 대한 지침을 제공해야 합니다.
