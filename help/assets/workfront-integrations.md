---
title: '[!DNL Experience Manager Assets] integration with [!DNL Adobe Workfront]'
description: 통합 소개 [!DNL Assets] 및 [!DNL Workfront]
role: Admin,Leader,Architect
feature: Integrations
source-git-commit: d75d9ac16f64b6770fcf35d58474c47c52b1585b
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 2%

---


# [!DNL Adobe Experience Manager] 로서의 [!DNL Cloud Service] [!DNL Assets] 통합 [!DNL Adobe Workfront] {#assets-integration-overview}

[!DNL Adobe Workfront] 은 한 곳에서 전체 작업 수명 주기를 관리하는 데 도움이 되는 작업 관리 애플리케이션입니다. 통합 [!DNL Workfront] 및 [!DNL Adobe Experience Manager Assets] 작업 및 디지털 자산 관리를 동적으로 연결하여 컨텐츠 속도 및 출시 시간을 향상시킬 수 있습니다. Workfront에서 작업을 관리하는 컨텍스트 내에서 사용자는 필요한 문서와 이미지에 액세스할 수 있습니다.

Adobe은 두 솔루션을 모두 통합하는 두 개의 서로 다른 커넥터를 제공합니다. 커넥터를 사용하면 복잡한 엔터프라이즈 자동화, 구성 및 확장 가능한 워크플로우를 사이에 만들 수 있습니다 [!DNL Assets] 및 [!DNL Workfront]. 게다가, [!DNL Assets Essentials] 는 새로운 [!DNL Workfront] 고객은 별도로 구매할 수 있습니다. 자세한 내용은 [[!DNL Workfront] and [!DNL Assets Essentials] 통합](https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/integration.html).

[!DNL Workfront for Experience Manage enhanced connector] 조직을 사용하여 다음을 수행할 수 있습니다.

* 간편한 공동 작업 크리에이티브 팀은 단 한 가지 작은 것에 대해 걱정할 수 있습니다. 이제 작업이 완료되면 단추를 클릭하여 AEM Assets으로 보낼 수 있습니다
* 모든 단계에서 자산을 보강합니다. 자산 라이프사이클의 각 단계에서 새 데이터를 수집합니다. 인수에서 게재에 이르기까지 조직은 주요 지표를 캡처하여 향후 자산 개발에 대한 보다 현명한 비즈니스 결정을 내릴 수 있습니다.
* 기존 자산을 참조합니다. 프로덕션에서 기존 자산을 쉽게 찾아 재사용할 수 있으며 새 프로젝트에 참조 항목으로 추가할 수 있습니다.
* 모든 메타데이터를 동기화합니다. 가능한 한 쉽게 추가하여 메타데이터를 향상시킵니다. 커넥터를 사용하면 메타데이터가 Workfront과 AEM Assets 간에 양방향 동기화됩니다
* 활용 [!DNL Experience Manager Assets] 디지털 관리 기능. 좋아하는 내에서 직접 모든 디지털 자산에 액세스할 수 있습니다 [!DNL Creative Cloud] 응용 프로그램. AI 기반의 스마트 태그 지정 및 자르기, 검색 도구, 동적 전달 [!DNL Dynamic Media]그리고 훨씬 더 많이

