---
title: ' [!DNL AEM Forms] as a Cloud Service 소개'
description: AEM Forms를 통해 업무용 양식을 제작하고 비즈니스 프로세스 워크플로를 만들 수 있고, 문서 서비스를 사용하여 문서를 생성하고 보호할 수 있습니다.
landing-page-description: AEM as a Cloud Service에서 양식을 사용하는 방법을 이해합니다.
role: Admin, Developer, User
feature: Adaptive Forms, Release Information
hide: true
hidefromtoc: true
source-git-commit: 4b4bc6f754c6336136d409cf49617c7fafd4f4c3
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 11%

---


# AEM Forms as a Cloud Service {#introduction}

<!-- Version Navigation -->
<div class="version-selector">
  <p><strong>다른 버전에 대한 설명서를 찾고 계십니까?</strong></p>
  <ul>
    <li><a href="https://experienceleague.adobe.com/docs/experience-manager-65/forms/home.html">AEM 6.5 Forms 설명서</a></li>
    <li><strong>AEM Forms as a Cloud Service</strong>(현재)</li>
  </ul>
</div>

## AEM Forms as a Cloud Service란?

AEM Forms as a Cloud Service은 디지털 양식 및 통신을 생성, 관리 및 제공하기 위한 Adobe의 클라우드 기반 솔루션입니다. 이를 통해 조직은 전체 고객 여정에서 복잡한 트랜잭션을 간단한 디지털 환경으로 변환할 수 있습니다. 이들 서비스를 통해 다음과 같은 작업을 수행할 수 있습니다.

* 등록과 온보딩 경험 디지털화 및 간소화
* 맞춤형 커뮤니케이션 제공
* 백오피스 워크플로 자동화
* 양식 및 통신 경험을 데이터 소스와 통합
* 양식의 성능 추적 및 최적화

이 서비스는 항상 최신 상태를 유지하고 항상 사용 가능하며 항상 학습합니다. 조직은 [!DNL AEM Forms] as a Cloud Service를 사용하여 로컬 인프라 없이도 클라우드에서 이러한 모든 기능을 사용할 수 있습니다. 또한 이 서비스는 항상 최신 기능을 유지하므로 조직은 복잡한 업그레이드 주기를 겪을 필요가 없습니다.

Adobe [!DNL Experience Manager Forms as a Cloud Service]는 고객 여정의 모든 단계를 지원하는 고객 중심 솔루션입니다.

<div class="card-container" style="display: flex; flex-wrap: wrap; gap: 20px; margin-bottom: 30px;">
  <div class="card" style="flex: 1 1 calc(50% - 20px); min-width: 300px; border: 1px solid #e1e1e1; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); transition: transform 0.3s ease, box-shadow 0.3s ease;">
    <div class="card-header" style="background-color: #f5f5f5; padding: 15px 20px; border-bottom: 1px solid #e1e1e1;">
      <h3>적응형 양식</h3>
    </div>
    <div class="card-body" style="padding: 20px; background-color: #ffffff;">
      <p>사용자 입력 및 장치 유형에 맞게 조정되는 반응형 동적 양식을 만들 수 있습니다.</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components">적응형 Forms 만들기</a> - 다양한 화면 크기와 사용자 입력에 자동으로 조정되는 양식을 작성합니다.</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction#available-components-a-breakdown-by-component-type">리치 구성 요소 라이브러리</a> - 다양한 입력 필드와 UI 구성 요소를 사용합니다.</li>
        <li><a href="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components">스타일 적응형 Forms</a> - 양식에 일관된 브랜딩 및 시각적 디자인 적용</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components">미리 만들어진 테마 및 템플릿 사용</a> - 바로 사용할 수 있는 구성 요소를 사용하여 개발 가속화</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/rule-editor-core-components/rule-editor-core-components">양식 유효성 검사</a> - 클라이언트측 및 서버측 유효성 검사 규칙 구현</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/configure-submit-actions-core-components">작업 제출</a> - 사용자가 양식을 제출할 때 수행되는 작업 구성</li>
        <li><a href="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/generate-document-of-record-core-components">기록 문서</a> - 제출된 양식 데이터의 영구 레코드 만들기</li>
        <li><a href="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/create-or-add-an-adaptive-form-to-aem-sites-page">AEM Sites 페이지에 Forms 추가</a> - 양식을 웹 사이트에 원활하게 통합</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/embed-adaptive-form-core-components-external-web-page">타사 웹 사이트 페이지에 Forms 추가</a> - 양식을 웹 사이트에 원활하게 통합</li>
      </ul>
    </div>
  </div>

