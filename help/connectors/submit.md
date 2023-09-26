---
title: AEM 커넥터 제출
description: Adobe Experience Manager(AEM) as a Cloud Service에서 커넥터를 올바르게 참조하고 배포하는 방법을 알아봅니다.
exl-id: 9be1f00e-3666-411c-9001-c047e90b6ee5
source-git-commit: 78ead5f15c2613d9c3bed3025b43423a66805c59
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 30%

---

# AEM 커넥터 제출

다음은 AEM(Adobe Experience Manager) 커넥터 제출을 위한 유용한 정보이며, 관련 문서를 참조하십시오. [구현](implement.md) 및  [유지 관리](maintain.md) 커넥터.

AEM 커넥터는 [Adobe Exchange](https://partners.adobe.com/technologyprogram/experiencecloud.html)에 나열되어 있습니다.

이전 AEM 솔루션에서는 다양한 AEM 인스턴스에 커넥터를 설치하기 위해 [패키지 관리자](/help/implementing/developing/tools/package-manager.md)를 사용했습니다. 그러나 AEM as a Cloud Service를 사용하면 Cloud Manager의 CI/CD 프로세스 중에 커넥터가 배포됩니다. 커넥터를 배포하려면 Maven 프로젝트의 pom.xml에서 커넥터를 참조해야 합니다.

패키지를 프로젝트에 포함하는 방법에는 여러 가지 옵션이 있습니다.

1. 파트너의 공개 저장소 - 파트너는 공개적으로 액세스할 수 있는 Maven 저장소에 콘텐츠 패키지를 호스팅할 수 있습니다.
1. 파트너의 암호로 보호된 저장소 - 파트너는 암호로 보호된 Maven 저장소에 콘텐츠 패키지를 호스팅할 수 있습니다. 다음을 참조하십시오 [암호로 보호된 maven 저장소](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/create-application-project/setting-up-project.html?lang=en#password-protected-maven-repositories) 설명서를 참조하십시오.
1. 번들형 아티팩트 - 이 경우 커넥터 패키지는 고객의 Maven 프로젝트에 로컬로 포함됩니다.

호스팅되는 위치에 관계없이 패키지는 공급업체에서 제공한 대로 pom.xml의 종속성으로 참조되어야 합니다.

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

ISV 파트너가 인터넷에 액세스할 수 있는(예: Cloud Manager에 액세스 가능) Maven 저장소에서 커넥터를 호스팅하는 경우 ISV는 `pom.xml` 를 배치할 수 있습니다. 그 이유는 (위의) 커넥터 종속성을 로컬 및 Cloud Manager를 통해 빌드 시 해결할 수 있기 때문입니다.

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

ISV 파트너가 커넥터를 다운로드 가능한 파일로 배포하도록 선택하는 경우 ISV가 지침을 제공해야 합니다. 지침은 AEM 프로젝트의 일부로 Git에 체크 인해야 하는 로컬 파일 시스템 Maven 저장소에 파일을 배포하는 방법을 설명해야 합니다. 이렇게 하면 Cloud Manager가 이러한 종속성을 해결할 수 있습니다.
