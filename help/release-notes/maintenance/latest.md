---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service의 현재 유지 관리 릴리스 정보입니다.'
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: e771913562b3770e5a504432d40c770804aadc4b
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 34%

---

# 유지 관리 릴리스 정보 {#maintenance-release-notes}

다음 섹션에서는 Experience Manager as a Cloud Service 현재 유지 관리 릴리스의 기술 릴리스 정보에 대해 간략히 소개합니다.

## 릴리스 13804 {#release-13804}

다음은 2023년 10월 10일에 공개적으로 릴리스된 유지 보수 릴리스 13804에 대한 지속적인 개선 사항을 요약했습니다. 이 유지 관리 릴리스는 이전 유지 관리 릴리스 13665의 업데이트입니다.

이 유지 관리 릴리스(2023.10.0)에 대한 기능 활성화는 전체 기능 세트를 제공합니다. 자세한 내용은 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html)을 참조하십시오.

### 개선 사항 {#enhancements-13804}

* GRANITE-47238: 감사 로그 유지 관리 - 고객 구성을 사용하기 위해 크론 작업을 제거하십시오.
* GRANITE-47123: 게시(Sling) - 기본적으로 단축 경로 캐시를 비동기식으로 초기화하여 시작 시간을 개선합니다.
* GRANITE-46618: 게시(복제) - 복제 상태 메시지 일괄 처리를 통해 게시 시작 속도를 개선합니다.
* GRANITE-47136: 인덱싱 (다운로드) - 체크섬 유효성 검사를 비활성화하여 새 병렬 인덱스 다운로더의 다운로드 속도를 개선합니다.
* GRANITE-47211: Publish(인프라) - 세그먼트 저장소 수정 이름을 저장하고 가져와서 게시 계층 배포의 분리를 개선합니다.
* GRANITE-47267: Apache Felix Http Jetty 4.2.18로 업데이트(요청 매개변수 처리에 대한 버그 수정 포함)[FELIX-6625](https://issues.apache.org/jira/browse/FELIX-6625)) 로컬 및 RDE 개발을 위한 성능이 개선되었습니다.
* GRANITE-47247: 서블릿 확인 시 성능이 개선된 Sling Servlets Resolver 2.9.14로 업데이트합니다.

### 해결된 문제 {#fixed-issues-13804}

* GRANITE-47376: 작성자(Infra) - 순환 재시작 후 DiscoveryTopologyUndefined 오류를 수정했습니다.
* CQ-4353436: AEM 웹 콘솔(Sling) - ServiceUserMapperImpl 유효성 검사기(주체/사용자)의 빈 구성이 AEM 인스턴스([11912](https://issues.apache.org/jira/browse/SLING-11912)).
* SKYOPS-63925: 변형 작업 - JDK 11 - ZipException으로 인한 TransformJob 오류 방지: 잘못된 CEN 헤더 오류(disableZip64ExtraFieldValidation JVM 플래그 포함).
* SKYOPS-63361: 변형 작업(로깅) 변형 작업으로 로깅이 개선되었습니다(CUSTOMER_EXTRACT 하위 단계).
* SKYOPS-64103: FACT Tool (Logging) - Clientlib 컴파일 오류 및 경고 메시지를 줄이거나 자릅니다.
* SKYOPS-65109: 팩트 도구(오류 처리) - 해결되지 않은 종속성이 있는 콘텐츠 패키지를 사용하면 제대로 보고된 오류가 발생합니다.
* SKYOPS-65368: FACT Tool (오류 처리) - 도구가 끝없는 포함 사이클로 실행되어 결국 Clientlibs의 원형 임베드에서 시간이 초과됩니다.
* SKYOPS-64031: RDE - ComponentCacheImpl이 중복 ResourceResolverFactory 등록으로 인해 일관성 없는 상태가 될 수 있습니다([12019](https://issues.apache.org/jira/browse/SLING-12019)).
* ASSETS-29105: RDE - RDE 기능 모델의 SecurityProviderRegistration requiredServicePids에 제한 공급자가 누락되었습니다.
* GRANITE-44674: CoralUI - 날짜 선택기 필수 필드 기능이 잘못되었습니다.

### 알려진 문제 {#known-issues-13804}

* CQ-4354836: 프로젝트 콘솔에서 워크플로우를 시작하거나 작업을 만들 수 없습니다.
* CQ-4354834 : 사용자가 받은 편지함 작업에 주석을 추가할 수 없습니다.

### 임베드된 기술 {#embedded-tech-13804}

| 기술 | 버전 | 링크 |
|---|---|---|
| AEM OAK | 1.56-T20230927085643-189caed | [Oak API 1.56.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.56.0/index.html) |
| AEM SLING API | 버전 2.27.2 | [Apache Sling API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 버전 1.4.20-1.4.0 | [HTML 템플릿 언어 사양](https://github.com/adobe/htl-spec) |
| AEM 핵심 구성 요소 | 버전 2.23.4 | [AEM WCM 핵심 구성 요소](https://github.com/adobe/aem-core-wcm-components) |
