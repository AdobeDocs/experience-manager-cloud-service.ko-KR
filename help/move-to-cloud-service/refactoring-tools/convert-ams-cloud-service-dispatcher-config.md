---
title: AMS를 클라우드 서비스 발송자 구성으로 Adobe Experience Manager로 변환
description: AMS를 클라우드 서비스 발송자 구성으로 Adobe Experience Manager로 변환
translation-type: tm+mt
source-git-commit: 3478827949356c4a4f5133b54c6cf809f416efef
workflow-type: tm+mt
source-wordcount: '1342'
ht-degree: 0%

---


# AMS를 클라우드 서비스 발송자 구성으로 Adobe Experience Manager(AEM)로 변환

## 소개 {#introduction}

이 섹션에서는 AMS 구성을 변환하는 방법에 대한 단계별 지침을 제공합니다.

>[!NOTE]
>이 프로세스에서는 사용자가 Dispatcher 구성 [관리에 설명된 것과 유사한 구조를 갖는 아카이브를 가지고 있다고 가정합니다](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/dispatcher-configurations.html).

## AMS를 클라우드 서비스 발송자 구성으로 AEM으로 변환하는 단계

1. **아카이브 추출 및 최종 접두사 제거**

   아카이브를 폴더에 추출하고, 직속 하위 폴더가 conf, conf.d, conf.dispatcher.d 및 conf.modules.d로 시작하는지 확인합니다. 그렇지 않으면 위쪽으로 옮겨라.

