---
title: 클라우드 서비스 SDK로서의 AEM
description: 완료 예정
translation-type: tm+mt
source-git-commit: 114bc678fc1c6e3570d6d2a29bc034feb68aa56d

---


# The AEM as a Cloud Service SDK {#aem-as-a-cloud-service-sdk}

클라우드 서비스 SDK로서 AEM은 다음 아티팩트로 구성됩니다.

* **Quickstart** Jar - 로컬 개발에 사용되는 AEM 런타임
* **Java API** Jar - AEM에서 Cloud 서비스로 개발할 수 있는 모든 허용되는 Java API를 노출하는 Java Jar/Maven 종속성이 있습니다. 이전에 Uberjar라고 함
* **Java** Jar - Java API Jar용 javadocs
* **발송자 도구** - 로컬에서 발송자를 기준으로 개발하는 데 사용되는 도구 세트입니다. Unix 및 Windows용 객체 분리

또한 AEM 6.5 이전 버전으로 이전에 배포된 일부 고객은 아래 결함을 사용하게 됩니다. 로컬 컴파일이 Quickstart jar에서 작동하지 않고 클라우드 서비스로 배포된 AEM에서 제거된 인터페이스 때문일 것으로 생각되는 경우 고객 지원에 문의하여 액세스 권한이 필요한지 여부를 확인하십시오. 이를 위해서는 백엔드를 변경해야 합니다.

* **6.5 더 이상 사용되지 않는 Java** API Jar - AEM 6.5 이후 제거된 추가 인터페이스 세트
* **6.5 더 이상 사용되지 않는 Javadoc** Jar - 추가 인터페이스 세트를 위한 Javadocs

## 클라우드 서비스 SDK로 AEM 액세스 {#accessing-the-aem-as-a-cloud-service-sdk}

* AEM 관리 콘솔의 Adobe Experience **Manager 정보** 아이콘을 확인하여 프로덕션에서 실행 중인 AEM 버전을 확인할 수 있습니다.
* 빠른 시작 jar 및 발송자 도구는 소프트웨어 배포 포털에서 [zip 파일로 다운로드할 수](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)있습니다. SDK 목록에 대한 액세스는 클라우드 서비스 환경으로 AEM Managed Services 또는 AEM을 사용하는 것으로 제한됩니다.
* Java API Jar 및 Javadoc Jar는 명령줄 또는 기본 IDE와 함께 전문적인 툴을 통해 다운로드할 수 있습니다.
* 마스터 프로젝트 속성은 다음 API Jar 패키지를 참조해야 합니다. 이 종속성은 모든 하위 패키지 홈에서도 참조되어야 합니다.

```
<dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>aem-sdk-api</artifactId>
  <version>2019.11.3006.20191108T223635Z-191201</version>
  <scope>provided</scope>
</dependency>
```

>[!NOTE] SDK의 버전 항목은 AEM 버전과 클라우드 서비스로 일치해야 합니다. AEM에 로그인한 다음 화면 오른쪽 상단에 있는 물음표로 이동하여 Adobe Experience Manager **[!UICONTROL 정보를 선택하면 사용 중인 버전을 확인할 수 있습니다]**

* 패키지가 호스팅된 maven 저장소의 원격 좌표를 pom 파일에 포함해야 합니다.

```
<repository>
    <id>adobe-aem-releases</id>
    <name>Adobe AEM Repository</name>
    <url>https://downloads.experiencecloud.adobe.com/content/maven/public</url>
    <releases>
        <enabled>true</enabled>
        <updatePolicy>never</updatePolicy>
    </releases>
    <snapshots>
        <enabled>false</enabled>
    </snapshots>
</repository>
```

## 새 SDK 버전으로 로컬 프로젝트 새로 고침 {#refreshing-a-local-prokect-with-a-new-skd-version}

새 SDK로 로컬 프로젝트를 새로 고치는 것이 언제부터 권장됩니까?

월별 유지 관리 릴리스 이후 적어도 새로 고치는 것이 *좋습니다* .

일일 유지 관리 릴리스 이후 새로 고치는 *선택* 사항입니다. 고객은 프로덕션 인스턴스가 새 AEM 버전으로 성공적으로 업그레이드되면 알림을 받게 됩니다. 일일 유지 관리 릴리스의 경우, 새로운 SDK가 완전히 변경되었을 것으로 예상되지 않습니다. 여전히 최신 SDK를 사용하여 로컬 AEM 개발자 환경을 가끔 새로 고친 다음 사용자 지정 애플리케이션을 다시 빌드하고 테스트하는 것이 좋습니다. 월별 유지 관리 릴리스에는 일반적으로 더 많은 영향을 주는 변경 사항이 포함되므로 개발자는 즉시 새로 고침, 다시 구성 및 테스트를 수행해야 합니다.