<div class="card" style="flex: 1 1 calc(50% - 20px); min-width: 300px; border: 1px solid #e1e1e1; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); transition: transform 0.3s ease, box-shadow 0.3s ease;">
    <div class="card-header" style="background-color: #f5f5f5; padding: 15px 20px; border-bottom: 1px solid #e1e1e1;">
      <h3>통신 API</h3>
    </div>
    <div class="card-body" style="padding: 20px; background-color: #ffffff;">
      <p>문서를 프로그래밍 방식으로 생성, 조작 및 보호합니다.</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#document-generation">개인화된 커뮤니케이션 생성</a> - 템플릿 및 데이터를 기반으로 사용자 지정된 문서를 만듭니다.</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#document-manipulation">PDF 조합 및 조작</a> - PDF 문서 결합, 분할 및 수정</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#convert-to-and-validate-pdfa-compliant-documents">PDF/A 문서 만들기</a> - 보관 품질 문서 생성</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#signature-apis">서명 적용</a> - 서명을 사용하여 문서 보안</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#encryption-apis">PDF 암호화 및 암호 해독</a> - 중요한 문서 콘텐츠 보호</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#create-PS-PCL-ZPL-documents">XDP를 PostScript으로 변환</a> - XDP 문서를 PostScript 형식으로 변환</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#create-PS-PCL-ZPL-documents">XDP를 PCL로 변환</a> - XDP 문서를 프린터 명령 언어로 변환</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#create-PS-PCL-ZPL-documents">XDP를 ZPL로 변환</a> - XDP 문서를 Zebra 인쇄 언어로 변환</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#convert-to-and-validate-pdfa-compliant-documents">PDF을 PDF/A 표준으로 변환</a> - 보관 호환 PDF 문서 만들기</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction#convert-pdf-documents-to-pdf-x-standards">디지털 서명 추가</a> - 인증을 위해 문서에 디지털 서명</li>
      </ul>
    </div>
  </div>

<div class="card" style="flex: 1 1 calc(50% - 20px); min-width: 300px; border: 1px solid #e1e1e1; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); transition: transform 0.3s ease, box-shadow 0.3s ease;">
    <div class="card-header" style="background-color: #f5f5f5; padding: 15px 20px; border-bottom: 1px solid #e1e1e1;">
      <h3>Forms용 Edge Delivery Services</h3>
    </div>
    <div class="card-body" style="padding: 20px; background-color: #ffffff;">
      <p>Edge Delivery Services을 사용하여 양식 만들기 및 전달:</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/overview">Edge Delivery Forms 개요</a> - Edge Delivery Services이 포함된 양식에 대해 알아보기</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/universal-editor/getting-started-universal-editor">Forms용 유니버설 편집기</a> - WYSIWYG 유니버설 편집기를 사용하여 양식 만들기</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/tutorial">문서 기반 작성</a> - Microsoft Word 또는 Google Docs을 사용하여 양식 만들기</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/universal-editor/style-theme-forms">Edge Delivery Forms 스타일 지정</a> - 양식에 사용자 지정 스타일 적용</li>
      </ul>
    </div>
  </div>

<div class="card" style="flex: 1 1 calc(50% - 20px); min-width: 300px; border: 1px solid #e1e1e1; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); transition: transform 0.3s ease, box-shadow 0.3s ease;">
    <div class="card-header" style="background-color: #f5f5f5; padding: 15px 20px; border-bottom: 1px solid #e1e1e1;">
      <h3>헤드리스 Forms</h3>
    </div>
    <div class="card-body" style="padding: 20px; background-color: #ffffff;">
      <p>모든 채널 또는 프론트엔드 프레임워크에서 양식 경험을 제공할 수 있습니다.</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-headless-adaptive-forms/using/overview">Headless Forms 소개</a> - Forms에 대한 Headless 접근 방식에 대해 알아보기</li>
        <li>React 또는 기타 프론트엔드 프레임워크를 사용하여 양식 작성</li>
        <li>모바일 앱, 웹 사이트 및 채팅 애플리케이션에 양식 통합</li>
        <li>양식 기능으로 기존 UI 구성 요소 활용</li>
        <li>프론트엔드 유연성을 유지하면서 백엔드 양식 논리 유지</li>
      </ul>
    </div>
  </div>

