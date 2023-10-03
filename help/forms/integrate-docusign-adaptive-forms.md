---
title: DocuSign을 적응형 양식과 통합하는 방법
description: 적응형 양식과 함께 DocuSign을 사용하여 전자 서명을 수집하는 방법에 대해 알아봅니다.
exl-id: fb2e75d6-e454-4999-a079-f663af79051f
source-git-commit: 92f89243b79c6c2377db3ca2b8ea244957416626
workflow-type: tm+mt
source-wordcount: '1559'
ht-degree: 10%

---

# 적응형 양식에 DocuSign 사용 {#integrate-aem-forms-with-DocuSign}

DocuSign은 탁월한 전자 서명 솔루션입니다. 계약서에 전자 서명하는 데 사용할 수 있습니다. DocuSign을 적응형 양식과 통합할 수 있습니다. 여러 수신자에게 전자 서명용 적응형 양식을 전송하는 데 도움이 됩니다. 전자 서명을 사용하면 다음과 같은 작업을 수행할 수 있습니다.

- 제안, 견적 및 계약 프로세스가 완전히 자동화된 모든 장치에서 거래를 성사시킵니다.
- 인적 자원 프로세스를 보다 빠르게 완료하고 직원에게 디지털 환경을 제공하십시오.
- 계약 주기 시간을 단축하고 공급업체를 더 빨리 온보딩하십시오.

