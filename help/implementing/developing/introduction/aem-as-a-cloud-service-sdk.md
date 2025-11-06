---
title: AEM as a Cloud Service SDK
description: AEM as a Cloud Service 소프트웨어 개발 키트에 대한 개요입니다.
exl-id: 06f3d5ee-440e-4cc5-877a-5038f9bd44c6
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1246'
ht-degree: 1%

---

# AEM as a Cloud Service SDK {#aem-as-a-cloud-service-sdk}

AEM as a Cloud Service SDK은 다음 아티팩트로 구성됩니다.

* **Quickstart Jar** - 로컬 개발에 사용되는 AEM 런타임입니다.
* **Java™ API Jar** - AEM as a Cloud Service에 대해 개발하는 데 사용할 수 있는 허용된 모든 Java™ API를 표시하는 Java™ Jar/Maven 종속성입니다. 이전에 Uberjar라고 했습니다.
* **Javadoc Jar** - Java™ API Jar에 대한 Java 문서.
* **Dispatcher 도구** - 로컬에서 Dispatcher에 대해 개발하는 데 사용되는 도구 집합입니다. UNIX® 및 Windows용 아티팩트를 구분합니다.

또한 이전에 AEM 6.5 이전 버전과 함께 배포된 일부 고객은 아래 아티팩트를 사용합니다. 로컬 컴파일이 QuickStart Jar에서 작동하지 않으며 AEM에 배포된 as a Cloud Service에서 인터페이스를 제거한 것으로 의심되는 경우 고객 지원 센터에 문의하십시오. 액세스 권한이 필요한지 여부를 확인할 수 있습니다. 백엔드를 변경해야 합니다.

* **6.5 사용되지 않는 Java™ API Jar** - AEM 6.5 이후 제거된 추가 인터페이스 세트입니다.
* **6.5 더 이상 사용되지 않는 Javadoc Jar** - 추가 인터페이스 세트에 대한 Java 문서.

>[!NOTE]
> 
> AEM as a Cloud Service과 SDK에는 여러 가지 다른 영역에서 차이점이 있습니다. 빠르고 반복적인 변경이 필요한 상황에 대해 Adobe은 신속한 개발 환경을 도입했습니다. 자세한 내용은 [빠른 개발 환경](/help/implementing/developing/introduction/rapid-development-environments.md)을 참조하세요.

## SDK을 위한 빌드 {#building-for-the-sdk}

AEM as a Cloud Service SDK을 사용하여 사용자 지정 코드를 빌드하고 배포합니다. [AEM Project Archetype 설명서](https://experienceleague.adobe.com/ko/docs/experience-manager-core-components/using/developing/archetype/using)를 참조하세요. 높은 수준에서 다음 단계가 수행됩니다.

* **컴파일 코드** - Source 코드가 컴파일되어 결과 콘텐츠 패키지가 생성됩니다.
* **아티팩트 빌드** - 아티팩트는 이 프로세스 동안 빌드됩니다.
* **번들 분석** - Maven 프로젝트에서 종속성 누락과 같은 문제를 찾는 Maven 분석기 플러그인을 사용하여 번들을 분석합니다.
* **아티팩트 배포** - 아티팩트가 로컬 서버에 배포됩니다.

Cloud Manager은 클라우드 환경에 배포할 때 동일한 단계를 실행합니다. 로컬에서 빌드를 수행하면 로컬 개발 및 테스트가 가능합니다. 개발자는 소스 제어에 커밋하기 전에 코드 또는 구조적 문제를 효율적으로 식별할 수 있습니다. 이 프로세스는 Cloud Manager 배포 트리거로 인한 지연을 방지하는 데 도움이 되며, 시간이 더 오래 걸릴 수 있습니다.

>[!NOTE]
>
>AEM as a Cloud Service SDK은 [Cloud Manager의 빌드 환경](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md)에서 지원하는 배포 및 Java 버전으로 빌드되어야 합니다. AEM as a Cloud Service 고객은 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)에서 Oracle JDK를 다운로드할 수 있습니다. Adobe의 Adobe Experience Manager 프로젝트 내 Oracle Java 기술에 대한 라이선스 및 지원 조건으로 인해 Java 11이 2026년 9월까지 확장 지원을 받게 되었습니다.

## AEM as a Cloud Service SDK 액세스 {#accessing-the-aem-as-a-cloud-service-sdk}

* AEM Admin Console의 **Adobe Experience Manager 정보** 아이콘을 확인하여 프로덕션에서 실행 중인 AEM 버전을 확인할 수 있습니다.
* [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)에서 QuickStart Jar 및 Dispatcher 도구를 zip 파일로 다운로드할 수 있습니다. SDK 목록에 대한 액세스는 AEM Managed Services 또는 AEM as a Cloud Service에 환경이 있는 사람들로 제한됩니다.
* Java™ API Jar 및 Javadoc Jar는 Maven 도구를 통해 명령줄 또는 기본 IDE로 다운로드할 수 있습니다.
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
>SDK의 버전 항목은 AEM as a Cloud Service 버전과 일치해야 합니다. AEM에 로그온하여 사용 중인 버전을 확인할 수 있습니다. 화면 오른쪽 상단에서 물음표로 이동하여 **[!UICONTROL Adobe Experience Manager 정보]**&#x200B;를 클릭합니다.


## 새 SDK 버전으로 로컬 프로젝트 새로 고침 {#refreshing-a-local-project-with-a-new-skd-version}

