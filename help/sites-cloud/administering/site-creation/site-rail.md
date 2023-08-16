---
title: 사이트 레일을 사용하여 사이트 테마 관리
description: 사이트 테마를 손쉽게 맞춤화하고 관리하는 데 도움이 되는 사이트 레일의 강력한 기능에 대해 알아봅니다.
feature: Administering
role: Admin
exl-id: 45785e5a-4fa2-4cf2-a300-f1865f6f5807
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 97%

---

# 사이트 레일을 사용하여 사이트 테마 관리 {#site-rail}

사이트 테마를 손쉽게 맞춤화하고 관리하는 데 도움이 되는 사이트 레일의 강력한 기능에 대해 알아봅니다.

## 개요 {#overview}

사이트 레일을 사용하면 사이트의 테마 및 템플릿 리소스를 관리할 수 있습니다. 콘텐츠 트리, 참조 또는 타임라인 레일 등의 [다른 레일과 같이](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector), 사이트 레일은 사이트 콘솔의 맨 왼쪽 패널에 나타나며 선택한 항목에 대한 정보를 표시합니다. 그러나 다른 레일과 달리 사이트 레일은 사이트 루트에만 적용됩니다.

사이트 레일을 사용하여 다음을 포함한 사이트의 테마 및 템플릿 관련 정보를 관리할 수 있습니다.

* [테마 소스 다운로드](#downloading-theme-sources)
* [와이어프레임과 같은 템플릿 리소스 다운로드](#downloading-template-resources)
* [테마 버전 보기 및 변경](#theme-vrsions)
* [프론트엔드 파이프라인 활성화](#enabling-the-front-end-pipeline)

>[!TIP]
>
>사이트 테마를 손쉽게 맞춤화할 수 있는 빠른 사이트 생성 도구 및 프론트엔드 파이프라인에 대해 알아보려면 [빠른 사이트 생성 여정](/help/journey-sites/quick-site/overview.md)을 검토하십시오.

## 테마 소스 다운로드 {#downloading-theme-sources}

[사이트 테마](site-templates.md)를 기반으로 AEM 사이트를 만들 때 사이트 레일을 사용하여 [사이트 테마](site-themes.md)를 다운로드할 수 있습니다.

사이트 콘솔에 표시되는 사이트 레일을 사용하여 사이트 루트를 선택해 사이트에 대한 테마 정보를 표시합니다.

![테마 소스 다운로드](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

**테마 소스 다운로드**&#x200B;를 탭하거나 클릭하여 맞춤화 목적으로 사이트 테마의 로컬 사본을 `.zip` 파일로 다운로드합니다.

## 템플릿 리소스 다운로드 {#downloading-template-resources}

[사이트 템플릿](site-templates.md)에는 사이트 콘텐츠 구조 및 [사이트 테마 외에도 다른 정보가 포함될 수 있습니다.](site-themes.md) 사이트 템플릿에는 와이어프레임 디자인 또는 기타 사이트 관련 파일 등이 포함될 수 있습니다.

사이트가 사이트 템플릿을 기반으로 하는 경우 사이트 콘솔에 표시되는 사이트 레일을 사용하여 사이트 루트를 선택해 추가 사이트 리소스를 포함하여 사이트에 대한 테마 정보를 표시할 수 있습니다.

![테마 소스 다운로드](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

**추가 템플릿 리소스 다운로드**&#x200B;라는 제목 아래의 버튼을 탭하거나 클릭하여 사용할 수 있는 파일의 로컬 사본을 다운로드합니다.

## 테마 버전 보기 및 변경 {#them-versions}

사이트가 사이트 템플릿을 기반으로 하는 경우 해당 테마는 이미 프론트엔드 개발자에 의해 맞춤화되었을 수 있습니다. 사이트 레일을 사용하여 현재 배포되고 있는 사이트 테마 버전을 확인하고 이전 버전으로 전환할 수 있습니다.

사이트 콘솔에 표시되는 사이트 레일을 사용하여 사이트 루트를 선택해 사이트에 대한 테마 정보를 표시합니다.

![레일의 사이트 버전](/help/sites-cloud/administering/assets/theme-versions.png)

현재 테마 버전이 마지막 업데이트의 타임스탬프가 포함된 커밋 해시와 함께 표시됩니다.

**버전 선택**&#x200B;을 탭하거나 클릭하여 이전 테마 버전을 조회합니다.

![테마 버전 선택](/help/sites-cloud/administering/assets/select-theme-versions.png)

변경하고자 하는 버전을 탭하거나 클릭한 다음 **적용**&#x200B;을 탭하거나 클릭하여 변경 내용을 적용합니다.

AEM에서 새 테마 버전이 프론트엔드 파이프라인을 통해 배포되었지만 사이트에 적용되지 않았음을 감지하면 알림 아이콘이 표시됩니다.

![새 테마 버전 표시기](/help/sites-cloud/administering/assets/new-theme-version.png)

**버전 선택** 버튼을 사용하여 새 테마 버전으로 업데이트할 수 있습니다.

## 프론트엔드 파이프라인 활성화 {#enabling-front-end-pipeline}

사이트가 사이트 템플릿을 사용하여 생성되지 않은 경우 프론트엔드 파이프라인을 사용하여 해당 테마를 맞춤화하고 배포할 수 없습니다.

그러나 사이트 레일을 사용하여 사이트에 대해 프론트엔드 파이프라인을 활성화할 수 있습니다.

사이트 콘솔에 표시되는 사이트 레일을 사용하여 사이트 루트를 선택해 사이트에 대한 테마 정보를 표시한 다음 **프론트엔드 파이프라인 활성화**&#x200B;를 탭하거나 클릭합니다.

![프론트엔드 파이프라인 활성화](/help/sites-cloud/administering/assets/enable-fep.png)

자세한 내용은 [프론트엔드 파이프라인 활성화](enable-front-end-pipeline.md) 문서를 참조하십시오.
