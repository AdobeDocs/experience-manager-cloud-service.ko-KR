---
title: 기존 설치에 대한 외부 종속성 제거
description: ' 설치  [!DNL Workfront for Experience Manager enhanced connector]'
feature: Integrations
source-git-commit: b61915a27968b11472ae458d7be3d73f3449fbbe
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 1%

---


# 기존 설치에 대한 외부 종속성 제거 {#remove-external-depedencies}

Adobe은 Workfront에 대한 기존 향상된 커넥터 설치에 대한 구성 단계를 실행하여 Hoodo 배포 지점에 대한 종속성을 제거할 것을 권장합니다.

>[!NOTE]
>
>2022년 3월 이전에 Workfront용 enhanced 커넥터를 설치한 경우에만 구성 단계를 실행합니다. 2022년 3월부터 Workfront에 대한 새로운 향상된 커넥터 설치에 대한 Hoodo 배포 포인트에 대한 종속성이 없습니다.

외부 종속성을 제거하려면 다음을 수행하십시오.

1. 상위에서 다음 Hoodo 저장소 구성을 제거합니다 `pom.xml`:

   ```XML
     <repository>
        <id>hoodoo-maven</id>
        <name>Hoodoo Repository</name>
        <url>https://gitlab.com/api/v4/projects/12715200/packages/maven</url>
     </repository>
   ```

1. 다음 서버 구성을 `settings.xml` 파일, 다음 위치에서 사용 가능 `./cloudmanager/maven/settings.xml`:

   ```XML
         <server>
            <id>hoodoo-maven</id>
            <configuration>
               <httpHeaders>
                     <property>
                        <name>Deploy-Token</name>
                        <value>xxxxxxxxxxxxxxxx</value>
                     </property>
               </httpHeaders>
            </configuration>
         </server>
   ```

1. 를 실행합니다 [새 설치 단계](workfront-connector-install.md).

