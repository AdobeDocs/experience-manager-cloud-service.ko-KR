---
title: 다양한 데이터 옵션을 사용하여 대화형 통신 편집기에서 PDF 미리 보기
description: 다양한 데이터 옵션을 사용하여 대화형 통신 편집기에서 PDF 미리 보기를 사용하면 세 가지 방식으로 대화형 통신을 미리 볼 수 있습니다.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: f772a193cce35a1054f5c6671557a6ec511671a9
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 13%

---


# 대화형 통신 편집기에서 PDF 미리 보기

>[!NOTE]
>
> 대화형 통신 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 액세스 권한을 요청하려면 회사 이메일 주소를 통해 `aem-forms-ea@adobe.com`으로 이메일을 보내시기 바랍니다.

>[!IMPORTANT]
>
> **변경될 수 있는 설명서**: 이 프롬프트 라이브러리는 현재 제품과의 일치 여부를 테스트 중이며 업데이트 및 개정이 이루어질 수 있습니다. 얼리 어답터 프로그램이 진행되는 동안 Forms Experience Builder가 계속 발전함에 따라 프롬프트. 예시 및 모범 사례가 변경될 수 있습니다.

PDF 미리보기 기능을 사용하면 데이터 없이, 로컬 JSON 기반 데이터를 사용하여 또는 구성된 데이터 모델의 샘플 데이터를 사용하여 세 가지 방법으로 대화형 커뮤니케이션을 미리 볼 수 있습니다.

## 주요 이점

- 샘플 데이터가 포함된 대화형 커뮤니케이션을 미리 확인하여 커뮤니케이션과 병합될 때 라이브 데이터가 표시되는 방식을 시각화합니다.

- 로컬 JSON 데이터 파일을 업로드하여 백엔드 설정 없이 데이터 기반 미리보기를 생성합니다.

- 연결된 양식 데이터 모델(FDM)을 사용하여 디자인 중에 샘플 데이터와의 실시간 데이터 통합을 시뮬레이션합니다.

- 데이터 옵션(데이터 없음, 로컬 데이터, FDM) 간을 쉽게 전환하여 레이아웃, 구조 및 개인화의 유효성을 검사합니다.

## 다양한 데이터 옵션을 사용하여 대화형 통신 편집기에서 PDF 미리 보기

유연한 테스트 및 유효성 검사를 위해 구성된 데이터 모델의 데이터, 로컬 데이터 또는 샘플 데이터를 사용하지 않고 대화형 커뮤니케이션을 미리 봅니다.

+++&#x200B;1. 데이터가 없는 미리 보기.

1.1. IC 편집기에서 대화형 통신을 엽니다.

1.2. PDF 미리 보기 옵션을 사용하고 **데이터 없음** 옵션을 선택하여 데이터가 없는 통신을 봅니다.

![IC 문서 찾기](/help/forms/interactive-communication/assets/nodata.png)

+++

+++&#x200B;2. 로컬 JSON 데이터로 미리 보기

2.1. 구조화된 JSON 파일을 준비합니다. 참조용으로 통신에 사용되는 JSON 스키마 [(FDM)](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/work-with-form-data-model)에서 샘플 데이터를 복사할 수 있습니다.

2.2. IC 편집기에서 **PDF 미리 보기** > 로컬 데이터 사용으로 이동합니다.

2.3. JSON 파일을 선택하고 업로드하여 제공된 데이터로 PDF 미리 보기를 렌더링합니다.

![IC 문서 찾기](/help/forms/interactive-communication/assets/localdata.png)

+++

+++&#x200B;3. 데이터 모델로 미리 보기 

3.1. 이미 구성된 IC의 양식 데이터 모델(FDM)에서 샘플 데이터를 사용하려면 **데이터 모델 사용**&#x200B;을 선택합니다.

3.2. 미리보기는 모델 필드의 데이터를 자동으로 채웁니다. 샘플 데이터를 처음 사용할 때 FDM에 저장해야 합니다. 그렇지 않으면 미리 보기가 데이터 없음으로 표시될 수 있습니다.

![IC 문서 찾기](/help/forms/interactive-communication/assets/datamodel.png)

+++

