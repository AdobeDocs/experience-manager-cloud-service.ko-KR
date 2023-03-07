---
title: Headless 설정
description: 이 빠른 시작 안내서를 통해 콘텐츠 모델, 콘텐츠 조각, GraphQL API와 같은 AEM as a Cloud Service의 강력한 Headless기능의 핵심을 배웁니다.
exl-id: 26c05122-5930-4b4e-91dd-287b7cc865ee
source-git-commit: d35b60810a1624390d3d9c82c2a364140ea37536
workflow-type: ht
source-wordcount: '287'
ht-degree: 100%

---

# Headless 설정 {#introduction}

다음은 AEM 및 Headless 기술에 이미 익숙한 사용자를 위해 AEM as a Cloud Service를 사용하여 5단계로 경험을 만들고 관리하고 전달하기 위한 간단한 경로입니다. 각 안내서는 이전 안내서를 기반으로 하므로 처음부터 끝까지 순서대로 살펴보는 것이 좋습니다

1. [구성 만들기](create-configuration.md)
1. [콘텐츠 조각 모델 만들기](create-content-model.md)
1. [Assets 폴더 만들기](create-assets-folder.md)
1. [콘텐츠 조각 만들기](create-content-fragment.md)
1. [API 요청 만들기](create-api-request.md)

>[!TIP]
>
>이 시작 안내서는 AEM 및 Headless 기술에 대한 지식이 있다고 가정합니다.
>
>AEM 또는 Headless를 처음 접하는 경우 Headless 설명서 여정에서 Headless와 AEM에서 지원하는 방식 모두에 대한 설명서와 AEM에서 Headless를 지원하는 방법에 대한 포괄적인 소개를 참조하십시오.
>
>* [Headless 개발자 여정](/help/journey-headless/developer/overview.md)
>* [Headless 콘텐츠 설계자 여정](/help/journey-headless/architect/overview.md)
>* [Headless 콘텐츠 작성 여정](/help/journey-headless/author/overview.md)
>* [Headless 번역 여정](/help/journey-headless/translation/overview.md).


## 대상자 {#audience}

설명된 작업은 AEM의 Headless 기능에 대한 기본적인 엔드투엔드 데모에 필요합니다. 테스트 AEM 인스턴스에 대한 관리자 액세스 권한이 있는 사람은 누구나 AEM의 Headless 게재를 이해하기 위해 이 안내서를 따를 수 있지만, 그중에서도 개발자 경험이 있는 사람이 이상적입니다.

그러나 프로덕션 상황에서는 여러 가상 사용자에 의해 여러 번 작업이 수행됩니다. 예:

* **관리자**&#x200B;는 콘텐츠에 대한 초기 구성 및 폴더 구조를 일반적으로 한 번만 또는 가끔 설정해야 합니다.
* **정보 설계자**&#x200B;는 일반적으로 조직의 요구 사항이 발전함에 따라 새로운 모델을 추가합니다.
* **콘텐츠 작성자**&#x200B;는 설계자가 정의한 모델을 기반으로 하는 콘텐츠 조각으로 새로운 콘텐츠를 지속적으로 생성합니다.

## 다음 단계 {#next-step}

자세히 알아볼 준비가 되셨습니까? 그렇다면 Headless 설정의 첫 번째 부분인 [구성 만들기](create-configuration.md)를 읽는 것에서부터 시작하십시오.
