---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
source-git-commit: 4aa4954f214545dcd768fdf955f1fc2f776da939
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 82%

---


# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 11835 {#release-11835}

다음은 2023년 4월 19일에 릴리스된 유지 관리 릴리스 11835에 대한 지속적인 개선 사항입니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 11382의 업데이트입니다.

이 유지 관리 릴리스에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [최신 릴리스 정보](/help/release-notes/release-notes-cloud/release-notes-current.md)를 참조하십시오.

### 해결된 문제 {#fixed-issues-11835}

- SITES-12573 - 하나의 변수가 지정되지 않으면 필터 내부의 변수를 사용하는 GraphQL 쿼리가 실패합니다. GraphQL을 AEM as a Cloud Service&#39;와 함께 사용하려면 이 릴리스로 업데이트하지 마십시오.
- SKYOPS-51970 - buildImage 스텝에서 사용된 FACT 버전의 확인된 회귀, 불일치 사용자 매핑 초래
- GRANITE-44542 - 문제가 패키지 필터에 포함된 폴더를 위한 패키지 노드 유형을 지정하지 않은(.content.xml with jcr:primaryType을 입력해서) 고객을 위해서 보고되었습니다. 이 때문에 이들 폴더가 nt:folder로 취급되며 다양한 사례에서 문제가 발생하고 있습니다.
- SKYOPS-56928 - Apache HTTPD 회귀로 인해 404 오류가 발생할 수 있습니다. 안전상의 이유로 이러한 문제가 발생하는 경우 이전 버전으로 롤백하는 것이 좋습니다. 파이프라인은 해당 기간 동안 실행되지 않습니다.

### 임베드된 기술 {#embedded-tech-11835}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.44-T20221206170501-6d59064 | [Oak API 1.44.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| AEM SLING API | 버전 2.27.0 | [Apache Sling API 2.27.0 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.21.2 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
