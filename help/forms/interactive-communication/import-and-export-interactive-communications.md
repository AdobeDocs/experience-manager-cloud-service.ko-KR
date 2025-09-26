---
title: 대화형 통신 가져오기 및 내보내기
description: 대화형 통신 가져오기 및 내보내기를 통해 사용자는 여러 환경의 통신을 원활하게 마이그레이션, 재사용 및 관리할 수 있습니다.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
index: false
hidefromtoc: true
source-git-commit: f772a193cce35a1054f5c6671557a6ec511671a9
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 14%

---


# 대화형 통신 가져오기 및 내보내기

>[!NOTE]
>
> 대화형 통신 기능은 얼리어답터 프로그램에서 사용할 수 있습니다. 액세스 권한을 요청하려면 회사 이메일 주소를 통해 `aem-forms-ea@adobe.com`으로 이메일을 보내시기 바랍니다.

>[!IMPORTANT]
>
> **변경될 수 있는 설명서**: 이 프롬프트 라이브러리는 현재 제품과의 일치 여부를 테스트 중이며 업데이트 및 개정이 이루어질 수 있습니다. 얼리 어답터 프로그램이 진행되는 동안 Forms Experience Builder가 계속 발전함에 따라 프롬프트. 예시 및 모범 사례가 변경될 수 있습니다.

대화형 통신(IC)의 가져오기 및 내보내기 기능을 사용하면 여러 환경에서 커뮤니케이션을 원활하게 마이그레이션, 재사용 및 관리할 수 있습니다. IC(대화형 통신)를 관련 조각 및 데이터 모델과 함께 한 환경에서 내보낸 다음 다른 환경으로 가져와 일관성을 보장하고 배포 중에 작업이 중복되지 않도록 할 수 있습니다.

## 주요 이점

- 여러 환경에서 IC를 간편하게 마이그레이션
- 조각, 데이터 모델 및 종속성을 유지합니다.
- 프로젝트 간 IC를 다시 만드는 데 드는 노력을 줄입니다.

## 대화형 통신 가져오기 및 내보내기

한 환경에서 대화형 통신(IC)을 만들고 아래 단계를 수행하여 IC를 내보내고 가져와서 다른 환경에서 재사용합니다.

+++&#x200B;1. 대화형 통신을 내보내는 방법

1.1. [만든 대화형 통신](https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/forms/interactive-communication/create-interactive-communication)&#x200B;(IC)을 선택합니다.
1.2. **다운로드** 옵션을 클릭하여 ZIP 파일로 내보냅니다.
1.3. 다운로드한 ZIP 파일에는 선택한 **템플릿**, **조각** 및 **데이터 모델**&#x200B;과 함께 IC가 포함되어 있습니다.

![IC 문서 찾기](/help/forms/interactive-communication/assets/downloadic.png)
+++

+++&#x200B;2. 대화형 통신을 가져오는 방법

2.1. 타겟 환경으로 이동합니다.
2.2. **Forms > Forms 및 문서 > 만들기 > 파일 업로드**(으)로 이동합니다.
2.3. ZIP 파일을 IC의 **가져오기**&#x200B;에 업로드합니다.

![IC 문서 찾기](/help/forms/interactive-communication/assets/uploadfile.png)

2.4. 업로드 후 IC가 관련 조각 및 데이터 모델과 함께 나타납니다.

![IC 문서 찾기](/help/forms/interactive-communication/assets/importfragment.png)
+++

+++&#x200B;3. 단편 가져오기 및 내보내기

3.1. 내보내려면 **Forms > Forms 및 문서**&#x200B;에서 필요한 조각을 선택한 다음 **다운로드**&#x200B;를 클릭하여 ZIP 파일로 내보냅니다.

3.2. 가져오려면 대상 환경으로 이동하여 Forms > Forms 및 문서 > 만들기 > **파일 업로드**&#x200B;로 이동한 다음 내보낸 ZIP 파일을 업로드합니다.

이를 통해 다양한 환경에서 조각을 손쉽게 재사용할 수 있으므로 설계의 일관성을 보장하고 작업의 중복을 줄일 수 있습니다.
+++
