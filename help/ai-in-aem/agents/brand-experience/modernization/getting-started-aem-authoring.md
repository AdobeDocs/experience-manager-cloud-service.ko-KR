---
title: AEM 제작 프로젝트용 Experience Modernation Agent 시작하기
description: Experience Modernation Console을 사용하여 Experience Modernation Agent를 시작할 때 AEM 작성 프로젝트에 필요한 특정 설정 단계에 대해 알아봅니다.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: 94a5e40b-af4a-42ed-922b-b1ec9bb82e24
source-git-commit: 81f85045212ca6fd92f2b665aeceaa0d4b92318c
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 1%

---

# AEM 제작 프로젝트용 Experience Modernation Agent 시작하기 {#getting-started-aem-authoring}

유니버설 편집기를 사용한 AEM 작성 프로젝트의 경우, 경험 현대화 에이전트의 준비는 표준 Edge Delivery 흐름과 다릅니다. 이 문서에서는 이러한 설정 차이점을 다룹니다. 아래 단계가 완료되면 기본 [Experience 현대화 에이전트 시작하기](getting-started.md) 안내서를 따르십시오.

## Edge Delivery Services 프로젝트 보고서 만들기 {#create-repo}

1. [`aem-block-collection-xwalk`](https://github.com/adobe-rnd/aem-block-collection-xwalk) 리포지토리를 템플릿으로 사용합니다(표준 Edge Delivery Services 표준 템플릿이 아님).
1. 저장소를 설정하려면 [유니버설 편집기 튜토리얼](https://www.aem.live/developer/ue-tutorial)을(를) 따르십시오.
   * AEM에서 사이트를 만들라는 메시지가 표시되면 중지합니다.
1. `paths.json`을(를) 삭제하고 이 변경 내용을 `main`에 커밋하세요.
1. [AEM 코드 커넥터](https://github.com/apps/aem-code-connector/installations/select_target) 앱을 리포지토리에 추가합니다.
   * 이렇게 하면 콘솔에서 코드를 검사할 수 있습니다.

## AEM에서 새 사이트 만들기 {#create-site}

1. AEM Sites 콘솔에서 **만들기** > **템플릿의 사이트**&#x200B;를 선택합니다.
1. Edge Delivery Services 템플릿을 사용하여 **AEM 사이트**&#x200B;를 선택하십시오.
   * 목록에 표시되지 않습니까? [템플릿을 설치합니다.](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases)
1. 제공된 대로 사이트의 **이름**(제목이 아님)을 유지합니다.
   * 사이트 이름은 고유 식별자로 사용됩니다.
   * 제목을 변경하여 표시할 수 있습니다.
1. **만들기**&#x200B;를 클릭합니다.
   * 사이트 페이지로 리디렉션됩니다.
   * 새 사이트가 즉시 표시되지 않는 경우 페이지를 새로 고칩니다.
1. [리포지토리를 설정할 때 아직 수행하지 않았다면](#create-repo)은(는) `fstab.yaml`을(를) 업데이트하여 AEM 호스트, git 소유자 및 git 리포지토리를 가리키도록 만들고 이러한 변경 내용을 `main`에 커밋합니다.
   * 지침은 [콘텐츠 원본 구성](/help/implementing/cloud-manager/edge-delivery/configure-content-source.md)을 참조하세요.

## 표준 시작 단계 계속 {#continue}

위의 단계가 완료되면 표준 시작 안내서를 계속 진행하여 콘텐츠 마이그레이션을 시작할 수 있습니다.

![콘텐츠 가져오기](assets/content-import.png)

표준 안내서에서 다음 단계를 수행합니다.

1. [Edge Delivery GitHub 저장소 준비](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#prepare-repo)
1. [Experience Modernation Console 열기](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#open-console)
1. [GitHub 저장소 연결](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#connect-repo)
1. [메시지 표시 시작](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md#start-prompting)

![콘텐트 가져옴](assets/content-imported-aem-authoring.png)

이러한 단계를 완료하여 콘텐츠를 마이그레이션한 후 다음 단계를 계속 진행합니다.

## 콘텐츠 유효성 검사 {#validate-content}

미리 보기 패널에서 선택한 페이지의 내용을 확인합니다. **오류** 단추를 클릭하면 모든 오류가 표시됩니다.
오류를 수정하려면 에이전트와 채팅 대화를 계속합니다. **채팅에 추가** 기능을 사용하여 페이지, 파서 파일 또는 변환기 파일의 특정 요소에 대한 수정 사항을 타깃팅합니다.

![상황에 맞는 채팅](assets/contextual-chat.png)

## 콘텐츠 업로드 {#upload-content}

콘텐츠를 AEM에 업로드하려면 다음 작업을 수행하십시오.

1. **콘텐츠** 보기에 있는지 확인하고 오른쪽 상단의 **콘텐츠 업로드** 단추를 클릭합니다.
1. **콘텐츠 패키지 만들기** 대화 상자에서 패키지에 포함할 페이지를 선택합니다.
   * 필요한 경우 **패키지 이름**&#x200B;을(를) 입력하십시오(비워 두면 기본적으로 사이트 이름으로 설정됨).
   * 목록을 관리하려면 **모두 선택**, **선택 지우기**, **모두 확장** 또는 **모두 축소**&#x200B;를 사용하세요.
1. **패키지 만들기**&#x200B;를 클릭합니다.

   ![콘텐츠 패키지 만들기 - 페이지 선택 및 만들기](assets/content-package.png)

1. 패키지를 만든 후 **콘텐츠 패키지 업로드** 대화 상자에 패키지가 준비되었음을 표시합니다.
   1. 로컬에 저장하려면 **패키지를 다운로드**&#x200B;하거나 업로드를 계속할 수 있습니다.
   1. **AEM에 업로드**&#x200B;에서 **AEM 사이트** 및 **AEM 호스트**(프로젝트 설정에서 미리 채워짐)를 확인합니다.
      * 필요한 경우 **이미지 업로드**&#x200B;를 선택된 상태로 두어 이미지를 포함합니다.
   1. **AEM에 업로드**&#x200B;를 클릭합니다.

   ![패키지를 AEM에 업로드하거나 다운로드할 준비가 되었습니다](assets/upload-package-start.png)

1. 이 대화 상자는 페이지 및 에셋이 AEM으로 전송될 때의 업로드 진행 상황을 보여줍니다. 업로드가 완료되면 성공 메시지와 업로드 로그가 표시됩니다. 대화 상자를 닫으려면 **닫기**&#x200B;를 클릭하십시오.

   ![AEM의 업로드 진행 상황 및 완료](assets/upload-package-complete.png)

가져온 콘텐츠는 이제 AEM에 있습니다. 기본 시작 안내서에서 [푸시 코드 변경](getting-started.md#push-code-changes)을 계속합니다.

## 추가 리소스 {#additional-resources}

* [Experience 현대화 에이전트 시작](getting-started.md) - 콘솔, 확인, 업로드 및 미리 보기를 포함한 전체 워크플로
* [경험 현대화 콘솔](console.md) - 콘솔 참조
* [유니버설 편집기 튜토리얼](https://www.aem.live/developer/ue-tutorial) - AEM 제작 및 유니버설 편집기 프로젝트 설정
* [`aem-block-collection-xwalk`](https://github.com/adobe-rnd/aem-block-collection-xwalk) - AEM 작성 및 유니버설 편집기 프로젝트의 템플릿 리포지토리
