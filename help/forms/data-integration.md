---
title: as a Cloud Service 데이터베이스를  [!DNL AEM Forms] 에 연결하는 방법
description: 적응형 양식 또는 AEM Workflow에서 RESTful 웹 서비스, SOAP 기반 웹 서비스 및 OData 서비스에 데이터를 검색하고 저장합니다.
feature: Adaptive Forms, Form Data Model
role: Admin, User
exl-id: 9d146275-de0a-4861-b060-d205ed6305f3
source-git-commit: 7b31a2ea016567979288c7a8e55ed5bf8dfc181d
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 3%

---

# 데이터베이스에 AEM Forms 연결 {#aem-forms-data-integration}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/data-integration.html) |
| AEM as a Cloud Service | 이 문서 |



![데이터 통합](do-not-localize/data-integeration.png)

엔터프라이즈 인프라스트럭처에는 데이터베이스, 웹 서비스, REST 서비스, OData 서비스 및 CRM 솔루션과 같은 다양한 백엔드 시스템 또는 데이터 소스가 포함됩니다. 이를 통합하여 엔터프라이즈 애플리케이션에 데이터를 제공하여 일상적인 업무를 수행하는 정보 시스템을 구축합니다. 반면에 애플리케이션은 데이터를 캡처하여 데이터 소스를 업데이트하기 위해 다시 전송합니다.

적응형 양식을 데이터베이스에 연결할 때 양식을 렌더링하는 동안 고객 데이터를 가져오기 위해 데이터 소스와의 통합이 필요합니다. 적응형 Forms의 사용자 입력을 기반으로 데이터 소스에서 데이터를 가져오는 사용 사례가 있습니다. 또한 적응형 양식을 데이터베이스로 보낼 때 제출된 적응형 양식 데이터를 다시 기록하여 각 데이터 소스를 업데이트할 수 있습니다.

분산형 모듈식 시스템에는 고유한 이점이 있지만 데이터 소스 간에 데이터 연관성을 통합하고 만드는 것이 과제입니다. 데이터 통합은 비즈니스 데이터 교환을 위해 애플리케이션에 연결된 서로 다른 데이터 소스를 사용하는 기능적이고 효율적인 엔터프라이즈 인프라의 핵심입니다.

## 데이터 통합 개요 {#data-integration-overview}

![aem-forms-data-integration](assets/aem-forms-data-integeration.png)

[!DNL AEM Forms] 데이터 통합을 통해 서로 다른 데이터 원본을 구성하고 [!DNL AEM Forms]에 연결할 수 있습니다. 연결된 데이터 소스 전반에 걸쳐 비즈니스 엔티티 및 서비스의 통합 데이터 표현 스키마를 생성할 수 있는 직관적인 사용자 인터페이스를 제공합니다. 통합 표현을 JSON 스키마의 확장인 양식 데이터 모델(FDM)이라고 합니다. FDM(양식 데이터 모델)의 엔티티를 데이터 모델 객체라고 합니다. FDM(양식 데이터 모델)을 사용하면 다음 작업을 수행할 수 있습니다.

* 연결된 데이터 소스에서 데이터 모델 개체, 속성 및 서비스에 액세스합니다.
* 사용자 지정 데이터 모델 개체 및 속성 만들기
* 데이터 소스 내 및 여러 데이터 모델 개체 간의 연결을 만듭니다.
* 데이터 모델 개체 서비스를 호출하여 데이터 소스에서 데이터를 쿼리하거나 씁니다.

양식 데이터 모델(FDM)을 생성했으면 이 모델을 사용하여 다음을 수행할 수 있습니다.

* 양식 데이터 모델(FDM)을 기반으로 적응형 Forms 만들기
* 구성된 데이터 소스에서 적응형 Forms 미리 채우기
* 적응형 양식 규칙을 사용하여 데이터 소스 서비스/작업 호출
* 제출된 적응형 양식 데이터를 데이터 소스에 쓰기

## 데이터 통합 시작 {#get-started-with-data-integration}

적응형 양식을 데이터베이스에 보내기 위한 데이터 통합을 구현하는 첫 번째 단계는 적응형 Forms에서 사용할 정보를 저장하는 데이터 소스를 식별하고 구성하는 것입니다. 그런 다음 하나 이상의 데이터 소스에서 데이터 모델 개체, 속성 및 서비스를 사용하는 양식 데이터 모델(FDM)을 만듭니다. 적응형 양식 필드가 각 데이터 소스 속성에 바인딩되는 FDM(양식 데이터 모델)을 기반으로 적응형 Forms을 생성할 수 있습니다.

또한 [!DNL AEM Forms]을(를) 사용하면 데이터 소스와 관계없이 양식 데이터 모델(FDM)을 만들고 나중에 양식 데이터 모델(FDM)의 데이터 모델 개체 및 속성을 데이터 소스와 연결하거나 바인딩할 수 있습니다. 양식 데이터 모델(FDM)을 작업하는 동안 데이터 소스에 대한 종속성을 제거합니다.

데이터 통합을 시작, 이해 및 구현하려면 다음 사항을 검토하십시오.

* [데이터 소스 구성](configure-data-sources.md)
* [양식 데이터 모델(FDM) 만들기](create-form-data-models.md)
* [양식 데이터 모델(FDM) 작업](work-with-form-data-model.md)
* [양식 데이터 모델(FDM) 사용](using-form-data-model.md)

>[!NOTE]
>
>[!UICONTROL Experience Manager Forms]은(는) 관계형 데이터베이스를 지원하지 않습니다.