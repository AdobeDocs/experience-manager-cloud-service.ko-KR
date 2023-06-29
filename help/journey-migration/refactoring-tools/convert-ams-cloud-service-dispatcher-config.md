---
title: AMS를 Adobe Experience Manager as a Cloud Service Dispatcher 구성으로 변환
description: AMS를 Adobe Experience Manager as a Cloud Service Dispatcher 구성으로 변환
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '1278'
ht-degree: 39%

---


# AMS를 Adobe Experience Manager (AEM) as a Cloud Service Dispatcher 구성으로 변환

## 소개 {#introduction}

이 섹션에서는 AMS 구성을 변환하는 방법에 대한 단계별 지침을 제공합니다.

>[!NOTE]
>이 섹션에서는 사용자가 [Dispatcher 구성 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/getting-started/dispatcher-configurations.html)에 설명된 것과 유사한 구조를 갖는 아카이브를 사용한다고 가정합니다.

## AMS를 AEM as a Cloud Service Dispatcher 구성으로 변환하는 단계

1. **아카이브 추출 및 최종 접두사 제거**

   아카이브를 폴더에 추출하고, 직속 하위 폴더가 conf, conf.d, conf.dispatcher.d 및 conf.modules.d로 시작하는지 확인합니다. 그렇지 않은 경우 계층 구조에서 위로 이동합니다.