1. **사용되지 않은 하위 폴더와 파일 제거**

   conf.d/*.conf와 일치하는 파일뿐만 아니라 하위 폴더 conf 및 conf.modules.d를 제거합니다.

1. **게시되지 않은 모든 가상 호스트 제거**

1. **가상 호스트 파일 제거**

   이름에 작성자, 비정상, 상태, lc 또는 플러시가 있는 conf.d/enabled_vhosts입니다. conf.d/available_vhosts에 연결되어 있지 않은 모든 가상 호스트 파일도 제거할 수 있습니다.

1. 포트 80을 참조하지 않는 가상 호스트 섹션 제거 또는 주석 추가

   포트 80이 아닌 다른 포트만을 참조하는 가상 호스트 파일에 섹션이 있는 경우

   `<VirtualHost *:443>`
   `...`
   `</VirtualHost>`
제거하거나 주석을 달 수 있습니다. 이러한 섹션의 문은 처리되지 않습니다. 이 문을 계속 유지하면 아무런 효과가 없는 상태로 편집하게 되므로 혼동됩니다.

1. **다시 쓰기 확인**

   * directory conf.d/rewrite를 입력합니다.

   * base_rewrite.rules 및 xforwarded_forcessl_rewrite.rules라는 파일을 제거하고 해당 파일을 참조하는 가상 호스트 파일에 포함 문을 제거해야 합니다.

   * 이제 conf.d/rewrite에 단일 파일이 포함되어 있는 경우 이름을 rewrite.rules로 변경해야 하며 가상 호스트 파일에서도 해당 파일을 참조하는 Include 문을 수정해야 합니다.

   * 그러나 폴더에 여러 개의 가상 호스트 특정 파일이 들어 있는 경우 해당 콘텐트를 가상 호스트 파일에서 해당 파일을 참조하는 Include 문으로 복사해야 합니다.

1. **변수 확인**

   1. directory conf.d/variables를 입력합니다.

   1. ams_default.vars라는 파일을 제거하고 해당 파일을 참조하는 가상 호스트 파일에서 Include 문을 제거해야 합니다.

   1. 이제 conf.d/변수에 단일 파일이 포함되어 있는 경우 custom.vars로 이름을 변경해야 하며 가상 호스트 파일에서도 해당 파일을 참조하는 Include 문을 수정해야 합니다.

   1. 그러나 폴더에 여러 개의 가상 호스트 특정 파일이 들어 있는 경우 해당 콘텐트를 가상 호스트 파일에서 해당 파일을 참조하는 Include 문으로 복사해야 합니다.

1. **화이트 리스트 제거**

   폴더 conf.d/white목록을 제거하고 해당 하위 폴더에 있는 일부 파일을 참조하는 가상 호스트 파일에 명령문 포함을 제거합니다.

1. **더 이상 사용할 수 없는 모든 변수 바꾸기**

   모든 가상 호스트 파일에서:

   PUBLISH_DOCROOT의 이름을 DISP_ID, PUBLISH_FORCE_SSL 또는 PUBLISH_WHITELIST_ENABLED라는 변수를 참조하는 DOCROTERemove 섹션으로 변경

1. **유효성 검사기를 실행하여 상태 확인**

   다음 httpd 하위 명령을 사용하여 디렉토리에서 검사기를 실행합니다.

   `$ validator httpd`
누락된 포함 파일에 대한 오류가 표시되면 해당 파일의 이름을 올바르게 변경했는지 확인하십시오.

   화이트리스트에 포함되지 않은 Apache 지시문이 표시되면 제거합니다.

1. **게시되지 않은 모든 팜 제거**

   이름에 작성자, 비정상, 상태, lc 또는 플러시가 있는 conf.dispatcher.d/enabled_farm의 팜 파일을 제거합니다. conf.dispatcher.d/available_farms에 연결되어 있지 않은 모든 팜 파일도 제거할 수 있습니다.

1. **팜 파일 이름 변경**

   conf.dispatcher.d/enabled_farm의 모든 팜은 *.farm 패턴과 일치하도록 이름을 변경해야 합니다. 따라서 customerX_farm.any라는 팜 파일의 이름을 customerX.farm으로 변경해야 합니다.

1. **캐시 확인**

   directory conf.dispatcher.d/cache를 입력합니다.

   미리 고정한 모든 파일을 제거합니다.

   conf.dispatcher.d/cache가 이제 비어 있는 경우, 표준 발송자 구성에서 d/cache/rules.any 파일을 이 폴더로 복사합니다. 표준 발송자 구성은 이 SDK의 src 폴더에서 찾을 수 있습니다. 팜 파일에도 있는 ams_*_cache.any 규칙 파일을 참조하는 $include 문을 적용하는 것을 잊지 마십시오.

   이제 conf.dispatcher.d/cache에 접미사 _cache.any가 있는 단일 파일이 포함되어 있는 경우 이 파일의 이름을 rules.any로 바꾸어야 하며 팜 파일에서도 해당 파일을 참조하는 $include 문을 적용한다는 것을 잊지 마십시오.

   그러나 폴더에 해당 패턴이 있는 여러 개의 팜 특정 파일이 들어 있는 경우 해당 콘텐트를 팜 파일에서 해당 파일을 참조하는 $include 문에 복사해야 합니다.

   _invalidate_allowed.any 접미어를 가진 파일을 제거합니다.

   기본 발송자 구성에서 해당 위치로 conf.dispatcher.d/cache/default_invalidate_any 파일을 복사합니다.

   각 팜 파일에서 cache/allowedClients 섹션의 내용을 제거하고 다음으로 바꿉니다.

   $include &quot;../cache/default_invalidate.any&quot;

1. **클라이언트 헤더 확인**

   directory conf.dispatcher.d/clientheaders를 입력합니다.

   미리 고정한 모든 파일을 제거합니다.

   이제 conf.dispatcher.d/clientheaders에 접미사 _clientheaders.any가 있는 단일 파일이 포함되어 있는 경우 이 파일의 이름을 clientheaders.any로 변경해야 하며 팜 파일에서도 해당 파일을 참조하는 $include 문을 수정해야 합니다.

   그러나 폴더에 해당 패턴이 있는 여러 개의 팜 특정 파일이 들어 있는 경우 해당 콘텐트를 팜 파일에서 해당 파일을 참조하는 $include 문에 복사해야 합니다.

   기본 발송자 구성에서 해당 위치로 conf.dispatcher/clientheaders/default_clientheaders.any 파일을 복사합니다.

   각 팜 파일에서 클라이언트 판독기를 바꾸려면 다음과 같이 보이는 명령문이 포함됩니다.

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_publish_clientheaders.any"`

   `$include "/etc/httpd/conf.dispatcher.d/clientheaders/ams_common_clientheaders.any"`

   with the statement:

   `$include "../clientheaders/default_clientheaders.any"`

1. **필터 확인**

   * directory conf.dispatcher.d/filters를 입력합니다.

   * 미리 고정한 모든 파일을 제거합니다.

   * 이제 conf.dispatcher.d/filters에 단일 파일이 포함되어 있는 경우 filters.any로 이름을 변경해야 합니다. 팜 파일에서도 해당 파일을 참조하는 $include 문을 수정해야 합니다.

   * 그러나 폴더에 해당 패턴이 있는 여러 개의 팜 특정 파일이 들어 있는 경우 해당 콘텐트를 팜 파일에서 해당 파일을 참조하는 $include 문에 복사해야 합니다.

   * 기본 발송자 구성에서 해당 위치로 conf.dispatcher/filters/default_filters.any 파일을 복사합니다.

   * 각 팜 파일에서 필터에는 다음과 같이 보이는 문이 포함됩니다.

   * $include `"/etc/httpd/conf.dispatcher.d/filters/ams_publish_filters.any"`with statement:

      `$include "../filters/default_filters.any"`

1. **렌더링 확인**

   * directory conf.dispatcher.d/renders를 입력합니다.

   * 해당 폴더의 모든 파일을 제거합니다.

   * 기본 발송자 구성에서 해당 위치로 conf.dispatcher.d/renders/default_renders.any 파일을 복사합니다.

   * 각 팜 파일에서 렌더링 섹션의 내용을 제거하고 다음으로 바꿉니다.

      `$include "../renders/default_renders.any"`

1. **가상 호스트 확인**

   * 디렉토리 이름을 `conf.dispatcher.d/vhosts to conf.dispatcher.d/virtualhosts` 변경하고 입력합니다.

   * 미리 고정한 파일을 제거합니다 `ams_`.

   * 이제 conf.dispatcher.d/virtualhosts가 단일 파일을 포함하는 경우 가상 호스트.any로 이름을 변경해야 합니다. 팜 파일에서도 해당 파일을 참조하는 $include 문을 수정해야 합니다.

   * 그러나 폴더에 해당 패턴이 있는 여러 개의 팜 특정 파일이 들어 있는 경우 해당 콘텐트를 팜 파일에서 해당 파일을 참조하는 $include 문에 복사해야 합니다.

   * 기본 발송자 구성에서 해당 위치로 conf.dispatcher/virtualhosts/default_virtualhosts.any 파일을 복사합니다.

   * 각 팜 파일에서 필터에는 다음과 같이 보이는 문이 포함됩니다.

      `$include "/etc/httpd/conf.dispatcher.d/vhosts/ams_publish_vhosts.any"`
with the statement:

      `$include "../virtualhosts/default_virtualhosts.any"`


1. **유효성 검사기를 실행하여 상태 확인**

   * 디스패처 하위 명령을 사용하여 디렉토리에서 검사기를 실행합니다.

      `$ validator dispatcher`

   * 누락된 포함 파일에 대한 오류가 표시되면 해당 파일의 이름을 올바르게 변경했는지 확인하십시오.

   * 정의되지 않은 변수와 관련된 오류가 표시되면 이름을 `PUBLISH_DOCROOT`바꿀 수 `DOCROOT`있습니다.

   * 다른 모든 오류는 유효성 검사기 도구 설명서의 문제 해결 섹션을 참조하십시오.

## 로컬 배포로 구성 테스트 {#testing-config-local-deployment}

>[!IMPORTANT]
> 로컬 배포로 구성을 테스트하려면 Docker를 설치해야 합니다.

Dispatcher SDK `docker_run.sh` 의 스크립트를 사용하여 구성에 배포에만 표시되는 다른 오류가 없는지 테스트할 수 있습니다.

1. 유효성 검사기를 사용하여 배포 정보 생성

   `validator full -d out`
전체 구성을 인증하고 배치 정보를 외부에서 생성합니다.

1. 해당 배포 정보를 사용하여 문서 이미지에서 디스패처 시작

   macOS 컴퓨터에서 실행 중인 AEM 게시 서버에서 포트 4503에서 수신 대기하면 다음과 같이 해당 서버 앞에서 디스패처를 시작할 수 있습니다.

   `$ docker_run.sh out docker.for.mac.localhost:4503 8080`

   그러면 컨테이너가 시작되고 로컬 포트 8080에 Apache가 표시됩니다.

## 새 발송자 구성 사용 {#using-dispatcher-config}

유효성 검사기가 더 이상 문제를 보고하지 않고 도커 컨테이너가 아무런 오류 또는 경고 없이 시작하는 경우 구성을 git 저장소의 d`ispatcher/src` 하위 디렉토리로 이동할 수 있습니다.