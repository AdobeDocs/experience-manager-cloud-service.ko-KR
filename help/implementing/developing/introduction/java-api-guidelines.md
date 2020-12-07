---
title: Java API 지침
description: AEM은 많은 Java API를 사용할 수 있도록 표시하는 풍부한 오픈 소스 소프트웨어 스택을 기반으로 구축되었습니다.
translation-type: tm+mt
source-git-commit: b927992107d7e7e4df5511a366c71449ff73ec93
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# Java API 지침 {#java-api-guidelines}

Adobe Experience Manager(AEM)은 개발 중에 사용할 수 있는 많은 Java API를 노출하는 풍부한 오픈 소스 소프트웨어 스택을 기반으로 구축되었습니다.

AEM은 다음과 같은 네 가지 기본 Java API 세트를 기반으로 기본 설정을 내림차순으로 만듭니다.

1. **Adobe Experience Manager(AEM)** - 페이지, 자산, 워크플로우 등과 같은 제품 개요
1. **[Apache Sling Web Framework](https://sling.apache.org/apidocs/sling11/)** - 리소스, 값 맵 및 HTTP 요청과 같은 REST 및 리소스 기반 추상적 개념입니다.
1. **[JCR(Apache Jackrabbit Oak)](http://jackrabbit.apache.org/oak/docs/oak_api/overview.html)**  - 노드, 속성 및 세션과 같은 데이터 및 컨텐츠 추상입니다.
1. **[OSGi(Apache Felix)](https://felix.apache.org)** - 서비스 및 (OSGi) 구성 요소와 같은 추상적 애플리케이션 컨테이너

AEM에서 API를 제공하는 경우 Sling, JCR 및 OSGi보다 선호합니다. AEM에서 API를 제공하지 않는 경우 JCR 및 OSGi보다 Sling을 선호합니다.

이러한 지침에 대한 자세한 내용은 문서 [Java API 우수 사례 이해를 참조하십시오.](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html)
