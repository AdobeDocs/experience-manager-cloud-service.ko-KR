---
title: Adobe Experience Manager as a Cloud Service에 대한 마이크로 프론트엔드 콘텐츠 조각 선택기 속성
description: 애플리케이션에서 콘텐츠 조각을 검색, 찾기 및 검색하도록 마이크로 프론트엔드 콘텐츠 조각 선택기를 구성하는 속성입니다.
role: Admin, User
exl-id: c81b5256-09fb-41ce-9581-f6d1ad316ca4
source-git-commit: 74b9493fc3cdba4a1fc64d1137f5c50c6bebca0a
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 4%

---

# 콘텐츠 조각 선택기 - 관련 속성 {#content-fragment-selector-related-properties}

마이크로 프론트엔드 콘텐츠 조각 선택기를 사용하면 저장소에서 콘텐츠 조각을 찾아보거나 검색하고 애플리케이션에서 사용할 수 있습니다.

다음 속성을 사용하여 콘텐츠 조각 선택기를 렌더링하는 방법과 사용 방법을 사용자 지정할 수 있습니다.

## 콘텐츠 조각 선택기 속성 {#content-fragment-selector-properties}

| 속성 | 유형 | 필수 | 기본값 | 설명 |
|--- |--- |--- |--- |--- |
| `ref` | 조각 선택기 참조 | | | `ContentFragmentSelector` 인스턴스를 참조하여 `reload`과(와) 같이 제공된 기능에 액세스할 수 있습니다. |
| `imsToken` | 문자열 | 아니요 | | 인증에 사용되는 IMS 토큰입니다. 제공하지 않으면 IMS 로그인 플로우가 시작됩니다. |
| `repoId` | 문자열 | 아니요 | | 조각 선택기에 사용되는 저장소 ID입니다. 제공된 경우 선택기가 지정된 저장소에 자동으로 연결되고 저장소 드롭다운이 숨겨집니다. 제공되지 않은 경우 사용자는 액세스 권한이 있는 사용 가능한 저장소 목록에서 저장소를 선택할 수 있습니다. |
| `defaultRepoId` | 문자열 | 아니요 | | 저장소 선택기가 표시되면 기본적으로 선택되는 저장소 ID입니다. `repoId`이(가) 제공되지 않은 경우에만 사용됩니다. `repoId`이(가) 설정되면 저장소 선택기가 숨겨지며 이 값은 무시됩니다. |
| `orgId` | 문자열 | 아니요 | | 인증에 사용되는 조직 ID입니다. 제공하지 않은 경우 사용자는 액세스 권한이 있는 다른 조직의 저장소를 선택할 수 있습니다. 사용자에게 저장소나 조직에 대한 액세스 권한이 없는 경우 콘텐츠가 로드되지 않습니다. |
| `locale` | 문자열 | 아니요 | `en-US` | 로케일. |
| `env` | 문자열 | 아니요 | | 배포 환경. 허용되는 환경 이름은 `Env` 형식을 참조하십시오. |
| `filters` | 조각 필터 | 아니요 | `{ folder: "/content/dam" }` | 콘텐츠 조각 목록에 적용할 필터. 기본적으로 `/content/dam` 아래의 조각이 표시됩니다. |
| `isOpen` | 부울 | 아니요 | `false` | 선택기의 열기 또는 닫기 여부를 제어하는 플래그. |
| `noWrap` | 부울 | 아니요 | `false` | 래핑 대화 상자 없이 조각 선택기를 렌더링할지 여부를 결정합니다. `true`(으)로 설정하면 조각 선택기가 상위 컨테이너에 직접 포함됩니다. 선택기를 사용자 지정 레이아웃 또는 워크플로우에 통합하는 데 유용합니다. |
| `onSelectionChange` | ({ contentFragments: `ContentFragmentSelection`, domainName?: `string`, tenantInfo?: `string`, repoId?: `string`, deliveryRepos?: `DeliveryRepository[]` }) => void | 아니요 | | 콘텐츠 조각 선택이 변경될 때마다 트리거되는 콜백 함수입니다. 현재 선택한 조각, 도메인 이름, 테넌트 정보, 저장소 ID 및 게재 저장소를 제공합니다. |
| `onDismiss` | () => void | 아니요 | | 닫기 작업을 수행할 때 트리거되는 콜백 함수(예: 선택기를 닫는 경우)입니다. |
| `onSubmit` | ({ contentFragments: `ContentFragmentSelection`, domainName?: `string`, tenantInfo?: `string`, repoId?: `string`, deliveryRepos?: `DeliveryRepository[]` }) => void | 아니요 | | 사용자가 선택을 확인할 때 트리거되는 콜백 함수입니다. 선택한 콘텐츠 조각, 도메인 이름, 테넌트 정보, 저장소 ID 및 게재 저장소를 수신합니다. |
| `theme` | &quot;light&quot; 또는 &quot;dark&quot; | 아니요 | | 조각 선택기에 대한 테마입니다. 기본적으로 unifiedShell 환경 테마로 설정됩니다. |
| `selectionType` | &quot;single&quot; 또는 &quot;multiple&quot; | 아니요 | `single` | 선택 유형을 사용하여 조각 선택기에 대한 선택을 제한할 수 있습니다. |
| `dialogSize` | &quot;fullscreen&quot; 또는 &quot;fullscreenTakeover&quot; | 아니요 | `fullscreen` | 대화 상자 크기를 제어하는 선택적 prop입니다. |
| `runningInUnifiedShell` | 부울 | 아니요 | | DestinationSelector가 UnifiedShell에서 실행되는지 또는 독립 실행형에서 실행되는지 여부. |
| `readonlyFilters` | ResourceReadonlyFiltersField[] | 아니요 | | 콘텐츠 조각 목록에 적용된 읽기 전용 필터. 사용자가 이러한 필터를 제거할 수 없습니다. |
| `selectedFragments` | ContentFragmentIdentifier[] | 아니요 | `[]` | 선택기가 열릴 때 사전 선택될 콘텐츠 조각의 초기 선택. |
| `hipaaEnabled` | 부울 | 아니요 | `false` | HIPAA 규정 준수 여부를 나타냅니다. |
| `inventoryView` | 재고 보기 유형 | 아니요 | `table` | 선택기에서 사용할 재고 기본 보기 유형입니다. |
| `inventoryViewToggleEnabled` | 부울 | 아니요 | `false` | 사용자가 테이블 및 그리드 보기 간을 전환할 수 있도록 인벤토리 보기 토글을 활성화할지 여부를 나타냅니다. |

