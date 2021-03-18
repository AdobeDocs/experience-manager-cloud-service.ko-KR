---
title: AEM as a Cloud Service SDK
description: Cloud Service 소프트웨어 개발 키트로서의 AEM 개요
translation-type: tm+mt
source-git-commit: 6b754a866be7979984d613b95a6137104be05399
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Cloud Service SDK {#aem-as-a-cloud-service-sdk}인 AEM

Cloud Service SDK로 AEM은 다음 가공물로 구성됩니다.

* **빠른 시작 Jar**  - 로컬 개발에 사용되는 AEM 런타임입니다.
* **Java API Jar**  - AEM에 대해 Cloud Service으로 개발할 수 있는 모든 허용되는 Java API를 표시하는 Java Jar/Maven 종속성을 사용합니다. 이전에 Uberjar라고 함
* **Javadoc Jar**  - Java API Jar용 javadocs
* **발송자 도구**  - Dispatcher 로컬에서 개발하는 데 사용되는 도구 세트입니다. unix 및 windows용 가공물 분리

또한 AEM 6.5 이전 버전으로 이전에 배포한 일부 고객은 아래 자료를 사용하게 됩니다. 로컬 컴파일이 Quickstart jar에서 작동하지 않고 AEM에서 Cloud Service으로 배포한 인터페이스로 인해 제거되었다고 의심되는 경우 고객 지원에 문의하여 액세스 권한이 필요한지 확인합니다. 백엔드 변경 사항이 필요합니다.

* **6.5 가치가 떨어진 Java API Jar**  - AEM 6.5 이후 제거된 추가 인터페이스 세트
* **6.5 더 이상 사용되지 않는 Javadoc Jar**  - 추가 인터페이스 세트에 대한 Javadocs

## SDK {#building-for-the-sdk} 빌드

Cloud Service SDK로 AEM을 사용하면 사용자 지정 코드를 작성하고 배포할 수 있습니다. 자세한 내용은 [AEM 프로젝트 원형 문서](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=en)를 참조하십시오. 높은 수준에서 다음 단계가 수행됩니다.

* **코드를 컴파일합니다**. 예상대로 소스 코드가 컴파일되어 결과 콘텐츠 패키지가 생성됩니다.
* **아티팩트를 제작할 수 있습니다**. 아티팩트는 이 프로세스 동안 빌드됩니다.
* **번들** 분석 번들은 누락된 종속성이 있는 Maven Analyzer 플러그인을 사용하여 분석됩니다. 이 플러그인은 Maven 프로젝트에서 발생하는 문제를 찾습니다
* **가공물을 배포합니다**. 가공물은 로컬 서버에 배포됩니다.

클라우드 환경에 배포하면 Cloud Manager에서 동일한 단계를 실행합니다. 로컬에서 빌드를 수행하면 로컬 개발 및 테스트를 수행할 수 있으므로 개발자는 소스 제어와 Cloud Manager 배포를 트리거하기 전에 코드 또는 구조적 문제를 효율적으로 확인할 수 있으므로 시간이 더 걸릴 수 있습니다.

## Cloud Service SDK {#accessing-the-aem-as-a-cloud-service-sdk}로 AEM 액세스

* AEM Admin Console **Adobe Experience Manager** 정보 아이콘을 확인하여 프로덕션에서 실행 중인 AEM 버전을 확인할 수 있습니다.
* 빠른 시작 jar 및 디스패처 도구는 [소프트웨어 배포 포털](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)에서 zip 파일로 다운로드할 수 있습니다. SDK 목록에 대한 액세스는 Cloud Service 환경으로 AEM Managed Services 또는 AEM이 있는 SDK 목록으로 제한됩니다.
* Java API Jar 및 Javadoc Jar는 명령줄 또는 기본 IDE를 사용하여 고급 도구를 통해 다운로드할 수 있습니다.
* 마스터 프로젝트 앱은 다음 API Jar 패키지를 참조해야 합니다. 이러한 종속성은 모든 하위 패키지 홈에서 참조되어야 합니다.

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
>SDK의 버전 항목은 Cloud Service의 AEM 버전과 일치해야 합니다. AEM에 로그인한 다음 화면 오른쪽 상단 모서리의 물음표로 이동하여 **[!UICONTROL Adobe Experience Manager 정보]**


## 새 SDK 버전 {#refreshing-a-local-project-with-a-new-skd-version}으로 로컬 프로젝트 새로 고침

새 SDK로 로컬 프로젝트를 새로 고치는 것이 권장됩니까?

월별 유지 관리 릴리스 이후 적어도 새로 고침은 *권장*&#x200B;입니다.

일일 유지 관리 릴리스 후에 새로 고치는 것은 *선택 사항*&#x200B;입니다. 프로덕션 인스턴스가 새 AEM 버전으로 성공적으로 업그레이드되면 고객에게 알립니다. 일일 유지 관리 릴리스의 경우, 새로운 SDK가 완전히 변경되었을 것으로 예상되지 않습니다. 그러나 최신 SDK로 로컬 AEM 개발자 환경을 가끔 새로 고친 다음 사용자 정의 애플리케이션을 다시 작성하고 테스트하는 것이 좋습니다. 월별 유지 관리 릴리스에는 일반적으로 보다 효과적인 변경 사항이 포함되므로 개발자는 즉시 새로 고침, 다시 구성 및 테스트를 수행해야 합니다.

다음은 로컬 환경을 새로 고치는 데 권장되는 절차입니다.

1. 유용한 컨텐츠가 소스 제어에서 프로젝트에 커밋되거나 나중에 가져올 수 있는 변경 가능한 컨텐츠 패키지에서 사용할 수 있는지 확인합니다.
1. Cloud Manager 파이프라인 빌드의 일부로 배포되지 않도록 로컬 개발 테스트 컨텐츠를 별도로 저장해야 합니다. 이는 로컬 개발에만 사용해야 하기 때문입니다
1. 현재 실행 중인 빠른 시작을 중지합니다.
1. 안전하게 보관하려면 `crx-quickstart` 폴더를 다른 폴더로 이동합니다.
1. Cloud Manager에 명시된 새로운 AEM 버전(여기에서 추가로 다운로드할 수 있도록 새로운 QuickStart Jar 버전을 식별하는 데 사용됨)을 확인합니다.
1. Software Distribution Portal에서 Production AEM 버전과 버전이 일치하는 QuickStart JAR를 다운로드합니다
1. 새 폴더를 만들고 새 QuickStart Jar를 안에 넣습니다.
1. 원하는 실행 모드(파일 이름 바꾸기 또는 `-r`을 통해 실행 모드 전달)로 새 QuickStart를 시작합니다.
   * 폴더에 이전 빠른 시작 항목이 남아 있지 않은지 확인하십시오.
1. AEM 애플리케이션 구축
1. PackageManager를 통해 AEM 애플리케이션을 로컬 AEM에 배포
1. PackageManager를 통해 로컬 환경 테스트에 필요한 변경 가능한 컨텐츠 패키지 설치
1. 필요에 따라 개발 및 변경 사항 배포

새로운 AEM 빠른 시작 버전과 함께 설치해야 하는 컨텐츠가 있는 경우 컨텐츠 패키지 및 프로젝트의 소스 제어에 해당 컨텐츠를 포함시키십시오. 그런 다음 매번 설치합니다.

SDK를 자주 업데이트(예: 2주마다)하고 전체 로컬 상태를 매일 처리하여 실수로 애플리케이션의 상태 저장 데이터에 의존하지 않도록 하는 것이 좋습니다.

CryptoSupport([AEM에서 Cloudservices 또는 SMTP Mail 서비스의 자격 증명을 구성하거나 응용 프로그램](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/adobe/granite/crypto/CryptoSupport.html)에서 CryptoSupport API를 사용하여 암호화된 속성이 AEM 환경의 첫 번째 시작에 자동으로 생성된 키로 암호화됩니다. cloudsetup은 환경별 CryptoKey를 자동으로 다시 사용하는 문제를 해결하지만 로컬 개발 환경에 암호화 키를 주입해야 합니다.

기본적으로 AEM은 폴더의 데이터 폴더 내에 키 데이터를 저장하도록 구성되지만 개발 시 보다 편리하게 재사용할 수 있도록 &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;을 사용하여 처음 시작할 때 AEM 프로세스를 초기화할 수 있습니다. 이렇게 하면 &quot;`/etc/key`&quot;에서 암호화 데이터가 생성됩니다.

암호화된 값이 포함된 컨텐츠 패키지를 재사용하려면 다음 단계를 수행해야 합니다.

* 로컬 quickstart.jar를 처음 시작할 때는 아래 매개 변수를 추가해야 합니다.&quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot; 항상 추가하는 것은 권장되지만 선택 사항입니다.
* 인스턴스를 처음 시작할 때 루트 &quot;`/etc/key`&quot;에 대한 필터가 포함된 패키지를 만듭니다. 이렇게 하면 모든 환경에서 재사용할 수 있는 비밀이 유지됩니다.
* 기밀이 포함된 변경 가능한 컨텐츠를 내보내거나 `/crx/de`을 통해 암호화된 값을 찾아 설치 간에 다시 사용할 패키지에 추가합니다
* 새 버전으로 교체하거나 여러 개발 환경에서 테스트를 위해 자격 증명을 공유해야 함) 새 인스턴스를 회전할 때마다 수동으로 다시 구성할 필요 없이 컨텐츠를 재사용할 수 있도록 2단계 및 3단계에서 생성된 패키지를 설치합니다. 이것은 이제 암호키가 동기화되었기 때문입니다.
