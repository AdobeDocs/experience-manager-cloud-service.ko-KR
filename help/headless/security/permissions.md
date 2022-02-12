---
title: '헤드리스 컨텐츠에 대한 권한 고려 사항 '
description: Adobe Experience Manager을 사용한 헤드리스 구현에 대한 다양한 권한 및 ACL 고려 사항에 대해 알아봅니다. 작성자와 게시 환경 모두에 필요한 다양한 가상 및 잠재적 권한 수준을 파악합니다.
feature: Content Fragments,GraphQL API
source-git-commit: c5d67e0ece40cdf7a9009436ec90305fe81425a2
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---


# 헤드리스 컨텐츠에 대한 권한 고려 사항

헤드리스 구현을 통해 해결해야 하는 몇 가지 보안 및 권한 영역이 있습니다. 권한 및 가상 사용자는 AEM 환경을 기반으로 광범위하게 고려될 수 있습니다 **작성자** 또는 **게시**. 각 환경에는 서로 다른 성향과 요구 사항이 있습니다.

## 작성자 서비스 고려 사항

작성 서비스는 내부 사용자가 컨텐츠를 작성, 관리 및 게시하는 곳입니다. 권한은 컨텐츠를 관리하는 다양한 가상 사용자를 중심으로 진행됩니다.

### 그룹 수준에서 권한 관리

가장 좋은 방법으로서, AEM의 그룹에서 권한을 설정해야 합니다. 로컬 그룹이라고도 하며 이러한 그룹은 AEM 작성 환경 내에서 관리할 수 있습니다.

