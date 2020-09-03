---
title: AEM 커넥터 제출
description: AEM 커넥터 제출
translation-type: tm+mt
source-git-commit: d4e376ab30bb3e1fb533ed32f6ac43580775787c
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 4%

---


AEM 커넥터 제출
===========================

아래에 제공된 정보는 AEM 커넥터를 제출하는 데 유용하며 커넥터 [구현](implement.md) 및 [유지 관리에 대한](maintain.md) 집필과 함께 읽어야 합니다.

AEM 커넥터는 [Adobe Exchange에 나열됩니다](https://partners.adobe.com/exchangeprogram/experiencecloud).

이전 AEM 솔루션에서 패키지 관리자는 다양한 AEM 인스턴스에 커넥터를 설치하는 데 사용되었습니다. 그러나 AEM을 Cloud Service으로 사용할 경우 Cloud Manager의 CI/CD 프로세스 동안 커넥터가 배포됩니다. 커넥터를 배포하려면 마비되는 프로젝트의 pom.xml에서 커넥터를 참조해야 합니다.

프로젝트에 패키지를 포함할 수 있는 방법에는 다양한 옵션이 있습니다.

1. 파트너의 공용 저장소 - 파트너가 공개적으로 액세스할 수 있는 다중 저장소에 컨텐츠 패키지를 호스트합니다.
1. 파트너의 암호로 보호된 저장소 - 파트너가 암호로 보호된 다중 저장소 내에 컨텐츠 패키지를 호스트합니다. 자세한 내용은 [암호로 보호된 세부 정보 저장소를](/help/onboarding/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repositories) 참조하십시오.
1. 번들 아티팩트 - 이 경우 커넥터 패키지는 고객의 고급 프로젝트에 로컬로 포함됩니다.

호스팅 위치에 관계없이 공급업체에서 제공한 대로 패키지를 pom.xml에서 종속성으로 참조해야 합니다.

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

ISV 파트너가 인터넷에 액세스할 수 있는(예: Cloud Manager 액세스 가능) 고급 리포지토리에서 커넥터를 호스팅하는 경우 ISV는 pom.xml을 삽입할 수 있는 저장소 구성을 제공해야 합니다. 따라서 연결 종속성을 빌드 시간(둘 로컬에서 그리고 Cloud Manager 모두)에 해결할 수 있습니다.

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

ISV 파트너가 Connector를 다운로드 가능한 파일로 배포하기로 선택한 경우, ISV는 이러한 종속성을 해결할 수 있도록 AEM 프로젝트의 일부로 Git에 파일을 체크 인해야 하는 로컬-파일 시스템 마웬 저장소에 파일을 배포할 수 있는 방법에 대한 지침을 제공해야 합니다.
