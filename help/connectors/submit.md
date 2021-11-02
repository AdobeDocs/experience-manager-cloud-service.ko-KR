---
title: AEM 커넥터 제출
description: AEM 커넥터 제출
exl-id: 9be1f00e-3666-411c-9001-c047e90b6ee5
source-git-commit: cf3273af030a8352044dcf4f88539121249b73e7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 4%

---

AEM 커넥터 제출
===========================

다음은 AEM Connectors 제출을 위한 유용한 정보이며, 관련 문서와 함께 읽어야 합니다 [구현](implement.md) 및  [유지](maintain.md) 커넥터.

AEM 커넥터는 [Adobe 교환](https://partners.adobe.com/exchangeprogram/experiencecloud).

이전 AEM 솔루션에서는 [패키지 관리자](/help/implementing/developing/tools/package-manager.md) 다양한 AEM 인스턴스에 커넥터를 설치하는 데 사용됩니다. 그러나 AEM as a Cloud Service을 사용하면 Cloud Manager의 CI/CD 프로세스 중에 커넥터가 배포됩니다. 커넥터를 배포하려면 maven 프로젝트의 pom.xml에서 커넥터를 참조해야 합니다.

프로젝트에 패키지를 포함할 수 있는 방법에는 다음과 같은 다양한 옵션이 있습니다.

1. Partner 의 공용 저장소 - 파트너는 공개적으로 액세스할 수 있는 maven 저장소에서 컨텐츠 패키지를 호스팅합니다
1. 파트너의 암호로 보호된 리포지토리 - 파트너가 암호로 보호된 maven 저장소에서 컨텐츠 패키지를 호스팅합니다. 자세한 내용은 [암호로 보호된 maven 저장소](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/create-application-project/setting-up-project.html?lang=en#password-protected-maven-repositories) 참조하십시오.
1. 번들 아티팩트 - 이 경우 커넥터 패키지는 고객의 전문 프로젝트에 로컬로 포함됩니다.

호스팅되는 위치에 관계없이 패키지는 공급업체에서 제공하는 대로 pom.xml에서 종속으로 참조되어야 합니다.

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

ISV 파트너가 인터넷에 액세스할 수 있는(예: Cloud Manager 액세스 가능) maven 저장소에서 커넥터를 호스팅하는 경우 ISV는 pom.xml을 배치할 수 있는 저장소 구성을 제공해야 하며, 따라서 커넥터 종속성(위)은 빌드 시(로컬과 Cloud Manager 둘 다) 해결될 수 있습니다.

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

ISV 파트너가 커넥터를 다운로드 가능한 파일로 배포하도록 선택하는 경우, ISV는 Cloud Manager가 이러한 종속성을 해결할 수 있도록 파일을 AEM 프로젝트의 일부로 Git에 체크 인해야 하는 로컬 파일 시스템 전문가 리포지토리에 배포하는 방법에 대한 지침을 제공해야 합니다.
