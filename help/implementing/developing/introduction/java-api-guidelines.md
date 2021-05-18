---
title: Java API 지침
description: AEM은 많은 Java API를 사용할 수 있도록 표시하는 풍부한 오픈 소스 소프트웨어 스택을 기반으로 합니다.
exl-id: 0be33ec9-a4c3-4400-99d3-ed8366c5b5f9
source-git-commit: cbcc20e75e4a0cb6d0e060039f4945ff4a85ff5c
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Java API 지침 {#java-api-guidelines}

AEM(Adobe Experience Manager)은 개발 중에 사용할 수 있는 많은 Java API를 표시하는 풍부한 오픈 소스 소프트웨어 스택을 기반으로 구축되었습니다.

AEM은 다음 4개의 기본 Java API 세트를 내림차순으로 기본 설정합니다.

1. **[Adobe Experience Manager(AEM)](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/index.html)**  - 페이지, 자산, 워크플로우 등 제품 개요
1. **[Apache Sling Web Framework](https://sling.apache.org/apidocs/sling11/)**  - 리소스, 값 맵 및 HTTP 요청과 같은 REST 및 리소스 기반 추상적 개념입니다.
1. **[JCR(Apache Jackrabbit Oak)](http://jackrabbit.apache.org/oak/docs/oak_api/overview.html)**  - 노드, 속성 및 세션과 같은 데이터 및 컨텐츠 추상입니다.
1. **[OSGi(Apache Felix)](https://felix.apache.org)**  - 서비스 및 (OSGi) 구성 요소와 같은 OSGi 애플리케이션 컨테이너 추상.

AEM에서 API를 제공하는 경우 Sling, JCR 및 OSGi보다 API를 선호합니다. AEM에서 API를 제공하지 않는 경우 JCR 및 OSGi보다 Sling을 선호합니다.

이러한 지침에 대한 자세한 내용은 [Java API 우수 사례 이해](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html) 문서를 참조하십시오.
