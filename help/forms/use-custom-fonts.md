---
title: 사용자 정의 글꼴 사용
description: 사용자 정의 글꼴 사용
exl-id: 88214d36-fb97-4d46-a9fe-71dbc7826eb1
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# 사용자 정의 글꼴 사용

**Cloud Service 커뮤니케이션 설명서는 베타에 있습니다**

Forms as a Cloud Service Communications를 사용하여 XDP 템플릿, XDP 기반 PDF 문서 또는 Acrobat 양식(AcroForm)을 XML 데이터와 결합하여 PDF 문서를 생성할 수 있습니다. 또한 Communications를 사용하여 PDF 및 XDP 문서를 결합, 재정렬 및 증가시키고 PDF 문서에 대한 정보를 얻을 수도 있습니다.

이전에 언급된 작업과 함께 Cloud Service 또는 사용자 정의 글꼴(조직 승인 글꼴)에 포함된 글꼴을 사용하여 생성된 PDF 문서를 렌더링할 수 있습니다. Cloud Service 개발 프로젝트를 사용하여 Cloud Service 환경에 사용자 정의 글꼴을 추가할 수 있습니다.

## PDF 문서 동작

다음을 수행할 수 있습니다 [글꼴 포함](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/api/sync/#tag/PDFOutputOptions) PDF 문서로 이동합니다. 글꼴을 포함하면 PDF 문서가 모든 플랫폼에서 동일하게 표시됩니다. 포함된 글꼴을 사용하여 일관된 모양과 느낌을 보장합니다. 글꼴이 포함되지 않은 경우 글꼴 렌더링은 Acrobat 또는 Acrobat Reader과 같은 PDF 뷰어 클라이언트의 렌더링 설정에 따라 달라집니다. 클라이언트 컴퓨터에서 글꼴을 사용할 수 있는 경우 PDF은 지정된 글꼴을 사용하고, 그렇지 않으면 PDF이 기본 대체 글꼴로 렌더링됩니다.

## Forms as a Cloud Service 환경에 사용자 정의 글꼴 추가 {#custom-fonts-cloud-service}

Cloud Service 환경에 사용자 정의 글꼴을 추가하려면 다음을 수행하십시오.

1. 을(를) 설정하고 엽니다. [지역 개발 프로젝트](setup-local-development-environment.md). 원하는 IDE를 사용할 수 있습니다.
1. 프로젝트의 최상위 폴더 구조에서 폴더(모듈)를 만들어 사용자 정의 글꼴을 저장하고 사용자 정의 글꼴을 폴더에 추가합니다. 예를 들어, fonts/src/main/resources
   ![글꼴 폴더](assets/fonts.png)

1. 개발 프로젝트의 fonts 모듈의 pom.xml 파일을 엽니다.
1. pom 파일에 jar 플러그인을 추가합니다.

   ```xml
   <plugin>
       <groupId>org.apache.maven.plugins</groupId>
       <artifactId>maven-jar-plugin</artifactId>
       <version>3.1.2</version>
       <configuration>
           <archive>
               <manifest>
                   <addDefaultEntries/>
                   <addDefaultImplementationEntries/>
               </manifest>
           </archive>
       </configuration>
   </plugin>
   ```


1. 추가 `<Font-Archive-Version>` 매니페스트 항목 .pom 파일을 입력하고 버전 값을 1로 설정합니다.

   ```xml
   <plugin>
       <groupId>org.apache.maven.plugins</groupId>
       <artifactId>maven-jar-plugin</artifactId>
       <version>3.1.2</version>
       <configuration>
           <archive>
               <manifest>
                   <addDefaultEntries/>
                   <addDefaultImplementationEntries/>
               </manifest>
               <manifestEntries>
                   <Font-Archive-Version>1</Font-Archive-Version>
                   <Font-Archive-Contents>/</Font-Archive-Contents>
               </manifestEntries> 
           </archive>
       </configuration>
   </plugin>
   ```

1. 글꼴 폴더를 `<modules>` pom 파일에 나열됩니다. 예:

   ```xml
   <modules>
       <module>all</module>
       <module>core</module>
       <module>ui.frontend</module>
       <module>ui.apps</module>
       <module>ui.apps.structure</module>
       <module>ui.config</module>
       <module>ui.content</module>
       <module>it.tests</module>
       <module>dispatcher</module>
       <module>dispatcher.ams</module>
       <module>dispatcher.cloud</module>
       <module>ui.tests</module>
       <module>fonts</module>
   </modules>
   ```

   글꼴 폴더에는 모든 사용자 정의 글꼴이 포함되어 있습니다.

1. 업데이트된 코드를 확인하고 [파이프라인 실행](/help/implementing/cloud-manager/deploy-code.md) 글꼴을 Cloud Service 환경에 배포합니다.

1. (선택 사항) 명령 프롬프트를 열고 로컬 프로젝트 폴더로 이동한 다음 아래 명령을 실행합니다. 이 명령은 관련 정보와 함께 .jar 파일의 글꼴을 패키지화합니다. .jar 파일을 사용하여 Forms Cloud Service 로컬 개발 환경에 사용자 정의 글꼴을 추가할 수 있습니다.

   ```shell
   mvn clean install
   ```

## 로컬 Forms Cloud Service 개발 환경에 사용자 정의 글꼴 추가 {#custom-fonts-cloud-service-sdk}

1. 로컬 개발 환경을 시작합니다.
1. 다음으로 이동 `<aem install directory>/crx-quickstart/install` 폴더를 입력합니다.
1. 배치 `<jar file contaning custom fonts and relevant deployment code>.jar` 설치 폴더로 이동합니다. .jar 파일이 없는 경우에는 [Forms as a Cloud Service 환경에 사용자 정의 글꼴 추가](#custom-fonts-cloud-service) 섹션을 클릭하여 파일을 생성합니다.
1. 를 실행합니다. [docker 기반 SDK 환경](setup-local-development-environment.md#docker-microservices)


   >[!NOTE]
   >
   >업데이트된 사용자 지정 글꼴 .jar 파일을 로컬 개발 환경에 배포할 때마다 Docker 기반 SDK 환경을 다시 시작합니다.
