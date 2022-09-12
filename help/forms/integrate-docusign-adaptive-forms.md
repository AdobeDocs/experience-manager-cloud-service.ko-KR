---
title: 적응형 양식과 DocuSign 통합
description: 적응형 양식으로 DocumentSign을 사용하여 전자 서명을 수집하는 방법을 알아봅니다.
exl-id: fb2e75d6-e454-4999-a079-f663af79051f
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1557'
ht-degree: 9%

---

# 적응형 양식으로 DocuSign 사용 {#integrate-aem-forms-with-DocuSign}

DocuSign은 뛰어난 전자 서명 솔루션입니다. 이를 사용하여 계약에 전자 서명을 할 수 있습니다. DocuSign을 적응형 양식과 통합할 수 있습니다. 여러 수신자에게 전자 서명을 위한 적응형 양식을 전송하는 데 도움이 됩니다. 전자 서명을 사용하면 다음 작업을 수행할 수 있습니다.

- 완전히 자동화된 제안, 견적 및 계약 프로세스를 사용하여 모든 장치의 거래를 마감합니다.
- 인적 자원 프로세스를 보다 신속하게 완료하고 직원들에게 디지털 경험을 제공합니다.
- 계약 주기를 단축하고 공급업체 가입을 보다 신속하게 처리합니다.

