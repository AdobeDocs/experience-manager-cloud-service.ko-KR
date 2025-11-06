---
title: AEM Forms과 Adobe Experience Platform 연결(AEP) | 데이터 통합 안내서
description: AEM Forms을 Adobe Experience Platform과 통합하여 고객 프로필을 활용하고, 양식 데이터를 제출하고, 개인화된 경험을 만드는 방법을 알아봅니다. 단계별 가이드.
contentOwner: Khushwant Singh
docset: CloudService
role: Admin, Developer, User
feature: Adaptive Forms, Core Components
exl-id: b0eb19d3-0297-4583-8471-edbb7257ded4
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2047'
ht-degree: 5%

---

# Adobe Experience Platform(AEP)과의 AEM Forms 통합 {#aem-forms-aep-integration}

<span class="preview"> 응용 Forms(AEM Forms)와 Adobe Experience Platform(AEP)를 연결하는 기능은 조기 액세스 프로그램 아래에 있습니다. 기능에 대한 액세스를 요청하려면 공식 주소에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com?subject=Request%20for%20Early%20Access%20to%20AEP%20Connector%20\(AEM%20Forms%20Integration%20with%20Adobe%20Experience%20Platform\)&body=Dear%20AEM%20Forms%20Team%2C%0D%0A%0D%0AI%20hope%20this%20message%20finds%20you%20well.%0D%0A%0D%0AI%20am%20writing%20to%20request%20access%20to%20the%20Early%20Access%20Program%20for%20the%20AEP%20Connector%2C%20which%20enables%20integration%20between%20AEM%20Forms%20and%20Adobe%20Experience%20Platform.%0D%0A%0D%0AOrganization%20Name%3A%20%5BYour%20organization%20name%5D%0D%0AOrganization%20ID%3A%20%5BYour%20organization%20ID%2C%20if%20available%5D%0D%0AUse%20Case%3A%20%5BBriefly%20describe%20your%20intended%20use%20case%2C%20including%20goals%20or%20benefits%20you%20aim%20to%20achieve%20with%20the%20integration%5D%0D%0A%0D%0AThank%20you%20for%20your%20time%20and%20consideration.%0D%0A%0D%0ABest%20regards%2C%0D%0A%5BYour%20Full%20Name%5D%0D%0A%5BYour%20Job%20Title%2C%20if%20applicable%5D%0D%0A%5BYour%20Contact%20Information%2C%20if%20appropriate%5D)(으)로 전자 메일을 보내면 됩니다. <a href="/help/forms/early-access-ea-features.md">조기 액세스 프로그램 </a> 페이지를 방문하여 사용 가능한 모든 혁신 및 기능을 확인할 수도 있습니다. . </span>

## 개요 {#overview}

AEM Forms과 Adobe Experience Platform을 연결하여 양식 경험을 변환할 수 있습니다. 이 강력한 통합을 통해 조직은 실시간 고객 프로필을 활용하여 개인화된 양식 환경을 구현하고, **Experience Platform에 AEM Forms 데이터 제출**&#x200B;을 간소화하며, Adobe 에코시스템에서 통합 고객 레코드를 만들 수 있습니다. 적응형 양식을 Experience Platform의 강력한 데이터 관리 기능과 연결하면 고객 데이터에 대한 단일 소스로 유지하면서 보다 적절한 경험을 생성하고 전환율을 향상시킬 수 있습니다.

### Adobe Experience Platform(AEP)용 AEM Forms 커넥터란 무엇입니까? {#what-is-connector}

Adobe Experience Platform(AEP)용 AEM Forms 커넥터는 AEM Forms에서 제공하는 기본 제공(OOTB) 커넥터로, AEM Forms과 Adobe Experience Platform(AEP) 간 원활한 통합을 지원합니다. 이 통합을 통해 AEP에서 사용할 수 있는 XDM 스키마를 사용하여 양식을 만들고 개인화 및 프로필 하이드레이션 목적으로 AEP에 데이터를 다시 제출할 수 있습니다.

## AEM Forms을 Adobe Experience Platform(AEP)와 연결하는 이유 {#benefits}

적응형 Forms과 Adobe Experience Platform을 연결하면 조직과 고객 모두에게 상당한 이점이 있습니다.

