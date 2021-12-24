---
title: '사용자 정의 글꼴 사용 '
description: '사용자 정의 글꼴 사용 '
source-git-commit: 7dd3785206b6d79caa500a155d3a6f3597303e65
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# 사용자 정의 글꼴 사용

**Cloud Service 커뮤니케이션 설명서는 베타에 있습니다**

Forms as a Cloud Service Communications를 사용하여 XDP 템플릿, XDP 기반 PDF 문서 또는 Acrobat Forms(AcroForm)를 XML 데이터와 결합하여 PDF 문서를 생성할 수 있습니다. 시스템 글꼴(Cloud Service에 포함된 글꼴) 또는 사용자 정의 글꼴(조직 승인 글꼴)을 사용하여 생성된 PDF 문서를 렌더링할 수 있습니다.

시스템 글꼴은 이미 Cloud Service에서 사용할 수 있습니다. Cloud Service 개발 프로젝트를 사용하여 Cloud Service 환경에 사용자 정의 글꼴을 추가할 수 있습니다.

## PDF 문서 동작

다음을 수행할 수 있습니다 [글꼴 포함](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/api/sync/#tag/PDFOutputOptions) PDF 문서에 추가하거나 글꼴의 이름을 지정합니다. 글꼴이 포함되면 PDF 문서가 모든 플랫폼에서 동일하게 표시됩니다(모양). 내장형 글꼴을 사용하여 일관된 모양과 느낌을 보장합니다. 글꼴이 포함되지 않은 경우 PDF 렌더링 클라이언트는 클라이언트 시스템에서 글꼴을 검색합니다. 클라이언트 컴퓨터에서 글꼴을 사용할 수 있는 경우 PDF은 지정된 글꼴을 사용하고, 그렇지 않으면 PDF이 대체 글꼴로 렌더링됩니다.

## Forms as a Cloud Service 환경에 사용자 정의 글꼴 추가

Cloud Service 환경에 사용자 정의 글꼴을 추가하려면 다음을 수행하십시오.

1. 로컬 개발 프로젝트를 설정하고 엽니다. 원하는 IDE를 사용할 수 있습니다.
1. 프로젝트의 최상위 폴더 구조에서 폴더를 만들어 사용자 정의 글꼴을 저장하고 사용자 정의 글꼴을 폴더에 추가합니다. 예를 들어, fonts/src/main/resources
   ![글꼴 폴더](assets/fonts.png)

1. 개발 프로젝트의 최상위 pom.xml 파일을 엽니다.
1. 추가 `<Font-Archive-Version>` .pom 파일에 대한 매니페스트 항목을 설정하고 버전 값을 1로 설정합니다.

   ```xml
   <plugin>
       <groupId>org.apache.maven.plugins</groupId>
       <artifactId>maven-jar-plugin</artifactId>
       <version>3.1.2</version>
       <configuration>
           <archive>
               <manifest>
                   </addDefaultEntries>
                   </addDefaultImplementationEntries>
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

1. 업데이트된 코드를 확인하고 [파이프라인 실행](/help/implementing/cloud-manager/deploy-code.md) 글꼴을 Cloud Service 환경에 배포합니다.
