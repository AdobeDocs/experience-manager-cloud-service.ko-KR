---
title: AEM Forms as a Cloud Service 릴리스 정보
description: AEM Forms as a Cloud Service의 새로운 기능, Beta 릴리스, 프리릴리스 정보 등에 대해 알 수 있습니다.
exl-id: 35950b81-6e45-4a75-bd27-8c28fd68e42e
source-git-commit: 8ed477ec0c54bb0913562b9581e699c0bdc973ec
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 90%

---


# [!DNL Experience Manager Forms] as a Cloud Service 릴리스 정보 {#overview}

Adobe Experience Manager [!DNL AEM Forms] as a Cloud Service는 지속적 개선이 이루어지고 있습니다. 최신 개선 사항을 확인하려면 이 페이지를 정기적으로 방문하십시오. 이 페이지에서는 다음에 대한 정보를 제공합니다.

- 새로운 기능
- 개선 사항
- 프리릴리스 기능
- 베타 기능
- 버그 수정
- 사용하지 않는 기능
- 특별 지침
- 향후 변경 계획

>[!NOTE]
>
>모든 AEM as a Cloud Service에 대한 릴리스 정보는 [최신 릴리스 정보](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=ko-KR)를 참조하십시오.

## 2021.10.0 {#sep-2021-10-0}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms-oct-2021}

- **적응형 Forms에 대한 Analytics**: 이제 적응형 Forms용 Adobe Analytics을 통해, 로그인된 및 로그인되지 않은(익명의) 사용자 행동을 포착하고 추적하여 사용자 인사이트를 수집할 수 있습니다. 데이터를 기반으로 정보에 입각한 결정을 내려 사용자 경험을 개선할 수 있습니다.

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms-oct-2021}

- **안전한 처리를 위한 AEM Workflow 데이터 외부화**: 민감한 개인 데이터(SPD)가 포함된, 처리 중인 AEM 워크플로 데이터(AEM Workflow 변수 데이터)를 안전히 처리될 수 있도록 고객 관리 저장소에 저장할 수 있습니다. 데이터 요소와 워크플로 변수는 AEM 저장소에 저장되지 않으며 워크플로 처리 중에 고객 관리 저장소에서 필요에 따라 가져옵니다.

### [!DNL Forms]의 베타 기능 {#sep-what-is-new-forms-oct-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [커뮤니케이션 API](aem-forms-cloud-service-communications.md)를 통해 템플릿과 XML 데이터를 결합하여 다양한 형식의 인쇄 문서를 생성할 수 있습니다. 이 서비스를 통해 동기화 모드와 배치 모드에서 문서를 생성할 수 있습니다. API를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.

   - XML 데이터로 템플릿 파일(PDF 및 XDP)을 채워 문서를 생성합니다.
   - 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식의 출력 양식을 생성합니다.

Beta 프로그램에 등록하려면 [!DNL formscsbeta@adobe.com]에 문의하십시오.

## 2021.9.0 {#sep-2021-09-0}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms-sep-2021}