* **통합 고객 프로필** - 양식 제출 데이터로 고객 프로필을 보강하여 고객 상호 작용 및 환경 설정에 대한 포괄적인 보기를 만듭니다.
* **개인화된 양식 환경** - 기존 프로필 데이터를 활용하여 필드를 미리 채우고 알려진 고객 정보를 기반으로 양식을 사용자 지정합니다.
* **간소화된 데이터 수집** - 사용자 지정 커넥터 또는 통합 코드를 빌드하지 않고 양식 데이터를 AEP 데이터 세트로 직접 캡처합니다.
* **실시간 데이터 활성화** - 즉각적인 활성화를 위해 Real-Time CDP을 통해 다른 Adobe 애플리케이션으로 양식 제출 데이터를 보냅니다.
* **간소화된 규정 준수 관리** - AEP을 통해 동의 및 데이터 거버넌스 정책을 중앙에서 관리합니다.
* **개발 시간 단축** - 모범 사례를 따르는 미리 만들어진 커넥터에서 사용자 지정 통합 작업을 제거하십시오.
* **양식 데이터를 사용한 고객 프로필 강화** - 모든 양식 제출로 고객 프로필을 자동으로 업데이트하고 개선하여 더 풍부한 고객 통찰력을 만듭니다.

## 주요 기능 {#key-features}

* AEP XDM 스키마를 사용하여 양식 만들기
* 개인화를 위해 AEP에 양식 데이터 제출
* 스트리밍 데이터 수집 지원
* 향상된 사용자 경험을 위해 프로필 하이드레이션 활성화
* AEP의 프로필 시스템과 통합
* 표준화된 데이터 수집을 위한 적응형 양식과 XDM 스키마 통합
* 실시간 데이터 처리를 가능하게 하는 forms용 AEP 스트리밍 연결

아래 비디오에서는 스키마 만들기, 데이터 구성 설정 및 인증과 같은 사전 요구 사항에 대한 단계별 안내서를 제공하며 적응형 Forms을 만들고 Adobe Experience Platform(AEP)에 연결하는 방법을 보여 줍니다

