---
title: 캐싱 성능 문제 해결
seo-title: Troubleshooting caching performance
description: 캐싱 성능 문제 해결
seo-description: Troubleshooting caching performance
contentOwner: khsingh
exl-id: eae44a6f-25b4-46e9-b38b-5cec57b6772c
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# 캐싱 성능 {#caching-performance}

Cloud Service 환경에서 적응형 Forms 캐시를 구성하거나 사용하는 동안 다음 문제 중 일부가 발생할 수 있습니다.

## 이미지 또는 비디오가 포함된 일부 적응형 Forms은 Dispatcher 캐시에서 자동으로 무효화되지 않습니다 {#images-videos-not-invalidated}

자산 브라우저에서 이미지 또는 비디오를 선택하여 적응형 양식에 추가할 수 있습니다. 이러한 이미지가 자산 편집기에서 편집되면 이러한 이미지가 포함된 적응형 양식의 캐시된 버전이 무효화되지 않습니다. 적응형 양식은 이전 이미지를 계속 표시합니다.

이 문제를 해결하려면 이미지 및 비디오를 게시한 후 이러한 자산을 참조하는 적응형 Forms을 명시적으로 게시 취소하고 게시합니다.

## 컨텐츠 조각 또는 경험 조각을 포함하는 일부 적응형 Forms은 Dispatcher 캐시에서 자동으로 무효화되지 않습니다 {#content-fragments-experience-fragments-not-invalidated}

컨텐츠 조각 또는 경험 조각을 적응형 양식에 추가할 수 있습니다. 이러한 조각이 독립적으로 편집되고 게시되면 그러한 조각을 포함하는 적응형 양식의 캐시된 버전이 무효화되지 않습니다. 적응형 양식에 이전 조각이 계속 표시됩니다.

이 문제를 해결하려면 업데이트된 컨텐츠 조각 또는 경험 조각을 게시한 후 이러한 자산을 사용하는 적응형 Forms을 명시적으로 게시 취소하고 게시합니다.

## 응용 Forms의 첫 번째 인스턴스만 캐시됩니다 {#only-first-instance-cached}

적응형 양식 URL에 현지화 정보가 포함되지 않고 구성 관리자의 브라우저 로케일 사용 옵션이 활성화되면, 첫 번째 요청(요청된 브라우저 로케일)에 따라 현지화된 버전의 적응형 양식이 제공되고 적응형 양식의 인스턴스가 캐시되어 모든 후속 사용자에게 전달됩니다.

문제를 해결하려면 다음 단계를 수행하십시오.

1. Experience Manager 프로젝트를 엽니다.
1. 를 엽니다. `dispatcher/scr/conf.d/rewrites/rewrite.rules` 참조하십시오.
1. 를 엽니다. `conf.d/httpd-dispatcher.conf` 또는 런타임에 로드하도록 구성된 기타 구성 파일입니다.
1. 다음 코드를 파일에 추가하고 저장합니다. 사용자 환경에 맞게 수정하는 샘플 코드입니다.

```shellscript
    # Handle actual URL convention (just pass through)
    RewriteRule "^/content/forms/af/(.*)[.](.*).html$" "/content/forms/af/$1.$2.html" [PT]
    
    # Handle selector-based redirection based on browser language
    <VirtualHost *:80>
            # Handle actual URL convention (just pass through)
    RewriteRule "^/content/forms/af/(.*)[.](.*).html$" "/content/forms/af/$1.$2.html" [PT]

    # Handle selector based redirection basded on browser language
    # The Rewrite Condition is looking for the Accept-Language header and if found takes the first two character which most likely will be the desired language selector.
    RewriteCond %{HTTP:Accept-Language} ^(..).*$ [NC]
    RewriteRule "^/content/forms/af/(.*).html$" "/content/forms/af/$1.%1.html" [R]
    RewriteRule "^/content/forms/af/(.*).html$" "/content/forms/af/$1.%1.html" [R]
```

## CDN 캐싱이 300초 후 작동하지 않습니다 {#cdn-caching-stops-working-after-300-seconds}

CDN 캐싱은 300초 후 작동하지 않으며 CDN에 캐싱하기 위한 모든 요청이 Dispatcher로 리디렉션됩니다.

이 문제를 해결하려면 페이지 헤더를 0으로 설정하십시오.

1. 에서 파일 만들기 `src\conf.d\available_vhosts`

1. 페이지에 다음 내용을 추가하여 페이지 헤더를 설정합니다

   ```shellscript
       <IfModule mod_headers.c>
               Header add X-Vhost "publish"
               Header set age 0
       </IfModule>
   ```

1. 파일을 저장하고 닫습니다.
1. 다음에 대한 소프트 링크 수정 `src\conf.d\enabled_vhosts\default.vhost` 새 파일을 가리키려면
