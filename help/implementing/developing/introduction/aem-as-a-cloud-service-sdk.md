---
title: AEM as a Cloud Service SDK
description: AEM as a Cloud Service 소프트웨어 개발 키트 개요
exl-id: 06f3d5ee-440e-4cc5-877a-5038f9bd44c6
source-git-commit: c08e442e58a4ff36e89a213aa7b297b538ae3bab
workflow-type: tm+mt
source-wordcount: '1179'
ht-degree: 1%

---

# AEM as a Cloud Service SDK {#aem-as-a-cloud-service-sdk}

AEM as a Cloud Service SDK는 다음 가공물로 구성됩니다.

* **Quickstart Jar** - 로컬 개발에 사용되는 AEM 런타임
* **Java API Jar** - AEM에서 Cloud Service으로 개발하는 데 사용할 수 있는 모든 허용된 Java API를 표시하는 Java Jar/Maven 종속성입니다. 이전에 Uberjar라고 함
* **Javadoc Jar** - Java API Jar용 javadocs
* **Dispatcher 도구** - 로컬로 Dispatcher에 대해 개발하는 데 사용되는 도구 세트입니다. unix 및 windows에 대해 별도의 객체

또한 AEM 6.5 이전 버전으로 이전에 배포된 일부 고객은 아래 가공물을 사용합니다. 로컬 컴파일이 Quickstart jar에서 작동하지 않고 AEM에서 제거된 as a Cloud Service 인터페이스 때문에 이러한 인터페이스가 없는 것으로 의심되는 경우 고객 지원 센터에 연락하여 액세스 권한이 필요한지 확인합니다. 이를 위해서는 백엔드를 변경해야 합니다.

* **6.5 더 이상 사용되지 않는 Java API Jar** - AEM 6.5 이후 제거된 추가적인 인터페이스 세트
* **6.5 더 이상 사용되지 않는 Javadoc Jar** - 추가적인 인터페이스 세트를 위한 Javadocs

## SDK용 빌드 {#building-for-the-sdk}

AEM as a Cloud Service SDK는 사용자 지정 코드를 작성하고 배포하는 데 사용됩니다. 자세한 내용은 [AEM 프로젝트 원형 설명서](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en). 높은 수준에서 다음 단계가 수행됩니다.

* **코드 컴파일**. 예상대로 소스 코드가 컴파일되어 결과 컨텐츠 패키지를 생성합니다
* **아티팩트 작성**. 가공물들은 이 프로세스 중에 작성됩니다
* **번들 분석**. 번들은 Maven Analyzer 플러그인을 사용하여 분석되며, 이 플러그인은 누락된 종속성과 같은 Maven 프로젝트에서 문제를 찾습니다
* **아티팩트 배포**. 객체는 로컬 서버에 배포됩니다.

클라우드 환경에 배포할 때 Cloud Manager에서 동일한 단계를 실행합니다. 빌드를 로컬에서 수행하면 로컬 개발 및 테스트를 수행할 수 있으므로 개발자가 소스 제어에 커밋하고 Cloud Manager 배포를 트리거하기 전에 코드 또는 구조적 문제를 효율적으로 검색할 수 있습니다. 이렇게 하면 시간이 더 오래 걸릴 수 있습니다.

## AEM as a Cloud Service SDK 액세스 {#accessing-the-aem-as-a-cloud-service-sdk}

* AEM Admin Console을 확인할 수 있습니다 **Adobe Experience Manager 정보** 아이콘을 사용하여 프로덕션에서 실행 중인 AEM 버전을 확인할 수 있습니다.
* 빠른 시작 jar 및 Dispatcher 도구는 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). SDK 목록에 대한 액세스는 AEM Managed Services 또는 AEM as a Cloud Service 환경을 사용하는 것으로 제한됩니다.
* Java API Jar 및 Javadoc Jar는 명령줄 또는 기본 설정 IDE로 maven 도구를 통해 다운로드할 수 있습니다.
* maven 프로젝트 모듈은 다음 API Jar 패키지를 참조해야 합니다. 이 종속성은 모든 하위 패키지 홈에서도 참조되어야 합니다.

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
>SDK용 버전 항목은 AEM as a Cloud Service 버전과 일치해야 합니다. AEM에 로그인한 다음, 화면의 오른쪽 상단 모서리에 있는 물음표로 이동하여 사용 중인 버전을 확인할 수 있습니다 **[!UICONTROL Adobe Experience Manager 정보]**


## 새 SDK 버전으로 로컬 프로젝트 새로 고침 {#refreshing-a-local-project-with-a-new-skd-version}

새 SDK를 사용하여 로컬 프로젝트를 새로 고치는 것이 좋습니다.

그렇습니다 *권장* 를 새로 고치려면 월별 유지 관리 릴리스 이후에 해야 합니다.

