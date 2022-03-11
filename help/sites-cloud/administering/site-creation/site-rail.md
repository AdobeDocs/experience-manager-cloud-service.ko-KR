---
title: 사이트 레일을 사용하여 사이트 테마 관리
description: 사이트 테마를 쉽게 사용자 지정하고 관리하는 데 도움이 되는 사이트 레일의 강력한 기능을 알아봅니다.
feature: Administering
role: Admin
exl-id: 45785e5a-4fa2-4cf2-a300-f1865f6f5807
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# 사이트 레일을 사용하여 사이트 테마 관리 {#site-rail}

사이트 테마를 쉽게 사용자 지정하고 관리하는 데 도움이 되는 사이트 레일의 강력한 기능을 알아봅니다.

## 개요 {#overview}

사이트 레일을 사용하면 사이트의 테마 및 템플릿 리소스를 관리할 수 있습니다. [다른 레일과 마찬가지로](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector) 컨텐츠 트리, 참조 또는 타임라인 레일과 같이, 사이트 레일은 사이트 콘솔에서 가장 왼쪽 패널로 표시되고 선택한 항목에 대한 정보가 표시됩니다. 다른 레일과 달리 사이트 레일은 사이트 루트에만 적용됩니다.

사이트 레일은 다음과 같은 사이트의 테마 및 템플릿 관련 정보를 관리하는 데 사용됩니다.

* [테마 소스 다운로드](#downloading-theme-sources)
* [와이어프레임과 같은 템플릿 리소스 다운로드](#downloading-template-resources)
* [테마 버전 보기 및 변경](#theme-vrsions)
* [프런트엔드 파이프라인 활성화](#enabling-the-front-end-pipeline)

>[!TIP]
>
>를 검토합니다. [빠른 사이트 만들기 여정](/help/journey-sites/quick-site/overview.md) 빠른 사이트 생성 도구 및 프런트 엔드 파이프라인에 익숙해져 사이트 테마를 쉽게 사용자 지정할 수 있습니다.

##  테마 소스 다운로드 {#downloading-theme-sources}

AEM에서 을 기반으로 사이트를 만들 때 [사이트 템플릿,](site-templates.md) 다음 파일을 다운로드할 수 있습니다. [사이트 테마](site-themes.md) 사이트 레일 사용.

사이트 콘솔에 사이트 레일이 표시되면 사이트의 루트를 선택하여 사이트에 대한 테마 정보를 표시합니다.

![테마 소스 다운로드](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

탭 또는 클릭 **테마 소스 다운로드** 사이트 테마의 로컬 복사본을 `.zip` 사용자 지정을 위한 파일입니다.

##  템플릿 리소스 다운로드 {#downloading-template-resources}

[사이트 템플릿](site-templates.md) 에는 사이트 컨텐츠 구조 및 [사이트 테마.](site-themes.md) 사이트 템플릿에는 와이어프레임 디자인 또는 기타 사이트 관련 파일이 포함될 수 있습니다.

사이트가 사이트 템플릿을 기반으로 하는 경우 사이트 콘솔에 사이트 레일이 표시되어 있는 경우 사이트의 루트를 선택하여 추가 사이트 리소스를 포함하여 사이트에 대한 테마 정보를 표시합니다.

![테마 소스 다운로드](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

제목 아래 단추나 단추를 탭하거나 클릭합니다 **추가 템플릿 리소스 다운로드** 사용 가능한 파일의 로컬 복사본을 다운로드하려면 다음을 수행하십시오.

## 테마 버전 보기 및 변경 {#them-versions}

사이트가 사이트 템플릿을 기반으로 하는 경우 프런트 엔드 개발자가 해당 테마를 이미 사용자 지정했을 수 있습니다. 사이트 레일을 사용하면 현재 배포되는 사이트 테마 버전을 보고 이전 버전으로 전환할 수 있습니다.

사이트 콘솔에 사이트 레일이 표시되면 사이트의 루트를 선택하여 사이트에 대한 테마 정보를 표시합니다.

![레일의 사이트 버전](/help/sites-cloud/administering/assets/theme-versions.png)

테마의 현재 버전이 마지막 업데이트 타임스탬프와 함께 커밋 해시와 함께 표시됩니다.

을(를) 탭하거나 클릭합니다 **버전 선택** 이전 버전의 테마를 보려면

![테마 버전 선택](/help/sites-cloud/administering/assets/select-theme-versions.png)

변경할 버전을 탭하거나 클릭한 다음, 을 탭하거나 클릭합니다 **적용** 을 클릭하여 변경합니다.

AEM에서 테마의 최신 버전이 프런트 엔드 파이프라인을 통해 배포되었지만 사이트에 적용되지 않았음을 감지하면 알림 아이콘이 표시됩니다.

![최신 버전의 테마 표시기](/help/sites-cloud/administering/assets/new-theme-version.png)

를 사용할 수 있습니다 **버전 선택** 새 테마 버전으로 업데이트하는 단추입니다.

## 프런트엔드 파이프라인 활성화 {#enabling-front-end-pipeline}

사이트 템플릿을 사용하여 사이트를 만들지 않은 경우 프런트 엔드 파이프라인을 사용하여 테마를 사용자 지정하고 배포할 수 없습니다.

하지만 사이트 레일을 사용하여 사이트에 대한 프런트엔드 파이프라인을 활성화할 수 있습니다.

사이트 콘솔에 사이트 레일이 표시되면 사이트의 루트를 선택하여 사이트에 대한 테마 정보를 표시한 다음 를 탭하거나 클릭합니다 **프런트엔드 파이프라인 활성화**.

![프런트엔드 파이프라인 활성화](/help/sites-cloud/administering/assets/enable-fep.png)

자세한 내용은 문서를 참조하십시오 [프런트엔드 파이프라인 활성화.](enable-front-end-pipeline.md)
