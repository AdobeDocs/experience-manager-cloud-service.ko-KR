---
title: 속성 기반 액세스 제어
description: 속성 기반 액세스 제어를 활성화하여 메타데이터 기반 규칙을 정의하여 Content Hub에서 사용할 수 있는 에셋에 대한 액세스 수준을 정의하는 방법에 대해 알아봅니다
role: Admin
badgeSaas: label="AEM Assets" type="Positive" tooltip="AEM Assets에 적용됩니다)."
exl-id: 05f54b05-40b8-4a6c-af8f-5c3f7a2089d4
source-git-commit: b736af556c8580d005097c27cceba050b21a57c9
workflow-type: tm+mt
source-wordcount: '2139'
ht-degree: 2%

---


# 속성 기반 액세스 제어 {#attribute-based-access-control}

Content Hub 관리자는 속성 기반 액세스 제어(ABAC)를 사용하여 메타데이터 기반 규칙을 정의하여 Content Hub에서 사용할 수 있는 에셋에 대한 액세스 수준을 제어할 수 있습니다.

조직의 관리자는 그룹 ID에 매핑된 사용자 그룹에 대한 규칙을 정의합니다. 규칙은 [논리 및 비교 연산자](#supported-rule-constructs)의 혼합이며, 관리자는 Content Hub 내에서 에셋 액세스를 관리하는 데 필요한 수만큼 규칙을 정의할 수 있습니다.

규칙은 메타데이터를 기반으로 합니다. 규칙에 정의된 조건이 에셋 메타데이터와 일치하는 경우 에셋이 사용자 그룹에 표시됩니다. Content Hub은 **모든 Assets** 및 **컬렉션** 내에서 사용할 수 있는 모든 자산에 대해 사용자 지정 메타데이터를 포함한 자산 메타데이터를 스캔하여 결과를 사용자 그룹에 표시합니다.

예를 들어 자산 메타데이터가 &quot;Brand = Brand X&quot; 및 &quot;Region = EMEA 또는 아메리카&quot;와 일치하는 경우 그룹 ID가 1011인 사용자 그룹에 대한 액세스를 허용합니다. Content Hub은 ID = 1011인 사용자 그룹에만 해당 자산을 표시합니다. 여기서 &#39;&#39;Brand = Brand X&#39;&#39; 및 &#39;&#39;지역 = EMEA 또는 아메리카&#39;&#39;입니다.

Content Hub의 ABAC 규칙은 다음 접근 방식을 사용하여 구성할 수 있습니다.

* Content Hub에서 [AI Assistant를 사용하는 **셀프서비스 구성**](#configure-abac-using-ai-assistant-in-content-hub)(AEM 거버넌스 에이전트 기반)
* **스프레드시트 기반 구성**&#x200B;부터 [Adobe 지원](#configure-abac-using-spreadsheet)까지

Content Hub의 AI Assistant를 통해 관리자는 메타데이터와 자연어를 사용하여 ABAC 규칙을 정의하고 관리할 수 있습니다. 이를 통해 규칙 구성 시간을 단축하고 수동 지원 워크플로우에 대한 의존도를 줄일 수 있습니다.

속성 기반 액세스 제어의 몇 가지 주요 이점은 다음과 같습니다.

* 폴더 구조에 대한 권한 종속을 제거합니다.
* 관리자가 자산을 업로드하고 권한 구조를 소급적으로 결정할 수 있도록 합니다.
* 중복 수를 줄이고 자산 무결성을 향상시킵니다. 동일한 에셋을 다른 그룹과 공유할 때 폴더 기반 권한에서 중복이 필요합니다.
* 규칙 기반의 세분화된 액세스 활성화
* 브랜드 및 지역 전반에 걸쳐 확장 가능한 거버넌스 지원
* 에셋 관리 개선

>[!VIDEO](https://video.tv.adobe.com/v/3475413/?learn=on&enablevpops){transcript=true}

## 속성 기반 액세스 제어를 활성화하는 방법 {#enable-attribute-based-access-control}

Content Hub의 ABAC 규칙은 다음 접근 방식을 사용하여 구성할 수 있습니다.

* **Content Hub에서 AI Assistant를 사용한 셀프서비스 구성(AEM 거버넌스 에이전트 제공)**\
  관리자는 Content Hub 내에서 자연어를 사용하여 직접 ABAC 규칙을 정의하고 관리할 수 있습니다.

* **Adobe 지원을 통한 스프레드시트 기반 구성**\
  관리자는 스프레드시트에서 ABAC 규칙을 정의하고 Adobe 지원을 통해 제출하여 구성할 수 있습니다.

## Content Hub에서 AI Assistant를 사용하여 ABAC 구성

AEM 거버넌스 에이전트가 제공하는 Content Hub의 AI Assistant를 사용하면 자연어를 사용하여 Content Hub에서 직접 ABAC 규칙을 만들고 관리할 수 있습니다.

다음과 같은 작업을 수행할 수 있습니다.
* 기존 규칙 검색
* 규칙 만들기
* 규칙 업데이트
* 규칙 삭제

이를 통해 관리자는 지원 워크플로우에 의존하지 않고 액세스 규칙을 만들고 관리할 수 있습니다.

### 시작하기에 앞서 {#before-you-begin-ai-assistant}

Content Hub for ABAC 규칙 구성에서 AI Assistant를 사용하기 전에 다음 사항을 확인하십시오.

* AEM as a Cloud Service 라이선스가 부여되었습니다.
* AEM 거버넌스 에이전트가 제공하는 AI 도우미를 조직에서 사용할 수 있습니다
* 아직 액세스 권한이 없는 경우 Adobe 담당자에게 문의하고 필요한 라이선스 단계를 완료하십시오
* GenAI 라이더는 구매 시도 프로그램에 필요하지 않습니다

### AI Assistant를 사용하여 ABAC 규칙을 구성하는 단계 {#steps-ai-assistant}

1. Content Hub에서 AI Assistant를 엽니다.

1. 간단한 지침부터 시작하세요.

   예:

   `Create a new rule in Content Hub`

   AI 어시스턴트가 규칙을 만드는 데 필요한 정보를 안내한다.

1. 자연어로 규칙을 정의합니다.

   예:

   `Frescopa Web Marketers user group should have access to assets where product equals Frescopa`

1. ABAC 규칙을 적용해야 하는 환경을 선택합니다.

1. 규칙을 적용하기 전에 검토하십시오.

   AI Assistant는 규칙의 구조화된 미리보기를 생성합니다. 아무 것도 자동으로 적용되지 않습니다. 생성된 규칙을 검토하거나, 필요한 경우 조정하거나, 적용하기 전에 작업을 취소할 수 있습니다.

1. 규칙을 저장하고 적용합니다.

   저장되면 메타데이터에 따라 규칙이 동적으로 적용됩니다.

이 검토 단계는 규칙이 적용되기 전에 정확성을 확인하는 데 도움이 됩니다.

### 프롬프트를 사용하여 ABAC 규칙 관리 {#manage-abac-rules-using-prompts}

AI Assistant를 사용하기 시작하면 ABAC 규칙을 대화식으로 관리할 수 있습니다.

**규칙 검색**

* 기존의 모든 Content Hub ABAC 규칙 표시

**규칙 만들기**

* 모든 에셋에 제품 마케팅 그룹 액세스 권한을 부여하는 규칙 만들기
* 지역이 EMEA인 자산에 대한 영업 그룹 액세스 권한을 부여합니다.

**규칙 업데이트**

* APAC를 포함하도록 EMEA 마케팅 그룹에 대한 규칙 업데이트

**규칙 삭제**

* 제품 마케팅 그룹에 대한 규칙 삭제

**메타데이터 및 그룹 탐색**

* 규칙을 설정할 사용 가능한 그룹 및 메타데이터 속성 표시

## 스프레드시트를 사용하여 ABAC 구성

조직에 대해 AI Assistant가 활성화되지 않은 경우 스프레드시트 기반 워크플로우를 사용하여 ABAC 규칙을 구성할 수 있습니다.

스프레드시트에서 규칙을 다운로드하고 정의하려면 **스프레드시트 다운로드**&#x200B;를 클릭하십시오. Adobe 지원 티켓을 만들고 스프레드시트에 정의된 규칙을 Adobe에 제공합니다.

[!BADGE 스프레드시트 다운로드]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/ABAC_Get_Started_Template.xlsx"}

이 문서에 설명된 지침을 사용하여 스프레드시트에서 규칙을 정의합니다.

>[!IMPORTANT]
>
>규칙을 정의한 후 스프레드시트의 **유효성 검사 오류** 탭으로 이동하여 **ABAC 유효성 검사 실행**&#x200B;을 클릭합니다. **전달된 모든 유효성 검사** 메시지는 정의된 규칙을 Adobe에 제공할 수 있음을 확인합니다.

### 스프레드시트를 사용하여 ABAC 규칙을 구성하는 단계 {#steps-spreadsheet}

1. ABAC 스프레드시트 템플릿을 다운로드합니다.
1. 메타데이터 기반 조건을 사용하여 스프레드시트에서 규칙을 정의합니다.
1. 각 규칙을 적절한 IMS 그룹 ID에 매핑합니다.
1. 주석에 규칙의 비즈니스 의도를 캡처합니다.
1. Adobe 지원 티켓을 제출하고 완성된 스프레드시트를 Adobe과 공유합니다.
1. Adobe은 조직에 대한 규칙을 구성합니다.

## 예제 속성 기반 액세스 제어 사용 사례 {#example-metadata-based-rules}

대규모 마케팅 롤아웃을 지원하려면 지역 및 브랜드의 다양한 팀원이 디지털 에셋에 액세스해야 합니다. 각 담당자는 지역 및 브랜드를 기반으로 특정 범위를 갖습니다. ABAC는 자산 메타데이터를 사용하여 이러한 규칙을 자동으로 적용합니다. 다음 표는 이 사용 사례와 적용되는 규칙에 대한 담당자를 보여 줍니다.

| 페르소나 | 역할 | 역할 설명 | 그룹 ID | 규칙 |
|---|---|---|---|---|
| John | EMEA 마케팅 리드 | EMEA의 모든 브랜드에서 마케팅 실행을 감독합니다. EMEA 시장을 겨냥한 모든 브랜드의 승인된 자산에 액세스해야 합니다. | group-emea-marketing | region = &quot;EMEA&quot; |
| 마이크 | APAC 마케팅 리드 | APAC의 모든 브랜드에서 마케팅 실행을 감독합니다. APAC 시장을 겨냥한 모든 브랜드의 승인된 자산에 액세스해야 합니다. | group-apac-marketing | region = &quot;APAC&quot; |
| 소피 | Brand X Manager(EMEA) | EMEA에서 Brand X ID 관리. EMEA 시장에 맞게 조정된 Brand X 승인 콘텐츠만 표시하면 됩니다. | group-emea-brandx | 지역 = &quot;EMEA&quot; &amp;&amp; 브랜드 = &quot;Brand X&quot; |
| Tom | 브랜드 Y 관리자 (APAC) | APAC에서 Brand Y ID를 관리합니다. APAC 시장에 맞게 조정된 Brand Y 승인 콘텐츠만 표시하면 됩니다. | 그룹-apac-brandy | 지역 = &quot;APAC&quot; &amp;&amp; 브랜드 = &quot;Y 브랜드&quot; |

Content Hub 관리자는 이러한 규칙을 사용하여 다음을 수행할 수 있습니다.

* **세분화된 규칙 기반 액세스**: 사용자는 수동 권한 할당 없이 자신의 지역 및 브랜드와 관련된 자산만 볼 수 있습니다.
* **원활한 글로벌 공동 작업**: 지역 및 브랜드 팀이 액세스 충돌 없이 동시에 작업합니다.
* **확장 가능한 미래 지향적 사용 권한**: 새로운 지역 또는 브랜드가 추가되면 메타데이터를 기반으로 규칙을 업데이트할 수 있습니다.

### ABAC가 유용한 추가 시나리오 {#additional-scenarios-abac}

ABAC는 다음 시나리오를 해결하는 데 도움이 될 수도 있습니다.

* **글로벌 브랜드 및 지역 액세스**: 팀에는 해당 브랜드 및 시장과 관련된 자산만 표시됩니다.
* **에이전시와 파트너 공동 작업**: 외부 에이전시와 파트너는 관련된 캠페인 자산에만 액세스할 수 있습니다.
* **다른 팀에 대한 역할 기반 액세스**: 마케팅, 판매 및 법률 팀과 같은 팀이 해당 기능과 관련된 에셋에 액세스할 수 있습니다.
* **지역별 법률 준수**: 사용자는 특정 규제 또는 지역 요구 사항에 대해 승인된 자산으로 제한될 수 있습니다.

>[!IMPORTANT]
>
>기본적으로 [spreadsheet](#configure-abac-spreadsheet)의 규칙으로 지정되지 않은 다른 모든 사용자 그룹은 액세스가 거부됩니다. 사용자가 ABAC 규칙이 정의된 그룹에 속하지 않으면 에셋에 액세스할 수 없습니다. 일부 사용자가 모든 에셋에 액세스할 수 있어야 하는 경우(예: 관리자) 스프레드시트에 그룹 ID가 있는 그룹을 포함하고 Adobe이 이를 적절히 구성할 수 있도록 그룹이 모든 에셋에 액세스할 수 있어야 한다고 지정합니다.

## 지원되는 규칙 구문 {#supported-rule-constructs}

* **논리 연산자**:
   * AND: 모든 조건이 true여야 함
   * OR: 하나 이상의 조건이 true여야 함

* **비교 연산자**:
   * 같음(=): 사용자 또는 자산 속성이 값과 일치하는지 확인합니다
   * 같지 않음(!=): 사용자 또는 에셋 속성이 값과 일치하지 않는지 확인합니다.

에셋 메타데이터 필드에 다중 지역 또는 태그와 같은 배열이 포함된 경우 같음 은 포함 로직을 참조하고 같지 않음 은 포함하지 않음 로직을 참조합니다.

이렇게 하면 ALLOW if region = emea 및 assetType != 프로토타입 및 태그와 같은 단순하고 표현적인 규칙을 작성할 수 !=.

## 지침 {#guidelines-attribute-based-access-control}

다음 지침은 AI Assistant 기반 및 스프레드시트 기반 구성 모두에 적용됩니다.

* ABAC 규칙은 Content Hub에 대해 승인된 자산에만 적용할 수 있습니다. 자세한 내용은 [Content Hub용 Assets 승인](/help/assets/approve-assets-content-hub.md)을 참조하십시오.
* DENY 규칙을 정의하지 마십시오. 항상 DENY 규칙을 ALLOW 규칙으로 변환합니다. 예를 들어 ALLOW if region = user-region DENY if assetType = prototype AND confidential = yes는 ALLOW if region = user-region AND (assetType != prototype OR confidential != yes)로 변환할 수 있습니다.
* ABAC 규칙은 Admin Console에서 사용할 수 있는 IMS 그룹 ID를 사용하여 사용자 그룹에 적용됩니다.
* AEM as a Cloud Service 작성자 환경을 사용하여 자산에 대한 [승인 대상](/help/assets/approve-assets-content-hub.md#set-approval-target)을 설정할 수 있습니다. 승인 대상 = 전달이 배달 + Content Hub에 사용 가능한 자산에 대한 것이므로 승인 대상 = Content Hub으로 승인된 자산에 ABAC 규칙이 적용됩니다. 승인 대상으로 표시된 Assets = 게재는 Content Hub의 모든 사용자에게 표시됩니다.
* ABAC 규칙에 사용된 메타데이터 스키마가 AEM에서 올바르게 정의되고 사용 가능한지 확인하십시오. ABAC 규칙에서 참조된 속성을 정의하는 AEM의 메타데이터 스키마 또는 스키마의 전체 경로를 제공합니다. 규칙 동작을 확인하고 액세스를 정확하게 평가하는 데 도움이 되도록 ABAC 조건과 일치하는 샘플 에셋이 있는 테스트 폴더를 선택적으로 만들 수 있습니다.
* 조건이 올바르게 작성되더라도 필요한 경우 해당 인텐트가 논리의 유효성을 검사하고 수정하는 데 도움이 되므로 주석의 비즈니스 의도를 캡처합니다.
* 브랜드, 지역 및 제품과 같은 액세스 규칙에 사용되는 메타데이터 값이 자산 간에 일관되게 유지되는지 확인합니다.
* 브랜드 기반 또는 지역 기반 액세스와 같은 주요 사용 사례로 시작합니다.
* AI Assistant를 사용하여 규칙을 정의할 때 명확한 프롬프트를 사용하십시오. AI Assistant가 의도를 구조화된 규칙으로 번역할 수 있도록 비즈니스 언어로 설명합니다.
* DRM용으로 설정된 PDF 라이센스 파일은 라이센스가 있는 에셋을 다운로드할 때 라이센스 정보를 검토할 수 있도록 모든 사용자가 볼 수 있는 상태로 유지되어야 합니다.

## 자주 묻는 질문 {#faqs-attribute-based-access-control-content-hub}

### AEM Assets Content Hub의 속성 기반 액세스 제어(ABAC)란 무엇입니까?

AEM Assets Content Hub의 속성 기반 액세스 제어(ABAC)를 사용하면 관리자가 메타데이터 기반 규칙을 정의하여 다양한 사용자 그룹이 디지털 에셋에 액세스하는 수준을 제어할 수 있습니다. 액세스는 에셋 메타데이터가 규칙에 지정된 조건과 일치하는지 여부에 따라 결정되므로 에셋 가시성을 세부적이고 동적으로 관리할 수 있습니다.

### 관리자는 AEM Assets Content Hub에서 ABAC를 사용하여 액세스 규칙을 어떻게 정의합니까?

관리자는 브랜드 또는 지역과 같은 에셋 메타데이터를 기반으로 조건을 만들고 이를 특정 사용자 그룹 ID에 연결하여 액세스 규칙을 정의합니다. 이러한 규칙은 논리 및 비교 연산자를 사용하여 사용자 그룹에 표시되는 에셋을 정확히 지정합니다.

### AEM Assets Content Hub에서 기존 폴더 기반 권한보다 ABAC를 사용할 때 얻을 수 있는 주요 이점은 무엇입니까?

ABAC를 사용하면 폴더 구조에서 권한에 대한 의존성을 제거할 수 있으며, 관리자가 에셋을 업로드하고 권한을 소급하여 할당할 수 있고, 필요한 중복 에셋의 수를 줄일 수 있습니다. 특히 여러 그룹과 자산을 공유해야 하는 경우 자산 무결성을 향상시키고 권한 관리를 단순화합니다.

### 관리자가 AEM Assets Content Hub 인터페이스에서 직접 ABAC 규칙을 설정할 수 있습니까?

관리자는 해당 조직에 대해 활성화된 경우 Content Hub에서 AI Assistant를 사용하여 ABAC 규칙을 구성할 수 있습니다. Adobe 지원을 통해 스프레드시트 기반 워크플로우를 계속 사용할 수도 있습니다.

### AEM Assets Content Hub에서 ABAC 규칙을 설정할 때 사용할 수 있는 메타데이터 조건 유형은 무엇입니까?

AEM Assets Content Hub의 ABAC 규칙은 AND 및 OR와 같은 논리 연산자와 같음 및 같지 않음 과 같은 비교 연산자를 사용할 수 있습니다. 규칙에 사용되는 메타데이터 속성은 AEM 메타데이터 스키마에서 올바르게 정의되어야 하며 사용할 수 있어야 하며 지역, 브랜드, 제품, 캠페인, 에셋 유형 또는 게시 상태와 같은 필드를 포함할 수 있습니다.

### AEM Assets Content Hub ABAC가 대규모 팀과 다양한 자산 요구 사항을 가진 조직에 특히 유용한 이유는 무엇입니까?

ABAC는 사용자 역할, 지역, 브랜드 또는 비즈니스 요구 사항에 따라 에셋에 대한 세분화된 규칙 기반 액세스를 가능하게 하므로 대규모 팀이 있는 조직에 유용합니다. 이를 통해 수동 권한 할당이나 자산의 과도한 중복 없이 사용자가 책임과 관련된 자산만 볼 수 있습니다.

### 관리자는 Adobe 지원 센터에 제출하기 전에 AEM Assets Content Hub용 ABAC 스프레드시트를 어떻게 준비해야 합니까?

관리자는 Adobe Admin Console에서 사용자 그룹을 만들고, 그룹 ID를 참고하고, 스프레드시트에서 각 그룹에 대한 권한 및 조건을 명확히 정의하고, 모든 메타데이터 속성이 적절한 스키마에 올바르게 매핑되었는지 확인하고, 설명 열을 사용하여 각 규칙의 비즈니스 의도를 명확히 해야 합니다.