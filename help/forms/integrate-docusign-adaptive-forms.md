---
title: DocuSign을 적응형 양식과 통합하는 방법
description: 적응형 양식과 함께 DocuSign을 사용하여 전자 서명을 수집하는 방법에 대해 알아봅니다.
exl-id: fb2e75d6-e454-4999-a079-f663af79051f
feature: Adaptive Forms, Acrobat Sign
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 7%

---

# 적응형 양식에 DocuSign 사용 {#integrate-aem-forms-with-DocuSign}

DocuSign은 탁월한 전자 서명 솔루션입니다. 계약서에 전자 서명하는 데 사용할 수 있습니다. DocuSign을 적응형 양식과 통합할 수 있습니다. 여러 수신자에게 전자 서명용 적응형 양식을 전송하는 데 도움이 됩니다. 전자 서명을 사용하면 다음과 같은 작업을 수행할 수 있습니다.

- 제안, 견적 및 계약 프로세스가 완전히 자동화된 모든 장치에서 거래를 성사시킵니다.
- 인적 자원 프로세스를 보다 빠르게 완료하고 직원에게 디지털 환경을 제공하십시오.
- 계약 주기 시간을 단축하고 공급업체를 더 빨리 온보딩하십시오.

AEM Forms as a Cloud Service 작업([DocuSign에 대한 사용자 지정 제출](#deploy-custom-submit-action)) 제출 액션은 DocuSign API를 사용하여 전자 서명용 적응형 양식을 전송하는 데 도움이 됩니다.

| Adobe의 전자 서명 솔루션인 Adobe Sign을 사용하여 적응형 양식에 전자 서명할 수도 있습니다. AEM Forms은 Adobe Sign과의 훨씬 더 긴밀한 통합을 제공하며 순차적 및 병렬 서명, 여러 인증 방법, 양식 서명 경험 등과 같은 보다 세밀한 제어 기능을 제공합니다. 자세한 내용은 [적응형 양식에서 Adobe Sign 사용](working-with-adobe-sign.md)을 참조하세요. |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

## 사전 요구 사항 {#prerequisites}

DocuSign과 AEM Forms을 통합하려면 다음 조건을 충족해야 합니다.

- DocuSign [개발자 계정](https://developers.docusign.com/platform/account/)
- DocuSign 애플리케이션
- DocuSign API 애플리케이션의 자격 증명(클라이언트 ID 및 클라이언트 보안).
- [DocuSign용 사용자 지정 제출 액션 및 클라우드 서비스](https://github.com/adobe/aem-forms-docusign-sample)
- (로컬 개발 환경에만 해당) [기록 문서 설정](setup-local-development-environment.md#docker-microservices).

## DocuSign용 사용자 지정 제출 액션 및 클라우드 서비스 구성 {#deploy-custom-submit-action}

AEM Forms as a Cloud Service docuSign에 대한 사용자 정의 제출 액션 제출 액션은 DocuSign API를 사용하여 전자 서명용 적응형 양식을 전송하는 데 도움이 됩니다. 사용자 지정 제출 액션에 대한 코드는 [AEM Forms 샘플 공용 git 저장소](https://github.com/adobe/aem-forms-docusign-sample)에서 사용할 수 있습니다. AEM Forms 환경에 있는 그대로 코드를 배포하거나 조직의 요구 사항에 따라 코드를 사용자 지정할 수 있습니다.

기본 사용자 지정 제출 작업과 DocuSign Cloud Service을 구성하려면 다음 단계를 수행하십시오.

1. [AEM Forms as a Cloud Service 프로젝트를 복제](setup-local-development-environment.md#forms-cloud-service-local-development-environment)하거나 [AEM Archetype 27](https://github.com/adobe/aem-project-archetype) 이상을 기반으로 [!DNL Experience Manager Forms]을(를) [!DNL Cloud Service] 프로젝트로 만듭니다. AEM Archetype을 기반으로 [!DNL Experience Manager Forms]을(를) [!DNL Cloud Service] 프로젝트로 만들려면:
   as a Cloud Service </br> 명령 프롬프트를 열고 아래 명령을 실행하여 [!DNL Experience Manager Forms] 프로젝트를 만듭니다.

   ```shell
   mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=27 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
   ```

   또한 환경을 반영하도록 위의 명령에서 `appTitle`, `appId` 및 `groupId`을(를) 변경하십시오.

1. [aem-forms-samples](https://github.com/adobe/aem-forms-docusign-sample) 리포지토리를 복제합니다. 이 저장소에는 DocuSign 서버에 연결하기 위한 DocuSign에 대한 사용자 정의 제출 액션과 구성 세부 정보가 들어 있습니다.

1. 선택한 IDE의 1단계에서 만든 AEM Forms as a Cloud Service 프로젝트를 엽니다.

1. 편집할 `[AEM Forms as a Cloud Service project]\pom.xml` 파일을 열고 다음 내용을 변경합니다.

   1. `<properties>` 태그의 끝에 다음 텍스트를 추가하십시오.

      ```shell
      <repository.location>maven_repository</repository.location>
      ```

   1. `<repositories>` 태그의 끝에 다음 텍스트를 추가하십시오.

      ```shell
       <repository>
          <id>project-repository</id>
          <url>file://${project.basedir}/${repository.location}</url>
       </repository>
      ```

      `<repositories>` 태그가 없으면 `<properties>` 태그 아래에 태그를 만드십시오.

   1. `<dependencyManagement>` 태그의 끝에 다음 텍스트를 추가하십시오.

      ```shell
       <dependency>
         <groupId>com.adobe.aemforms.samples</groupId>
         <artifactId>forms.integration.docusign.all</artifactId>
         <type>zip</type>
         <version>1.0.0</version>
       </dependency>
      ```

1. Cloud Service 프로젝트 폴더에 있는 `all/pom.xml` 파일에서 다음 단계를 수행하십시오.

   1. `<embeddeds>` 태그의 끝에 다음 텍스트를 추가하십시오.

      ```shell
       <embedded>
          <groupId>com.adobe.aemforms.samples</groupId>
          <artifactId>forms.integration.docusign.all</artifactId>
          <type>zip</type>
          <target>/apps/moonlightprodprogram-vendor-packages/application/install</target>
       </embedded>
      ```

   1. `<dependencies>` 태그의 끝에 다음 텍스트를 추가하십시오.

      ```shell
       <dependency>
          <groupId>com.adobe.aemforms.samples</groupId>
          <artifactId>forms.integration.docusign.all</artifactId>
          <type>zip</type>
       </dependency>
      ```

1. 명령 프롬프트를 열고 `aem-forms-samples\forms-integration-docusign`(3단계에서 복제)으로 이동한 후 다음 명령을 실행합니다.

   ```shell
   mvn clean install -Dinstall.dir="<AEM Forms as a Cloud Service project path>/maven_repository"
   ```

   `<AEM Forms as a Cloud Service project path>`은(는) 이 절차의 1단계에서 만든 폴더의 이름을 참조합니다.

1. 로컬 개발 환경에 프로젝트를 배포합니다. 다음 명령을 사용하여 로컬 개발 환경에 배포할 수 있습니다

   `mvn -PautoInstallPackage clean install`

   이 단계를 실행한 후에는 로컬 개발 환경에서 적응형 양식에 대한 제출 옵션 목록 및 [DocuSign 클라우드 서비스 구성](#configure-docusign-with-aem-forms)에서 사용할 수 있는 새로운 사용자 지정 제출 액션 [DocuSign 전자 서명으로 제출](#enabledocusign)을 볼 수 있습니다.

1. as a Cloud Service [코드를 컴파일하여  [!DNL AEM Forms] 환경에 배포](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#customer-releases)합니다.

## [!DNL DocuSign]과(와) [!DNL AEM Forms] 통합 {#configure-docusign-with-aem-forms}

전제 조건이 갖추어지면 다음 단계를 통해 작성자 인스턴스에서 [!DNL DocuSign]을(를) [!DNL AEM Forms]과(와) 통합합니다.

1. **[!UICONTROL 도구]** ![hammer](assets/hammer.png) > **[!UICONTROL Cloud Service]** > **[!UICONTROL DocuSign]**(으)로 이동한 다음 구성을 호스트할 폴더를 선택하십시오.

1. 구성 페이지에서 **[!UICONTROL 만들기]**&#x200B;를 선택하여 AEM Forms에서 [!DNL DocuSign] 구성을 만듭니다.
1. **[!UICONTROL DocuSign 구성 만들기]** 페이지의 **[!UICONTROL 일반]** 탭에서 구성에 대한 **[!UICONTROL 이름]**&#x200B;을 지정하고 **[!UICONTROL 다음]**&#x200B;을 선택합니다. 선택적으로 **[!UICONTROL 제목]**&#x200B;을 지정할 수 있습니다.

1. 현재 브라우저 창의 URL을 메모장에 복사합니다. 이 URL은 이후 단계에서 [!DNL AEM Forms]를 사용해 [!DNL DocuSign]을 구성하는 데 필요합니다.

1. [!DNL DocuSign] 애플리케이션에 대한 OAuth 설정을 구성합니다.

   1. 브라우저 창을 열고 [!DNL DocuSign] [개발자 계정](https://admindemo.docusign.com/apps-and-keys)에 로그인합니다.
   1. [!DNL AEM Forms]에 대해 구성된 앱을 엽니다.
   1. **[!UICONTROL 리디렉션 URI]** 상자에서 이전 단계에서 복사한 URL을 추가하고 **[!UICONTROL 저장]**&#x200B;을 클릭합니다.
   1. 통합 및 암호 키를 메모해 둡니다.

   [!DNL DocuSign] 애플리케이션에 대한 OAuth 설정을 구성하고 키를 얻는 방법에 대한 단계별 정보는 [애플리케이션에 대한 oAuth 설정 구성](https://support.docusign.com/guides/ndse-admin-guide-api-and-keys) 개발자 문서를 참조하십시오.

1. **[!UICONTROL DocuSign 구성 만들기]** 페이지로 돌아갑니다. **[!UICONTROL 설정]** 탭에서 **[!UICONTROL OAuth URL]** 필드에 다음 기본 URL이 언급되어 있습니다.

   `https://account-d.docusign.com/oauth/auth`

1. **[!UICONTROL 클라이언트 ID]**(DocuSign 통합 키) 및 **[!UICONTROL 클라이언트 암호]**(DocuSign 암호 키)를 지정하십시오.

1. **[!UICONTROL DocuSign에 연결]**&#x200B;을 선택합니다. 자격 증명을 입력하라는 메시지가 뜨면 [!DNL DocuSign] 애플리케이션 생성 시 사용한 계정의 사용자 이름과 비밀번호를 입력합니다. `your developer account`에 대한 액세스를 확인하는 메시지가 표시되면 **[!UICONTROL 액세스 허용]**&#x200B;을 클릭하세요. 자격 증명이 올바르면 성공 메시지가 나타납니다.

1. [!DNL DocuSign] 구성을 만들려면 **[!UICONTROL 만들기]**&#x200B;를 선택하십시오.

1. 구성을 선택하고 **[!UICONTROL Publish]**&#x200B;을 클릭한 다음 구성을 선택하고 **[!UICONTROL Publish]**&#x200B;을 클릭합니다. 해당 게시 환경에 구성이 복사됩니다.

1. 위의 모든 단계를 개발자, 스테이지 및 생산 인스턴스(어느 것이든 남은 인스턴스에)에 반복하여, 해당 환경을 위한 [!DNL AEM Forms]를 사용한 [!DNL DocuSign] 구성을 완료합니다.

이제 AEM Forms 환경이 DocuSign을 사용하도록 구성되었습니다. Cloud Service에 사용되는 구성 컨테이너를 [!DNL DocuSign]을 위해 활성화하고자 하는 모든 적응형 양식에 추가해야 합니다. 적응형 양식의 속성에서 구성 컨테이너를 지정할 수 있습니다.

### 적응형 양식에서 [!DNL DocuSign] 사용 {#enabledocusign}

기존 적응형 양식에 대해 [!DNL DocuSign]을(를) 활성화하거나 [!DNL DocuSign]이(가) 활성화된 적응형 양식을 만들 수 있습니다. 다음 중 하나를 선택합니다.

- [ [!DNL DocuSign] 활성화된 적응형 양식 만들기](#create-an-adaptive-form-for-docusign)
- 기존 적응형 양식에 대해 [사용 [!DNL DocuSign] 합니다](#editafsign).

#### DocuSign용 적응형 양식 만들기 {#create-an-adaptive-form-for-docusign}

Sign이 활성화된 적응형 양식을 만들려면 다음 작업을 수행하십시오.

1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**&#x200B;로 이동합니다.
1. **[!UICONTROL 만들기]**&#x200B;를 선택하고 **[!UICONTROL 적응형 양식]**&#x200B;을 선택하세요. 템플릿 목록이 나타납니다. 템플릿을 선택하고 **[!UICONTROL 다음]**&#x200B;을(를) 선택하십시오.
1. **[!UICONTROL 기본]** 탭에서:

   1. 적응형 양식에 대해 **[!UICONTROL 이름]** 및 **[!UICONTROL 제목]**&#x200B;을 지정하십시오.

   1. [통합 [!DNL DocuSign] 을(를)  [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md)하는 동안 만든 [구성 컨테이너](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms)를 선택하십시오.

   구성 컨테이너에는 환경에 대해 구성된 [!DNL DocuSign] Cloud Service이 포함되어 있습니다. 이러한 서비스는 적응형 양식 편집기에서 선택할 수 있습니다.

1. **[!UICONTROL 양식 모델]** 탭에서 다음 옵션 중 하나를 선택합니다.

   - 사용자 지정 양식 서식 파일이 있고 양식 서식 파일을 기반으로 기록 문서가 필요한 경우 **[!UICONTROL 양식 서식 파일을 기록 문서 서식 파일로 연결]** 옵션을 선택하고 기록 문서 서식 파일을 선택하십시오. 옵션을 사용하면 서명을 위해 전송된 문서에 관련 양식 템플릿을 기반으로 하는 필드만 표시됩니다. 적응형 양식의 모든 필드가 표시되지는 않습니다.

   - 사용자 지정 양식 서식 파일이 없는 경우 **[!UICONTROL 기록 문서 생성]** 옵션을 선택하십시오. 옵션을 사용하면 서명을 위해 전송된 문서에 적응형 양식의 모든 필드가 표시됩니다.

1. **[!UICONTROL 만들기를 선택합니다.]** 기호가 활성화된 적응형 양식이 만들어집니다. [!DNL DocuSign] 필드를 양식에 추가하고 서명을 위해 보낼 수 있습니다.
1. 편집 모드에서 적응형 양식을 엽니다. **[!UICONTROL 콘텐츠]** 탭에서 **[!UICONTROL 양식 컨테이너]**&#x200B;를 선택하고 ![구성](assets/configure-icon.svg)을 선택합니다.

1. **[!UICONTROL 제출]** 섹션의 **[!UICONTROL 제출 액션]** 드롭다운 목록에서 **[!UICONTROL DocuSign 전자 서명으로 제출]**&#x200B;을 선택합니다.

1. **[!UICONTROL 작업 구성]** 섹션에서 **[!UICONTROL 추가]**&#x200B;를 선택하여 받는 사람을 추가하고 받는 사람의 전자 메일 주소를 지정하십시오. 받는 사람을 더 추가하려면 **[!UICONTROL 추가]**&#x200B;를 다시 선택하십시오.

1. **[!UICONTROL 전자 메일 제목]** 필드에 전자 메일 메시지의 제목을 지정합니다. 전자 메일 메시지에 첨부 파일을 포함하려면 **첨부 파일 포함**&#x200B;을 선택하세요.

1. 속성을 저장하려면 ![저장](assets/save_icon.svg)을(를) 선택하십시오.

#### 적응형 양식에 [!DNL DocuSign] 사용 {#editafsign}

기존 적응형 양식에서 [!DNL DocuSign]을(를) 사용하려면:

1. **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**&#x200B;로 이동합니다.
1. 적응형 양식을 선택하고 **[!UICONTROL 속성]**&#x200B;을 선택합니다.
1. **[!UICONTROL 기본]** 탭에서 [!DNL DocuSign]을(를) [!DNL AEM Forms]과(와) 통합하는 동안 만든 [구성 컨테이너](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms)을(를) 선택합니다.
1. **[!UICONTROL 양식 모델]** 탭에서 다음 옵션 중 하나를 선택합니다.

   - 사용자 지정 양식 서식 파일이 있고 양식 서식 파일을 기반으로 기록 문서가 필요한 경우 **[!UICONTROL 양식 서식 파일을 기록 문서 서식 파일로 연결]** 옵션을 선택하고 기록 문서 서식 파일을 선택하십시오. 옵션을 사용하면 서명을 위해 전송된 문서에 관련 양식 템플릿을 기반으로 하는 필드만 표시됩니다. 적응형 양식의 모든 필드가 표시되지는 않습니다.

   - 사용자 지정 양식 서식 파일이 없는 경우 **[!UICONTROL 기록 문서 생성]** 옵션을 선택하십시오. 옵션을 사용하면 서명을 위해 전송된 문서에 적응형 양식의 모든 필드가 표시됩니다.

1. **[!UICONTROL 저장 및 닫기]**&#x200B;를 선택합니다. [!DNL DocuSign]에 대해 적응형 양식을 사용할 수 있습니다. 이제 양식에 [!DNL DocuSign] 필드를 추가하고 서명을 위해 전송할 수 있습니다.

1. 편집 모드에서 적응형 양식을 엽니다. **[!UICONTROL 콘텐츠]** 탭에서 **[!UICONTROL 양식 컨테이너]**&#x200B;를 선택하고 ![구성](assets/configure-icon.svg)을 선택합니다.

1. **[!UICONTROL 제출]** 섹션의 **[!UICONTROL 제출 액션]** 드롭다운 목록에서 **[!UICONTROL DocuSign 전자 서명으로 제출]**&#x200B;을 선택합니다.

1. **[!UICONTROL 작업 구성]** 섹션에서 **[!UICONTROL 추가]**&#x200B;를 선택하여 받는 사람을 추가하고 받는 사람의 전자 메일 주소를 지정하십시오. 받는 사람을 더 추가하려면 **[!UICONTROL 추가]**&#x200B;를 다시 선택하십시오.

1. **[!UICONTROL 전자 메일 제목]** 필드에 전자 메일 메시지의 제목을 지정합니다. 전자 메일 메시지에 첨부 파일을 포함하려면 **첨부 파일 포함**&#x200B;을 선택하세요.

1. 속성을 저장하려면 ![저장](assets/save_icon.svg)을(를) 선택하십시오.