그룹 구성원을 관리하는 가장 쉬운 방법은 IMS(Adobe Identity Management System) 그룹을 사용하고 를 할당하는 것입니다 [IMS 그룹을 로컬 AEM 그룹에 추가](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/ims-support.html?lang=en#managing-permissions-in-aem).

![Admin Console 권한 흐름](assets/admin-console-aem-group-permissions.png)

높은 수준에서 프로세스는 다음과 같습니다.

1. 를 사용하여 새 IMS 사용자 또는 기존 IMS 사용자 그룹에 IMS 사용자 추가 [Admin Console](https://adminconsole.adobe.com/)
1. IMS 그룹은 사용자가 로그인할 때 AEM으로 동기화됩니다.
1. AEM 그룹에 IMS 그룹 할당.
1. AEM 그룹에 대한 권한을 설정합니다.
1. 사용자가 AEM에 로그인하고 IMS를 통해 인증되면 AEM 그룹의 권한을 상속합니다.

>[!TIP]
>
> IMS 및 AEM 사용자 및 그룹 관리에 대한 자세한 비디오 연습이 제공됩니다 [여기](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html).

관리하려면 **그룹** AEM에서 **도구** > **보안** > **그룹**.

AEM에서 그룹의 권한을 관리하려면 **도구** > **보안** > **권한**.

### DAM 사용자

이 컨텍스트에서 &quot;DAM&quot;은 디지털 자산 관리를 의미합니다. 다음 **DAM 사용자** 는 AEM에서 디지털 자산 및 컨텐츠 조각을 관리하는 &quot;일상적인&quot; 사용자에게 사용할 수 있는 기본 그룹입니다. 이 그룹에서는 **보기**, **추가**, **업데이트**, **delete**, 및 **게시** AEM Assets의 컨텐츠 조각 및 기타 모든 파일.

그룹 멤버십에 IMS를 사용하는 경우 해당 IMS 그룹을 의 구성원으로 추가합니다 **DAM 사용자** 그룹에 속해 있어야 합니다. IMS 그룹의 구성원은 AEM 환경에 로그인할 때 DAM 사용자 그룹의 권한을 상속합니다.

#### DAM 사용자 그룹 사용자 지정

즉시 사용 가능한 그룹의 권한을 직접 수정하지 않는 것이 좋습니다. 대신, 을 따라 모델링된 고유한 그룹을 만들 수도 있습니다 **DAM 사용자** 그룹 권한 및 다른 **폴더** AEM Assets 내에서 사용할 수 있습니다.

더 세분화된 권한을 얻으려면 **권한** AEM의 콘솔에서 경로를 업데이트하고 `/content/dam` 보다 구체적인 경로, 즉 `/content/dam/mycontentfragments`.

이 사용자 그룹에 컨텐츠 조각을 만들고 편집할 수 있는 권한을 제공하되 삭제하지는 않는 것이 좋습니다. 편집에 대한 권한을 검토 및 할당하되 삭제하지 않으려면 다음을 참조하십시오 [컨텐츠 조각 - 삭제 고려 사항](/help/assets/content-fragments/content-fragments-delete.md).

### 모델 편집기

수정할 수 있는 기능 **컨텐츠 조각 모델** 는 관리자 또는 **작은 그룹** 권한이 향상된 사용자 컨텐츠 조각 모델 수정에는 많은 다운스트림 효과가 있습니다.

>[!CAUTION]
>
>컨텐츠 조각 모델 을 수정하면 헤드리스 애플리케이션이 사용하는 기본 GraphQL API가 변경됩니다.

컨텐츠 조각 모델을 관리하지만 전체 관리자 액세스 권한이 없는 그룹을 만들려면 다음과 같은 액세스 제어 항목이 있는 그룹을 생성할 수 있습니다.

| 경로 | 권한 | 권한 |
|-----| -------------| ---------|
| `/conf` | **허용** | `jcr:read` |
| `/conf/<config-name>/settings/dam/cfm` | **허용** | `rep:write`, `crx:replicate` |

## 서비스 권한 게시

게시 서비스는 &quot;라이브&quot; 환경으로 간주되며 일반적으로 GraphQL API 소비자가 상호 작용하는 것입니다. 작성 서비스에서 편집하고 승인되면 컨텐츠가 게시 서비스에 게시됩니다. 그러면 헤드리스 애플리케이션은 GraphQL API를 통해 게시 서비스에서 승인된 컨텐츠를 사용합니다.

기본적으로 AEM 게시 서비스의 GraphQL 끝점을 통해 노출된 콘텐츠는 인증되지 않은 사용자를 포함하여 모든 사람이 액세스할 수 있습니다.

### 컨텐츠 권한

AEM GraphQL API를 통해 노출되는 컨텐츠는 [폐쇄된 사용자 그룹(CUG)](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/closed-user-groups.html) 자산 폴더의 컨텐츠에 액세스할 수 있는 AEM 사용자 그룹(및 그 구성원)을 지정하는 자산 폴더에 설정합니다.

자산 CUG는 다음 작업을 통해 작동합니다.

* 먼저, 폴더 및 하위 폴더에 대한 모든 액세스를 거부합니다
* 그런 다음 CUG 목록에 나열된 모든 AEM 사용자 그룹에 대해 폴더 및 하위 폴더에 대한 읽기 액세스를 허용합니다

GraphQL API를 통해 노출된 컨텐츠가 포함된 자산 폴더에서 CUG를 설정할 수 있습니다. AEM Publish에서 자산 폴더에 대한 액세스는 사용자가 직접 아닌 사용자 그룹을 통해 제어되어야 합니다. GraphQL API에 의해 노출된 컨텐츠가 포함된 자산 폴더에 대한 액세스 권한을 부여하는 AEM 사용자 그룹을 생성(또는 재사용)합니다.

#### 인증 체계를 선택합니다{#publish-permissions-users}

다음 [AEM Headless SDK](https://github.com/adobe/aem-headless-client-js#create-aemheadless-client) 에서는 두 가지 유형의 인증을 지원합니다.

* [토큰 기반 인증](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) 단일 기술 계정에 바인딩된 서비스 자격 증명을 사용합니다.
* AEM 사용자를 사용한 기본 인증.

### GraphQL API에 액세스

을 제공하는 HTTP 요청 [적절한 인증 자격 증명](https://github.com/adobe/aem-headless-client-js#create-aemheadless-client) aem 게시 서비스의 GraphQL API 엔드포인트에 자격 증명에 읽을 수 있는 권한이 있는 컨텐츠와 익명으로 액세스할 수 있는 컨텐츠가 포함됩니다. GraphQL API의 다른 소비자는 CUGs 보호 폴더에서 컨텐츠를 읽을 수 없습니다.

