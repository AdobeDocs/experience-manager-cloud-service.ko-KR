---
title: 얼리어답터 및 프리릴리스 기능 통합을 위한 기능 전환 활성화
description: 기능 토글 은 관리자가 런타임 환경에서 새로운 기능을 활성화할 수 있는 AEM의 기능입니다.
feature: Adaptive Forms, Foundation Components, Core Components
role: User, Developer
source-git-commit: cc4fccc51f487170bf6c14e4b302a8d5912c33a0
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 1%

---

# Adobe Experience Software Development Kit(AEM SDK)의 기능 전환

AEM의 기능 전환을 사용하면 관리자가 런타임 시 코드를 변경하지 않고 얼리어답터 및 프리릴리스 기능을 관리하는 데 적합한 기능을 활성화하거나 비활성화할 수 있습니다. 점진적인 롤아웃, A/B 테스트 및 불안정한 기능의 빠른 비활성화를 지원합니다.

이 문서에서는 SDK 및 Dispatcher을 사용하여 AEM as a Cloud Service을 시뮬레이션하는 AEM 로컬 SDK 설정에서 기능 전환을 활성화하는 방법을 다룹니다. 이 설정은 팀이 클라우드에 배포하기 전에 프로덕션과 유사한 환경에서 테스트하는 데 도움이 됩니다.

## AEM SDK 설정에서 기능 전환을 사용하는 이유는 무엇입니까?

AEM SDK 설정에서 작업할 때 기능에서 도움말을 토글합니다.

* 실험 기능을 안전하게 테스트합니다.

* 새 구성 요소를 단계적으로 롤아웃

* 여러 환경에서 단일 코드 베이스를 유지 관리합니다.

* 배포 및 업그레이드 시 위험 감소

## 사전 요구 사항

AEM SDK 설정에서 기능 전환을 활성화하기 전에 다음을 확인하십시오.

* 사용자가 `forms-users` 그룹의 구성원입니다.

* `http://<author-instance-url>:portnumber/system/console/bundles`(으)로 이동하여 **(com.adobe.granite.toggle.impl.dev-1.1.2.jar)** 번들이 있는지 확인합니다. 없는 경우 [링크에서 번들을 다운로드](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/com.adobe.granite.toggle.impl.dev-1.1.2%20.jar)합니다.

  ![기능 전환](/help/forms/assets/aem-web-console-bundle.png)

### 기능 활성화 전환

AEM SDK 인스턴스에서 기능 전환을 활성화하려면 다음 단계를 따르십시오.

1. AEM Forms 인스턴스에 로그인.

1. 다음으로 이동 `http://author-instance-url:portnumber/system/console/configMgr`.

1. 구성 관리자에서 Adobe Granite 동적 전환 공급자를 검색합니다.

   ![기능 전환](/help/forms/assets/aem-web-console-confi.png)

1. ✏️ 아이콘을 클릭합니다.
1. 토글 사용 섹션에서 ➕ 을(를) 클릭합니다.
1. 아래 이미지에 표시된 대로 기능에 대한 기능 전환 ID를 추가합니다.
   ![기능 전환](/help/forms/assets/feature-toggle.png)

1. 저장을 클릭합니다.

>[!NOTE]
>
> 얼리어답터 기능과 관련된 문서에서 기능 전환 ID를 찾을 수 있습니다.


### 기능 비활성화 전환

토글이 활성화된 피쳐에 대해 피쳐 토글을 비활성화하려면 아래 단계를 따르십시오.

1. AEM Forms 인스턴스에 로그인.
1. 다음으로 이동 `http://author-instance-url:portnumber/system/console/configMgr`.
1. 구성 관리자에서 Adobe Granite 동적 전환 공급자를 검색합니다.
1. ✏️ 아이콘을 클릭합니다.
1. [사용 안 함 전환] 섹션에서 ➕을(를) 클릭합니다.
1. 비활성화할 기능의 토글 번호를 추가합니다.

   ![기능 전환](/help/forms/assets/disable-toggle-feature.png)

### 기술적 고려 사항

기능 전환은 런타임으로 관리되며 개발 또는 테스트 설정에 가장 적합합니다. AEM SDK 설정에서 토글이 버전 제어되고 CI/CD와 동기화되는지 확인합니다. 변경 사항을 반영하려면 페이지 새로 고침 또는 캐시 지우기가 필요할 수 있습니다.

>[!NOTE]
>
> 프로덕션 환경에 대해 기능 토글을 활성화하려면 Adobe 지원 팀에 문의하십시오.

