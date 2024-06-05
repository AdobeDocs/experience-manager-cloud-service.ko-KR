---
title: AEM as a Cloud Service SDK
description: AEM as a Cloud Service 소프트웨어 개발 키트 개요
exl-id: 06f3d5ee-440e-4cc5-877a-5038f9bd44c6
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1213'
ht-degree: 1%

---

# AEM as a Cloud Service SDK {#aem-as-a-cloud-service-sdk}

AEM as a Cloud Service SDK는 다음 아티팩트로 구성됩니다.

* **Quickstart Jar** - 로컬 개발에 사용되는 AEM 런타임
* **Java™ API Jar** - AEM as a Cloud Service에 대해 개발하는 데 사용할 수 있는 허용된 모든 Java™ API를 노출하는 Java™ Jar/Maven 종속성. 이전에 Uberjar라고 함
* **Javadoc Jar** - Java™ API Jar에 대한 javadocs
* **Dispatcher 도구** - 로컬에서 Dispatcher에 대해 개발하는 데 사용되는 도구 세트 UNIX® 및 Windows용 개별 객체

또한 이전에 AEM 6.5 이전 버전과 함께 배포된 일부 고객은 아래 아티팩트를 사용합니다. 로컬 컴파일이 Quickstart jar에서 작동하지 않고 AEM에서 as a Cloud Service으로 배포한 인터페이스를 제거한 것으로 의심되는 경우 고객 지원 센터에 문의하십시오. 액세스 권한이 필요한지 여부를 확인할 수 있습니다. 백엔드를 변경해야 합니다.

* **6.5 더 이상 사용되지 않는 Java™ API Jar** - AEM 6.5 이후 제거된 추가 인터페이스 세트
* **6.5 더 이상 사용되지 않는 Javadoc Jar** - 추가 인터페이스 세트의 Javadocs

## SDK용 빌드 {#building-for-the-sdk}

AEM as a Cloud Service SDK는 사용자 지정 코드를 빌드하고 배포하는 데 사용됩니다. 다음을 참조하십시오. [AEM Project Archetype 설명서](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html). 높은 수준에서 다음 단계가 수행됩니다.

* **컴파일 코드**. 예상대로 소스 코드가 컴파일되어 결과 콘텐츠 패키지가 생성됩니다
* **아티팩트 작성**. 아티팩트는 이 프로세스 중에 빌드됩니다.
* **번들 분석**. 번들은 종속성 누락과 같은 Maven 프로젝트의 문제를 찾는 Maven Analyzer 플러그인을 사용하여 분석됩니다
* **아티팩트 배포**. 아티팩트가 로컬 서버에 배포됩니다.

클라우드 환경에 배포할 때 Cloud Manager에서 동일한 단계를 실행합니다. 로컬에서 빌드를 수행하면 로컬 개발 및 테스트가 가능합니다. 개발자는 소스 제어를 커밋하고 Cloud Manager 배포를 트리거하기 전에 코드 또는 구조적 문제를 효율적으로 발견할 수 있으며, 이 작업에는 더 많은 시간이 걸릴 수 있습니다.

>[!NOTE]
>
>AEM as a Cloud Service SDK는에서 지원하는 Java 배포 및 버전을 사용하여 빌드해야 합니다. [Cloud Manager의 빌드 환경](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md). AEM as a Cloud Service 고객은 다음 위치에서 Oracle JDK를 다운로드할 수 있습니다. [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) Adobe Experience Manager 프로젝트에서 사용할 경우 Adobe의 라이선스 및 Oracle Java 기술에 대한 지원 약관으로 인해 2026년 9월까지 Java 11 확장 지원이 제공됩니다.

## AEM as a Cloud Service SDK 액세스 {#accessing-the-aem-as-a-cloud-service-sdk}

* AEM Admin Console을 확인할 수 있습니다 **Adobe Experience Manager 정보** 아이콘을 클릭하여 프로덕션에서 실행 중인 AEM 버전을 확인합니다.
* Quickstart jar 및 Dispatcher 도구는 에서 zip 파일로 다운로드할 수 있습니다. [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). SDK 목록에 대한 액세스는 AEM Managed Services AEM 또는 as a Cloud Service에 환경이 있는 사람들로 제한됩니다.
* Java™ API Jar 및 Javadoc Jar는 명령줄 또는 기본 IDE를 사용하여 Maven 도구를 통해 다운로드할 수 있습니다.
* Maven 프로젝트 pom은 다음 API Jar 패키지를 참조해야 합니다. 하위 패키지 폼에 대한 종속성도 참조해야 합니다.