## ImsAuthProps 속성 {#imsauthprops-properties}

`ImsAuthProps` 속성은 콘텐츠 조각 선택기에서 `imsToken`을(를) 가져오는 데 사용하는 인증 정보 및 흐름을 정의합니다. 이러한 속성을 설정하여 인증 플로우의 동작 방법을 제어하고 다양한 인증 이벤트에 대한 리스너를 등록할 수 있습니다.

| 속성 이름 | 설명 |
|--- |--- |
| `imsClientId` | 인증 용도로 사용되는 IMS 클라이언트 ID를 나타내는 문자열 값입니다. 이 값은 Adobe에서 제공하며 Adobe AEM CS 조직에만 해당됩니다. |
| `imsScope` | 인증에 사용되는 범위를 설명합니다. 범위는 응용 프로그램이 조직 리소스에 대해 갖는 액세스 수준을 결정합니다. 여러 범위는 쉼표로 구분할 수 있습니다. |
| `redirectUrl` | 인증 후 사용자가 리디렉션되는 URL을 나타냅니다. 이 값은 일반적으로 애플리케이션의 현재 URL로 설정됩니다. `redirectUrl`이(가) 제공되지 않으면 `ImsAuthService`에서 `imsClientId`을(를) 등록하는 데 사용되는 redirectUrl을 사용합니다. |
| `modalMode` | 인증 흐름을 모달(팝업)로 표시할지 여부를 나타내는 부울. `true`(으)로 설정하면 인증 흐름이 팝업에 표시됩니다. `false`(으)로 설정하면 전체 페이지를 다시 로드할 때 인증 흐름이 표시됩니다.<br>**참고:** 더 나은 UX를 위해 사용자에게 브라우저 팝업이 비활성화된 경우 이 값을 동적으로 제어할 수 있습니다. |
| `onImsServiceInitialized` | Adobe IMS 인증 서비스가 초기화될 때 호출되는 콜백 함수입니다. 이 함수는 Adobe IMS 서비스를 나타내는 개체인 `service` 매개 변수 하나를 사용합니다. 자세한 내용은 [`ImsAuthService`](#imsauthservice-ims-auth-service)을(를) 참조하십시오. |
| `onAccessTokenReceived` | Adobe IMS 인증 서비스에서 `imsToken`을(를) 받을 때 호출되는 콜백 함수입니다. 이 함수는 액세스 토큰을 나타내는 문자열인 `imsToken` 매개 변수 하나를 사용합니다. |
| `onAccessTokenExpired` | 액세스 토큰이 만료된 경우 호출되는 콜백 함수입니다. 이 함수는 일반적으로 새 액세스 토큰을 얻기 위해 새 인증 흐름을 트리거하는 데 사용됩니다. |
| `onErrorReceived` | 인증 중에 오류가 발생할 때 호출되는 콜백 함수입니다. 이 함수는 오류 유형과 오류 메시지의 두 매개 변수를 사용합니다. 오류 유형은 오류의 유형을 나타내는 문자열이고, 오류 메시지는 오류 메시지를 나타내는 문자열이다. |

## ImsAuthService 속성 {#imsauthservice-properties}

`ImsAuthService` 클래스는 콘텐츠 조각 선택기에 대한 인증 흐름을 처리합니다. Adobe IMS 인증 서비스에서 `imsToken`을(를) 가져옵니다. `imsToken`은(는) 사용자를 인증하고 Adobe Experience Manager(AEM) CS 저장소에 대한 액세스 권한을 부여하는 데 사용됩니다. ImsAuthService는 `ImsAuthProps` 속성을 사용하여 인증 흐름을 제어하고 다양한 인증 이벤트에 대한 수신기를 등록합니다. 편리한 `registerContentFragmentSelectorAuthService` 함수를 사용하여 콘텐츠 조각 선택기에 `ImsAuthService` 인스턴스를 등록할 수 있습니다. 다음 함수는 `ImsAuthService` 클래스에서 사용할 수 있습니다. 그러나 `registerContentFragmentSelectorAuthService` 함수를 사용하는 경우에는 이러한 함수를 직접 호출할 필요가 없습니다.

| 함수 이름 | 설명 |
|--- |--- |
| `isSignedInUser` | 사용자가 현재 서비스에 로그인되어 있는지 여부를 확인하고 그에 따라 부울 값을 반환합니다. |
| `getImsToken` | 현재 로그인한 사용자에 대한 인증 `imsToken`을(를) 검색합니다. 이 인증은 자산 _렌디션 생성과 같은 다른 서비스에 대한 요청을 인증하는 데 사용할 수 있습니다._ |
| `signIn` | 사용자의 로그인 프로세스를 시작합니다. 이 함수는 `ImsAuthProps`을(를) 사용하여 팝업 또는 전체 페이지 다시 로드에서 인증을 표시합니다. |
| `signOut` | 사용자를 서비스에서 로그아웃하고 인증 토큰을 무효화하며 보호된 리소스에 액세스하려면 다시 로그인해야 합니다. 이 함수를 호출하면 현재 페이지가 다시 로드됩니다. |
| `refreshToken` | 현재 로그인한 사용자에 대한 인증 토큰을 새로 고침하여 만료되지 않도록 하고 보호된 리소스에 대한 액세스를 중단하지 않도록 합니다. 후속 요청에 사용할 수 있는 새 인증 토큰을 반환합니다. |
