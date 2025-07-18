---
title: 기존 설치에 대해 외부 종속성 제거
description: 기존 설치에 대해 외부 종속성 제거
feature: Workfront Integrations and Apps
exl-id: 5b28ce97-2719-47b8-a386-77d4aaddbe81
role: Admin
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 17%

---

# 기존 설치에 대해 외부 종속성 제거 {#remove-external-depedencies}

Adobe에서는 Workfront에 대해 기존 향상된 커넥터 설치에 대한 구성 단계를 실행하여 Hoodoo 배포 지점에 대한 종속성을 제거할 것을 권장합니다.

>[!NOTE]
>
>2022년 3월 이전에 Workfront용 향상된 커넥터를 설치한 경우에만 구성 단계를 수행하십시오. 2022년 3월부터 Workfront에 새롭게 향상된 커넥터 설치를 위한 Hoodoo 배포 지점에 종속성이 없습니다.

외부 종속성을 제거하려면 다음 작업을 수행하십시오.

1. 부모 `pom.xml`에서 다음 Hoodoo 저장소 구성을 제거하십시오.

   ```XML
     <repository>
        <id>hoodoo-maven</id>
        <name>Hoodoo Repository</name>
        <url>https://gitlab.com/api/v4/projects/12715200/packages/maven</url>
     </repository>
   ```

1. `./cloudmanager/maven/settings.xml`에서 사용할 수 있는 `settings.xml` 파일에서 다음 서버 구성을 제거합니다.

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

1. [새 설치 단계](workfront-connector-install.md)를 실행합니다.
