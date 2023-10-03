---
title: 기록 문서 템플릿을 만들기 위해 Forms Designer를 다운로드하고 설치하는 방법
description: 기록 문서의 템플릿 역할을 하는 XDP 및 PDF 양식 템플릿을 만들려면 Forms Designer를 사용하십시오.
keywords: Designer 설치, Forms designer 설치, Forms Designer 설치를 위한 요구 사항
exl-id: d6f1cb21-c48b-406d-8d47-482d7a1b4cc3
source-git-commit: defeee2fee42c6274c71438d6f9fde6e49a05081
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 9%

---

# Forms Designer 다운로드 및 설치 {#installing-and-configuring-designer}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM as a Cloud Service | 이 문서 |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/jee-installation/installing-configuring-designer.html) |

디자이너는 XDP 및 PDF 양식 템플릿 작성을 간소화하는 포인트 앤 클릭 그래픽 양식 디자인 도구입니다. 양식 템플릿을 디자인하고 해당 논리를 정의하며 엄격한 법적 요구 사항을 충족할 수 있습니다. XDP 및 PDF 양식은 적응형 양식에서 기록 문서 템플릿 역할을 합니다. 이러한 양식 템플릿은 다음과 다릅니다. [적응형 양식 템플릿](template-editor.md).

## 전제 조건 {#pre-requisites}

최신 버전의 AEM Forms Designer 64비트 또는 32비트를 설치하려면 Designer를 설치하고 구성할 다음 소프트웨어와 최소 하드웨어가 필요합니다.

+++ 64비트 디자이너(권장)

* [!DNL Microsoft® Windows® 2016 Server] 또는 [!DNL Microsoft® Windows® 2019 Server], 및 [!DNL Microsoft® Windows® 10]
* 최소 2GB RAM
* 20GB의 디스크 공간
* 그래픽 메모리 - 128MB GPU(256MB 권장)
* 2.35GB의 사용 가능한 하드 디스크 공간
* 1024 X 768 픽셀 이상의 모니터 해상도
* 비디오 하드웨어 가속(옵션)
* Acrobat Pro DC, Acrobat Standard DC 또는 Adobe Acrobat Reader DC.
* Designer를 설치할 수 있는 관리 권한입니다.
* [!DNL Microsoft® Visual C++ 2019] (VC 14.28 이상) 64비트 런타임

+++

+++ 32비트 디자이너

* [!DNL Microsoft® Windows® 2016 Server], [!DNL Microsoft® Windows® 2019 Server], 또는 [!DNL Microsoft® Windows® 10]
* 32비트 OS의 경우 1GB RAM 또는 64비트 OS의 경우 2GB RAM
* 32비트 OS용 16GB 디스크 공간 또는 64비트 OS용 20GB 디스크 공간
* 그래픽 메모리 - 128MB GPU(256MB 권장)
* 2.35GB의 사용 가능한 하드 디스크 공간
* 1024 X 768 픽셀 이상의 모니터 해상도
* 비디오 하드웨어 가속(옵션)
* Acrobat Pro DC, Acrobat Standard DC 또는 Adobe Acrobat Reader DC.
* Designer를 설치할 수 있는 관리 권한입니다.
* Microsoft® Visual C++ 2019(VC 14.28 이상) 32비트 런타임

+++

## Designer 설치 {#install-designer}

>[!NOTE]
>
> 64비트 버전의 Forms Designer를 설치하기 전에 32비트 버전의 Designer를 제거합니다.

Designer를 설치하려면 다음 단계를 수행하십시오.

1. 에서 Designer 다운로드 [소프트웨어 배포](https://experience.adobe.com/downloads).
1. setup.exe 를 두 번 클릭하여 설치 관리자를 실행합니다.
1. 계속 진행하여 개인화 화면에 세부 정보를 제공합니다.
1. 사용권 계약에 동의하면 **[!UICONTROL 다음]** 계속합니다.
1. (선택 사항) 기본 설치 경로를 변경하여 원하는 위치에 Designer를 설치합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 클릭 **[!UICONTROL 뒤로]** 기본 설정을 변경합니다. Designer를 설치하려면 **[!UICONTROL 설치]**.
1. 클릭 **[!UICONTROL 완료]** 설치가 완료되는 시점입니다.

## 추가 참조 {#see-also}

* [사용자 정의 글꼴 사용](/help/forms/use-custom-fonts.md)
* [적응형 양식 기반의 독립 실행형 코어 구성 요소 만들기](/help/forms/creating-adaptive-form-core-components.md)
* [적응형 양식을 만들거나 AEM Sites 페이지에 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