<div class="card" style="flex: 1 1 calc(50% - 20px); min-width: 300px; border: 1px solid #e1e1e1; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); transition: transform 0.3s ease, box-shadow 0.3s ease;">
    <div class="card-header" style="background-color: #f5f5f5; padding: 15px 20px; border-bottom: 1px solid #e1e1e1;">
      <h3>워크플로 자동화</h3>
    </div>
    <div class="card-body" style="padding: 20px; background-color: #ffffff;">
      <p>양식 및 문서 관련 비즈니스 프로세스 자동화:</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference#assign-task-step">비즈니스 프로세스 만들기</a> - 승인 또는 피드백을 위한 양식, 제출 후 워크플로 또는 등록 프로세스를 관리할 백엔드 워크플로를 라우팅합니다.</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference#sign-document-step">AEM 워크플로에서 Adobe Sign 사용</a> - 서명용 문서 보내기 </li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference#generate-document-of-record-step">기록 문서 생성 </a> - 요청 시 또는 양식 제출 시 생성</li>
      </ul>
    </div>
  </div>

<div class="card" style="flex: 1 1 calc(50% - 20px); min-width: 300px; border: 1px solid #e1e1e1; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); transition: transform 0.3s ease, box-shadow 0.3s ease;">
    <div class="card-header" style="background-color: #f5f5f5; padding: 15px 20px; border-bottom: 1px solid #e1e1e1;">
      <h3>전자 서명</h3>
    </div>
    <div class="card-body" style="padding: 20px; background-color: #ffffff;">
      <p>양식 및 문서에 법적 구속력이 있는 전자 서명 추가:</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/forms/integrate/services/adobe-sign-integration-adaptive-forms">Adobe Sign 통합</a> - 적응형 Forms에서 전자 서명 사용</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference#sign-document-step">워크플로에 전자 서명 추가</a> - 비즈니스 프로세스에 서명 단계 포함</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference#generate-document-of-record-step">서명이 있는 기록 문서</a> - 양식 제출의 서명된 기록 생성</li>
      </ul>
    </div>
  </div>

<div class="card" style="flex: 1 1 calc(50% - 20px); min-width: 300px; border: 1px solid #e1e1e1; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); transition: transform 0.3s ease, box-shadow 0.3s ease;">
    <div class="card-header" style="background-color: #f5f5f5; padding: 15px 20px; border-bottom: 1px solid #e1e1e1;">
      <h3>Analytics 및 Insights</h3>
    </div>
    <div class="card-body" style="padding: 20px; background-color: #ffffff;">
      <p>양식 사용 및 성능에 대한 통찰력을 얻으십시오.</p>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation">Adobe Analytics 사용</a> - 양식 사용 및 성능 추적</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/integrate-aem-forms-with-adobe-analytics">수동 Analytics 통합</a> - 세부 추적을 위해 Analytics 설정</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/view-understand-aem-forms-analytics-reports">분석 보고서 보기</a> - 양식 성능 및 사용자 동작 분석</li>
      </ul>
    </div>
  </div>