- **적응형 양식에서 Adobe Sign 역할 사용**: 비즈니스 및 엔터프라이즈 서비스 수준을 위한 Adobe Sign은 계약 수신자의 역할을 서명자 이상으로 확장하는 옵션을 제공하여 워크플로 요구 사항에 보다 잘 부합하도록 합니다. 이제 [계약의 각 수신자가 적응형 양식에서 자신의 역할을 구성할 수 있으며,](working-with-adobe-sign.md#addsignerstoanadaptiveform) 서명자는 기본 역할입니다.

- **적응형 Forms에 대한 Analytics**: 이제 을 캡처하고 [Adobe Analytics을 통해 사용자 동작 추적](integrate-aem-forms-with-adobe-analytics.md) 를 사용하여 적응형 Forms에서 사용자 인사이트를 수집합니다. 데이터를 기반으로 정보에 입각한 결정을 내려 사용자 경험을 개선할 수 있습니다.

- **AEM Forms를 Microsoft Dynamics 및 Salesforce에 손쉽게 연결**: 이 서비스는 Microsoft Dynamics 및 Salesforce를 위한 즉시 사용 가능한 데이터 소스 구성 및 데이터 모델을 제공하여 [개발자가 Microsoft Dynamics 및 Salesforce를 적응형 양식의 데이터 소스로 더 빠르고 간편하게 구성할 수 있게 해 줍니다](configure-msdynamics-salesforce.md).

- **DocuSign을 이용한 적응형 양식 전자 서명:** [DocuSign을 사용해 적응형 양식에 전자 서명할 수 있습니다](integrate-docusign-adaptive-forms.md). 이 서비스는 적응형 양식에 DocuSign을 사용하는 맞춤형 제출 액션을 제공합니다.

### [!DNL Forms]의 베타 기능 {#sep-what-is-new-forms-prerelease}

- **통합 스토리지 커넥터:** 통합 스토리지 커넥터를 사용하여 고객 관리 저장소에서 처리 중인 데이터를 외부화합니다. 예를 들어 민감한 개인 데이터(SPD)가 포함된, 처리 중인 AEM Workflow 데이터(AEM Workflow 변수 데이터)를 고객 관리 저장소에 저장할 수 있습니다.
  <!--* Enable Forms Portal's save and resume functionality and store adaptive forms drafts in a customer-managed data repository.-->

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [커뮤니케이션 API](aem-forms-cloud-service-communications.md)를 통해 XDP 템플릿과 XML 데이터를 결합하여 다양한 형식의 인쇄 문서를 생성할 수 있습니다. 이 서비스를 사용하면 동기화 모드에서 문서를 생성할 수 있습니다. API를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.
   - XML 데이터로 템플릿 파일을 채워 문서를 생성합니다.
   - 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식의 출력 양식을 생성합니다.
   - XFA 양식 PDF 및 Adobe Acrobat Form에서 인쇄 PDF 파일을 생성합니다.

Beta 프로그램에 등록하려면 [!DNL formscsbeta@adobe.com]에 문의하십시오.

### 제한 사항 {#limitations}

- Adobe Analytics는 인증된 사용자에 대한 양식 메트릭만 추적할 수 있습니다.

<!--

### New features available in [!DNL Forms] prerelease channel {#prerelease-features-forms-sep-2021}

* **Forms Portal:**  In a typical forms-centric portal deployment scenario, forms development and portal development are two disjoint activities. While Form Designers design and store forms in a repository, Web Developers create a web application to list forms and handle submission of forms. Forms are copied over to the web tier as there is no communication between the forms repository and the web application.

  Such scenarios often result in management issues and production delays. For example, if there is a newer version of a form available in the repository, you need to replace the form on the web tier, modify the web application, and redeploy the form on the public site. Redeploying the web application might cause some server downtime. Typically, the server downtime is a planned activity and therefore the changes cannot be pushed to the public site instantaneously.

  AEM Forms provides portal components that reduce management overheads and production delays. The components equip Web Developers to create and customize a forms portal on websites authored using Adobe Experience Manager (AEM). The form portal components allow you to add the following functionality:

  * List forms in customized layouts. Out of the box, List view and Card view are provided.

  * List published adaptive forms on an AEM Sites page.

  * Enable searching of forms based on a various criteria, such as form properties, metadata, and tags.

  * Lists drafts and submissions related to Adaptive Form created by user.

  -->

## 2021.8.0 {#aug-2021-08-0}

### [!DNL Forms]의 새로운 기능 {#what-is-new-forms-aug-2021}

<!-- * Automated Forms Conversion service can [convert PDF Forms in Italian and Portuguese language](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) to Adaptive Forms. -->

- Forms as a Cloud Service용 AEM Archetype 프로젝트에는 이제 [Microsoft Dynamics 및 Salesforce용 양식 데이터 모델](setup-local-development-environment.md)이 포함됩니다.

- **Acroform 기반 기록 문서**: AEM Forms as a Cloud Service는 XFA 기반 양식 템플릿 외에 기록 문서용 템플릿으로도 [Adobe Acrobat Form PDF(Acroform PDF)](generate-document-of-record-for-non-xfa-based-adaptive-forms.md)을 사용할 수 있도록 지원합니다.

- **Microsoft Azure 데이터 스토어 커넥터**: 이제 [양식 데이터 모델을 Microsoft Azure Storage에 연결](configure-azure-storage.md)할 수 있습니다. 적응형 양식 데이터를 검색하여 Microsoft Azure Storage에 BLOB로 저장할 수 있습니다.

### [!DNL Forms]의 베타 기능 {#aug-what-is-new-forms-prerelease}

- **통합 스토리지 커넥터:** 통합 스토리지 커넥터를 사용하여 고객 관리 저장소에서 처리 중인 데이터를 외부화합니다. 예를 들어 다음 작업을 수행할 수 있습니다.

   - Forms 포털의 저장 및 재개 기능을 활성화하고 적응형 양식 초안을 고객 관리 데이터 저장소에 저장합니다.
   - 민감한 개인 데이터(SPD)가 포함된, 처리 중인 AEM Workflow 데이터(AEM Workflow 변수 데이터)를 고객 관리 저장소에 저장합니다.

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [커뮤니케이션 API](aem-forms-cloud-service-communications.md)를 통해 XDP 템플릿과 XML 데이터를 결합하여 다양한 형식의 인쇄 문서를 생성할 수 있습니다. 이 서비스를 사용하면 동기화 모드에서 문서를 생성할 수 있습니다. API를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.
   - XML 데이터로 템플릿 파일을 채워 문서를 생성합니다.
   - 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식의 출력 양식을 생성합니다.
   - XFA 양식 PDF 및 Adobe Acrobat Form에서 인쇄 PDF 파일을 생성합니다.

Beta 프로그램에 등록하려면 [!DNL formscsbeta@adobe.com]에 문의하십시오.

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#prerelease-features-forms-aug-2021}

- **적응형 양식에서 Adobe Sign 역할 사용**: 비즈니스 및 엔터프라이즈 서비스 수준을 위한 Adobe Sign은 계약 수신자의 역할을 서명자 이상으로 확장하는 옵션을 제공하여 워크플로 요구 사항에 보다 잘 부합하도록 합니다. 이제 [계약의 각 수신자가 적응형 양식에서 자신의 역할을 구성할 수 있으며,](working-with-adobe-sign.md#addsignerstoanadaptiveform) 서명자는 기본 역할입니다.

- **적응형 Forms에 대한 Analytics**: 이제 적응형 Forms용 Adobe Analytics을 통해 사용자 행동을 포착하고 추적하여 사용자 인사이트를 수집할 수 있습니다. 데이터를 기반으로 정보에 입각한 결정을 내려 사용자 경험을 개선할 수 있습니다.

- **AEM Forms를 Microsoft Dynamics 및 Salesforce에 손쉽게 연결**: 이 서비스는 Microsoft Dynamics 및 Salesforce를 위한 즉시 사용 가능한 데이터 소스 구성 및 데이터 모델을 제공하여 [개발자가 Microsoft Dynamics 및 Salesforce를 적응형 양식의 데이터 소스로 더 빠르고 간편하게 구성할 수 있게 해 줍니다](configure-msdynamics-salesforce.md).

## 2021.7.0 {#july-2021-07-0}

### [!DNL Forms]의 새로운 기능 {#july-what-is-new-forms}

- 이제 자동 양식 전환 서비스를 사용하여 [프랑스어, 독일어 및 스페인어로 된 PDF 양식을 적응형 양식으로 변환](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model)할 수 있습니다.
- 템플릿 편집기에 별도의 패널을 추가하여 적응형 양식 구성 요소와 관련된 오류를 표시합니다. 모든 적응형 양식 오류를 한 위치에서 통합하고 해결 시간을 단축하는 데 도움이 됩니다.

### [!DNL Forms] 프리릴리스 채널에서 사용할 수 있는 새로운 기능 {#july-prerelease-features-forms}

- **Acroform 기반 기록 문서**: XFA 기반 양식 템플릿 외에 [기록 문서의 템플릿으로도 Adobe Acrobat Form PDF(Acroform PDF)를 사용](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html)할 수 있습니다.

- **Microsoft Azure 데이터 스토어 커넥터**: 이제 [양식 데이터 모델을 Microsoft Azure Storage에 연결](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html)할 수 있습니다. 적응형 양식 데이터를 검색하여 Microsoft Azure Storage에 BLOB로 저장할 수 있습니다.

- **변수 데이터 외부화**: 조직에서 관리하는 외부 스토리지 시스템에 AEM Workflow 변수 데이터를 저장할 수 있습니다.

### [!DNL Forms]의 베타 기능 {#july-what-is-new-forms-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [커뮤니케이션 API](aem-forms-cloud-service-communications.md)를 통해 XDP 템플릿과 XML 데이터를 결합하여 다양한 형식의 인쇄 문서를 생성할 수 있습니다. 이 서비스를 사용하면 동기화 모드에서 문서를 생성할 수 있습니다. API를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.
   - XML 데이터로 템플릿 파일을 채워 문서를 생성합니다.
   - 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식의 출력 양식을 생성합니다.
   - XFA 양식 PDF 및 Adobe Acrobat Form에서 인쇄 PDF 파일을 생성합니다.

## 2021.6.0 {#july-2021-06-0}

### [!DNL Forms]의 새로운 기능 {#june-what-is-new-forms}

- AEM 받은 편지함에서 맞춤 열을 필터링할 수 있는 기능이 추가되었습니다.
- 테마 편집기를 사용해 적응형 양식 편집기 레이어를 스타일링함으로써 Captcha 구성 요소를 스타일링할 수 있는 기능이 추가되었습니다.
- 소스 PDF 양식의 논리적 섹션을 자동 감지하고 이를 해당 적응형 양식 패널로 변환하는 속도와 정확도를 개선했습니다.
- PDF 또는 XDP 파일을 폴더 간에 이동하는 이동 액션을 추가했습니다.

### [!DNL Forms]의 베타 기능 {#june-what-is-new-forms-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]**: 커뮤니케이션 API를 통해 XDP 템플릿과 XML 데이터를 결합하여 다양한 형식의 인쇄 문서를 생성할 수 있습니다. 이 서비스를 사용하면 동기화 모드에서 문서를 생성할 수 있습니다. API를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.

   - XML 데이터로 템플릿 파일을 채워 최종 양식 문서를 생성합니다.
   - 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식의 출력 양식을 생성합니다.
   - XFA 형식 PDF 및 Adobe Acrobat Form(AcroForm)에서 인쇄 PDF를 생성합니다.

- **변수 데이터 외부화**: 조직에서 관리하는 외부 스토리지 시스템에 AEM Workflow 변수 데이터를 저장할 수 있습니다.

Beta 프로그램에 등록하려면 [!DNL formscsbeta@adobe.com]에 문의하십시오.

### [!DNL Forms]의 수정된 버그 {#june-forms-bugs-fixed}

- When a field is validated before submitting data to backend service via 양식 데이터 모델(FDM)을 통해 백엔드 서비스로 데이터를 제출하기 전에 필드를 유효성 검사하는 경우, 유효성 검사는 성공하지만 양식 데이터 모델 서비스가 사후 유효성 검사를 불러오지 못합니다.
- Apple iOS 디바이스에서 표준 HTML 업로드 필드가 포함된 양식을 제출할 경우, 때때로 파일의 콘텐츠가 전송되지 않고 반대편에서 0바이트 파일이 수신됩니다. Apple iOS 15.1은 이 문제에 대한 해결 방법을 제공합니다.

## 2021.5.0 {#may-2021-05-0}

## [!DNL Adobe Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms]의 새로운 기능 {#may-what-is-new-forms}

- **상황별 도움말**: 작성자가 편집기의 다양한 기능을 더 잘 이해하도록 돕기 위해 적응형 양식 편집기, 템플릿 편집기, 테마 편집기에 대한 상황별 도움말을 추가했습니다.
- **속성 브라우저의 오류 메시지**: 적응형 양식 속성 브라우저에서 각 속성에 대한 오류 메시지를 추가했습니다. 이러한 메시지는 필드의 허용 값을 이해하는 데 도움이 됩니다.

### [!DNL Forms]의 예정된 베타 기능 {#may-what-is-new-forms-prerelease}

Output as a Cloud service: Output 서비스는 XDP 템플릿과 XML 데이터를 결합하여 다양한 형식의 인쇄 문서를 생성할 수 있도록 합니다. 이 서비스를 사용하면 동기화 모드와 비동기화 배치 모드에서 문서를 생성할 수 있습니다. Output 서비스를 사용하면 다음과 같은 기능을 제공하는 애플리케이션을 만들 수 있습니다.

- XML 데이터로 템플릿 파일을 채워 최종 양식 문서를 생성합니다.
- 비대화형 PDF 인쇄 스트림을 포함하여 다양한 형식의 출력 양식을 생성합니다.
- XFA 양식 PDF에서 인쇄 PDF를 생성합니다.

Beta 프로그램에 등록하려면 formscsbeta@adobe.com에 문의하십시오.

### [!DNL Forms]의 수정된 버그 {#may-forms-bugs-fixed}

- AEM Forms Workflow의 작업 할당 단계에서 액션 버튼의 기본값 아이콘을 코랄 아이콘으로 대체할 때 워크플로가 작동을 멈추고 예외 사항을 기록합니다. 기본값 아이콘을 사용하면 워크플로가 원래대로 작동합니다.
- 레이아웃 레이어에서 열의 수를 바꾸고 레이어 편집기를 열어 패널에서 일부 구성 요소를 드래그하면 적응형 양식 편집기의 콘텐츠 영역에 사각형의 파란색 상자가 나타나기 시작하고 편집기가 응답하지 않습니다.
- 적응형 또는 외부 애셋의 URL 제공과 관련된 규칙 편집기 옵션의 오류 메시지가 너무 길고 사용자 친화적이지 않습니다.

## 2021.4.0 {#april-2021-04-0}

### [!DNL Forms]의 새로운 기능 {#april-what-is-new-forms}

- **Adobe Sign이 활성화된 적응형 양식에서 정부 ID 신원 인증 방법 사용**

  고급 머신 러닝 알고리즘으로 더욱 강력해진 Adobe Sign의 정부 ID 프로세스는 고품질의 수령인 신원 인증을 확보할 수 있는 능력을 전 세계 기업에 제공합니다. 이제 Adobe Sign이 활성화된 적응형 양식에서 정부 ID 신원 인증 방법을 사용할 수 있습니다.

  정부 ID는 수신자에게 다음을 지시하는 프리미엄 신원 인증 방법입니다 [정부에서 발급한 신분증(운전면허증, 주민등록증, 여권) 이미지 업로드](https://helpx.adobe.com/kr/in/sign/using/adobesign-authentication-government-id.html)를 누르고 해당 문서가 진짜인지 평가합니다.

- **비동기 적응형 양식 제출을 위한 양식 내 서명 경험 사용 지원**

  이제 비동기 적응형 양식 제출을 위해 양식 내 서명 환경을 사용할 수 있습니다. 또한 [!DNL Experience Manager Sites] 페이지에 적응형 양식을 임베드하고 적응형 양식 제출을 위해 양식 내 서명 환경을 사용할 수 있습니다.

- **작업 할당 단계를 위해 적응형 양식을 미리 채우는 동안 변수를 사용하여 첨부 파일을 지정하도록 지원**

  이제 작업 할당 단계를 위해 적응형 양식을 미리 채우는 동안 문서 유형 변수를 사용하여 적응형 양식에 대한 입력 첨부 파일을 선택할 수 있습니다.

- **JSON 유형 변수에 대한 값을 설정하기 위해 리터럴 옵션을 사용하도록 지원**

  리터럴 옵션을 사용하여 AEM Workflow의 변수 설정 단계에서 JSON 유형 변수의 값을 설정할 수 있습니다. 리터럴 옵션을 사용하면 문자열 포맷으로 JSON을 지정할 수 있습니다.

- **로컬 개발 환경을 사용하여 기록 문서(DoR) 생성**

  XDP를 클라우드 서비스 인스턴스와 AEM Forms as a Cloud Service SDK(로컬 개발 환경)에서 기록 문서 템플릿으로 사용할 수 있습니다. 이전에는 지원이 클라우드 서비스 인스턴스로만 제한되었습니다.

### [!DNL Forms]에서 수정된 버그 {#april-bug-fixes-forms}

- 기록 문서를 생성하도록 구성된 AEM Workflow에 기록 문서를 생성하지 않도록 구성된 적응형 양식을 제출하는 경우, 오류 메시지가 표시되지 않고 작업 제출이 실패합니다.