다음은 로컬 환경을 새로 고치는 데 권장되는 절차입니다.

1. 유용한 컨텐츠가 소스 제어에서 프로젝트에 커밋되거나 나중에 가져올 수 있는 변경 가능한 컨텐츠 패키지에서 사용할 수 있는지 확인하십시오
1. Cloud Manager 파이프라인 빌드의 일부로 배포되지 않도록 로컬 개발 테스트 컨텐츠를 별도로 저장해야 합니다. 이는 로컬 개발에만 사용해야 하기 때문입니다
1. 현재 실행 중인 빠른 시작 중지
1. 안전하게 보관하기 위해 폴더를 다른 폴더로 `crx-quickstart` 이동
1. Cloud Manager에 명시된 새 AEM 버전을 참고하십시오. 이 버전은 새 QuickStart Jar 버전을 식별하는 데 사용됩니다.
1. Software Distribution Portal에서 Production AEM 버전과 일치하는 QuickStart JAR 다운로드
1. 완전히 새로운 폴더를 만들고 새 QuickStart Jar를 안에 넣습니다.
1. 원하는 실행 모드(파일 이름 바꾸기 또는 을 통해 실행 모드 전달)로 새 QuickStart를 시작합니다 `-r`.
   * 폴더에 이전 빠른 시작 항목이 남아 있지 않은지 확인하십시오.
1. AEM 애플리케이션 구축
1. PackageManager를 통해 AEM 애플리케이션을 로컬 AEM에 배포
1. PackageManager를 통해 로컬 환경 테스트에 필요한 변경 가능한 컨텐츠 패키지 설치
1. 필요에 따라 개발 및 변경 사항 배포

각 새로운 AEM 빠른 시작 버전에 설치해야 하는 컨텐츠가 있는 경우 컨텐츠 패키지와 프로젝트의 소스 제어에 포함시키십시오. 그런 다음 매번 설치합니다.

SDK를 자주 업데이트(예: 2주)하고 전체 로컬 상태를 매일 처리하여 응용 프로그램의 상태 저장 데이터에 실수로 의존하지 않도록 하는 것이 좋습니다.

CryptoSupport에 의존하는 경우(AEM에서 Cloudservices 또는 SMTP 메일 서비스의 자격 증명을 구성하거나 응용[](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/crypto/CryptoSupport.html)프로그램에서 CryptoSupport API를 사용하여) 암호화된 속성은 AEM 환경의 첫 번째 시작에 자동으로 생성된 키로 암호화됩니다. cloudsetup은 환경별 CryptoKey를 자동으로 다시 사용하는 문제를 해결하지만 로컬 개발 환경에 암호화 키를 주입해야 합니다.

기본적으로 AEM은 폴더의 데이터 폴더 내에 키 데이터를 저장하도록 구성되지만 개발 시 보다 쉽게 재사용할 수 있도록 AEM 프로세스를 &quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot;로 처음 시작할 때 초기화할 수 있습니다. 이렇게 하면 &quot;`/etc/key`&quot;에서 암호화 데이터가 생성됩니다.

암호화된 값이 포함된 컨텐츠 패키지를 재사용하려면 다음 단계를 따르십시오.

* 처음에 로컬 quickstart.jar를 시작할 때 아래 매개 변수를 추가해야 합니다.&quot;`-Dcom.adobe.granite.crypto.file.disable=true`&quot; 항상 추가하는 것은 권장되지만 선택 사항입니다.
* 인스턴스를 처음 시작할 때 루트 &quot;`/etc/key`&quot;에 대한 필터가 포함된 패키지를 만듭니다. 이렇게 하면 재사용하고자 하는 모든 환경에서 다시 사용할 수 있는 비밀이 유지됩니다.
* 기밀 정보가 포함된 변경 가능한 컨텐츠를 내보내거나, 설치 시 다시 사용할 `/crx/de` 패키지에 해당 암호화된 값을 추가하여 검색합니다
* 새로운 인스턴스를 스핀업할 때마다(새 버전으로 대체하거나 여러 개발 환경에서 테스트를 위해 자격 증명을 공유해야 함), 2단계 및 3단계에서 생성된 패키지를 설치하여 수동으로 다시 구성할 필요 없이 컨텐츠를 재사용할 수 있습니다. 이것은 이제 암호키가 동기화되었기 때문입니다.