<div class="card" style="flex: 1 1 calc(50% - 20px); min-width: 300px; border: 1px solid #e1e1e1; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); transition: transform 0.3s ease, box-shadow 0.3s ease;">
    <div class="card-header" style="background-color: #f5f5f5; padding: 15px 20px; border-bottom: 1px solid #e1e1e1;">
      <h3>데이터 통합</h3>
    </div>
    <div class="card-body" style="padding: 20px; background-color: #ffffff;">
      <p>양식을 기존 데이터 소스 및 시스템에 연결합니다.</p>
      <h4>Adobe 에코시스템</h4>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/use-adobe-sign/working-with-adobe-sign">Adobe Sign</a> - Adobe Sign을 통해 전자 서명 전송</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/integrate-adaptive-form-with-market-engage/integrate-form-to-marketo-engage">Marketo Engage</a> - Adobe Marketo Engage과 양식 통합</li>
        <li><a href="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#invoke-an-aem-workflow">AEM 워크플로</a> - 양식 제출을 통해 AEM 워크플로 트리거</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#workfront-fusion">Workfront</a> - Adobe Workfront Fusion에 적응형 양식 제출</li>
      </ul>
      <h4>Microsoft 통합</h4>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-msdynamics">Microsoft Dynamics 365</a> - Microsoft의 CRM과 통합</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage">Azure Blob 저장소</a> - Microsoft 클라우드 저장소에 양식 데이터 저장</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/connect-to-sharepoint/connect-forms-to-sharepoint-document-library">SharePoint 문서 라이브러리</a> - Microsoft SharePoint 문서 라이브러리에 연결</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#connect-af-sharepoint-list">SharePoint 목록</a> - Microsoft SharePoint 목록에 연결</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#submit-to-onedrive">OneDrive</a> - Microsoft OneDrive에 연결</li>
        <li><a href="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/forms/integrate/services/forms-microsoft-power-automate-integration">Microsoft Power Automate</a> - Microsoft Power Automate 플로우 트리거</li>
      </ul>
      <h4>기타 데이터 소스 및 서비스</h4>
      <ul>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/aem-forms-salesforce-integration">Salesforce</a> - Salesforce CRM과 통합</li>
        <li><a href="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#submit-to-rest-endpoint">RESTful 서비스</a> - 모든 REST API 끝점에 연결</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-data-sources">RDBMS 데이터베이스</a> - 관계형 데이터베이스에 연결</li>
        <li><a href="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#send-email">전자 메일</a> - 전자 메일을 통해 양식 데이터 보내기</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/introduction-to-forms-portal/save-core-component-based-form-as-draft">Forms 포털</a> - 초안을 저장하려면 Forms 포털에 제출</li>
        <li><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#send-pdf-via-email">이메일을 통해 PDF 보내기</a> - 제출된 양식의 PDF 버전에 이메일을 보냅니다.</li>
        <li><a href="https://experienceleague.adobe.com/ko/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#submit-using-form-data-model">양식 데이터 모델을 사용하여 제출</a> - 양식 데이터 모델을 사용하여 데이터 제출</li>
      </ul>
    </div>
  </div>
</div>

## AEM Forms as a Cloud Service 시작하기

<div class="card-container" style="display: flex; flex-wrap: wrap; gap: 20px; margin-bottom: 30px;">
  <div class="card" style="flex: 1 1 calc(50% - 20px); min-width: 300px; border: 1px solid #e1e1e1; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); transition: transform 0.3s ease, box-shadow 0.3s ease;">
    <div class="card-header" style="background-color: #f5f5f5; padding: 15px 20px; border-bottom: 1px solid #e1e1e1;">
      <h3>비즈니스 사용자용</h3>
    </div>
    <div class="card-body" style="padding: 20px; background-color: #ffffff;">
      <ol style="margin-top: 10px; padding-left: 25px;">
        <li style="margin-bottom: 8px;"><strong>기본 사항 이해</strong>: <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components">적응형 Forms</a>와 비즈니스 프로세스를 디지털화하는 방법에 대해 알아봅니다.</li>
        <li style="margin-bottom: 8px;"><strong>템플릿 탐색</strong>: <a href="https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components">미리 만들어진 템플릿 및 테마</a>를 탐색하여 양식 프로젝트를 시작하십시오.</li>
        <li style="margin-bottom: 8px;"><strong>양식 작성 학습</strong>: <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/introduction-forms-authoring">양식 작성 가이드</a>에 따라 첫 번째 양식을 만드십시오.</li>
      </ol>
    </div>
  </div>

<div class="card" style="flex: 1 1 calc(50% - 20px); min-width: 300px; border: 1px solid #e1e1e1; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); transition: transform 0.3s ease, box-shadow 0.3s ease;">
    <div class="card-header" style="background-color: #f5f5f5; padding: 15px 20px; border-bottom: 1px solid #e1e1e1;">
      <h3>개발자용</h3>
    </div>
    <div class="card-body" style="padding: 20px; background-color: #ffffff;">
      <ol style="margin-top: 10px; padding-left: 25px;">
        <li style="margin-bottom: 8px;"><strong>환경 설정</strong>: AEM Forms용 <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/setup-local-development-environment">로컬 개발 환경</a>을 구성합니다.</li>
        <li style="margin-bottom: 8px;"><strong>아키텍처 학습</strong>: AEM Forms as a Cloud Service의 <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/forms-overview/aem-forms-cloud-service-architecture">아키텍처 이해</a>.</li>
        <li style="margin-bottom: 8px;"><strong>API 탐색</strong>: Forms 확장 및 통합을 위해 사용 가능한 API </a> 및 SDK를 <a href="https://developer-stage.adobe.com/experience-cloud/experience-manager-apis/api/stable/forms/">에 숙지하십시오.</li>
      </ol>
    </div>
  </div>

