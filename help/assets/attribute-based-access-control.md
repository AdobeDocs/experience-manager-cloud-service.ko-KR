---
title: 속성 기반 액세스 제어
description: 속성 기반 액세스 제어를 활성화하여 메타데이터 기반 규칙을 정의하여 Content Hub에서 사용할 수 있는 에셋에 대한 액세스 수준을 정의하는 방법에 대해 알아봅니다
role: Admin
exl-id: 05f54b05-40b8-4a6c-af8f-5c3f7a2089d4
source-git-commit: ea1760a3076fa0e18dca38fe856ff0ef78b18f07
workflow-type: tm+mt
source-wordcount: '976'
ht-degree: 4%

---

# 속성 기반 액세스 제어 {#attribute-based-access-control}

Content Hub 관리자는 속성 기반 액세스 제어(ABAC)를 사용하여 메타데이터 기반 규칙을 정의하여 Content Hub에서 사용할 수 있는 에셋에 대한 액세스 수준을 정의할 수 있습니다.

조직의 관리자는 그룹 ID에 매핑된 사용자 그룹에 대한 규칙을 정의합니다. 규칙은 [논리 및 비교 연산자](#supported-rule-constructs)의 혼합이며 관리자는 Content Hub 내에서 에셋 액세스를 관리하는 데 필요한 수만큼 규칙을 정의할 수 있습니다.

규칙은 메타데이터를 기반으로 하며, 규칙에 정의된 조건이 에셋 메타데이터와 일치하는 경우 에셋이 사용자 그룹에 표시됩니다. Content Hub은 **모든 Assets** 및 **컬렉션** 내에서 사용할 수 있는 모든 자산에 대한 사용자 지정 메타데이터를 포함하는 자산 메타데이터를 스캔하여 결과를 사용자 그룹에 표시합니다.

예를 들어, 자산 메타데이터가 &quot;Brand = Brand X&quot; 및 &quot;Region = EMEA 또는 아메리카&quot;와 일치하는 경우 그룹 ID가 1011인 사용자 그룹에 대한 액세스를 허용합니다. Content Hub은 ID = 1011인 사용자 그룹에만 해당 자산을 표시합니다. 여기서 브랜드 = `Brand X`, 지역 = `EMEA` 또는 `Americas`입니다.

속성 기반 액세스 제어의 몇 가지 주요 이점은 다음과 같습니다.

* 폴더 구조에 대한 권한 종속을 제거합니다.

* 관리자가 자산을 업로드하고 권한 구조를 소급적으로 결정할 수 있도록 합니다.

* 중복 횟수를 줄여 자산 무결성을 향상시킵니다. 폴더 기반 권한에서는 동일한 자산이 다른 그룹과 공유될 때 중복이 필요합니다.

## 속성 기반 액세스 제어를 활성화하는 방법 {#enable-attribute-based-access-control}

현재는 Content Hub 사용자 인터페이스를 사용하여 속성 기반 액세스 제어 규칙을 직접 만들 수 없습니다.

스프레드시트에서 규칙을 다운로드하고 정의하려면 **스프레드시트 다운로드**&#x200B;를 클릭하십시오. Adobe 지원 티켓을 만들고 스프레드시트에 정의된 규칙을 Adobe에 제공합니다.

[!BADGE 스프레드시트 다운로드]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/ABAC_Get_Started_Template_Validator.xlsx"}


이 문서에 정의된 지침을 사용하여 스프레드시트에서 규칙을 정의합니다.

>[!IMPORTANT]
>
> 규칙을 정의한 후 스프레드시트의 **유효성 검사 오류** 탭으로 이동하여 **ABAC 유효성 검사 실행**&#x200B;을 클릭합니다. **모든 유효성 검사 통과** 메시지를 통해 정의된 규칙을 Adobe에 제공할 수 있음을 확인합니다.

## 예제 속성 기반 액세스 제어 사용 사례 {#example-metadata-based-rules}

대규모 마케팅 롤아웃을 지원하려면 지역 및 브랜드의 다양한 팀원이 디지털 에셋에 액세스해야 합니다. 각 담당자는 지역 및 브랜드를 기반으로 특정 범위를 갖습니다. ABAC는 에셋 메타데이터를 통해 이러한 규칙을 자동으로 적용합니다. 다음 표는 이 사용 사례에 대한 다양한 유형의 가상 사용자와 적용되는 규칙을 보여 줍니다.

| 담당자 | 역할 | 역할 설명 | 그룹 ID | 규칙 |
|---------------------|----------------|-----------------|------------|------------|
| John | EMEA 마케팅 리드 | EMEA의 모든 브랜드에서 마케팅 실행을 감독합니다. EMEA 시장을 겨냥한 모든 브랜드의 승인된 자산에 액세스해야 합니다. | group-emea-marketing | region = &quot;EMEA&quot; |
| 마이크 | APAC 마케팅 리드 | APAC의 모든 브랜드에서 마케팅 실행을 감독합니다. APAC 시장을 겨냥한 모든 브랜드의 승인된 자산에 액세스해야 합니다. | group-apac-marketing | region = &quot;APAC&quot; |
| 소피 | Brand X Manager(EMEA) | EMEA에서 Brand X ID 관리. EMEA 시장에 맞게 조정된 Brand X 승인 콘텐츠만 표시하면 됩니다. | group-emea-brandx | 지역 = &quot;EMEA&quot; &amp;&amp; 브랜드 = &quot;Brand X&quot; |
| Tom | 브랜드 Y 관리자 (APAC) | APAC에서 Brand Y ID를 관리합니다. APAC 시장에 맞게 조정된 Brand Y 승인 콘텐츠만 표시하면 됩니다. | 그룹-apac-brandy | 지역 = &quot;APAC&quot; &amp;&amp; 브랜드 = &quot;Y 브랜드&quot; |

Content Hub 관리자는 이러한 규칙을 사용하여 다음을 수행할 수 있습니다.

* **세분화된 규칙 기반 액세스**: 사용자는 지역 및 브랜드와 관련된 자산만 볼 수 있으며 수동 권한 할당은 없습니다.

* **원활한 글로벌 공동 작업**: 지역 및 브랜드 팀이 액세스 충돌 없이 동시에 작업했습니다.

* **확장 가능한 미래 지향적 사용 권한**: 새로운 지역 또는 브랜드가 추가되면 메타데이터를 기반으로 규칙을 업데이트할 수 있습니다.

>[!IMPORTANT]
>
> 기본적으로 [spreadsheet](#enable-attribute-based-access-control)의 규칙으로 지정되지 않은 다른 모든 사용자 그룹은 액세스가 거부됩니다. 사용자가 ABAC 규칙이 정의된 그룹에 속하지 않으면 어떤 에셋에도 액세스할 수 없습니다. 모든 에셋에 액세스할 수 있는 일부 사용자가 필요한 경우(예: 관리자), 그룹 ID가 있는 그룹은 이 특정 그룹이 모든 에셋에 액세스해야 하며 Adobe에서 자동으로 구성한다는 세부 정보와 함께 스프레드시트에 언급되어야 합니다.


## 지원되는 규칙 구문 {#supported-rule-constructs}

* **논리 연산자**:
   * AND: 모든 조건이 true여야 함
   * OR: 하나 이상의 조건이 true여야 함
* **비교 연산자**:
   * 같음(=): 사용자 또는 자산 속성이 값과 일치하는지 확인합니다
   * 같지 않음(!)=): 사용자 또는 에셋 속성이 값과 일치하지 않는지 확인합니다

에셋 메타데이터 필드에 배열(예: 여러 지역 또는 태그)이 포함된 경우 `Equals`은(는) `contains` 논리를 참조하고 `Not Equals`은(는) `does not contain` 논리를 참조합니다.

이렇게 하면 ALLOW if region = emea AND assetType != 프로토타입 및 태그 != 기밀입니다.

## 지침 {#guidelines-attribute-based-access-control}

* ABAC 규칙은 Content Hub에 대해 승인된 자산에만 적용할 수 있습니다. 자세한 내용은 [Content Hub용 Assets 승인](/help/assets/approve-assets-content-hub.md)을 참조하십시오.

* DENY 규칙을 지정하지 말고 대신 항상 DENY를 ALLOW 규칙으로 변환합니다. 예를 들어 `ALLOW if region = <user-region> DENY if assetType = prototype AND confidential = yes`을(를) `ALLOW if region = <user-region> AND (assetType != prototype OR confidential != yes)`(으)로 변환할 수 있습니다.

* ABAC 규칙은 Admin Console에서 사용할 수 있는 IMS 그룹 ID를 사용하여 사용자 그룹에 적용됩니다.


* AEM as a Cloud Service 작성자 환경을 사용하여 자산에 대한 [승인 대상](/help/assets/approve-assets-content-hub.md#set-approval-target)을 설정할 수 있습니다. 승인 대상 = `Content Hub`이(가) `Delivery` + `Delivery`에 사용 가능한 자산에 대한 것이므로 승인 대상 = `Content Hub`인 승인된 자산에 ABAC 규칙이 적용됩니다. 승인 대상으로 표시된 Assets = `Delivery`이(가) 콘텐츠 허브의 모든 사용자에게 표시됩니다.

* ABAC 규칙에 사용된 메타데이터 스키마가 AEM에서 올바르게 정의되고 사용 가능한지 확인하십시오. ABAC 규칙에서 참조된 속성을 정의하는 AEM 메타데이터 스키마의 전체 경로를 제공합니다. ABAC 조건과 일치하는 메타데이터 값이 있는 몇 가지 샘플 에셋이 있는 테스트 폴더를 선택적으로 만들 수 있습니다. 이렇게 하면 규칙 동작을 확인하고 액세스를 정확하게 평가하는 데 도움이 됩니다.

* 필요한 경우 논리의 유효성을 검사하고 수정하는 데 도움이 되므로 조건이 올바르게 작성되었는지 여부에 관계없이 규칙의 비즈니스 의도를 주석에 캡처합니다.

* DRM용으로 설정된 라이센스 PDF 파일은 사용자가 라이센스가 있는 에셋을 다운로드할 때 볼 수 있도록 모두에게 표시되어야 합니다.