1. **사용하지 않는 하위 폴더 및 파일 제거**

   conf, conf.modules.d 하위 폴더 및 conf.d/*.conf와 일치하는 파일을 제거합니다.

1. **게시되지 않은 모든 가상 호스트 제거**

1. **가상 호스트 파일 제거**

   이름에 작성자, 비정상, 상태, lc 또는 플러시가 있는 conf.d/enabled_vhosts. conf.d/available_vhosts에 연결되어 있지 않은 모든 가상 호스트 파일도 제거할 수 있습니다.

1. 포트 80을 참조하지 않는 가상 호스트 섹션 제거 또는 주석 달기

   가상 호스트 파일에 포트 80 이외의 다른 포트만 참조하는 섹션이 있는 경우

   `<VirtualHost *:443>`
   `...`
   `</VirtualHost>`
해당 섹션을 제거하거나 주석을 답니다. 이러한 섹션의 문은 처리되지 않지만, 이 문을 계속 유지하면 아무것도 적용되지 않은 상태로 편집을 종료할 수 있으므로 혼동을 줄 수 있습니다.

1. **rewrites 확인**

   * directory conf.d/rewrites를 입력합니다.

   * base_rewrite.rules 및 xforwarded_forcessl_rewrite.rules 파일을 제거하고, 이 파일을 참조하는 Include 문을 가상 호스트 파일에서 제거해야 합니다.

   * 이제 conf.d/rewrites에 단일 파일이 포함되어 있는 경우 이름을 rewrite.rules로 변경하고 가상 호스트 파일에서도 이 파일을 참조하는 Include 문을 수정해야 합니다.

   * 그러나 폴더에 가상 호스트별 파일이 여러 개 있는 경우 해당 컨텐츠를 가상 호스트 파일에서 해당 파일을 참조하는 Include 문에 복사해야 합니다.

1. **변수 확인**

   1. directory conf.d/variables를 입력합니다.

   1. ams_default.vars 파일을 제거하고, 이 파일을 참조하는 Include 문을 가상 호스트 파일에서 제거해야 합니다.

   1. 이제 conf.d/variables에 단일 파일이 포함되어 있는 경우 이름을 custom.vars로 변경하고, 가상 호스트 파일에서도 이 파일을 참조하는 Include 문을 수정해야 합니다.

   1. 그러나 폴더에 가상 호스트별 파일이 여러 개 있는 경우 해당 컨텐츠를 가상 호스트 파일에서 해당 파일을 참조하는 Include 문에 복사해야 합니다.

1. **허용 목록 제거**

   conf.d/whitelists 폴더를 제거하고 해당 하위 폴더에 있는 일부 파일을 참조하는 가상 호스트 파일에서 Include 문을 제거합니다.

1. **더 이상 사용할 수 없는 변수 모두 바꾸기**

   모든 가상 호스트 파일에서 다음을 수행합니다.

   PUBLISH_DOCROOT를 DOCROOT로 이름을 바꾸고,
DISP_ID, PUBLISH_FORCE_SSL 또는 PUBLISH_WHITELIST_ENABLED 변수를 참조하는 섹션을 제거합니다.

1. **검사기를 실행하여 상태 확인**

   httpd 하위 명령을 사용하여 디렉토리에서 Dispatcher 검사기를 실행합니다.

   `$ validator httpd`
누락된 &quot;include&quot; 파일에 대한 오류가 표시되면 해당 파일의 이름을 올바르게 변경했는지 확인합니다.

   허용 목록에 포함되지 않은 Apache 지시문이 표시되면 제거합니다.

1. **게시되지 않은 모든 팜 제거**

   이름에 작성자, 비정상, 상태, lc 또는 플러시가 있는 conf.dispatcher.d/enabled_farms의 팜 파일을 제거합니다. conf.dispatcher.d/available_farms에 연결되어 있지 않은 모든 팜 파일도 제거할 수 있습니다.

1. **팜 파일 이름 변경**

   conf.dispatcher.d/enabled_farms의 모든 팜 이름은 *.farm 패턴과 일치하도록 이름을 변경해야 합니다. 예를 들어, 이름 바꾸기 `customerX_farm.any` 끝 `customerX.farm`.

1. **cache 확인**

   directory conf.dispatcher.d/cache를 입력합니다.

   `ams_` 접두어가 있는 파일을 모두 제거합니다.

   이제 conf.dispatcher.d/cache가 비어 있으면 파일을 복사합니다. `conf.dispatcher.d/cache/rules.any` 표준 Dispatcher 구성에서 이 폴더로. 표준 Dispatcher 구성은 이 SDK의 src 폴더에서 확인할 수 있습니다. 다음을 참조하는 $include 문을 수정하는 것을 잊지 마십시오. `ams_*_cache.any` 팜 파일의 규칙 파일도 참조하십시오.

   이제 conf.dispatcher.d/cache에 접미사가 포함된 단일 파일이 있습니다 `_cache.any`, 이름을 로 변경해야 합니다. `rules.any`. 팜 파일에서도 이 파일을 참조하는 $include 문을 수정해야 합니다.

   그러나 폴더에 이 패턴의 팜 특정 파일이 여러 개 있는 경우 해당 컨텐츠를 팜 파일에서 이를 참조하는 $include 문에 복사해야 합니다.

   접미사가 있는 모든 파일 제거 `_invalidate_allowed.any`.

   기본 Dispatcher 구성에서 conf.dispatcher.d/cache/default_invalidate_any 파일을 해당 위치에 복사합니다.

   각 팜 파일에서 cache/allowedClients 섹션의 내용을 제거하고 다음과 같이 바꿉니다.

   $include &quot;../cache/default_invalidate.any&quot;

1. **client headers 확인**

   directory conf.dispatcher.d/clientheaders를 입력합니다.

   `ams_` 접두어가 있는 파일을 모두 제거합니다.

   conf.dispatcher.d/clientheaders에 접미사가 있는 단일 파일이 포함된 경우 `_clientheaders.any`, 이름을 로 바꿉니다. `clientheaders.any`. 팜 파일에서도 이 파일을 참조하는 $include 문을 수정해야 합니다.

   그러나 폴더에 이 패턴의 팜 특정 파일이 여러 개 있는 경우 해당 컨텐츠를 팜 파일에서 이를 참조하는 $include 문에 복사해야 합니다.

   파일 복사 `conf.dispatcher/clientheaders/default_clientheaders.any` 기본 Dispatcher 구성에서 해당 위치로

   각 팜 파일에서 `clientheader` &quot;include&quot; 문은 다음과 같이 표시됩니다.

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"`

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"`

   다음 문으로 바꿉니다.

   `$include "../clientheaders/default_clientheaders.any"`

1. **filter 확인**

   * directory conf.dispatcher.d/filters를 입력합니다.

   * `ams_` 접두어가 있는 파일을 모두 제거합니다.

   * 이제 conf.dispatcher.d/filters에 단일 파일이 포함되어 있는 경우 이름을 로 바꾸십시오. `filters.any`. 팜 파일에서도 이 파일을 참조하는 $include 문을 수정해야 합니다.

   * 그러나 폴더에 이 패턴의 팜 특정 파일이 여러 개 있는 경우 해당 컨텐츠를 팜 파일에서 이를 참조하는 $include 문에 복사해야 합니다.

   * 파일 복사 `conf.dispatcher/filters/default_filters.any` 기본 Dispatcher 구성에서 해당 위치로

   * 각 팜 파일에서 다음과 같이 표시되는 filter &quot;include&quot; 문을 모두 바꿉니다.

   * $include `"/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"`
다음과 같이 바꿉니다.

     `$include "../filters/default_filters.any"`

1. **renders 확인**

   * directory conf.dispatcher.d/renders를 입력합니다.

   * 해당 폴더의 파일을 모두 제거합니다.

   * 파일 복사 `conf.dispatcher.d/renders/default_renders.any` 기본 Dispatcher 구성에서 해당 위치로

   * 각 팜 파일에서 renders 섹션의 내용을 제거하고 다음과 같이 바꿉니다.

     `$include "../renders/default_renders.any"`

1. **virtualhosts 확인**

   * 디렉토리 이름을 `conf.dispatcher.d/vhosts to conf.dispatcher.d/virtualhosts`로 변경하고 입력합니다.

   * `ams_` 접두어가 있는 파일을 모두 제거합니다.

   * 이제 conf.dispatcher.d/virtualhosts에 단일 파일이 포함되어 있는 경우 이름을 로 바꿉니다 `virtualhosts.any`. 팜 파일에서도 이 파일을 참조하는 $include 문을 수정해야 합니다.

   * 그러나 폴더에 이 패턴의 팜 특정 파일이 여러 개 있는 경우 해당 컨텐츠를 팜 파일에서 이를 참조하는 $include 문에 복사해야 합니다.

   * 파일 복사 `conf.dispatcher/virtualhosts/default_virtualhosts.any` 기본 Dispatcher 구성에서 해당 위치로

   * 각 팜 파일에서 다음과 같이 표시되는 filter &quot;include&quot; 문을 모두 바꿉니다.

     `$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"`
다음 문으로 바꿉니다.

     `$include "../virtualhosts/default_virtualhosts.any"`


1. **검사기를 실행하여 상태 확인**

   * Dispatcher 하위 명령을 사용하여 디렉토리에서 Dispatcher 유효성 검사기를 실행합니다.

     `$ validator dispatcher`

   * 누락된 &quot;include&quot; 파일에 대한 오류가 표시되면 해당 파일의 이름을 올바르게 변경했는지 확인합니다.

   * 정의되지 않은 변수 `PUBLISH_DOCROOT`와 관련된 오류가 표시되면 이름을 `DOCROOT`로 바꿀 수 있습니다.

   * 다른 모든 오류에 대해서는 유효성 검사기 도구 설명서의 문제 해결 섹션을 참조하십시오.

## 로컬 배포로 구성 테스트 {#testing-config-local-deployment}

>[!IMPORTANT]
>
>로컬 배포로 구성을 테스트하려면 Docker를 설치해야 합니다.

Dispatcher SDK에서 `docker_run.sh` 스크립트를 사용하여 구성에 배포에만 표시되는 다른 오류가 없는지 테스트할 수 있습니다.

1. 유효성 검사기를 사용하여 배포 정보 생성.

   `validator full -d out`
전체 구성을 확인하고 배포 정보를 생성합니다.

1. 해당 배포 정보를 사용하여 도커 이미지에서 Dispatcher를 시작합니다.

   macOS 컴퓨터에서 실행 중인 AEM 게시 서버를 사용하여 포트 4503에서 수신 대기하면 다음과 같이 해당 서버 앞에서 Dispatcher를 시작할 수 있습니다.

   `$ docker_run.sh out docker.for.mac.localhost:4503 8080`

   컨테이너를 시작하고 로컬 포트 8080에서 Apache를 표시합니다.

## 새 Dispatcher 구성 사용 {#using-dispatcher-config}

유효성 검사기가 더 이상 문제를 보고하지 않고 Docker 컨테이너가 아무런 오류 또는 경고 없이 시작하는 경우 구성을 git 저장소의 d`ispatcher/src` 하위 디렉토리로 이동할 수 있습니다.