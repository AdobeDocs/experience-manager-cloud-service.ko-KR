---
title: 미리보기 또는 게시 인스턴스에 양식을 게시하거나 게시 취소하는 방법
description: AEM 작성 환경에서 양식을 게시 또는 게시 취소하여 인스턴스를 미리 보거나 게시하는 방법에 대해 알아봅니다. 스테이징 환경에서 양식을 테스트하든, 최종 사용자를 위해 라이브로 배포하든 상관없이 AEM에서는 이 프로세스를 효율적으로 관리할 수 있는 간소화된 도구를 제공합니다.
Keywords: 6.5 forms to cloud service, 6.5 forms to cs, manage publication, , AEM Forms 6.5 to Cloud Service, AEM form migration to cloud service, Forms Manage publication, AF Manage publication, Adaptive Forms Manage publication, Cloud Manage publication
contentOwner: khsingh
feature: Adaptive Forms
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
role: User, Developer
level: Intermediate
source-git-commit: 242dcbc5bb541dfac601454fb75dec3bdff1ea64
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 0%

---


# Experience Manager Forms&#x200B;에서 게시 관리

Adobe Experience Manager Forms 관리자는 작성자 인스턴스의 양식을 Experience Manager Forms에 게시할 수 있습니다. 나중에 양식 또는 폴더를 게시하도록 예약할 수 있습니다. 게시되면 사용자는 양식에 액세스하고 양식을 채울 수 있습니다.

Experience Manager Forms 인터페이스에서 사용 가능한 Publish 또는 게시 관리 옵션을 사용하여 양식을 게시하거나 게시 취소할 수 있습니다. Experience Manager Forms에서 원래 양식 또는 폴더를 추가로 수정하는 경우 Experience Manager Forms에서 다시 게시하기 전까지는 변경 사항이 게시 인스턴스에 반영되지 않습니다. 진행 중인 작업 변경 사항을 게시 인스턴스에서 사용할 수 없도록 합니다. 관리자가 게시한 변경 사항만 게시 인스턴스에서 사용할 수 있습니다.

## Publish 옵션을 사용한 Publish forms

게시 옵션을 사용하면 양식을 즉시 게시할 수 있습니다. Experience Manager Forms 콘솔에서 상위 폴더로 이동하여 게시할 양식을 선택합니다. 도구 모음에서 Publish 옵션을 클릭하고 양식과 함께 게시될 모든 참조 자산을 확인한 다음 Publish을 클릭합니다.

컴퓨터의 스크린샷

설명이 자동으로 생성됨

## 게시 관리를 사용하여 Publish 또는 양식 게시 취소


게시 관리를 사용하면 선택한 대상에 콘텐츠를 게시하거나 게시를 취소하고, 양식 및 문서 폴더의 게시 목록에 콘텐츠를 추가하고, 게시할 참조를 선택하고, 나중에 게시할 날짜 또는 시간에 게시를 예약할 수 있습니다.


Experience Manager Forms 콘솔에서 상위 폴더로 이동하여 게시할 양식을 선택합니다. 도구 모음에서 게시 관리 옵션을 클릭합니다.


컴퓨터의 스크린샷

설명이 자동으로 생성됨



게시 관리 인터페이스에서 다음 옵션을 사용할 수 있습니다.

* 액션

   * Publish: 선택한 대상에 Publish forms 추가
   * 게시 취소: 대상에서 양식 게시 취소

* 대상

   * Publish: Publish forms에서 Experience Manager Forms (AEM) Publish 인스턴스로 이동합니다.
   * 미리 보기: Publish forms에서 Experience Manager Forms(AEM) 미리 보기 인스턴스.

* 예약 중

   * 지금: Publish forms 즉시
   * 나중에: 활성화 날짜 또는 시간을 기반으로 하는 Publish 양식



계속하려면 **다음**&#x200B;을 클릭하세요. 범위 탭에서 콘텐츠 추가 옵션을 사용하여 게시할 콘텐츠를 더 추가합니다. 예를 들어 Forms 또는 기록 문서 파일을 더 추가할 수 있습니다.

### 콘텐츠 추가

Experience Manager Forms에 게시하면 게시 목록에 더 많은 컨텐츠(양식, 에셋 및 폴더)를 추가할 수 있습니다. formsanddocuments 폴더에서 목록에 양식, 에셋 또는 폴더를 추가할 수 있습니다. 그러나 한 번에 여러 폴더에서 에셋을 추가할 수는 없습니다.

컴퓨터의 스크린샷

설명이 자동으로 생성됨

콘텐츠를 추가하려면 **콘텐츠 추가** 단추를 클릭하십시오. 폴더에서 여러 자산을 추가하거나 한 번에 여러 폴더를 추가할 수 있습니다. 그러나 한 번에 여러 폴더에서 에셋을 추가할 수는 없습니다.

양식 또는 기타 에셋에 대해 게시하거나 게시하지 않도록 참조를 구성하려면 양식 또는 에셋을 선택하고 게시된 참조 를 클릭합니다.

컴퓨터의 스크린샷

설명이 자동으로 생성됨

게시된 참조 대화 상자에서 게시하지 않을 에셋의 선택을 취소하고 완료를 클릭합니다.


컴퓨터의 스크린샷

설명이 자동으로 생성됨


## Publish 또는 나중에 양식 게시 취소


나중에 게시 또는 게시 취소 옵션을 사용하면 나중에 양식을 게시하거나 게시 취소할 수 있을 뿐만 아니라 워크플로우를 구성할 수도 있습니다. 워크플로가 완료되면 양식이 게시되거나 게시 취소됩니다. 양식을 게시하거나 게시 취소하도록 예약하려면 다음 작업을 수행하십시오.

1. Experience Manager Forms 콘솔에서 상위 폴더로 이동하고 게시 일정을 예약하려는 양식을 선택합니다.
1. 도구 모음에서 게시 관리 옵션을 클릭합니다.
1. Publish 또는 작업에서 게시 취소 를 클릭한 다음 콘텐츠를 게시하거나 게시 취소할 대상을 선택합니다.

   * 미리보기: 미리보기 옵션을 사용하여 Experience Manager Forms 미리보기 환경에 게시하거나 게시 취소합니다. Experience Manager Forms 미리보기 환경은 개발 양식에서 테스트하는 데 사용됩니다.
   * Publish: Experience Manager Forms Publish 옵션을 사용하여 양식을 프로덕션 환경에서 사용할 준비가 되면 Experience Manager Forms 게시 환경으로 보냅니다.


1. 예약에서 나중에 를 선택합니다.

1. 활성화 날짜 를 선택하고 날짜 및 시간을 지정합니다. 다음 을 클릭합니다.

   컴퓨터의 스크린샷

   설명이 자동으로 생성됨

1. 범위 탭에서 컨텐츠를 추가합니다(필요한 경우). 다음 을 클릭합니다.

   컴퓨터의 스크린샷

   설명이 자동으로 생성됨

1, (선택 사항) 워크플로우 탭에서 워크플로우 제목을 지정합니다. 나중에 Publish 를 클릭합니다.

컴퓨터의 스크린샷

설명이 자동으로 생성됨

## 게시 상태 확인

게시 상태를 확인하는 방법에는 여러 가지가 있습니다.

* 대상 인스턴스에 로그인하여 게시된 양식 및 기타 에셋을 확인합니다(예약된 날짜 또는 시간에 따라 다름).

* 타임라인 보기를 사용하여 게시 상태를 확인합니다.

* 적응형 Forms 편집기에서 페이지 정보 메뉴를 사용합니다.