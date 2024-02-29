---
description: 이 자습서에는 양식 섹션을 반복 가능하게 만드는 지침이 포함되어 있습니다
title: Edge Delivery Services에서 반복 가능한 섹션
feature: Edge Delivery Services
source-git-commit: 3b24d0cd4099e0b8eb48c977f460b25c168af220
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 1%

---


# Edge 게재에서 반복 가능한 섹션

반복 가능 섹션은 동일한 데이터가 여러 번 발생하는 경우 정보를 수집하기 위해 중복 또는 여러 번 복제되는 양식의 구성 요소입니다.

예를 들어 대출을 신청하는 사용자로부터 정보를 수집하는 데 사용되는 양식을 생각해 보자. 양식은 공동 대출자의 세부 사항을 포함한 개인 정보를 사용자가 제공할 수 있도록 한다. 사용자는 공동 지원자에 대한 상세내역을 입력할 수 있으며, 이 섹션은 반복 가능합니다.

![양식의 반복 가능한 섹션](/help/forms/assets/eds-repeatable.png)

## 사전 요구 사항

AEM Boilerplate를 사용하여 EDS(Edge Delivery Service) Github 프로젝트를 설정하고 로컬 컴퓨터에서 해당 Github 저장소를 복제합니다. 자세한 내용은 [개발자 튜토리얼](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/build/tutorial.html)을 참조하십시오.

## Edge 게재에서 반복 가능한 섹션

대출 신청서 양식을 예로 들어 보겠습니다. 이 양식을 통해 사용자는 개인 정보를 제출할 수 있습니다. 반복 가능한 섹션을 사용하여 최소 및 최대 3개의 공동 지원자 섹션을 추가하는 옵션과 함께 공동 지원자 세부 정보를 포함할 수 있습니다.

>[!NOTE]
>
> * SharePoint 사이트 또는 Google 드라이브에서 Microsoft Excel을 작성하여 양식에서 필드 세트를 반복 가능하게 할 수 있습니다.
> * 이 경우 Microsoft SharePoint의 예를 살펴보겠습니다. SharePoint 폴더를 컨텐츠 소스로 만들려면에 설명된 단계를 수행합니다 [Sharepoint 사용 방법](https://www.aem.live/docs/setup-customer-sharepoint).


Edge 게재에서 반복 가능한 섹션을 추가하려면:

1. [Microsoft Excel을 사용하여 양식 작성](#author-form)
2. [양식 미리 보기 및 게시](#preview-form)

### Microsoft Excel을 사용하여 양식 작성 {#author-form}

1. Microsoft SharePoint 계정으로 이동하여 AEM Edge 게재 프로젝트 디렉터리를 열거나 만듭니다.
2. 기존 Microsoft Excel 파일을 열거나 새로 만듭니다.
이 예제에서는 이름이 인 Excel 시트를 사용합니다 `loan-application.xlsx` 이(가) Microsoft SharePoint 사이트에서 만들어졌습니다.
3. 다음 레이블이 지정된 새 열 추가 `Repeatable`, `Min`, 및 `Max` Microsoft Excel 파일에서
4. 다음에 대한 값 지정 `Repeatable` 열 형식 `True` 반복 가능하게 만들 필드 집합용입니다.
5. 다음에 대한 값을 지정합니다. `Min` 및 `Max` 열. 다음 `Min` 값은 패널이 반복되는 최소 발생 횟수를 나타내는 반면 `Max` 값은 패널이 반복되는 최대 발생 횟수를 나타냅니다.
6. Microsoft Excel 파일을 저장합니다.

>[!NOTE]
>
> 다음 [대출 신청](/help/forms/assets/loan-application.xlsx) 참조용 excel 시트.

### Edge 게재 서비스를 사용하여 양식 미리보기/게시

1. Microsoft SharePoint 사이트에서 새 문서 파일을 열거나 만들어 를 사용하여 Excel 시트를 사이트에 포함 `Form Block`. 예를 들어 `index` 파일 및 추가 `Form Block`.
2. 명령 프롬프트를 열고 로컬 컴퓨터의 AEM Edge 게재 프로젝트 디렉터리로 이동한 다음 다음과 같이 명령을 실행합니다. `aem up`.

양식에서 액세스할 수 있습니다. `https://localhost:3000`, 여기서 `Add` 버튼은 공동 지원자 세부 정보 입력을 위한 새로운 반복 가능 섹션을 추가합니다. 다음을 클릭하여 반복 가능 섹션을 삭제할 수도 있습니다. `Delete` 단추를 클릭합니다.

>[!NOTE]
>
> localhost에서 양식에 액세스하는 동안 &quot;페이지를 찾을 수 없음&quot; 오류가 발생하면 양식이 있는 URL 앞에 Microsoft SharePoint 사이트의 디렉터리 이름을 추가하십시오. 예, `http://localhost:3000/<dir-name>/`