그렇습니다 *옵션* 매일 유지 관리 릴리스 후에 새로 고치려면 다음을 수행하십시오. 프로덕션 인스턴스가 새 AEM 버전으로 성공적으로 업그레이드되면 고객에게 표시됩니다. 일별 유지 관리 릴리스의 경우, 새 SDK가 조금이라도 변경되었다면 변경되지 않았을 것입니다. 여전히 최신 SDK를 사용하여 로컬 AEM 개발자 환경을 새로 고친 다음 사용자 지정 애플리케이션을 다시 빌드하고 테스트하는 것이 좋습니다. 월별 유지 관리 릴리스에는 일반적으로 더 중요한 변경 사항이 포함되므로 개발자는 즉시 새로 고침, 재구성 및 테스트를 수행해야 합니다.

다음은 로컬 환경을 새로 고치는 데 권장되는 절차입니다.

1. 유용한 콘텐츠가 소스 제어에서 프로젝트에 커밋되거나 나중에 가져올 수 있는 가변 콘텐츠 패키지에서 사용할 수 있는지 확인하십시오
1. 로컬 개발 테스트 컨텐츠는 Cloud Manager 파이프라인 빌드의 일부로 배포되지 않도록 별도로 저장해야 합니다. 로컬 개발에만 사용해야 하기 때문입니다
1. 현재 실행 중인 빠른 시작을 중지합니다
1. 이동 `crx-quickstart` 안전한 보관을 위해 다른 폴더에 폴더 추가
1. Cloud Manager에 나와 있는 새 AEM 버전을 확인합니다(추가로 다운로드할 새 QuickStart Jar 버전을 식별하는 데 사용됩니다.)
1. Software Distribution Portal에서 Production AEM 버전과 일치하는 버전의 QuickStart JAR를 다운로드합니다
1. 완전히 새로운 폴더를 만들고 새 QuickStart Jar를 내부에 넣습니다
1. 원하는 실행 모드로 새 QuickStart를 시작합니다(파일 이름 바꾸기 또는 를 통해 실행 모드로 전달) `-r`).
   * 폴더에 이전 빠른 시작의 남은 항목이 없는지 확인합니다.
1. AEM 애플리케이션 빌드
1. PackageManager 를 통해 로컬 AEM에 AEM 애플리케이션 배포
1. PackageManager 를 통해 로컬 환경 테스트에 필요한 가변 컨텐츠 패키지를 설치합니다
1. 필요에 따라 개발 및 변경 사항 배포

각 새로운 AEM 빠른 시작 버전과 함께 설치해야 하는 컨텐츠가 있는 경우 컨텐츠 패키지 및 프로젝트의 소스 제어에 포함하십시오. 그런 다음 매번 설치합니다.

SDK를 자주(예: 2주별) 업데이트하고 실수로 응용 프로그램의 상태 저장 데이터에 의존하지 않도록 전체 로컬 상태를 매일 삭제하는 것이 좋습니다.

CryptoSupport([AEM에서 또는 애플리케이션에서 CryptoSupport API를 사용하여 Cloudservices 또는 SMTP 메일 서비스의 자격 증명을 구성하거나](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/granite/crypto/CryptoSupport.html))로 설정되면 암호화된 속성은 AEM 환경의 첫 번째 시작 시 자동으로 생성되는 키에 의해 암호화됩니다. cloudsetup에서는 환경별 CryptoKey를 자동으로 재사용하는 동안 로컬 개발 환경에 암호키를 주입해야 합니다.

기본적으로 AEM은 폴더의 데이터 폴더 내에 키 데이터를 저장하도록 구성되지만 개발 시 보다 쉽게 재사용할 수 있도록 &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. 이렇게 하면 &quot;&quot;에서 암호화 데이터가 생성됩니다.`/etc/key`&quot;.

암호화된 값이 포함된 컨텐츠 패키지를 다시 사용하려면 다음 단계를 수행해야 합니다.

* 처음에 로컬 quickstart.jar를 시작할 때 아래 매개 변수를 추가해야 합니다. &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. 항상 추가하는 것은 권장되지만, 선택 사항입니다.
* 인스턴스를 처음 시작할 때 루트에 대한 필터가 포함된 패키지를 만듭니다. &quot;`/etc/key`&quot;. 이렇게 하면 재사용하려는 모든 환경에서 재사용할 수 있는 비밀이 유지됩니다
* 비밀을 포함하는 가변 콘텐츠를 내보내거나 를 통해 암호화된 값을 찾습니다. `/crx/de` 를 패키지에 추가하는 방법은 설치 간에 재사용할 수 있습니다
* 새 인스턴스를 스핀업할 때마다(새 버전으로 대체하거나 여러 개발 환경에서 테스트를 위한 자격 증명을 공유해야 함), 2단계 및 3단계에서 생성된 패키지를 설치하여 수동으로 다시 구성할 필요 없이 컨텐츠를 재사용할 수 있습니다. 이제 암호키가 동기화되기 때문입니다.
