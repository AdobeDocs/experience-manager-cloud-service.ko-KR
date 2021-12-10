---
title: '[!DNL AEM Forms] as a Cloud Service 릴리스 노트'
description: '[!DNL AEM Forms] as a Cloud Service 릴리스 노트'
exl-id: 35950b81-6e45-4a75-bd27-8c28fd68e42e
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 2%

---


# [!DNL Experience Manager Forms] as a Cloud Service 노트 {#overview}

Adobe Experience Manager [!DNL AEM Forms] as a Cloud Service은 지속적으로 개선됩니다. 최신 개선 사항을 확인하려면 이 페이지를 정기적으로 방문하십시오. 이 페이지에서는 다음에 대한 정보를 제공합니다.

- 새로운 기능
- 개선 사항
- 시험판 기능
- 베타 기능
- 버그 수정
- 사용하지 않는 기능
- 특별 지침
- 향후 변경 계획

>[!NOTE]
>
>기타 모든 AEM as a Cloud Service 릴리스 구성 요소의 릴리스 노트는 다음을 참조하십시오. [현재 릴리스 노트](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=ko-KR).

## 2021.10.0 {#sep-2021-10-0}

### 의 새로운 기능 [!DNL Forms] {#what-is-new-forms-oct-2021}

- **응용 Forms용 Analytics**: 이제 Adaptive Forms을 통해 Adobe Analytics을 통해 로그인된 사용자와 로그인하지 않은(익명) 모두의 동작을 캡처하고 추적하여 최종 사용자 통찰력을 얻을 수 있습니다. 최종 사용자 경험을 향상시키기 위해 데이터를 기반으로 현명한 결정을 내릴 수 있습니다.

### 에서 사용할 수 있는 새로운 기능 [!DNL Forms] 사전 릴리스 채널 {#prerelease-features-forms-oct-2021}

- **보안 처리를 위한 AEM 워크플로우 데이터 표면화**: 안전한 처리를 위해 고객 관리 저장소에 민감한 개인 데이터(SPD) 요소를 포함하는 처리 중인 AEM 워크플로우 데이터(AEM Workflow Variables 데이터)를 저장할 수 있습니다. 데이터 요소와 워크플로우 변수는 AEM 저장소에 저장되지 않으며 워크플로우를 처리하는 동안 고객 관리 저장소에서 주문형 가져옵니다.

### 의 베타 기능 [!DNL Forms] {#sep-what-is-new-forms-oct-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [통신 API](aem-forms-cloud-service-communications.md) 서식 파일과 XML 데이터를 결합하여 인쇄 문서를 다양한 형식으로 생성하는 데 도움이 됩니다. 이 서비스를 사용하면 문서를 동기식과 배치 모드로 생성할 수 있습니다. API를 사용하면 다음을 수행할 수 있는 애플리케이션을 만들 수 있습니다.

   - XML 데이터로 템플릿 파일(PDF 및 XDP)을 채워서 문서를 생성합니다.
   - 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식으로 출력 양식을 생성합니다.

에 쓸 수 있습니다. [!DNL formscsbeta@adobe.com] 베타 프로그램에 등록하려면

## 2021.9.0 {#sep-2021-09-0}

### 의 새로운 기능 [!DNL Forms] {#what-is-new-forms-sep-2021}

