---
title: 대화형 통신 소개
description: AEM Forms Interactive Communications를 사용하여 쉽게 동적 데이터 기반 커뮤니케이션을 디자인합니다.
feature: Release Information
role: Admin
hide: true
hidefromtoc: true
source-git-commit: a771aa7e683cfbcacc8a9d5765c63d50169a2756
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 3%

---


# 대화형 통신

Interactive Communications는 비즈니스 서신, 문서, 명세서, 혜택 공지, 마케팅 이메일, 청구서 및 환영 키트와 같은 데이터 기반 대화형 통신의 작성, 수집 및 전달을 중앙 집중화하여 관리합니다.

직관적인 포인트 앤 클릭 그래픽 디자인 도구(대화형 통신 편집기)를 사용하여 인쇄, 웹 또는 보관을 위한 서신 및 비즈니스 문서를 생성할 수 있습니다. 편집기를 사용하여 서신을 디자인하고, 데이터 소스에 연결하고, 논리를 정의하고, 해당 서신과 일치하거나 엄격한 법적 요구 사항을 충족하도록 수정할 수 있습니다.

금융 기관에서 계좌 명세서를 생성하고 정부 기관에서 혜택 공지를 간소화하는 Interactive Communications는 쉽고 효율적으로 고품질, 보안 및 법적 규정을 준수하는 서신을 작성하는 데 유용한 도구입니다.

![인터랙티브 커뮤니케이션 편집기](/help/forms/assets/ic-editor.png)

## 핵심 기능

대화형 통신 편집기의 핵심 기능은 다음과 같습니다.

| 기능 | 설명 |
|------------|-------------|
| **사용자 친화적인 디자인** | 최소한의 기술 지식이 필요한 직관적인 포인트 앤 클릭 인터페이스 |
| **데이터 통합** | 동적 콘텐츠 생성을 위해 스키마, 데이터베이스 및 웹 서비스에 연결 |
| **다중 채널 디자인** | 규정 준수를 통해 인쇄 및 디지털 형식 전반에 통합 환경 구축 |
| **다이내믹 콘텐츠** | 비즈니스 논리 및 데이터 바인딩을 사용하여 개인화된 콘텐츠 생성 |
| **형식 유연성** | PDF, HTML, PCL, PostScript® 및 ZPL 형식으로 출력 |
| **언어 지원** | 사용자 정의 글꼴 지원을 통해 여러 언어로 통신 만들기 |
| **리치 미디어** | 텍스트, 이미지 및 대화형 요소를 원활하게 통합 |
| **버전 제어** | 변경 내용 추적 및 문서 기록 유지 |
| **템플릿 지원** | 효율적인 문서 생성을 위해 처음부터 새로 만들거나 템플릿을 사용합니다. |
| **클라우드 통합** | AEM Formsas a Cloud Service 에서 직접 문서 편집 |


## 온보딩

Forms as a Cloud Service 초기 배포를 위한 액세스 프로그램(Early Access program)에서 대화형 통신 편집기를 사용할 수 있습니다. 조직 ID에 대한 액세스를 요청하려면 공식 주소에서 [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)로 Forms as a Cloud Service 배포에 대한 프로그램 세부 정보를 전자 메일로 보내십시오. 액세스 권한이 제공되면 [첫 번째 서신 만들기](/help/forms/create-your-first-communication.md)를 시작합니다.








<!-- 


The Interactive Communication editor runs in any modern browser. It can be used to: 

* generate dynamic data-driven documents or correspondences and customized business documents or correspondences for print, web, or archival. 

* develop PDF documents for integration into existing workflows by binding communications to adaptive forms, XML schemas, XML sample files, databases, and web services. 

* integrate business data and render communications as a number of file types, including Adobe PDF, HTML, and printing for PCL, Adobe PostScript&reg; and Zebra (ZPL) printers.

* create interactive data capture applications by leading users through a series of visually appealing and streamlined panels, improving usability and reducing data entry errors.

## Key Features of the editor 

* **User-Friendly Interface**: The Interactive Communication editor features a point-and-click design tool that is easy to use, allowing designers to create professional communications without extensive technical knowledge.

* **Design Flexibility**: Users can design communications that match both paper and digital formats, ensuring consistency and compliance with legislative requirements.

* **Data Integration**: The tool seamlessly connects communication fields to various data sources, including XML schemas, sample files, databases, and web services.

* **Logic Definition**: Designers can define intricate logic within their communications, enhancing functionality and interactivity. 

* **Communication Creation**: Create a communication from scratch or from a template, offering flexibility and efficiency in document generation.

* **Rich Media Integration**: Add text, images, and art to your communications, creating visually appealing and engaging communication.

* **Seamless Editing**: Edit your communication documents saved in AEM Forms as a Cloud Service, ensuring easy access and continuous updates.

* **Change Tracking**: Track and review changes, maintaining a clear record of document modifications and ensuring version control.


![Output Formats and Usages](/help/assets/interactive-communication.png){align="center"}

## Usage across AEM Forms

Documents, templates, or designs created in Interactive Communication editor offer several key applications:

| **Usage**                                      | **Description**                                                                 |
|-------------------------------------------------|---------------------------------------------------------------------------------|
| PDF Document or Correspondence Creation                          | Used to generate PDF documents or correspondence for various business needs.                      |
| Document of Record Templates                   | Serves as custom templates for Documents of Record.                    |
| AEM Forms Communication APIs                   | Used as a template for various AEM Forms Communication APIs for seamless integration and automation. |


## Onboarding

The Interactive Communication editor is available for free to AEM Forms as a Cloud Service customers. You can write to mailto:aem-forms-ea@adobe.com from your official address to request access.

Adobe enables access for your organization and provide required privileges to the person designated as administrator in your organization. 

## Supported languages 

You can use the editor to create communication in languages of your choice. You can also use custom fonts in a communication. 


<!-- Communications that are created in Interactive Communication Editor can be merged with business data and rendered as a number of file types, including Adobe PDF, HTML, and printing for PCL, Adobe PostScript&reg; and Zebra (ZPL) printers.

Communication author can fill fields of a communication to personalize it for a reciever and print it, or print and fill the communication by hand. 

Communication developers can also use Interactive Communication Editor to create applications that generate dynamic, data-driven documents and produce customized business documents for print, web, or archival. 

Using communication designs, developers can create, interactive data capture applications by leading users through a series of visually appealing and streamlined panels, improving usability and reducing data entry errors. 

You can also build and maintain data capture solutions that read from, validate against, and add to corporate data sources. 

With Interactive Communication, you can integrate PDF documents into existing workflows by binding forms to XML schemas, XML sample files, databases, and web services. Forms and documents that are created in Designer can be merged with business data and rendered as a number of file types, including Adobe PDF, HTML, and printing for PCL, Adobe PostScript&reg; and Zebra (ZPL) printers. -->

## 다음

* [첫 번째 서신 만들기](/help/forms/create-your-first-communication.md)
* [자주 묻는 문제](/help/forms/interactive-communications-faq.md)
* 용어 및 개념 숙지
* 대화형 통신 편집기 연습
* 조각 만들기
* 서신 미리 보기 및 테스트

