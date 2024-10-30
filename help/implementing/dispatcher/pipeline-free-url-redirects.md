---
title: 파이프라인 없는 URL 리디렉션
description: Git 또는 Cloud Manager 파이프라인에 액세스하지 않고 301 또는 302 리디렉션을 선언하는 방법을 알아봅니다.
feature: Dispatcher
role: Admin
source-git-commit: 567c75f456f609dbc254753b439151d0f4100bc0
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 0%

---

# 파이프라인 없는 URL 리디렉션 {#pipeline-free-redirects}

>[!NOTE]
>이 기능은 아직 릴리스되지 않았습니다.

여러 가지 이유로 조직에서 301(또는 302) 리디렉션을 유발하는 방식으로 URL을 다시 작성합니다. 즉, 브라우저가 다른 페이지로 리디렉션됩니다.

시나리오에는 다음이 포함됩니다.

* 제거된 HTML 페이지이므로 `404 Page Not Found` 오류가 표시되지 않고 대체 페이지(경우에 따라 홈 페이지)로 이동됩니다.
* 이름이 변경된 HTML 페이지.
* SEO 최적화.

AEM as a Cloud Service은 클라이언트측 리디렉션을 구현하기 위해 [몇 가지 접근 방식](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/administration/url-redirection)을 제공하지만, 이 문서에 설명된 전략인 파이프라인 없는 리디렉션은 다음과 같은 경우에 유용한 선택입니다.

* 리디렉션을 유지 관리하는 사람은 소스 제어에 파일 변경 내용을 커밋할 권한이 없거나 Cloud Manager 웹 계층 구성 파이프라인을 실행할 권한이 없는 비즈니스 사용자입니다.
* 리디렉션의 수는 몇 개에서 수만 개에 이른다.
* 사용자 지정 프로젝트로 만들거나 [ACS Commons Rewrite Map 관리자](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html)를 사용하여 사용자 인터페이스의 옵션을 원하는 경우

이 기능의 핵심은 AEM Apache/Dispatcher이 게시 저장소의 지정된 위치에 배치된 하나 이상의 재작성 맵 파일을 로드(또는 재로드)하는 기능입니다. 파일이 도착하는 방법은 이 기능의 범위를 벗어나지만 다음 방법 중 하나를 고려할 수 있습니다.

* 작성자 사용자 인터페이스에서 재작성 맵을 에셋으로 수집하고 게시합니다.
* URL 매핑을 관리하고 맵 다시 작성 파일을 게시할 수 있는 사용자 인터페이스가 포함된 [ACS Commons Rewrite Map 관리자](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html)를 설치하는 중입니다.
* 사용자 정의 응용 프로그램을 작성함으로써 완벽한 유연성을 제공합니다. 예를 들어 URL 매핑을 관리하는 사용자 인터페이스 또는 명령줄 인터페이스 또는 재작성 맵을 업로드하는 양식 중 하나를 선택합니다. 그러면 AEM API를 사용하여 재작성 맵 파일을 게시할 수 있습니다.

>[!NOTE]
> 이 기능을 사용하려면 AEM 버전 **18311 이상이 필요합니다**.

## 맵 다시 작성 {#rewrite-map}

재작성 맵은 기본적으로 300초마다 Apache HTTP 서버에 의해 다시 로드됩니다(변경된 경우)(값은 구성 가능). 파일 형식은 [Apache 설명서](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html#txt)에 설명된 일반 텍스트 키-값 맵 RewriteMap 파일 형식을 따라야 합니다.

다시 작성 맵 파일의 위치를 지정하려면 이름이 `managed-rewrite-maps.yaml`인 파일을 만들어야 하며 Cloud Manager 전체 스택 파이프라인 또는 웹 계층 파이프라인을 사용하여 한 번 배포해야 합니다. Dispatcher 구성의 [src/opt-in](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/dispatcher.cloud/src/opt-in) 폴더에 파일을 만들어야 합니다. [유연한 모드 파일 구조](/help/implementing/dispatcher/validation-debug.md#flexible-mode-file-structure)를 사용해야 합니다.

다음 패턴으로 구성할 수 있습니다.

```
maps:
- name: my.map
  path: <path-in-publish-repository>/redirectmap.txt
```

예를 들어 맵 다시 작성 파일을 배치하기 위해 선택한 메서드가 맵 파일을 `mysite-redirectmap.txt`(이)라는 자산으로 AEM에 수집한 다음 게시하는 경우 `/content/dam` 아래에 폴더를 지정할 수 있습니다.

```
maps:
- name: my.map
  path: /content/dam/redirectmaps/mysite-redirectmap.txt
```

그런 다음 `rewrites/rewrite.rules` 또는 `<yourfile>.vhost`과(와) 같은 Apache 구성 파일에서 이름 속성(`my.map`(위의 샘플에서)에서 참조하는 맵 파일을 구성해야 합니다.

`RewriteMap` 지시문은 `sdbm`(단순 DBM) 형식을 사용하여 DBM(데이터베이스 관리자) 파일 형식으로 데이터가 저장되었음을 나타내야 합니다.

나머지 구성은 `redirectmap.txt`의 형식에 따라 다릅니다. 아래 샘플에 표시된 가장 간단한 형식은 원본 URL과 매핑된 URL 간의 일대일 매핑입니다.

```
# RewriteMap from managed rewrite maps
RewriteMap map.foo dbm=sdbm:/tmp/rewrites/my.map
RewriteCond ${map.foo:$1} !=""
RewriteRule ^(.*)$ ${map.foo:$1|/} [L,R=301]
```


## 고려 사항 {#considerations}

다음 사항에 유의하십시오.

* 기본적으로 다시 작성 맵을 로드할 때 전체 맵 파일이 로드될 때까지 기다리지 않고 Apache가 시작되므로 전체 맵이 로드될 때까지 일시적으로 불일치가 발생할 수 있습니다. Apache가 전체 맵 콘텐츠가 로드될 때까지 기다리도록 이 설정을 변경할 수 있지만 Apache가 시작되는 데에는 더 오랜 시간이 걸립니다. Apache가 대기하도록 이 동작을 변경하려면 `wait:true`을(를) `managed-rewrite-maps.yaml` 파일에 추가하십시오.
* 로드 빈도를 변경하려면 `ttl: <integer>`을(를) `managed-rewrite-maps.yaml` 파일에 추가하십시오. 예 `ttl: 120`.
* Apache에는 RewriteMap 단일 항목에 대해 1024 길이 제한이 있습니다.