<div class="card" style="flex: 1 1 calc(50% - 20px); min-width: 300px; border: 1px solid #e1e1e1; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); transition: transform 0.3s ease, box-shadow 0.3s ease;">
    <div class="card-header" style="background-color: #f5f5f5; padding: 15px 20px; border-bottom: 1px solid #e1e1e1;">
      <h3>관리자용</h3>
    </div>
    <div class="card-body" style="padding: 20px; background-color: #ffffff;">
      <ol style="margin-top: 10px; padding-left: 25px;">
        <li style="margin-bottom: 8px;"><strong>Cloud Service에 온보딩</strong>: <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/setup-forms-cloud-service">온보딩 가이드</a>에 따라 AEM Forms as a Cloud Service을 설정하십시오.</li>
        <li style="margin-bottom: 8px;"><strong>서비스 구성</strong>: Adobe Analytics과 같은 다른 Adobe 서비스와의 <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation">통합을 설정</a>합니다.</li>
        <li style="margin-bottom: 8px;"><strong>AEM 6.5에서 마이그레이션</strong>: AEM 6.5에서 온 경우 <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/migrate-to-forms-as-a-cloud-service.html">마이그레이션 안내서</a>를 따라 Cloud Service으로 이동하십시오.</li>
      </ol>
    </div>
  </div>
</div>

## 얼리 어답터 기능

<div class="card" style="flex: 1 1 calc(50% - 20px); min-width: 300px; border: 1px solid #e1e1e1; border-radius: 8px; overflow: hidden; box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); transition: transform 0.3s ease, box-shadow 0.3s ease; margin-bottom: 30px;">
  <div class="card-header" style="background-color: #f5f5f5; padding: 15px 20px; border-bottom: 1px solid #e1e1e1;">
    <h3>AEM Forms 조기 액세스 프로그램</h3>
  </div>
  <div class="card-body" style="padding: 20px; background-color: #ffffff;">
    <p><a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/forms-overview/early-access-ea-features">AEM Forms 조기 액세스 프로그램</a>에서는 다음을 포함한 최신 기능을 일반적으로 사용하기 전에 독점적으로 액세스할 수 있습니다.</p>
    <ul style="margin-top: 10px; padding-left: 25px;">
      <li style="margin-bottom: 8px;"><strong>AEM Forms AI Assistant(Gen AI)</strong> - AI 기반 제안을 사용하여 양식을 더 빨리 만들기</li>
      <li style="margin-bottom: 8px;"><strong>AEM Forms Workfront Fusion Connector</strong> - 양식 제출로 트리거된 워크플로 자동화</li>
      <li style="margin-bottom: 8px;"><strong>대화형 Forms</strong> - 모든 AEM Sites 페이지에서 채팅 스타일 양식 경험을 만듭니다.</li>
      <li style="margin-bottom: 8px;"><strong>Edge Delivery용 WYSIWYG 작성</strong> - Edge Delivery Services용 유니버설 편집기를 사용하여 양식 작성</li>
      <li style="margin-bottom: 8px;"><strong>AEM Forms-Marketo 커넥터</strong> - 양식 제출을 Marketo Engage과 통합</li>
    </ul>
    <p>혁신적인 조기 액세스 기능 및 자세한 설명서에 대한 전체 목록을 보려면 <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/forms-overview/early-access-ea-features">AEM Forms 조기 액세스 프로그램 페이지</a>를 참조하세요.</p>
  </div>
</div>

<div style="background-color: #f0f7ff; border-left: 4px solid #1473e6; padding: 20px; margin: 30px 0; border-radius: 4px;">
  <h3 style="margin-top: 0; color: #1473e6;">시작할 준비가 되셨습니까?</h3>
  <p>오늘 <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/setup-forms-cloud-service" style="font-weight: bold; color: #1473e6;">AEM Forms as a Cloud Service에 온보딩</a>하여 조직의 디지털 양식 환경을 혁신하십시오.</p>
</div>