AEM Forms as a Cloud Service [DocuSign에 대한 사용자 지정 제출 작업](#deploy-custom-submit-action). 제출 작업은 DocumentSign API를 사용하여 전자 서명을 위한 적응형 양식을 전송하는 데 도움이 됩니다.

| Adobe의 전자 서명 솔루션인 Adobe Sign을 사용하여 적응형 양식에 전자 서명할 수도 있습니다. AEM Forms은 Adobe Sign과 더욱 긴밀하게 통합되어 있으며 순차적 및 병렬 서명, 여러 인증 방법, 양식 서명 경험 등과 같은 보다 세밀하게 제어할 수 있습니다. 자세한 내용은 [적응형 양식에서 Adobe Sign 사용](working-with-adobe-sign.md). |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

## 사전 요구 사항 {#prerequisites}

DocuSign을 AEM Forms과 통합하려면 다음 항목이 필요합니다.

- DocuSign [개발자 계정](https://developers.docusign.com/platform/account/)
- DocuSign 응용 프로그램
- DocuSign API 애플리케이션의 자격 증명(클라이언트 ID 및 클라이언트 암호)입니다.
- [DocuSign용 사용자 정의 제출 작업 및 클라우드 서비스](https://github.com/adobe/aem-forms-docusign-sample)
- (로컬 개발 환경만 해당) [레코드의 설정 문서](setup-local-development-environment.md#docker-microservices).

## DocuSign에 대한 사용자 지정 제출 작업 및 클라우드 서비스 구성 {#deploy-custom-submit-action}

AEM Forms as a Cloud Service은 DocumentSign에 대한 사용자 지정 제출 작업을 제공합니다. 제출 작업은 DocumentSign API를 사용하여 전자 서명을 위한 적응형 양식을 전송하는 데 도움이 됩니다. 사용자 지정 제출 작업에 대한 코드는 [AEM Forms 샘플 공개 git 리포지토리](https://github.com/adobe/aem-forms-docusign-sample). 코드를 AEM Forms 환경에 있는 그대로 배포하거나 조직의 요구 사항에 따라 사용자 지정할 수 있습니다.

바로 사용 가능한 사용자 지정 제출 작업 및 DocumentSign Cloud Service을 구성하려면 다음 단계를 수행하십시오.

1. [AEM Forms as a Cloud Service 프로젝트 복제](setup-local-development-environment.md#forms-cloud-service-local-development-environment) 또는 만들기 [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] 프로젝트 기반 [AEM Archetype 27](https://github.com/adobe/aem-project-archetype) 또는 나중에 사용합니다. 을(를) 만들려면 [!DNL Experience Manager Forms] 로서의 [!DNL Cloud Service] AEM Archetype을 기반으로 하는 프로젝트:
   </br> 명령 프롬프트를 열고 아래 명령을 실행하여 [!DNL Experience Manager Forms] as a Cloud Service 프로젝트:

   ```shell
   mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=27 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
   ```

   또한, `appTitle`, `appId`, 및 `groupId`를 입력하여 환경을 반영하십시오.

1. 복제 [aem-forms-samples](https://github.com/adobe/aem-forms-docusign-sample) 저장소. 이 저장소에는 DocuSign에 대한 사용자 지정 제출 작업과 DocuSign 서버에 연결할 구성 세부 사항이 포함되어 있습니다.

1. 선택한 IDE에서 편집을 위해 1단계에서 만든 AEM Forms as a Cloud Service 프로젝트를 엽니다.

1. 를 엽니다. `[AEM Forms as a Cloud Service project]\pom.xml` 편집할 파일로 다음 변경 작업을 수행합니다.

   1. 의 끝에 다음 텍스트를 추가합니다 `<properties>` 태그:

      ```shell
      <repository.location>maven_repository</repository.location>
      ```

   1. 의 끝에 다음 텍스트를 추가합니다 `<repositories>` 태그:

      ```shell
       <repository>
          <id>project-repository</id>
          <url>file://${project.basedir}/${repository.location}</url>
       </repository>
      ```

      없는 경우 `<repositories>` 태그를 만든 후 태그 아래에 태그를 만듭니다 `<properties>` 태그에 가깝게 포함했습니다.

   1. 의 끝에 다음 텍스트를 추가합니다 `<dependencyManagement>` 태그:

      ```shell
       <dependency>
         <groupId>com.adobe.aemforms.samples</groupId>
         <artifactId>forms.integration.docusign.all</artifactId>
         <type>zip</type>
         <version>1.0.0</version>
       </dependency>
      ```

1. 에서 다음 단계를 수행하십시오. `all/pom.xml` Cloud Service 프로젝트 폴더에서 사용할 수 있는 파일:

   1. 의 끝에 다음 텍스트를 추가합니다 `<embeddeds>` 태그:

      ```shell
       <embedded>
          <groupId>com.adobe.aemforms.samples</groupId>
          <artifactId>forms.integration.docusign.all</artifactId>
          <type>zip</type>
          <target>/apps/moonlightprodprogram-vendor-packages/application/install</target>
       </embedded>
      ```

   1. 의 끝에 다음 텍스트를 추가합니다 `<dependencies>` 태그:

      ```shell
       <dependency>
          <groupId>com.adobe.aemforms.samples</groupId>
          <artifactId>forms.integration.docusign.all</artifactId>
          <type>zip</type>
       </dependency>
      ```

1. 명령 프롬프트를 열고 다음 위치로 이동합니다. `aem-forms-samples\forms-integration-docusign` (3단계에서 복제됨) 및 다음 명령을 실행합니다.

   ```shell
   mvn clean install -Dinstall.dir="<AEM Forms as a Cloud Service project path>/maven_repository"
   ```

   `<AEM Forms as a Cloud Service project path>` 는 이 절차의 1단계에서 생성된 폴더의 이름을 나타냅니다.

1. 프로젝트를 로컬 개발 환경에 배포합니다. 다음 명령을 사용하여 로컬 개발 환경에 배포할 수 있습니다

   `mvn -PautoInstallPackage clean install`

   이러한 단계를 실행한 후 새 사용자 지정 제출 작업을 볼 수 있습니다 [DocuSign 전자 서명을 사용하여 제출](#enabledocusign) 적응형 양식 및 [DocuSign 클라우드 서비스 구성](#configure-docusign-with-aem-forms) 를 사용하도록 선택할 수 있습니다.

1. 컴파일 및 [코드를 [!DNL AEM Forms] as a Cloud Service 환경](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#customer-releases).

## 통합 [!DNL DocuSign] with [!DNL AEM Forms] {#configure-docusign-with-aem-forms}

사전 요구 사항이 준비되면 다음 단계를 수행하여 을 통합합니다 [!DNL DocuSign] with [!DNL AEM Forms] 작성자 인스턴스에 표시합니다.

1. 다음으로 이동 **[!UICONTROL 도구]** ![망치](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL DocuSign]** 구성을 호스트할 폴더를 선택합니다.

1. 구성 페이지에서 **[!UICONTROL 만들기]** 만들기 [!DNL DocuSign] AEM Forms의 구성.
1. 에서 **[!UICONTROL 일반]** 의 탭 **[!UICONTROL DocuSign 구성 만들기]** 페이지에서, **[!UICONTROL 이름]** 구성에 대해 를 탭하고 **[!UICONTROL 다음]**. 원할 경우 **[!UICONTROL 제목]**.

1. 현재 브라우저 창의 URL을 메모장에 복사합니다. 이 URL은 이후 단계에서 [!DNL AEM Forms]를 사용해 [!DNL DocuSign]을 구성하는 데 필요합니다.

1. [!DNL DocuSign] 애플리케이션에 대한 OAuth 설정을 구성합니다.

   1. 브라우저 창을 열고 [!DNL DocuSign][ 개발자 계정에 로그인합니다](https://admindemo.docusign.com/apps-and-keys).
   1. 에 대해 구성된 앱을 엽니다. [!DNL AEM Forms].
   1. 에서 **[!UICONTROL 리디렉션 URI]** 상자에서 이전 단계에서 복사한 URL을 추가하고 을(를) 클릭합니다 **[!UICONTROL 저장]**.
   1. 통합 및 비밀 키를 참조하십시오.

   [!DNL DocuSign] 애플리케이션에 대한 OAuth 설정을 구성하고 키를 얻는 방법에 대한 단계별 정보는 [애플리케이션에 대한 oAuth 설정 구성](https://support.docusign.com/guides/ndse-admin-guide-api-and-keys) 개발자 문서를 참조하십시오.

1. 로 돌아갑니다. **[!UICONTROL DocuSign 구성 만들기]** 페이지. 에서 **[!UICONTROL 설정]** 탭, **[!UICONTROL OAuth URL]** 필드에 다음 기본 URL이 설명되어 있습니다.

   `https://account-d.docusign.com/oauth/auth`

1. 을(를) 지정합니다. **[!UICONTROL 클라이언트 ID]** (DocuSign 통합 키) 및 **[!UICONTROL 클라이언트 암호]** (DocuSign 암호 키).

1. 탭 **[!UICONTROL DocuSign에 연결]**. 자격 증명을 입력하라는 메시지가 뜨면 [!DNL DocuSign] 애플리케이션 생성 시 사용한 계정의 사용자 이름과 비밀번호를 입력합니다. 에 대한 액세스 확인을 묻는 경우 `your developer account`를 클릭합니다. **[!UICONTROL 액세스 허용]**. 자격 증명이 올바르면 성공 메시지가 나타납니다.

1. 탭 **[!UICONTROL 만들기]** 를 클릭하여 [!DNL DocuSign] 구성.

1. 구성을 선택하고 을(를) 클릭합니다 **[!UICONTROL 게시]**&#x200B;를 클릭하고 구성을 선택한 다음 를 클릭합니다. **[!UICONTROL 게시]**. 해당 게시 환경에 구성이 복사됩니다.

1. 위의 모든 단계를 개발자, 스테이지 및 생산 인스턴스(어느 것이든 남은 인스턴스에)에 반복하여, 해당 환경을 위한 [!DNL AEM Forms]를 사용한 [!DNL DocuSign] 구성을 완료합니다.

이제 AEM Forms 환경이 DocuSign을 사용하도록 구성되었습니다. Cloud Service에 사용되는 구성 컨테이너를 [!DNL DocuSign]을 위해 활성화하고자 하는 모든 적응형 양식에 추가해야 합니다. 적응형 양식의 속성에서 구성 컨테이너를 지정할 수 있습니다.

### 사용 [!DNL DocuSign] 적응형 양식에 {#enabledocusign}

다음을 활성화할 수 있습니다 [!DNL DocuSign] 기존 적응형 양식에 대해 또는 [!DNL DocuSign] 적응형 양식을 활성화했습니다. 다음 중 하나를 선택합니다.

- [만들기 [!DNL DocuSign] 적응형 양식 사용](#create-an-adaptive-form-for-docusign)
- [활성화 [!DNL DocuSign] 기존 적응형 양식](#editafsign).

#### DocuSign용 적응형 양식 만들기 {#create-an-adaptive-form-for-docusign}

서명 사용 적응형 양식을 만들려면 다음을 수행하십시오.

1. 다음으로 이동 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.
1. 탭 **[!UICONTROL 만들기]** 을(를) 선택합니다. **[!UICONTROL 적응형 양식]**. 템플릿 목록이 나타납니다. 템플릿을 선택하고 탭합니다 **[!UICONTROL 다음]**.
1. 에서 **[!UICONTROL 기본]** 탭:

   1. 을(를) 지정합니다. **[!UICONTROL 이름]** 및 **[!UICONTROL 제목]** 추가 정보.

   1. 을(를) 선택합니다 [구성 컨테이너](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) 다음 기간 동안 [통합 [!DNL DocuSign] with [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md).
   구성 컨테이너에는 [!DNL DocuSign] 환경에 대해 구성된 Cloud Services. 이러한 서비스는 적응형 양식 편집기에서 선택할 수 있습니다.

1. 에서 **[!UICONTROL 양식 모델]** 탭에서 다음 옵션 중 하나를 선택합니다.

   - 사용자 지정 양식 서식 파일이 있고 양식 서식 파일을 기반으로 한 기록 문서가 필요한 경우 **[!UICONTROL 양식 서식 파일을 레코드 문서로 연결]** 옵션을 선택하고 레코드 문서 템플릿을 선택합니다. 옵션을 사용하면 서명을 위해 전송된 문서가 연관된 양식 템플릿을 기반으로 하는 필드만 표시됩니다. 적용형 양식의 모든 필드가 표시되지 않습니다.

   - 사용자 지정 양식 템플릿이 없는 경우 **[!UICONTROL 기록 문서 생성]** 선택 사항입니다. 옵션을 사용하면 서명을 위해 전송된 문서에 적응형 양식의 모든 필드가 표시됩니다.

1. 탭 **[!UICONTROL 만들기.]** 서명 사용 적응형 양식이 만들어집니다. 을(를) 추가할 수 있습니다 [!DNL DocuSign] 필드를 양식에 입력하고 서명을 위해 전송합니다.
1. 편집 모드에서 적응형 양식을 엽니다. 에서 **[!UICONTROL 컨텐츠]** 탭에서 **[!UICONTROL 양식 컨테이너]** 탭 ![구성](assets/configure-icon.svg).

1. 에서 **[!UICONTROL 제출]** 섹션, **[!UICONTROL DocuSign 전자 서명을 사용하여 제출]** 에서 **[!UICONTROL 작업 제출]** 드롭다운 목록.

1. 에서 **[!UICONTROL 작업 구성]** 섹션, 탭 **[!UICONTROL 추가]** 수신자를 추가하고 수신자의 이메일 주소를 지정하려면 탭 **[!UICONTROL 추가]** 다시 한 번 더 수신자를 추가합니다.

1. 에서 이메일 메시지의 제목을 지정합니다 **[!UICONTROL 이메일 제목]** 필드. 선택 **첨부 파일 포함** 전자 메일 메시지에 첨부 파일을 포함하도록 업데이트되고 수정되었습니다.

1. 탭 ![저장](assets/save_icon.svg) 속성을 저장합니다.

#### 활성화 [!DNL DocuSign] 적용형 양식 {#editafsign}

를 사용하려면 [!DNL DocuSign] 기존 적응형 양식에서:

1. 다음으로 이동 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.
1. 적응형 양식을 선택하고 탭합니다 **[!UICONTROL 속성]**.
1. 에서 **[!UICONTROL 기본]** 탭에서 을 선택합니다 [구성 컨테이너](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) 통합 중 생성됨 [!DNL DocuSign] with [!DNL AEM Forms].
1. 에서 **[!UICONTROL 양식 모델]** 탭에서 다음 옵션 중 하나를 선택합니다.

   - 사용자 지정 양식 서식 파일이 있고 양식 서식 파일을 기반으로 한 기록 문서가 필요한 경우 **[!UICONTROL 양식 서식 파일을 레코드 문서로 연결]** 옵션을 선택하고 레코드 문서 템플릿을 선택합니다. 옵션을 사용하면 서명을 위해 전송된 문서가 연관된 양식 템플릿을 기반으로 하는 필드만 표시됩니다. 적용형 양식의 모든 필드가 표시되지 않습니다.

   - 사용자 지정 양식 템플릿이 없는 경우 **[!UICONTROL 기록 문서 생성]** 선택 사항입니다. 옵션을 사용하면 서명을 위해 전송된 문서에 적응형 양식의 모든 필드가 표시됩니다.

1. 탭 **[!UICONTROL 저장 및 닫기]**. 적응형 양식은 다음에 대해 활성화됩니다. [!DNL DocuSign]. 이제 [!DNL DocuSign] 필드를 양식에 입력하고 서명을 위해 전송합니다.

1. 편집 모드에서 적응형 양식을 엽니다. 에서 **[!UICONTROL 컨텐츠]** 탭에서 **[!UICONTROL 양식 컨테이너]** 탭 ![구성](assets/configure-icon.svg).

1. 에서 **[!UICONTROL 제출]** 섹션, **[!UICONTROL DocuSign 전자 서명을 사용하여 제출]** 에서 **[!UICONTROL 작업 제출]** 드롭다운 목록.

1. 에서 **[!UICONTROL 작업 구성]** 섹션, 탭 **[!UICONTROL 추가]** 수신자를 추가하고 수신자의 이메일 주소를 지정하려면 탭 **[!UICONTROL 추가]** 다시 한 번 더 수신자를 추가합니다.

1. 에서 이메일 메시지의 제목을 지정합니다 **[!UICONTROL 이메일 제목]** 필드. 선택 **첨부 파일 포함** 전자 메일 메시지에 첨부 파일을 포함하도록 업데이트되고 수정되었습니다.

1. 탭 ![저장](assets/save_icon.svg) 속성을 저장합니다.