>[!VIDEO](https://video.tv.adobe.com/v/3457850/)

<span> 이 비디오는 핵심 구성 요소에만 적용됩니다. UE/Foundation 구성 요소에 대해서는 문서를 참조하십시오.</span>

## 사전 요구 사항 {#prerequisites}

AEM Forms에서 AEP 커넥터를 설정하기 전에 Adobe Experience Platform에서 다음을 완료했는지 확인하십시오.

1. 스키마 설정
   * [XDM 스키마 만들기](https://experienceleague.adobe.com/ko/docs/experience-platform/xdm/tutorials/create-schema-ui)
   * [프로파일링에 스키마 사용](https://experienceleague.adobe.com/ko/docs/experience-platform/xdm/tutorials/create-schema-ui#profile)
   * [ID 필드 정의](https://experienceleague.adobe.com/ko/docs/experience-platform/xdm/tutorials/create-schema-ui#profile)

2. 데이터 구성
   * [데이터 집합 만들기](https://experienceleague.adobe.com/ko/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/create-datasets)
   * [스트리밍 연결을 설정](https://experienceleague.adobe.com/ko/docs/experience-platform/ingestion/tutorials/create-streaming-connection)&#x200B;(나중에 스트리밍 끝점 URL이 필요하므로 지금 기록해 두십시오.)

3. 인증
   * Adobe Developer Console에서 [API 자격 증명 생성](https://experienceleague.adobe.com/ko/docs/experience-platform/landing/platform-apis/api-authentication#generate-credentials)&#x200B;(클라이언트 ID 및 클라이언트 암호)


## 구현 절차

### &#x200B;1. AEP 클라우드 구성 만들기

1. **Adobe Experience Manager 인스턴스** > **도구** > **클라우드 서비스** > **Adobe Experience Platform**&#x200B;로 이동합니다.
1. 구성을 저장할 **구성 컨테이너**&#x200B;를 선택하십시오.
1. **만들기**&#x200B;를 클릭하여 AEP 구성 마법사를 엽니다.
1. 다음 세부 정보를 입력합니다.
   * 제목
   * 클라이언트 ID(개발자 콘솔에서 가져옴)
   * 클라이언트 암호(개발자 콘솔에서 획득)
   * OAuth URL(기본 URL이 있지만 개발자 콘솔에서도 가져올 수 있음)

   ![AEP 클라우드 구성](/help/forms/assets/aep-cloud-configuration.png)

1. 연결을 설정하려면 **연결**&#x200B;을 클릭하세요. 연결을 설정한 후 다음 추가 설정을 구성합니다.
   * 기본 URL: platform.adobe.io (기본 URL이며 개발자 콘솔에서 가져올 수 있습니다. oauth 및 platform URL의 기본값은 prod URL입니다. 단계에 연결해야 하는 경우 단계 URL을 사용해야 합니다.)
   * 조직 ID(클라이언트 ID/암호와 함께 개발자 콘솔에서 가져옴)
   * 샌드박스 이름(개발 및 프로덕션 환경 모두에 필요)

### &#x200B;2. XDM 스키마 통합을 사용하여 양식 만들기 {#form-creation}

>[!BEGINTABS]

>[!TAB 기초 구성 요소]

스키마 통합을 통해 기초 구성 요소를 기반으로 하는 적응형 양식을 만들려면 다음 단계를 수행하십시오.

1. 양식 만들기 마법사에 액세스합니다.
   * **Adobe Experience Manager 인스턴스** > **Forms** > **Forms 및 문서**&#x200B;로 이동합니다.
   * **만들기** > **적응형 양식**&#x200B;을 클릭합니다.
1. **소스** 탭에서 기초 템플릿을 선택합니다.
1. **데이터** 탭에서 **Adobe Experience Platform** 옵션을 선택합니다.
1. 속성 창에서 클라우드 구성을 선택합니다.

   ![](/help/forms/assets/xdm-schema-integration.png)

   시스템은 Adobe Experience Platform에서 사용 가능한 모든 스키마를 로드합니다

   >[!NOTE]
   >
   >
   > * 프로필 사용 및 비시스템 생성 스키마만 가져옵니다.
   > * 초기 스키마 로드는 처음 설정할 때 시간이 걸릴 수 있습니다.

1. 스키마의 해당/필수 필드를 선택합니다. 자세한 단계는 비디오 를 참조하십시오.
1. 제출 탭에서:
   * **Adobe Experience Platform에 제출** 제출 액션 선택
   * **Experience Platform에 AEM Forms 데이터 제출**&#x200B;에 대한 양식 제출 설정 구성
1. 속성 창에서 다음을 수행합니다.
   * 스트리밍 URL 추가(AEP 소스 > 스트리밍 연결에서 가져옴)
   * 데이터 흐름 ID 추가( AEP 소스 > 흐름 > API 사용 정보에 있음)
1. **저장**&#x200B;을 클릭합니다. 양식 세부 정보 제공:
   * 제목
   * 이름
   * 저장소 경로
1. 양식에 제출 단추를 추가합니다. 양식을 AEP에 데이터를 제출할 준비가 되었습니다.

>[!TAB 핵심 구성 요소]

스키마 통합을 통해 핵심 구성 요소를 기반으로 하는 적응형 양식을 만들려면 다음 단계를 수행하십시오.

1. 양식 만들기 마법사에 액세스합니다.
   * **Adobe Experience Manager 인스턴스** > **Forms** > **Forms 및 문서**&#x200B;로 이동합니다.
   * **만들기** > **적응형 양식**&#x200B;을 클릭합니다.
1. **소스** 탭에서 핵심 구성 요소 기반 템플릿을 선택합니다.
1. **데이터** 탭에서 **Adobe Experience Platform** 옵션을 선택합니다.
1. 속성 창에서 클라우드 구성을 선택합니다.

   ![](/help/forms/assets/xdm-schema-integration.png)

   시스템은 Adobe Experience Platform에서 사용 가능한 모든 스키마를 로드합니다

   >[!NOTE]
   >
   >
   > * 프로필 사용 및 비시스템 생성 스키마만 가져옵니다.
   > * 초기 스키마 로드는 처음 설정할 때 시간이 걸릴 수 있습니다.

1. 스키마의 해당/필수 필드를 선택합니다. 자세한 단계는 비디오 를 참조하십시오.
1. 제출 탭에서:
   * **Adobe Experience Platform에 제출** 제출 액션 선택
   * **Experience Platform에 AEM Forms 데이터 제출**&#x200B;에 대한 양식 제출 설정 구성
1. 속성 창에서 다음을 수행합니다.
   * 스트리밍 URL 추가(AEP 소스 > 스트리밍 연결에서 가져옴)
   * 데이터 흐름 ID 추가( AEP 소스 > 흐름 > API 사용 정보에 있음)
1. **저장**&#x200B;을 클릭합니다. 양식 세부 정보 제공:
   * 제목
   * 이름
   * 저장소 경로
1. 양식에 제출 단추를 추가합니다. 양식을 AEP에 데이터를 제출할 준비가 되었습니다.

>[!TAB 범용 편집기]

스키마 통합과 함께 범용 편집기를 사용하여 작성된 적응형 양식을 만들려면 다음 단계를 수행하십시오.

1. 양식 만들기 마법사에 액세스합니다.
   * **Adobe Experience Manager 인스턴스** > **Forms** > **Forms 및 문서**&#x200B;로 이동합니다.
   * **만들기** > **적응형 양식**&#x200B;을 클릭합니다.
1. **소스** 탭에서 Edge Delivery 기반 템플릿을 선택합니다.
1. **데이터** 탭에서 **Adobe Experience Platform** 옵션을 선택합니다.
1. 속성 창에서 클라우드 구성을 선택합니다.

   ![스키마 통합](/help/forms/assets/xdm-schema-integration.png)

   시스템은 Adobe Experience Platform에서 사용 가능한 모든 스키마를 로드합니다

   >[!NOTE]
   >
   >
   > * 프로필 사용 및 비시스템 생성 스키마만 가져옵니다.
   > * 초기 스키마 로드는 처음 설정할 때 시간이 걸릴 수 있습니다.

1. 스키마의 해당/필수 필드를 선택합니다. 자세한 단계는 비디오 를 참조하십시오.
1. 제출 탭에서:
   * **Adobe Experience Platform에 제출** 제출 액션 선택
   * **Experience Platform에 AEM Forms 데이터 제출**&#x200B;에 대한 양식 제출 설정 구성

     >[!NOTE]
     >
     >* 범용 편집기 인터페이스에 데이터 소스 아이콘이 표시되지 않거나 오른쪽 속성 패널에 바인드 참조 속성이 표시되지 않으면 Extension Manager에서 **데이터 소스** 확장을 사용하도록 설정하십시오.
     >* 범용 편집기 인터페이스에 **양식 속성 편집** 아이콘이 표시되지 않으면 Extension Manager에서 **양식 속성 편집** 확장 기능을 활성화합니다.
     > 
     >* 범용 편집기에서 확장 기능을 활성화하거나 비활성화하는 방법을 알아보려면 [Extension Manager 기능 하이라이트](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions) 문서를 참조하십시오.

   현재 범용 편집기의 양식 미리 채우기 서비스는 지원되지 않습니다.

1. 속성 창에서 다음을 수행합니다.
   * 스트리밍 URL 추가(AEP 소스 > 스트리밍 연결에서 가져옴)
   * 데이터 흐름 ID 추가( AEP 소스 > 흐름 > API 사용 정보에 있음)
1. **저장**&#x200B;을 클릭합니다. 양식 세부 정보 제공:
   * 제목
   * 이름
   * 저장소 경로
1. 양식에 제출 단추를 추가합니다. 양식을 AEP에 데이터를 제출할 준비가 되었습니다.

>[!ENDTABS]

## 중요 참고 사항 {#important-notes}

* 양식을 통해 제출된 데이터는 약 10~15분 후 AEP에 표시됩니다
* 기본적으로 프로필이 활성화된 스키마만 나열됩니다
* 데이터 제출은 모든 스키마에 대해 작동하지만 미리 채우기 기능은 프로필이 활성화된 스키마로 제한됩니다
* 프로필이 활성화되지 않은 스키마의 데이터는 나중에 프로필이 활성화되더라도 프로필 생성에 사용되지 않습니다
* **양식 데이터를 사용한 고객 프로필 보강**&#x200B;을(를) 사용하려면 XDM 스키마에 올바른 ID 필드 구성이 필요합니다.
* **Experience Platform에 AEM Forms 데이터 제출**&#x200B;은(는) 실시간 데이터 흐름을 보장하기 위해 **양식용 AEP 스트리밍 연결**&#x200B;을 사용합니다.

## 모범 사례 {#best-practices}

1. 프로파일링을 활성화하기 전에 스키마 구조를 신중하게 계획하십시오.
1. **Forms용 AEP 스트리밍 연결**&#x200B;을 설정할 때 데이터 볼륨 및 시스템 확장 요구 사항을 고려하십시오.
1. 프로덕션 배포 전에 철저하게 통합 테스트
1. 데이터 수집 및 프로필 작성 프로세스 모니터링
1. 필요한 데이터만 수집하려면 **적응형 양식과 XDM 스키마 통합 디자인**
1. **양식 데이터를 사용한 고객 프로필 강화**&#x200B;를 전략적으로 사용하여 개인화를 향상시킵니다.

## 기술적 고려 사항 {#technical-considerations}

* 커넥터는 데이터 제출을 위해 공개 스트리밍 API를 사용합니다
* 프로필 만들기는 ID 필드를 기반으로 합니다
* AEP에서 데이터 통합이 자동으로 발생
* 통합은 새 양식 만들기와 기존 양식 수정을 모두 지원합니다
* 적응형 양식과 XDM 스키마 통합은 다양한 터치포인트 간에 데이터 구조를 표준화합니다
* forms용 AEP 스트리밍 연결은 실시간 데이터 수집 기능을 제공합니다

## 자주 묻는 질문 (FAQ) {#faq}

### 일반 질문 {#general-questions}

**Q: &quot;이 커넥터를 여러 AEM Forms 제품에서 사용할 수 있습니까?**
A: 아니요. 이 통합은 AEM Forms as a Cloud Service에서만 사용할 수 있으며 조기 액세스 프로그램 아래에 있습니다.

**Q: 이 커넥터가 적응형 Forms 핵심 구성 요소와 기초 구성 요소에서 모두 작동합니까?**
A: 이 커넥터는 적응형 Forms 핵심 구성 요소 및 적응형 Forms Foundation 구성 요소와 함께 작동합니다.

**Q: 단일 양식에서 여러 AEP 데이터 세트로 데이터를 보낼 수 있습니까?**
A: 현재 각 양식은 하나의 데이터 세트에만 제출할 수 있습니다.

**Q: 처리할 수 있는 양식 제출 횟수에 제한이 있습니까?**
답변: 양식 제출에는 AEP 스트리밍 수집 [할당량 및 속도 제한](https://experienceleague.adobe.com/ko/docs/experience-platform/data-lifecycle/api/quota)이 적용됩니다.

<!-- 
>
**Q: Can form attachments be sent to AEP?**
A: No, form attachments cannot be directly sent to AEP. You would need to store attachments separately and only send metadata to AEP. -->

### 구현 질문 {#implementation-questions}

**Q: AEM Forms과 AEP 간의 연결 문제를 해결하려면 어떻게 합니까?**
A: 클라우드 구성 설정을 확인하고 API 자격 증명이 올바른지 확인한 다음 스트리밍 끝점 URL이 제대로 구성되었는지 확인합니다.

**Q: 이 통합에서 사용자 지정 XDM 스키마를 사용할 수 있습니까?**
A: 예. 사용자 지정 XDM 스키마는 AEP에서 올바르게 구성되고 미리 채우기 기능이 프로필에 대해 활성화되어 있는 한 사용할 수 있습니다.

**Q: AEP 프로필 데이터로 양식 미리 채우기를 사용하려면 어떻게 합니까?**
A: 스키마가 프로필에서 활성화되었는지 그리고 스키마에 정의된 ID 필드와 동일한 필드를 사용하도록 양식이 구성되어 있는지 확인합니다.

**Q: AEP으로 전송하기 전에 데이터를 변환해야 하는 경우 어떻게 해야 합니까?**
A: 양식 규칙 또는 사용자 정의 함수를 사용하여 제출하기 전에 데이터를 변환할 수 있습니다. 복잡한 변환의 경우 사용자 지정 제출 액션을 사용하는 것이 좋습니다.

**Q: 하이브리드 배포 모델에 이 통합을 사용할 수 있습니까?**
A: 아니요. 이 통합은 AEM Forms as a Cloud Service에만 적용됩니다.

## 요약 및 다음 단계 {#summary-next-steps}

Adobe Experience Platform과 AEM Forms 통합을 통해 조직은 양식과 광범위한 Experience Platform 에코시스템 간에 원활한 데이터 흐름을 만들 수 있습니다. 이 통합을 통해 보다 개인화된 양식 경험을 구축하고, 데이터 수집을 간소화하며, 중요한 양식 제출 데이터로 고객 프로필을 개선할 수 있습니다.

이 통합을 시작하려면 다음을 수행하십시오.

1. **액세스 요청** - 아직 참가하지 않았다면 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com?subject=Request%20for%20Early%20Access%20to%20AEP%20Connector%20\(AEM%20Forms%20Integration%20with%20Adobe%20Experience%20Platform\)&body=Dear%20AEM%20Forms%20Team%2C%0D%0A%0D%0AI%20hope%20this%20message%20finds%20you%20well.%0D%0A%0D%0AI%20am%20writing%20to%20request%20access%20to%20the%20Early%20Access%20Program%20for%20the%20AEP%20Connector%2C%20which%20enables%20integration%20between%20AEM%20Forms%20and%20Adobe%20Experience%20Platform.%0D%0A%0D%0AOrganization%20Name%3A%20%5BYour%20organization%20name%5D%0D%0AOrganization%20ID%3A%20%5BYour%20organization%20ID%2C%20if%20available%5D%0D%0AUse%20Case%3A%20%5BBriefly%20describe%20your%20intended%20use%20case%2C%20including%20goals%20or%20benefits%20you%20aim%20to%20achieve%20with%20the%20integration%5D%0D%0A%0D%0AThank%20you%20for%20your%20time%20and%20consideration.%0D%0A%0D%0ABest%20regards%2C%0D%0A%5BYour%20Full%20Name%5D%0D%0A%5BYour%20Job%20Title%2C%20if%20applicable%5D%0D%0A%5BYour%20Contact%20Information%2C%20if%20appropriate%5D)에 연락하여 조기 액세스 프로그램에 참가하십시오.
2. **환경 준비** - AEM Forms과 Adobe Experience Platform 모두에서 필요한 권한과 구성을 가지고 있는지 확인합니다.
3. **구현 단계에 따라** - 위의 안내서를 사용하여 클라우드 구성을 설정하고 XDM 스키마 통합을 통해 첫 번째 AEP 연결 양식을 만드십시오.
4. **철저하게 테스트** - 개발 환경에서 데이터 제출 및 미리 채우기 기능의 유효성을 검사합니다.
5. **프로덕션 계획** - 구현 팀과 함께 프로덕션에서 Experience Platform에 AEM Forms 데이터 제출 배포 일정을 예약합니다.

## 관련 리소스 {#related-resources}

* [AEM Forms as a Cloud Service 설명서](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/home.html?lang=ko)
* [Adobe Experience Platform 설명서](https://experienceleague.adobe.com/docs/experience-platform/landing/home.html?lang=ko)
* [XDM 시스템 개요](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html?lang=ko)
* [Adobe Experience Platform에서 스트리밍 수집](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html?lang=ko)
* [실시간 고객 프로필 개요](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=ko)
* [AEM Forms 조기 액세스 기능](/help/forms/early-access-ea-features.md)
* [핵심 구성 요소를 사용하여 적응형 Forms 만들기](/help/forms/creating-adaptive-form-core-components.md)
* [AEM Forms에서 양식 데이터 모델 사용](/help/forms/using-form-data-model.md)

<!--
Schema markup for technical documentation
{
  "@context": "https://schema.org",
  "@type": "TechArticle",
  "headline": "Connect AEM Forms with Adobe Experience Platform (AEP) | Data Integration Guide",
  "description": "Learn how to integrate AEM Forms with Adobe Experience Platform to leverage customer profiles, submit form data, and create personalized experiences.",
  "datePublished": "2025-05-28",
  "author": {
    "@type": "Corporation",
    "name": "Adobe"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Adobe Experience League",
    "logo": {
      "@type": "ImageObject",
      "url": "https://experienceleague.adobe.com/assets/img/favicons/apple-touch-icon.png"
    }
  },
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/aem-forms-aep-connector.html"
  },
  "articleSection": "AEM Forms",
  "keywords": "AEM Forms, Adobe Experience Platform, XDM schema, data integration, form submission, customer profiles, personalization"
}
-->