```
<dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>aem-sdk-api</artifactId>
  <version>2019.11.3006.20191108T223635Z-191201</version>
  <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>SDK의 버전 항목은 AEM as a Cloud Service의 버전과 일치해야 합니다. AEM에 로그온하면 사용 중인 버전을 확인할 수 있습니다. 화면 오른쪽 상단에서 물음표로 이동하여 을 선택합니다 **[!UICONTROL Adobe Experience Manager 정보]**.


## 새 SDK 버전으로 로컬 프로젝트 새로 고침 {#refreshing-a-local-project-with-a-new-skd-version}

로컬 프로젝트를 새 SDK로 새로 고치는 것이 언제 권장됩니까?

Adobe *추천* 월별 유지 관리 릴리스 이후 새로 고치는 중입니다.

다음과 같습니다. *선택 사항* 매일 유지 관리 릴리스 후에 새로 고침합니다. 프로덕션 인스턴스가 새 AEM 버전으로 성공적으로 업그레이드되면 고객에게 알림이 표시됩니다. 일별 유지 관리 릴리스의 경우 새 SDK가 크게 변경되지는 않을 것으로 예상됩니다. 로컬 AEM 개발자 환경을 최신 SDK로 새로 고친 다음 사용자 지정 애플리케이션을 다시 빌드하고 테스트하는 것이 좋습니다. 월별 유지 관리 릴리스에는 일반적으로 보다 효과적인 변경 사항이 포함되므로 개발자는 즉시 새로 고치고, 다시 빌드하고, 테스트해야 합니다.

다음은 로컬 환경을 새로 고치는 데 권장되는 절차입니다.

1. 유용한 콘텐츠를 소스 제어에서 프로젝트에 커밋하거나 나중에 가져올 수 있도록 가변 콘텐츠 패키지에서 사용할 수 있는지 확인하십시오.
1. 로컬 개발 테스트 콘텐츠는 Cloud Manager 파이프라인 빌드의 일부로 배포되지 않도록 별도로 저장해야 합니다. 그 이유는 지역 개발에만 활용되고 있기 때문이다.
1. 현재 실행 중인 빠른 시작을 중지합니다.
1. 이동 `crx-quickstart` 안전한 보관을 위해 다른 폴더로 이동하십시오.
1. Cloud Manager에 기록된 새 AEM 버전을 확인합니다(계속 다운로드할 새 QuickStart Jar 버전을 식별하는 데 사용됨).
1. 소프트웨어 배포 포털에서 프로덕션 AEM 버전과 일치하는 버전이 있는 QuickStart JAR를 다운로드합니다.
1. 새 폴더를 만들고 새 QuickStart Jar 를 내부에 넣습니다.
1. 원하는 실행 모드로 새 빠른 시작을 시작합니다(파일 이름을 바꾸거나 를 통해 실행 모드로 전달). `-r`).
   * 폴더에 이전 빠른 시작이 남아 있지 않은지 확인하십시오.
1. AEM 애플리케이션을 빌드합니다.
1. 패키지 관리자를 통해 AEM 애플리케이션을 로컬 AEM에 배포합니다.
1. 패키지 관리자를 통해 로컬 환경 테스트에 필요한 변경 가능한 콘텐츠 패키지를 설치합니다.
1. 필요에 따라 개발을 계속하고 변경 사항을 배포합니다.

각 새 AEM 빠른 시작 버전과 함께 설치해야 하는 콘텐츠가 있는 경우 콘텐츠 패키지 및 프로젝트의 소스 제어에 포함하십시오. 그런 다음 매번 설치합니다.

SDK를 자주 업데이트(예: 격주)하고 전체 로컬 상태를 매일 삭제하여 애플리케이션의 상태 저장 데이터에 실수로 의존하지 않도록 하는 것이 좋습니다.

CryptoSupport에 의존하는 경우([AEM에서 클라우드 서비스 또는 SMTP 메일 서비스의 자격 증명을 구성하거나 애플리케이션에서 CryptoSupport API를 사용하여](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/granite/crypto/CryptoSupport.html)) 암호화된 속성은 키로 암호화됩니다. 이 키는 AEM 환경의 첫 번째 시작 시 자동으로 생성됩니다. 클라우드 설정은 환경별 CryptoKey를 자동으로 재사용하는 것을 처리하지만, 로컬 개발 환경에 CryptoKey를 주입해야 합니다.

기본적으로 AEM은 폴더의 데이터 폴더 내에 키 데이터를 저장하도록 구성되지만 개발에서 쉽게 재사용할 수 있도록 AEM 프로세스를 처음 시작할 때 &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. 이 프로세스는 의 암호화 데이터를 생성합니다.`/etc/key`&quot;.

암호화된 값이 포함된 컨텐츠 패키지를 재사용하려면 다음 단계를 따르십시오.

* 로컬 quickstart.jar를 처음 시작할 때 아래 매개 변수를 추가해야 합니다. &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. 항상 추가하는 것이 좋지만 선택 사항입니다.
* 인스턴스를 처음 시작할 때 루트 &quot;&quot;에 대한 필터가 포함된 패키지를 만듭니다.`/etc/key`&quot;. 이 패키지에는 재사용할 모든 환경에서 암호를 재사용할 수 있도록 설정되어 있습니다.
* 비밀을 포함하는 변경 가능한 콘텐츠를 내보내거나 `/crx/de` 따라서 여러 설치에서 재사용되는 패키지에 추가할 수 있습니다.
* 새 인스턴스를 스핀업할 때마다(새 버전으로 대체하거나 여러 개발 환경에서 테스트를 위한 자격 증명을 공유해야 함) 2단계와 3단계에서 생성된 패키지를 설치하십시오. 이렇게 하면 수동으로 재구성할 필요 없이 콘텐츠를 재사용할 수 있습니다. 그 이유는 이제 암호키가 동기화되어 있기 때문입니다.