AEM Forms은 as a Cloud Service으로 [DocuSign에 대한 사용자 정의 제출 액션](#deploy-custom-submit-action). 제출 액션은 DocuSign API를 사용하여 전자 서명용 적응형 양식을 전송하는 데 도움이 됩니다.

| Adobe의 전자 서명 솔루션인 Adobe Sign을 사용하여 적응형 양식에 전자 서명할 수도 있습니다. AEM Forms은 Adobe Sign과의 훨씬 더 긴밀한 통합을 제공하며 순차적 및 병렬 서명, 여러 인증 방법, 양식 서명 경험 등과 같은 보다 세밀한 제어 기능을 제공합니다. 자세한 내용은 [적응형 양식에서 Adobe Sign 사용](working-with-adobe-sign.md). |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

## 사전 요구 사항 {#prerequisites}

DocuSign과 AEM Forms을 통합하려면 다음 조건을 충족해야 합니다.

- 도큐사인 [개발자 계정](https://developers.docusign.com/platform/account/)
- DocuSign 애플리케이션
- DocuSign API 애플리케이션의 자격 증명(클라이언트 ID 및 클라이언트 보안).
- [DocuSign용 사용자 정의 제출 액션 및 클라우드 서비스](https://github.com/adobe/aem-forms-docusign-sample)
- (로컬 개발 환경에만 해당) [기록 문서 설정](setup-local-development-environment.md#docker-microservices).

## DocuSign용 사용자 지정 제출 액션 및 클라우드 서비스 구성 {#deploy-custom-submit-action}

AEM Forms as a Cloud Service에서는 DocuSign에 대한 사용자 지정 제출 액션을 제공합니다. 제출 액션은 DocuSign API를 사용하여 전자 서명용 적응형 양식을 전송하는 데 도움이 됩니다. 사용자 지정 제출 액션 코드는에서 사용할 수 있습니다. [AEM Forms 샘플 공개 git 저장소](https://github.com/adobe/aem-forms-docusign-sample). AEM Forms 환경에 있는 그대로 코드를 배포하거나 조직의 요구 사항에 따라 코드를 사용자 지정할 수 있습니다.

기본 사용자 지정 제출 작업과 DocuSign Cloud Service을 구성하려면 다음 단계를 수행하십시오.

1. [AEM Forms as a Cloud Service 프로젝트 복제](setup-local-development-environment.md#forms-cloud-service-local-development-environment) 또는 만들기 [!DNL Experience Manager Forms] as a [!DNL Cloud Service] 프로젝트 기준 [AEM Archetype 27](https://github.com/adobe/aem-project-archetype) 나중에 을(를) 만들려면 [!DNL Experience Manager Forms] as a [!DNL Cloud Service] AEM Archetype 기반 프로젝트:
   </br> 명령 프롬프트를 열고 아래 명령을 실행하여 [!DNL Experience Manager Forms] as a Cloud Service 프로젝트:

   ```shell
   mvn -B archetype:generate -DarchetypeGroupId=com.adobe.aem -DarchetypeArtifactId=aem-project-archetype -DarchetypeVersion=27 -DaemVersion="cloud" -DappTitle="My Site" -DappId="mysite" -DgroupId="com.mysite" -DincludeForms="y"
   ```

   또한, 변경 `appTitle`, `appId`, 및 `groupId`를 입력하여 위의 명령을 사용할 수 있습니다.

1. 복제 [aem-forms-samples](https://github.com/adobe/aem-forms-docusign-sample) 리포지토리. 이 저장소에는 DocuSign 서버에 연결하기 위한 DocuSign에 대한 사용자 정의 제출 액션과 구성 세부 정보가 들어 있습니다.

1. 선택한 IDE에서 편집할 수 있도록 1단계에서 만든 AEM Forms as a Cloud Service 프로젝트를 엽니다.

1. 를 엽니다. `[AEM Forms as a Cloud Service project]\pom.xml` 편집할 파일 및 다음 변경 작업을 수행합니다.

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

      없는 경우 `<repositories>` 태그, 아래 태그 만들기 `<properties>` 태그에 가깝게 배치하십시오.

   1. 의 끝에 다음 텍스트를 추가합니다 `<dependencyManagement>` 태그:

      ```shell
       <dependency>
         <groupId>com.adobe.aemforms.samples</groupId>
         <artifactId>forms.integration.docusign.all</artifactId>
         <type>zip</type>
         <version>1.0.0</version>
       </dependency>
      ```

1. 에서 다음 단계를 수행합니다. `all/pom.xml` Cloud Service 프로젝트 폴더에서 사용할 수 있는 파일:

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

1. 명령 프롬프트를 열고 다음 위치로 이동합니다. `aem-forms-samples\forms-integration-docusign` (3단계에서 복제) 다음 명령을 실행합니다.

   ```shell
   mvn clean install -Dinstall.dir="<AEM Forms as a Cloud Service project path>/maven_repository"
   ```

   `<AEM Forms as a Cloud Service project path>` 는 이 절차의 1단계에서 만든 폴더의 이름을 나타냅니다.

1. 로컬 개발 환경에 프로젝트를 배포합니다. 다음 명령을 사용하여 로컬 개발 환경에 배포할 수 있습니다

   `mvn -PautoInstallPackage clean install`

   이러한 단계를 실행한 후 새 사용자 지정 제출 액션을 볼 수 있습니다 [DocuSign 전자 서명으로 제출](#enabledocusign) 적응형 양식 및 용 제출 옵션 목록에서 사용 가능 [DocuSign 클라우드 서비스 구성](#configure-docusign-with-aem-forms) 를 로컬 개발 환경에서 사용해야 합니다.

1. 컴파일 및 [에 코드 배포 [!DNL AEM Forms] as a Cloud Service 환경](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#customer-releases).

## 통합 [!DNL DocuSign] 포함 [!DNL AEM Forms] {#configure-docusign-with-aem-forms}

전제 조건이 갖추어지면 다음 단계를 수행하여 을 통합합니다 [!DNL DocuSign] 포함 [!DNL AEM Forms] 작성자 인스턴스에서 참조할 수 있습니다.

1. 다음으로 이동 **[!UICONTROL 도구]** ![망치](assets/hammer.png) > **[!UICONTROL Cloud Service]** > **[!UICONTROL DocuSign]** 구성을 호스팅할 폴더를 선택하십시오.

1. 구성 페이지에서 을 누릅니다. **[!UICONTROL 만들기]** 만들려면 [!DNL DocuSign] AEM Forms의 구성
1. 다음에서 **[!UICONTROL 일반]** 의 탭 **[!UICONTROL DocuSign 구성 만들기]** 페이지, 지정 **[!UICONTROL 이름]** 구성을 보려면 다음을 누르십시오. **[!UICONTROL 다음]**. 다음을 선택적으로 지정할 수 있습니다. **[!UICONTROL 제목]**.

1. 현재 브라우저 창의 URL을 메모장에 복사합니다. 이 URL은 이후 단계에서 [!DNL AEM Forms]를 사용해 [!DNL DocuSign]을 구성하는 데 필요합니다.

1. [!DNL DocuSign] 애플리케이션에 대한 OAuth 설정을 구성합니다.

   1. 브라우저 창을 열고 [!DNL DocuSign][ 개발자 계정에 로그인합니다](https://admindemo.docusign.com/apps-and-keys).
   1. 에 대해 구성된 앱 열기 [!DNL AEM Forms].
   1. 다음에서 **[!UICONTROL 리디렉션 URI]** 상자에서 이전 단계에서 복사한 URL을 추가하고 을 클릭합니다. **[!UICONTROL 저장]**.
   1. 통합 및 암호 키를 메모해 둡니다.

   [!DNL DocuSign] 애플리케이션에 대한 OAuth 설정을 구성하고 키를 얻는 방법에 대한 단계별 정보는 [애플리케이션에 대한 oAuth 설정 구성](https://support.docusign.com/guides/ndse-admin-guide-api-and-keys) 개발자 문서를 참조하십시오.

1. 로 돌아가기 **[!UICONTROL DocuSign 구성 만들기]** 페이지를 가리키도록 업데이트하는 중입니다. 다음에서 **[!UICONTROL 설정]** 탭, **[!UICONTROL OAuth URL]** 필드에는 다음 기본 URL이 언급되어 있습니다.

   `https://account-d.docusign.com/oauth/auth`

1. 다음을 지정합니다. **[!UICONTROL 클라이언트 ID]** (DocuSign 통합 키) 및 **[!UICONTROL 클라이언트 암호]** (DocuSign 비밀 키).

1. 누르기 **[!UICONTROL DocuSign에 연결]**. 자격 증명을 입력하라는 메시지가 뜨면 [!DNL DocuSign] 애플리케이션 생성 시 사용한 계정의 사용자 이름과 비밀번호를 입력합니다. 다음에 대한 액세스를 확인해달라는 메시지가 뜨는 경우 `your developer account`, 클릭 **[!UICONTROL 액세스 허용]**. 자격 증명이 올바르면 성공 메시지가 나타납니다.

1. 누르기 **[!UICONTROL 만들기]** 을(를) 만들려면 [!DNL DocuSign] 구성.

1. 구성을 선택하고 **[!UICONTROL 게시]**&#x200B;을 클릭하고 구성을 선택한 다음 을 클릭합니다 **[!UICONTROL 게시]**. 해당 게시 환경에 구성이 복사됩니다.

1. 위의 모든 단계를 개발자, 스테이지 및 생산 인스턴스(어느 것이든 남은 인스턴스에)에 반복하여, 해당 환경을 위한 [!DNL AEM Forms]를 사용한 [!DNL DocuSign] 구성을 완료합니다.

이제 AEM Forms 환경이 DocuSign을 사용하도록 구성되었습니다. Cloud Service에 사용되는 구성 컨테이너를 [!DNL DocuSign]을 위해 활성화하고자 하는 모든 적응형 양식에 추가해야 합니다. 적응형 양식의 속성에서 구성 컨테이너를 지정할 수 있습니다.

### 사용 [!DNL DocuSign] 적응형 양식 {#enabledocusign}

다음을 활성화할 수 있습니다. [!DNL DocuSign] 기존 적응형 양식 또는 [!DNL DocuSign] 적응형 양식을 활성화했습니다. 다음 중 하나를 선택합니다.

- [만들기 [!DNL DocuSign] 적응형 양식 활성화됨](#create-an-adaptive-form-for-docusign)
- [사용 [!DNL DocuSign] 기존 적응형 양식의 경우](#editafsign).

#### DocuSign용 적응형 양식 만들기 {#create-an-adaptive-form-for-docusign}

Sign이 활성화된 적응형 양식을 만들려면 다음 작업을 수행하십시오.

1. 다음으로 이동 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.
1. 누르기 **[!UICONTROL 만들기]** 및 선택 **[!UICONTROL 적응형 양식]**. 템플릿 목록이 나타납니다. 템플릿 선택 및 탭 **[!UICONTROL 다음]**.
1. 다음에서 **[!UICONTROL 기본]** 탭:

   1. 다음을 지정합니다. **[!UICONTROL 이름]** 및 **[!UICONTROL 제목]** 적응형 양식용.

   1. 다음 항목 선택 [구성 컨테이너](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) 생성 시간 [통합 [!DNL DocuSign] 포함 [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md).

   구성 컨테이너에는 [!DNL DocuSign] 환경에 맞게 구성된 Cloud Service. 이러한 서비스는 적응형 양식 편집기에서 선택할 수 있습니다.

1. 다음에서 **[!UICONTROL 양식 모델]** 탭에서 다음 옵션 중 하나를 선택합니다.

   - 사용자 정의 양식 서식 파일이 있고 양식 서식 파일을 기반으로 기록 문서가 필요한 경우 **[!UICONTROL 양식 템플릿을 기록 문서 템플릿으로 연결]** 옵션을 선택하고 기록 문서 템플릿을 선택합니다. 옵션을 사용하면 서명을 위해 전송된 문서에 관련 양식 템플릿을 기반으로 하는 필드만 표시됩니다. 적응형 양식의 모든 필드가 표시되지는 않습니다.

   - 사용자 정의 양식 템플릿이 없는 경우 **[!UICONTROL 기록 문서 생성]** 옵션을 선택합니다. 옵션을 사용하면 서명을 위해 전송된 문서에 적응형 양식의 모든 필드가 표시됩니다.

1. **[!UICONTROL 만들기를 탭합니다.]** 서명이 활성화된 적응형 양식이 만들어집니다. 다음을 추가할 수 있습니다. [!DNL DocuSign] 필드를 양식으로 보내고 서명을 위해 보냅니다.
1. 편집 모드에서 적응형 양식을 엽니다. 다음에서 **[!UICONTROL 콘텐츠]** 탭에서 다음을 누릅니다. **[!UICONTROL 양식 컨테이너]** 및 탭 ![구성](assets/configure-icon.svg).

1. 다음에서 **[!UICONTROL 제출]** 섹션, 선택 **[!UICONTROL DocuSign 전자 서명으로 제출]** 다음에서 **[!UICONTROL 제출 액션]** 드롭다운 목록입니다.

1. 다음에서 **[!UICONTROL 작업 구성]** 섹션, 탭 **[!UICONTROL 추가]** 수신자를 추가하고 수신자의 이메일 주소를 지정합니다. 누르기 **[!UICONTROL 추가]** 수신자를 더 추가하려면 다시 시도하십시오.

1. 에서 이메일 메시지의 제목을 지정합니다. **[!UICONTROL 이메일 제목]** 필드. 선택 **첨부 파일 포함** 전자 메일 메시지에 첨부 파일을 포함합니다.

1. ![저장](assets/save_icon.svg)을 탭하여 변경 내용을 저장합니다.

#### 사용 [!DNL DocuSign] 적응형 양식용 {#editafsign}

사용 [!DNL DocuSign] 기존 적응형 양식에서:

1. 다음으로 이동 **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms 및 문서]**.
1. 적응형 양식을 선택하고 을 누릅니다 **[!UICONTROL 속성]**.
1. 다음에서 **[!UICONTROL 기본]** 탭에서 [구성 컨테이너](adobe-sign-integration-adaptive-forms.md#configure-adobe-sign-with-aem-forms) 통합하는 동안 생성됨 [!DNL DocuSign] 포함 [!DNL AEM Forms].
1. 다음에서 **[!UICONTROL 양식 모델]** 탭에서 다음 옵션 중 하나를 선택합니다.

   - 사용자 정의 양식 서식 파일이 있고 양식 서식 파일을 기반으로 기록 문서가 필요한 경우 **[!UICONTROL 양식 템플릿을 기록 문서 템플릿으로 연결]** 옵션을 선택하고 기록 문서 템플릿을 선택합니다. 옵션을 사용하면 서명을 위해 전송된 문서에 관련 양식 템플릿을 기반으로 하는 필드만 표시됩니다. 적응형 양식의 모든 필드가 표시되지는 않습니다.

   - 사용자 정의 양식 템플릿이 없는 경우 **[!UICONTROL 기록 문서 생성]** 옵션을 선택합니다. 옵션을 사용하면 서명을 위해 전송된 문서에 적응형 양식의 모든 필드가 표시됩니다.

1. 누르기 **[!UICONTROL 저장 및 닫기]**. 적응형 양식이 다음에 대해 활성화되어 있습니다. [!DNL DocuSign]. 이제 다음을 추가할 수 있습니다. [!DNL DocuSign] 필드를 양식으로 보내고 서명을 위해 보냅니다.

1. 편집 모드에서 적응형 양식을 엽니다. 다음에서 **[!UICONTROL 콘텐츠]** 탭에서 다음을 누릅니다. **[!UICONTROL 양식 컨테이너]** 및 탭 ![구성](assets/configure-icon.svg).

1. 다음에서 **[!UICONTROL 제출]** 섹션, 선택 **[!UICONTROL DocuSign 전자 서명으로 제출]** 다음에서 **[!UICONTROL 제출 액션]** 드롭다운 목록입니다.

1. 다음에서 **[!UICONTROL 작업 구성]** 섹션, 탭 **[!UICONTROL 추가]** 수신자를 추가하고 수신자의 이메일 주소를 지정합니다. 누르기 **[!UICONTROL 추가]** 수신자를 더 추가하려면 다시 시도하십시오.

1. 에서 이메일 메시지의 제목을 지정합니다. **[!UICONTROL 이메일 제목]** 필드. 선택 **첨부 파일 포함** 전자 메일 메시지에 첨부 파일을 포함합니다.

1. ![저장](assets/save_icon.svg)을 탭하여 변경 내용을 저장합니다.