로컬 프로젝트를 새 SDK으로 새로 고치는 것이 언제 권장됩니까?

Adobe *월별 유지 관리 릴리스 이후에 새로 고치는 것이 좋습니다*.

매일 유지 관리 릴리스 후에 새로 고치는 것은 *선택적*&#x200B;입니다. 프로덕션 인스턴스가 새 AEM 버전으로 성공적으로 업그레이드되면 고객에게 알림이 표시됩니다. 일일 유지 관리 릴리스의 경우, 새 SDK이 전혀 크게 변경되지 않았을 것으로 예상됩니다. 여전히 Adobe에서는 로컬 AEM 개발자 환경을 최신 SDK으로 새로 고친 다음 사용자 지정 애플리케이션을 다시 빌드하고 테스트하는 것이 좋습니다. 월별 유지 관리 릴리스에는 일반적으로 보다 효과적인 변경 사항이 포함되므로 개발자는 즉시 새로 고치고, 다시 빌드하고, 테스트해야 합니다.

**로컬 프로젝트를 새 SDK 버전으로 새로 고치려면 다음 작업을 수행하십시오.**

1. 모든 유용한 컨텐츠가 소스 제어에 커밋되는지 확인합니다. 또는 나중에 가져올 수 있도록 가변 콘텐츠 패키지에 저장됩니다.
1. 로컬 개발 테스트 콘텐츠는 Cloud Manager 파이프라인 빌드의 일부로 배포되지 않도록 별도로 저장해야 합니다. 그 이유는 지역 개발에만 활용되고 있기 때문이다.
1. 현재 실행 중인 빠른 시작을 중지합니다.
1. 안전하게 보관하려면 `crx-quickstart` 폴더를 다른 폴더로 이동하십시오.
1. Cloud Manager에 나와 있는 새 AEM 버전을 확인합니다(계속 다운로드할 새 QuickStart Jar 버전을 식별하는 데 사용됨).
1. 소프트웨어 배포 포털에서 프로덕션 AEM 버전과 일치하는 버전이 있는 QuickStart Jar를 다운로드합니다.
1. 새 폴더를 만들고 새 QuickStart Jar 를 내부에 넣습니다.
1. 원하는 실행 모드로 새 빠른 시작을 시작합니다(`-r`을 통해 파일 이름을 바꾸거나 실행 모드로 전달).
폴더에 이전 빠른 시작이 남아 있지 않은지 확인하십시오.
1. AEM 애플리케이션 구축.
1. 패키지 관리자를 통해 AEM 애플리케이션을 로컬 AEM에 배포합니다.
1. 패키지 관리자를 통해 로컬 환경 테스트에 필요한 변경 가능한 콘텐츠 패키지를 설치합니다.
1. 필요에 따라 개발을 계속하고 변경 사항을 배포합니다.

각각의 새로운 AEM 빠른 시작 버전과 함께 설치해야 하는 콘텐츠가 있는 경우 콘텐츠 패키지 및 프로젝트의 소스 제어에 포함하십시오. 그런 다음 매번 설치합니다.

Adobe에서는 SDK을 자주 업데이트할 것을 권장합니다(예: 격주). 또한 애플리케이션에서 실수로 상태 저장 데이터에 의존하지 않도록 전체 로컬 상태를 매일 삭제합니다.

클라우드 서비스용 CryptoSupport, SMTP 메일 구성 또는 CryptoSupport API를 사용하는 경우 암호화된 속성은 키로 보호됩니다. 자세한 내용은 [CryptoSupport API 설명서](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/adobe/granite/crypto/CryptoSupport.html)를 참조하세요. 이 키는 AEM 환경의 첫 번째 시작 시 자동으로 생성됩니다. 클라우드 설정은 환경별 CryptoKey를 자동으로 재사용하는 것을 처리하지만, 로컬 개발 환경에 CryptoKey를 주입해야 합니다.

기본적으로 AEM은 폴더의 데이터 폴더 내에 키 데이터를 저장하도록 구성되지만 개발에서 쉽게 재사용할 수 있도록 AEM 프로세스를 처음 시작할 때 &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;로 초기화할 수 있습니다. 이 프로세스는 &quot;`/etc/key`&quot;에 암호화 데이터를 생성합니다.

**암호화된 값이 들어 있는 콘텐츠 패키지를 다시 사용하려면:**

* 처음에 로컬 quickstart.jar를 시작할 때 아래 매개 변수를 추가해야 합니다. &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;. Adobe은 선택적으로 항상 추가할 것을 권장합니다.
* 인스턴스를 처음 시작할 때 루트 &quot;`/etc/key`&quot;에 대한 필터가 포함된 패키지를 만드십시오. 이 패키지에는 재사용할 모든 환경에서 암호를 재사용할 수 있도록 설정되어 있습니다.
* 비밀이 포함된 변경 가능한 콘텐츠를 내보냅니다. 또는 `/crx/de`을(를) 통해 암호화된 값을 조회하여 설치 시 재사용되는 패키지에 추가할 수 있습니다.
* 새 인스턴스를 스핀업할 때마다(새 버전으로 대체하거나 여러 개발 환경에서 테스트를 위한 자격 증명을 공유해야 함) 2단계와 3단계에서 생성된 패키지를 설치하십시오. 이렇게 하면 수동으로 재구성할 필요 없이 콘텐츠를 재사용할 수 있습니다. 그 이유는 이제 암호키가 동기화되어 있기 때문입니다.

