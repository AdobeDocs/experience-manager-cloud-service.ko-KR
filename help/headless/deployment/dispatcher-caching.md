---
title: GraphQL 지속 쿼리 - Dispatcher에서 캐싱 활성화
description: Dispatcher는 Adobe Experience Manager 게시 환경 앞에 있는 캐싱 및 보안 계층입니다. AEM Headless에서 지속 쿼리에 대한 캐싱을 활성화할 수 있습니다.
feature: Dispatcher, GraphQL API
exl-id: 30a97e56-6699-41c4-a4eb-fc6236667f8f
source-git-commit: ea5b404e83c11f0057342bff22ba45e6b0ead124
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 81%

---

# GraphQL 지속 쿼리 - Dispatcher에서 캐싱 활성화 {#graphql-persisted-queries-enabling-caching-dispatcher}

>[!CAUTION]
>
>Dispatcher에서 캐싱이 활성화된 경우 [CORS 필터](/help/headless/deployment/cross-origin-resource-sharing.md)가 필요하지 않으므로 해당 섹션은 무시해도 됩니다.

지속 쿼리 캐싱은 기본적으로 Dispatcher에서 활성화되어 있지 않습니다. 원본이 여러 개인 CORS(원본 간 리소스 공유)를 사용하는 고객은 Dispatcher 구성을 검토하고 업데이트해야 하므로 기본값으로 활성화할 수는 없습니다.

>[!NOTE]
>
>Dispatcher는 `Vary` 헤더를 캐시하지 않습니다.
>
>다른 CORS 관련 헤더의 캐싱은 Dispatcher에서 활성화할 수 있지만 CORS 원본이 여러 개인 경우에는 충분하지 않을 수 있습니다.

>[!NOTE]
>
>Dispatcher에 대한 자세한 설명서는 [Dispatcher 안내서](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html)를 참조하십시오.

## 지속 쿼리 캐싱 활성화 {#enable-caching-persisted-queries}

지속 쿼리의 캐싱을 활성화하려면 `CACHE_GRAPHQL_PERSISTED_QUERIES` Dispatcher 변수를 정의합니다.

1. `global.vars` Dispatcher 파일에 변수를 추가합니다.

   ```xml
   Define CACHE_GRAPHQL_PERSISTED_QUERIES
   ```

>[!NOTE]
>
>지속 쿼리에 대해 Dispatcher 캐싱이 활성화된 경우 다음을 사용 `Define CACHE_GRAPHQL_PERSISTED_QUERIES` an `ETag` Dispatcher가 응답에 헤더를 추가합니다.
>
>기본적으로 `ETag` 헤더는 다음 지시문으로 구성됩니다.
>
>```
>FileETag MTime Size 
>```
>
>그러나 이 설정은 응답의 작은 변경 사항을 고려하지 않으므로 지속 쿼리 응답에 사용할 때 문제를 일으킬 수 있습니다.
>
>개인을 달성하려면 `ETag` 계산 *각각* 에 고유한 응답 `FileETag Digest` dispatcher 구성에서 설정을 사용해야 합니다.
>
>```xml
><Directory />    
>   ...    
>   FileETag Digest
></Directory> 
>```

>[!NOTE]
>
>[캐시할 수 있는 문서에 대한 Dispatcher의 요구 사항](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/troubleshooting/dispatcher-faq.html#how-does-the-dispatcher-return-documents%3F)을 준수하기 위해 Dispatcher는 `.json` 접미사를 모든 지속 쿼리 URL에 추가하여 결과를 캐시할 수 있도록 합니다.
>
>이 접미사는 지속 쿼리 캐싱이 활성화되면 다시 쓰기 규칙에 의해 추가됩니다.

## Dispatcher의 CORS 구성 {#cors-configuration-in-dispatcher}

CORS 요청을 사용하는 고객은 Dispatcher에서 CORS 구성을 검토하고 업데이트해야 할 수도 있습니다.

* `Origin` 헤더는 Dispatcher를 통해 AEM 게시로 전달되어서는 안 됩니다.
   * `clientheaders.any` 파일을 확인하십시오.
* 대신 Dispatcher 수준에서 허용된 원본에 대해 CORS 요청을 평가해야 합니다. 또한 이 접근 방식을 사용하면 CORS 관련 헤더를 모든 경우에 한 곳에서 올바르게 설정할 수 있습니다.
   * 이러한 구성은 `vhost` 파일에 추가해야 합니다. 예시 구성은 아래와 같으며, 간단하게 CORS 관련 부분만 제공되었습니다. 특정 사용 사례에 맞게 조정할 수 있습니다.

  ```xml
  <VirtualHost *:80>
     ServerName "publish"
  
     # ...
  
     <IfModule mod_headers.c>
         Header add X-Vhost "publish"
  
          ################## Start of the CORS specific configuration ##################
  
          SetEnvIfExpr "req_novary('Origin') == ''"  CORSType=none CORSProcessing=false
          SetEnvIfExpr "req_novary('Origin') != ''"  CORSType=cors CORSProcessing=true CORSTrusted=false
  
          SetEnvIfExpr "req_novary('Access-Control-Request-Method') == '' && %{REQUEST_METHOD} == 'OPTIONS' && req_novary('Origin') != ''  " CORSType=invalidpreflight CORSProcessing=false
          SetEnvIfExpr "req_novary('Access-Control-Request-Method') != '' && %{REQUEST_METHOD} == 'OPTIONS' && req_novary('Origin') != ''  " CORSType=preflight CORSProcessing=true CORSTrusted=false
          SetEnvIfExpr "req_novary('Origin') -strcmatch 'https://%{HTTP_HOST}*'"  CORSType=samedomain CORSProcessing=false
  
          # For requests that require CORS processing, check if the Origin can be trusted
          SetEnvIfExpr "%{HTTP_HOST} =~ /(.*)/ " ParsedHost=$1
  
          ################## Adapt the regex to match CORS origin for your environment
          SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*.your-domain.tld(:\d+)?$)#" CORSTrusted=true
  
          # Extract the Origin header 
          SetEnvIfNoCase ^Origin$ ^https://(.*)$ CORSTrustedOrigin=https://$1
  
          # Flush If already set
          Header unset Access-Control-Allow-Origin
          Header unset Access-Control-Allow-Credentials
  
          # Trusted
          Header always set Access-Control-Allow-Credentials "true" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Origin "%{CORSTrustedOrigin}e" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Methods "GET" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Max-Age 1800 "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Headers "Origin, Accept, X-Requested-With, Content-Type, Access-Control-Request-Method, Access-Control-Request-Headers" "expr=reqenv('CORSTrusted') == 'true'"
  
          # Non-CORS or Not Trusted
          Header unset Access-Control-Allow-Credentials "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Allow-Origin "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Allow-Methods "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Max-Age "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
  
          # Always vary on origin, even if its not there.
          Header merge Vary Origin
  
          # CORS - send 204 for CORS requests which are not trusted
          RewriteCond expr "reqenv('CORSProcessing') == 'true' && reqenv('CORSTrusted') == 'false'"
          RewriteRule "^(.*)" - [R=204,L]
  
          ################## End of the CORS specific configuration ##################
  
     </IfModule>
  
     <Directory />
  
         # ...
  
     </Directory>
  
     # ...
  
  </VirtualHost>
  ```
