---
title: 기록 문서 템플릿을 만들기 위해 Forms Designer을 다운로드하고 설치하는 방법
description: Forms Designer을 사용하여 기록 문서의 템플릿 역할을 하는 XDP 및 PDF 양식 템플릿을 만듭니다.
keywords: Designer 설치, Forms 디자이너 설치, Forms Designer 설치 요구 사항
feature: Adaptive Forms, Forms Designer
role: Admin, Developer, User
exl-id: d6f1cb21-c48b-406d-8d47-482d7a1b4cc3
source-git-commit: 527c9944929c28a0ef7f3e617ef6185bfed0d536
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 9%

---

# Forms Designer 다운로드 및 설치 {#installing-and-configuring-designer}

| 버전 | 문서 링크 |
| -------- | ---------------------------- |
| AEM as a Cloud Service | 이 문서 |
| AEM 6.5 | [여기 클릭](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/jee-installation/installing-configuring-designer.html) |

Designer은 XDP 및 PDF 양식 템플릿 작성을 간소화하는 포인트 앤 클릭 그래픽 양식 디자인 도구입니다. 양식 템플릿을 디자인하고 해당 논리를 정의하며 엄격한 법적 요구 사항을 충족할 수 있습니다. XDP 및 PDF 양식은 적응형 양식에서 기록 문서 템플릿 역할을 합니다. 이러한 양식 서식 파일은 [적응형 양식 서식 파일](template-editor.md)과 다릅니다.

## 전제 조건 {#pre-requisites}

최신 버전의 AEM Forms Designer 64비트 또는 32비트를 설치하려면 Designer을 설치하고 구성하려면 다음 소프트웨어와 최소 하드웨어가 필요합니다.

+++ 64비트 Designer(권장)

* [!DNL Microsoft® Windows® 2016 Server] 또는 [!DNL Microsoft® Windows® 2019 Server], [!DNL Microsoft® Windows® 10]
* 최소 2GB RAM
* 20GB의 디스크 공간
* 그래픽 메모리 - 128MB GPU(256MB 권장)
* 2.35GB의 사용 가능한 하드 디스크 공간
* 1024 X 768 픽셀 이상의 모니터 해상도
* 비디오 하드웨어 가속(옵션)
* Acrobat Pro DC, Acrobat Standard DC 또는 Adobe Acrobat Reader DC.
* Designer을 설치할 수 있는 관리 권한입니다.
* [!DNL Microsoft® Visual C++ 2019](VC 14.28 이상) 64비트 런타임

+++

+++ 32비트 Designer

* [!DNL Microsoft® Windows® 2016 Server], [!DNL Microsoft® Windows® 2019 Server] 또는 [!DNL Microsoft® Windows® 10]
* 32비트 OS의 경우 1GB RAM 또는 64비트 OS의 경우 2GB RAM
* 32비트 OS용 16GB 디스크 공간 또는 64비트 OS용 20GB 디스크 공간
* 그래픽 메모리 - 128MB GPU(256MB 권장)
* 2.35GB의 사용 가능한 하드 디스크 공간
* 1024 X 768 픽셀 이상의 모니터 해상도
* 비디오 하드웨어 가속(옵션)
* Acrobat Pro DC, Acrobat Standard DC 또는 Adobe Acrobat Reader DC.
* Designer을 설치할 수 있는 관리 권한입니다.
* Microsoft® Visual C++ 2019(VC 14.28 이상) 32비트 런타임

+++

## Designer 설치 {#install-designer}

>[!NOTE]
>
> 64비트 버전의 Forms Designer을 설치하기 전에 32비트 버전의 Designer을 제거합니다.

Designer을 설치하려면 다음 단계를 수행하십시오.

1. [소프트웨어 배포](https://experience.adobe.com/downloads)에서 Designer을 다운로드합니다.
1. setup.exe 를 두 번 클릭하여 설치 관리자를 실행합니다.
1. 계속 진행하여 Personalization 화면에 세부 사항을 제공합니다.
1. 사용권 계약에 동의하면 **[!UICONTROL 다음]**&#x200B;을 클릭하여 계속 진행하십시오.
1. (선택 사항) 기본 설치 경로를 변경하여 선택한 위치에 Designer을 설치합니다. **[!UICONTROL 다음]**&#x200B;을 클릭합니다.
1. 환경 설정을 변경하려면 **[!UICONTROL 뒤로]**&#x200B;를 클릭하십시오. Designer을 설치하려면 **[!UICONTROL 설치]**&#x200B;를 클릭하십시오.
1. 설치가 완료되면 **[!UICONTROL 마침]**&#x200B;을 클릭합니다.

## 추가 참조 {#see-also}

* [사용자 정의 글꼴 사용](/help/forms/use-custom-fonts.md)
* [적응형 양식 기반의 독립 실행형 코어 구성 요소 만들기](/help/forms/creating-adaptive-form-core-components.md)
* [적응형 양식을 만들거나 AEM Sites 페이지에 추가](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Forms Designer을 사용하여 기록 문서(DoR) 템플릿 및 양식 조각 만들기](/help/forms/use-forms-designer.md)


<!--

>[!MORELIKETHIS]
>
>* [Use Forms Designer to create Document of Record (DoR) templates and form fragments](/help/forms/use-forms-designer.md)

-->