플랫폼 지원 및 기타 를 참조하십시오 [향상된 커넥터를 위한 사전 요구 사항](https://one.workfront.com/s/csh?context=2467&amp;pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>Adobe을 사용하려면 [!DNL Adobe Workfront for Experience Manager enhanced connector] 인증된 파트너를 통해 [!DNL Adobe Professional Services]. 인증된 파트너 또는 [!DNL Adobe Professional Services]Adobe에서 지원하지 않습니다.
>
>Adobe은 [!DNL Adobe Workfront] 및 [!DNL Adobe Experience Manager] 이 커넥터를 이중화합니다. 이러한 경우 고객은 이 커넥터를 사용하는 상태에서 전환해야 할 수 있습니다.

## 서로 다른 통합 비교 [!DNL Assets] 및 [!DNL Workfront] {#feature-parity-matrix}

다음은 다양한 유형의 통합을 통해 사용할 수 있는 기능에 대한 세부 사항입니다 [!DNL Assets] 및 [!DNL Workfront].

| 기능 | 설명 | [!DNL Workfront] 및 [!DNL Assets Essentials] | [!DNL Workfront] 대상 [!DNL Experience Manager] 커넥터 | [!DNL Workfront for Experience Manager enhanced connector] |
|----|----|----|------|-----|
| 배포 메서드 | 적합한 [!DNL Assets] 제공 | Assets Essentials | Cloud Service, Adobe Managed Services, 온-프레미스 | Cloud Service, Adobe Managed Services, 온-프레미스 |
| 에서 디지털 파일 보내기 [!DNL Workfront] to [!DNL Assets] | 최신 버전의 WF 문서를 AEM Assets에 업로드하여 새로운 버전의 문서로 연결할 수 있습니다. | ✓ | ✓ | ✓ |
| 수동으로 AEM 폴더를 Workfront 개체에 연결 | 기존 AEM 폴더를 Workfront 폴더로 연결할 수 있으며 하위 자산이 새 Workfront 문서로 연결됩니다. | ✓ | ✓ | ✓ |
| 링크 [!DNL Assets] Workfront 개체 | AEM의 기존 자산은 새 Workfront 문서에 연결되거나 기존 문서의 새 버전으로 연결할 수 있습니다. | ✓ | ✓ | ✓ |
| 연결된 폴더에 추가된 자산은 자동으로 AEM으로 전송됩니다 | 문서가 연결된 폴더에 추가되면 연결된 자산이 자동으로 AEM Assets에 새 자산으로 업로드됩니다. | ✓ | ✓ | ✓ |
| Workfront 내에서 연결된 AEM Assets 다운로드 | 자산이 Workfront에 연결되어 있으면 사용자는 자산의 바이트를 다운로드할 수 있습니다. | ✓ | ✓ | ✓ |
| Workfront 내에서 AEM Assets 검색 | Workfront의 AEM Assets 선택기를 사용하면 자산을 전체 텍스트 검색으로 검색할 수 있습니다. | ✓ | ✓ | ✓ |
| Workfront 내에서 AEM 폴더 계층 구조 보기 및 탐색 | Workfront의 AEM Assets 선택기를 사용하면 AEM에 설정된 사용자의 연결된 액세스 제어 및 권한에 의해 제한된 AEM Assets 계층 구조를 검색할 수 있습니다. | ✓ | ✓ | ✓ |
| Workfront에서 AEM Assets에서 자산 연결 해제 | AEM의 기존 연결된 자산은 연결된 Workfront 문서에서 연결을 해제할 수 있습니다. 이렇게 해도 AEM 내의 원래 자산은 삭제되지 않습니다. | ✓ | ✓ | ✓ |
| Workfront에서 AEM Assets에 새로 버전이 지정된 자산 추가 | Workfront의 문서에 새로 추가된 버전이 추가되면 사용자는 새 버전을 AEM으로 보내 기존 버전을 바꿀 수 있습니다. | ✓ | ✓ | ✓ |
| AEM에 직접 사용자를 클릭할 때 Workfront에 연결된 자산 | 사용자는 Workfront 내에서 연결된 자산을 미리 보기 위해 AEM으로 이동됩니다. | ✓ | ✓ | 사용자 지정 |
| Workfront에서 연결된 AEM 폴더를 자동으로 만들기 | 개체 상태를 사용하여 Workfront에 연결된 AEM 폴더를 자동으로 만듭니다. Workfront Portfolio, 프로그램 및 프로젝트를 기반으로 AEM 폴더를 자동으로 구성합니다. | 아니오 | 아니오 | ✓ |
| 주석 동기화 | 다음에서 자산에 대한 주석을 자동으로 동기화 [!DNL Workfront] to [!DNL Assets] | 아니오 | ✓ | ✓ |
| AEM Assets에 Workfront 자산 메타데이터 매핑 | Workfront 개체 및 사용자 지정 양식 속성은 AEM 자산 메타데이터 속성에 매핑될 수 있습니다. 초기 업로드/링크 시 값이 푸시됩니다. | ✓ | ✓ | ✓ |
| Workfront에서 문서 사용자 지정 Forms 자동 만들기 | AEM 워크플로우를 사용하여 Workfront 문서, 작업 및 문제에 사용자 지정 양식을 첨부합니다. | 아니오 | 사용자 지정 양식을 수동으로 추가한 다음 자동 동기화가 작동합니다 | ✓ |
| AEM Assets과 Workfront 간 메타데이터의 양방향 자동 업데이트 | AEM Assets과 Workfront 간의 메타데이터를 자동으로 업데이트합니다. | 아니오 | ✓ | ✓ |
| AEM Assets 폴더에 Workfront 메타데이터 매핑 | Workfront 프로젝트 메타데이터를 연결된 AEM 폴더와 동기화합니다. | 아니오 | 아니오 | ✓ |
| 새 버전으로 AEM 메타데이터 업데이트 | AEM에서 구성을 수행하여 Workfront의 새로 버전이 지정된 자산도 메타데이터의 변경 사항을 사용하여 푸시하는지 여부를 결정할 수 있습니다. | 아니오 | 아니오 | ✓ |
| Workfront에서 사용자 지정 Forms 변경 시 AEM 메타데이터 자동 업데이트 | Workfront은 지정된 AEM 자산 메타데이터 속성이 문서 사용자 지정 양식에 매핑되도록 구성됩니다. 자산이 처음 연결되거나 자산이 업데이트되면 이러한 메타데이터 속성 값이 해당 Workfront 문서 사용자 지정 양식 필드에 복사됩니다. AEM에서 시작된 변경 사항이 Workfront에서 변경된 것처럼 AEM에서 다시 전송되지 않도록 주의해야 합니다. | 아니오 | ✓ | ✓ |
| 연결된 자산에 새 증명 버전 만들기 | Workfront에서 자산을 연결하면 증명을 자동으로 생성할 수 있습니다. | 아니오 | ✓ | 사용자 지정 |
| Workfront 개체에 상태 설정 | AEM 워크플로우를 사용하여 구성 가능한 조건을 기반으로 Workfront 개체 상태 설정 | 아니오 | 아니오 | ✓ |
| AEM 게시 환경 또는 Brand Portal에 자산 게시 | Workfront 사용자에게 연결된 자산을 AEM 게시 환경 또는 Brand Portal에 자동으로 게시할 수 있는 옵션을 제공합니다. | 아니오 | 아니오 | ✓ |
