---
title: GraphQL 지속 쿼리 - Dispatcher에서 캐싱 활성화
description: Dispatcher는 Adobe Experience Manager Publish 환경 앞에 있는 캐싱 및 보안 계층입니다. AEM Headless에서 지속 쿼리에 대한 캐싱을 활성화할 수 있습니다.
feature: Dispatcher, GraphQL API
source-git-commit: 6f07089812e587834784aeda7e62d3e4614f45a1
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 5%

---


# GraphQL 지속 쿼리 - Dispatcher에서 캐싱 활성화 {#graphql-persisted-queries-enabling-caching-dispatcher}

>[!CAUTION]
>
>Dispatcher에서 캐싱이 활성화되면 [CORS 필터](/help/headless/deployment/cross-origin-resource-sharing.md) 가 필요하지 않으므로 해당 섹션을 무시할 수 있습니다.

지속 쿼리의 캐싱은 Dispatcher에서 기본적으로 활성화되지 않습니다. 여러 출처가 있는 CORS(원본 간 리소스 공유)를 사용하는 고객은 Dispatcher 구성을 검토하고 업데이트해야 하므로 기본 활성화가 불가능합니다.

>[!NOTE]
>
>Dispatcher가 를 캐시하지 않습니다. `Vary` 머리글입니다.
>
>Dispatcher에서 다른 CORS 관련 헤더의 캐싱을 활성화할 수 있지만, CORS 출처가 여러 개일 경우 충분하지 않을 수 있습니다.

## 지속 쿼리 캐싱 활성화 {#enable-caching-persisted-queries}

지속 쿼리의 캐싱을 활성화하려면 Dispatcher 변수를 정의합니다 `CACHE_GRAPHQL_PERSISTED_QUERIES`:

1. Dispatcher 파일에 변수 추가 `global.vars`:

   ```xml
   Define CACHE_GRAPHQL_PERSISTED_QUERIES
   ```

>[!NOTE]
>
>을 준수하려면 [캐시할 수 있는 문서에 대한 Dispatcher의 요구 사항](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/troubleshooting/dispatcher-faq.html#how-does-the-dispatcher-return-documents%3F), Dispatcher는 접미사를 추가합니다 `.json` 결과를 캐시할 수 있도록 모든 지속 쿼리 URL에 매핑합니다.
>
>지속 쿼리 캐시가 활성화되면 이 접미사는 재작성 규칙에 의해 추가됩니다.

## Dispatcher의 CORS 구성 {#cors-configuration-in-dispatcher}

CORS 요청을 사용하는 고객은 Dispatcher에서 CORS 구성을 검토하고 업데이트해야 할 수 있습니다.

* 다음 `Origin` 헤더는 Dispatcher를 통해 AEM 게시로 전달할 수 없습니다.
   * 다음 확인: `clientheaders.any` 파일.
* 대신 CORS 요청은 Dispatcher 수준에서 허용된 출처를 평가해야 합니다. 또한 이 접근 방법에서는 모든 경우에 CORS 관련 헤더가 한 위치에서 올바르게 설정되도록 합니다.
   * 이러한 구성을 다음에 추가해야 합니다. `vhost` 파일. 예시적인 구성이 아래에 주어지며, 단순화를 위해, CORS-관련 부분만이 제공되었다. 특정 사용 사례에 맞게 조정할 수 있습니다.

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