- **적응형 양식에서 Adobe Sign 역할 사용**: 비즈니스 및 엔터프라이즈 서비스 수준용 Adobe Sign은 서명자 외에 계약 수신자의 역할을 확장하여 워크플로우 요구 사항에 보다 잘 부합할 수 있는 옵션을 제공합니다. 이제 다음을 수행할 수 있습니다 [각 동의 수신자가 적응형 양식에서 자신의 역할을 구성할 수 있도록 설정](working-with-adobe-sign.md#addsignerstoanadaptiveform)서명자가 기본 역할인 경우

- **응용 Forms용 Analytics**: 이제 및 를 캡처할 수 있습니다. [Adobe Analytics을 통한 최종 사용자 동작 추적](integrate-aem-forms-with-adobe-analytics.md) 적응형 Forms이 최종 사용자 통찰력을 수집할 수 있습니다. 최종 사용자 경험을 향상시키기 위해 데이터를 기반으로 현명한 결정을 내릴 수 있습니다.

- **Microsoft Dynamics 및 Salesforce와 AEM Forms을 손쉽게 연결**: 이 서비스는 Microsoft Dynamics 및 Salesforce용 기본 데이터 소스 구성 및 데이터 모델을 제공하여 만듭니다 [개발자가 적응형 양식의 데이터 소스로 Microsoft Dynamics 및 Salesforce를 구성할 수 있는 빠르고 쉬운 방법](configure-msdynamics-salesforce.md).

- **DocuSign을 사용하여 적응형 양식에 전자 서명:** [DocuSign을 사용하여 적응형 양식에 전자 서명할 수 있습니다](integrate-docusign-adaptive-forms.md). 이 서비스는 적응형 양식과 함께 DocuSign을 사용하기 위한 사용자 지정 제출 작업을 제공합니다.

### 의 베타 기능 [!DNL Forms] {#sep-what-is-new-forms-prerelease}

- **통합 스토리지 커넥터:** Unified Storage Connector를 사용하여 고객 관리 리포지토리에서 처리 중인 데이터를 외부화할 수 있습니다. 예를 들어, 고객 관리 저장소에 SPD(중요 개인 데이터)를 포함하는 처리 중인 AEM 워크플로우 데이터(AEM 워크플로우 변수 데이터)를 저장할 수 있습니다.

   <!--* Enable Forms Portal’s save and resume functionality and store adaptive forms drafts in a customer-managed data repository.-->

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [통신 API](aem-forms-cloud-service-communications.md) XDP 템플릿과 XML 데이터를 결합하여 다양한 형식으로 인쇄 문서를 생성하는 데 도움이 됩니다. 이 서비스를 통해 동기 모드로 문서를 생성할 수 있습니다. API를 사용하면 다음을 수행할 수 있는 애플리케이션을 만들 수 있습니다.
   - XML 데이터로 템플릿 파일을 채워서 문서를 생성합니다.
   - 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식으로 출력 양식을 생성합니다.
   - XFA 양식 PDF 및 Adobe Acrobat 양식에서 인쇄 PDF 파일을 생성합니다.

에 쓸 수 있습니다. [!DNL formscsbeta@adobe.com] 베타 프로그램에 등록하려면

### 제한 사항 {#limitations}

- Adobe Analytics은 인증된 사용자에 대해서만 양식 지표를 추적할 수 있습니다.

<!--

### New features available in [!DNL Forms] prerelease channel {#prerelease-features-forms-sep-2021}

* **Forms Portal:**  In a typical forms-centric portal deployment scenario, forms development and portal development are two disjoint activities. While Form Designers design and store forms in a repository, Web Developers create a web application to list forms and handle submission of forms. Forms are copied over to the web tier as there is no communication between the forms repository and the web application.

  Such scenarios often result in management issues and production delays. For example, if there is a newer version of a form available in the repository, you need to replace the form on the web tier, modify the web application, and redeploy the form on the public site. Redeploying the web application might cause some server downtime. Typically, the server downtime is a planned activity and therefore the changes cannot be pushed to the public site instantaneously.

  AEM Forms provides portal components that reduce management overheads and production delays. The components equip Web Developers to create and customize a forms portal on websites authored using Adobe Experience Manager (AEM). The form portal components allow you to add the following functionality:

  * List forms in customized layouts. Out of the box, List view and Card view are provided.

  * List published adaptive forms on an AEM Sites page.

  * Enable searching of forms based on a various criteria, such as form properties, metadata, and tags.

  * Lists drafts and submissions related to Adaptive Form created by end user.

  -->

## 2021.8.0 {#aug-2021-08-0}

### 의 새로운 기능 [!DNL Forms] {#what-is-new-forms-aug-2021}

<!-- * Automated Forms Conversion service can [convert PDF Forms in Italian and Portuguese language](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) to Adaptive Forms. -->

- 이제 Forms as a Cloud Service용 AEM Archetype 프로젝트에 다음이 포함됩니다 [Microsoft Dynamics 및 Salesforce용 양식 데이터 모델](setup-local-development-environment.md).

- **Acroform 기반 레코드 문서**: AEM Forms as a Cloud Service 지원 [Adobe Acrobat 양식 PDF(Acroform PDF)](generate-document-of-record-for-non-xfa-based-adaptive-forms.md) XFA 기반 양식 템플릿 외에 기록 문서에 대한 템플릿으로 사용됩니다.

- **Microsoft Azure 데이터 저장소 커넥터**: 이제 다음을 수행할 수 있습니다 [Microsoft Azure 저장소에 양식 데이터 모델 연결](configure-azure-storage.md). 적응형 양식 데이터를 검색하고 BLOB으로 Microsoft Azure 저장소에 저장할 수 있습니다.

### 의 베타 기능 [!DNL Forms] {#aug-what-is-new-forms-prerelease}

- **통합 스토리지 커넥터:** Unified Storage Connector를 사용하여 고객 관리 리포지토리에서 처리 중인 데이터를 외부화할 수 있습니다. 예를 들어 다음 작업을 수행할 수 있습니다.

   - Forms Portal의 저장 및 재개 기능을 활성화하고 고객 관리 데이터 저장소에 적응형 양식 초안을 저장합니다.
   - 고객 관리 저장소에 SPD(중요 개인 데이터)가 포함된 처리 중인 AEM 워크플로우 데이터(AEM Workflow 변수 데이터)를 저장합니다.

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [통신 API](aem-forms-cloud-service-communications.md) XDP 템플릿과 XML 데이터를 결합하여 다양한 형식으로 인쇄 문서를 생성하는 데 도움이 됩니다. 이 서비스를 통해 동기 모드로 문서를 생성할 수 있습니다. API를 사용하면 다음을 수행할 수 있는 애플리케이션을 만들 수 있습니다.
   - XML 데이터로 템플릿 파일을 채워서 문서를 생성합니다.
   - 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식으로 출력 양식을 생성합니다.
   - XFA 양식 PDF 및 Adobe Acrobat 양식에서 인쇄 PDF 파일을 생성합니다.

에 쓸 수 있습니다. [!DNL formscsbeta@adobe.com] 베타 프로그램에 등록하려면

### 에서 사용할 수 있는 새로운 기능 [!DNL Forms] 사전 릴리스 채널 {#prerelease-features-forms-aug-2021}

- **적응형 양식에서 Adobe Sign 역할 사용**: 비즈니스 및 엔터프라이즈 서비스 수준용 Adobe Sign은 서명자 외에 계약 수신자의 역할을 확장하여 워크플로우 요구 사항에 보다 잘 부합할 수 있는 옵션을 제공합니다. 이제 다음을 수행할 수 있습니다 [각 동의 수신자가 적응형 양식에서 자신의 역할을 구성할 수 있도록 설정](working-with-adobe-sign.md#addsignerstoanadaptiveform)서명자가 기본 역할인 경우

- **응용 Forms용 Analytics**: 이제 Adobe Analytics for Adaptive Forms을 통해 최종 사용자 행동을 캡처하고 추적하여 최종 사용자 통찰력을 수집할 수 있습니다. 최종 사용자 경험을 향상시키기 위해 데이터를 기반으로 현명한 결정을 내릴 수 있습니다.

- **Microsoft Dynamics 및 Salesforce와 AEM Forms을 손쉽게 연결**: 이 서비스는 Microsoft Dynamics 및 Salesforce용 기본 데이터 소스 구성 및 데이터 모델을 제공하여 만듭니다 [개발자가 적응형 양식의 데이터 소스로 Microsoft Dynamics 및 Salesforce를 구성할 수 있는 빠르고 쉬운 방법](configure-msdynamics-salesforce.md).

## 2021.7.0 {#july-2021-07-0}

### 의 새로운 기능 [!DNL Forms] {#july-what-is-new-forms}

- 이제 Automated forms conversion 서비스를 사용하여 다음을 수행할 수 있습니다 [프랑스어, 독일어 및 스페인어 언어로 PDF forms 변환](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) 적응형 양식에 추가할 수 있습니다.
- 적응형 양식 구성 요소와 관련된 오류를 표시하는 별도의 패널을 템플릿 편집기에 추가했습니다. 모든 적응형 양식 오류를 한 위치에서 통합하고 해결 시간을 줄이는 데 도움이 됩니다.

### 에서 사용할 수 있는 새로운 기능 [!DNL Forms] 사전 릴리스 채널 {#july-prerelease-features-forms}

- **Acroform 기반 레코드 문서**: 다음을 수행할 수도 있습니다 [Adobe Acrobat 양식 PDF 사용(Acroform PDF)](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html) XFA 기반 양식 템플릿 외에 기록 문서에 대한 템플릿으로 사용됩니다.

- **Microsoft Azure 데이터 저장소 커넥터**: 이제 다음을 수행할 수 있습니다 [Microsoft Azure 저장소에 양식 데이터 모델 연결](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html). 적응형 양식 데이터를 검색하고 BLOB으로 Microsoft Azure 저장소에 저장할 수 있습니다.

- **변수 데이터 외부자**: 조직에서 관리하는 외부 스토리지 시스템에 AEM Workflow 변수의 데이터를 저장할 수 있습니다.

### 의 베타 기능 [!DNL Forms] {#july-what-is-new-forms-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [통신 API](aem-forms-cloud-service-communications.md) XDP 템플릿과 XML 데이터를 결합하여 다양한 형식으로 인쇄 문서를 생성하는 데 도움이 됩니다. 이 서비스를 통해 동기 모드로 문서를 생성할 수 있습니다. API를 사용하면 다음을 수행할 수 있는 애플리케이션을 만들 수 있습니다.
   - XML 데이터로 템플릿 파일을 채워서 문서를 생성합니다.
   - 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식으로 출력 양식을 생성합니다.
   - XFA 양식 PDF 및 Adobe Acrobat 양식에서 인쇄 PDF 파일을 생성합니다.

## 2021.6.0 {#july-2021-06-0}

### 의 새로운 기능 [!DNL Forms] {#june-what-is-new-forms}

- AEM 받은 편지함에서 사용자 지정 열을 필터링하는 기능이 추가되었습니다.
- 적응형 양식 편집기의 테마 편집기와 스타일 레이어를 사용하여 Captcha 구성 요소의 스타일을 지정하는 기능이 추가되었습니다.
- 소스 PDF forms에서 논리 섹션을 자동으로 감지하여 해당 적응형 양식 패널로 변환하는 속도와 정확도를 개선했습니다.
- 한 폴더에서 다른 폴더로 PDF 또는 XDP 파일을 이동하는 이동 작업을 추가했습니다.

### 의 베타 기능 [!DNL Forms] {#june-what-is-new-forms-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]**: Communication API를 사용하면 XDP 템플릿과 XML 데이터를 결합하여 다양한 형식으로 인쇄 문서를 생성할 수 있습니다. 이 서비스를 통해 동기 모드로 문서를 생성할 수 있습니다. API를 사용하면 다음을 수행할 수 있는 애플리케이션을 만들 수 있습니다.

   - XML 데이터로 템플릿 파일을 채워서 최종 양식 문서를 생성합니다.
   - 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식으로 출력 양식을 생성합니다.
   - XFA 양식 PDF 및 Adobe Acrobat 양식(AcroForm)에서 인쇄 PDF을 생성합니다.

- **변수 데이터 외부자**: 조직에서 관리하는 외부 스토리지 시스템에 AEM Workflow 변수의 데이터를 저장할 수 있습니다.

에 쓸 수 있습니다. [!DNL formscsbeta@adobe.com] 베타 프로그램에 등록하려면

### 에서 해결된 버그 [!DNL Forms] {#june-forms-bugs-fixed}

- FDM(양식 데이터 모델)을 통해 백엔드 서비스에 데이터를 제출하기 전에 필드의 유효성을 검사하면 유효성 검사가 성공하지만 양식 데이터 모델 서비스가 사후 유효성 검사를 호출하지 못합니다.
- Apple iOS 장치에서 표준 HTML 업로드 필드가 포함된 양식을 제출하는 경우 때로 파일의 컨텐츠가 전송되지 않고 다른 끝에는 0바이트 파일이 수신됩니다. Apple iOS 15.1에서는 문제에 대한 수정 사항을 제공합니다.

## 2021.5.0 {#may-2021-05-0}

## [!DNL Adobe Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### 의 새로운 기능 [!DNL Forms] {#may-what-is-new-forms}

- **상황별 도움말**: 작성자가 다양한 편집기의 기능을 더 잘 이해할 수 있도록 적응형 양식 편집기, 템플릿 편집기 및 테마 편집기에 대한 상황별 도움말을 추가했습니다.
- **속성 브라우저의 오류 메시지**: 응용 Forms 속성 브라우저에 각 속성에 대한 오류 메시지가 추가되었습니다. 이러한 메시지는 필드에 대해 허용되는 값을 이해하는 데 도움이 됩니다.

### 예정된 베타 기능 [!DNL Forms] {#may-what-is-new-forms-prerelease}

클라우드 서비스로 출력: 출력 서비스를 사용하면 XDP 템플릿과 XML 데이터를 결합하여 다양한 형식으로 인쇄 문서를 생성할 수 있습니다. 이 서비스를 사용하면 동기식 및 비동기식 배치 모드로 문서를 생성할 수 있습니다. 출력 서비스를 통해 다음을 수행할 수 있는 응용 프로그램을 만들 수 있습니다.

- XML 데이터로 템플릿 파일을 채워서 최종 양식 문서를 생성합니다.
- 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식으로 출력 양식을 생성합니다.
- XFA 양식 PDF에서 인쇄 PDF을 생성합니다.

formscsbeta@adobe.com에 편지를 보내 베타 프로그램에 등록할 수 있습니다.

### 에서 해결된 버그 [!DNL Forms] {#may-forms-bugs-fixed}

- AEM Forms Workflows의 작업 할당 단계에서 작업 단추의 기본 아이콘을 coral 아이콘으로 바꾸면 워크플로우가 작동하지 않고 예외가 기록됩니다. 워크플로우는 기본 아이콘을 사용할 때 예상대로 수행됩니다.
- 레이아웃 레이어에서 열 수를 변경하고 편집 레이어를 열고 패널에서 일부 구성 요소를 드래그하면 적응형 양식 편집기의 콘텐츠 영역에 파란색 사각형 상자가 나타나고 편집기가 응답하지 않습니다.
- 적응형 또는 외부 자산의 URL 제공과 관련된 규칙 편집기 옵션의 오류 메시지가 너무 길며 사용자에게 친절하지 않습니다.

## 2021.4.0 {#april-2021-04-0}

### 의 새로운 기능 [!DNL Forms] {#april-what-is-new-forms}

- **Adobe Sign에서 활성화된 응용 Forms에서 정부 ID 인증 방법 사용**

   고급 기계 학습 알고리즘을 기반으로 하는 Adobe Sign의 정부 ID 프로세스는 전 세계 기업을 대상으로 수신자의 ID에 대한 고품질 인증을 획득하는 기능을 제공합니다. 이제 Adobe Sign이 활성화된 적응형 Forms에서 정부 기관 ID 인증 방법을 사용할 수 있습니다.

   정부 ID는 수신자에게 지시하는 프리미엄 ID 인증 방법입니다 [정부가 발행한 신분증명서(운전면허증, 국민 신분증, 여권) 이미지를 업로드합니다](https://helpx.adobe.com/in/sign/using/adobesign-authentication-government-id.html), 및에서 해당 문서를 평가하여 인증 문서인지 확인합니다.

- **비동기 적응형 양식 제출을 위해 양식 서명 환경을 사용하도록 지원**

   이제 비동기 적응형 양식 제출에 양식 서명 경험을 사용할 수 있습니다. 적응형 양식을 [!DNL Experience Manager Sites] 적응형 양식 제출을 위해 양식 서명 환경을 사용하고 페이지를 변경해야 합니다.

- **작업 할당 단계에서 적응형 양식을 미리 채우는 동안 변수를 사용하여 첨부 파일을 지정할 수 있도록 지원합니다**

   작업 지정 단계에 대해 적응형 양식을 미리 채우는 동안 이제 문서 유형 변수를 사용하여 적응형 양식에 대한 입력 첨부 파일을 선택할 수 있습니다.

- **리터럴 옵션을 사용하여 JSON 유형 변수에 대한 값을 설정할 수 있도록 지원합니다**

   AEM Workflow의 설정 변수 단계에서 리터럴 옵션을 사용하여 JSON 유형 변수의 값을 설정할 수 있습니다. 리터럴 옵션을 사용하면 문자열 형태로 JSON을 지정할 수 있습니다.

- **로컬 개발 환경을 사용하여 기록 문서(DoR) 작성**

   XDP를 Cloud Service 인스턴스 및 AEM Forms as a Cloud Service SDK(로컬 개발 환경)에서 기록 문서로 사용할 수 있습니다. 이전에는 지원이 Cloud Service 인스턴스로만 제한되었습니다.

### 의 버그 수정 [!DNL Forms] {#april-bug-fixes-forms}

- 기록 문서를 생성하지 않도록 구성된 적응형 양식을 기록 문서를 생성하도록 구성된 AEM Workflow에 제출하면 오류 메시지가 표시되지 않고 작업을 제출할 수 없습니다.
