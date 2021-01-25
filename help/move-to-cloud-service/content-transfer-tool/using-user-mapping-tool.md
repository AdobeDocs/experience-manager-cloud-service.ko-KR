---
title: 사용자 매핑 도구 사용
description: 사용자 매핑 도구 사용
translation-type: tm+mt
source-git-commit: 664c278494a5ac88362b994946060ab3baa846d8
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# 사용자 매핑 도구 사용 {#user-mapping-tool}

## 개요 {#overview}

Cloud Service에서 AEM으로 전환 여정의 일부로, 사용자와 그룹을 기존 AEM 시스템에서 AEM으로 Cloud Service으로 이동시켜야 합니다. 이는 컨텐츠 전송 도구에 의해 수행됩니다.

Cloud Service로서 AEM의 주요 변경 사항은 작성 계층에 액세스하기 위해 Adobe ID를 완벽하게 통합하는 것입니다.  이렇게 하려면 사용자 및 사용자 그룹을 관리하기 위해 Adobe Admin Console을 사용해야 합니다. 사용자 프로필 정보는 모든 Adobe 클라우드 애플리케이션에서 Single Sign-On을 제공하는 Adobe Identity Management System(IMS)에 중앙 집중화되어 있습니다. 자세한 내용은 Identity Management을 참조하십시오. 이러한 변경 사항으로 인해 Cloud Service 작성자 인스턴스에서 사용자와 그룹이 중복되지 않도록 기존 사용자 및 그룹을 IMS ID에 매핑해야 합니다.

## 중요 고려 사항 {#important-considerations}

고려해야 할 몇 가지 예외적인 사례가 있다. 다음 특정 사례가 기록되고 해당 사용자나 그룹이 매핑되지 않습니다.

1. 사용자에게 jcr 노드의 `profile/email` 필드에 이메일 주소가 없는 경우.

1. 사용된 조직 ID에 대한 IMS 시스템에서 지정된 이메일을 찾을 수 없는 경우(또는 다른 이유로 IMS ID를 검색할 수 없는 경우)

1. 사용자가 현재 비활성화되어 있으면 비활성화되어 있지 않은 것처럼 처리됩니다.  매핑되고 정상적으로 마이그레이션되며 클라우드 인스턴스에서 비활성화된 상태로 유지됩니다.

## 사용자 매핑 도구 {#using-user-mapping-tool} 사용

사용자 매핑 도구는 IMS 사용자를 이메일로 조회하고 IMS ID를 반환할 수 있도록 해주는 API를 사용합니다. 이 API를 사용하려면 사용자가 조직의 클라이언트 ID, 클라이언트 암호 및 액세스 토큰/전달자 토큰을 만들어야 합니다.

다음 단계에 따라 설정합니다.

1. Adobe ID을 사용하여 [Adobe 개발자 콘솔](https://console.adobe.io)로 이동합니다.
1. 새 프로젝트 만들기 또는 기존 프로젝트 열기
1. API 추가
1. 사용자 관리 API 선택
1. JWT 자격 증명 만들기
1. 키 쌍 생성 또는 공개 키 업로드(rsa가 좋지 않음)
1. 액세스 토큰(또는 JWT 토큰 또는 무기명 토큰)을 생성합니다.
1. 이 모든 정보(클라이언트 ID, 클라이언트 암호, 기술 계정 ID, 기술 계정 이메일, 조직 ID, 액세스 토큰)를 안전한 장소에 저장합니다.