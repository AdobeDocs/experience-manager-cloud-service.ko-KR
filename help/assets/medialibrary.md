---
title: AEM Assets와 AEM MediaLibrary
description: AEM 자산 및 FAQ와 관련된 질문입니다. AEM Media Library(두 가지 차이점 포함)
contentOwner: AG
translation-type: tm+mt
source-git-commit: 82dd9bd69fe994f74c7be8a571e386f0e902f6a1

---


# AEM Assets와 AEM MediaLibrary FAQ {#aem-assets-vs-aem-medialibrary}

AEM(Adobe Experience Manager) 자산은 AEM 플랫폼의 필수 요소입니다. 이러한 매끄러운 통합은 AEM의 주요 장점으로 보이며 컨텐츠 작성자의 일관성 및 높은 생산성을 보장합니다.

## AEM Assets 소개 {#what-is-aem-assets}

AEM Assets는 고객이 웹 기반 저장소에서 디지털 자산(이미지, 비디오, 문서 및 오디오 클립)을 관리할 수 있도록 해주는 AEM Platform의 애플리케이션입니다. AEM 자산에는 메타데이터 지원, 변환, 디지털 자산 관리 파인더 및 사용자 인터페이스를 통한 관리가 포함되어 있습니다.

## AEM 미디어 라이브러리란? {#what-is-the-aem-media-library}

AEM 미디어 라이브러리는 이미지 및 기타 공유 리소스가 저장되는 AEM WCM 컨텐츠 저장소의 지정된 부분입니다. 미디어 라이브러리는 AEM WCM의 디지털 자산 관리 기능을 사용합니다.

## AEM WCM 파섹 {#what-do-i-get-from-aem-assets-that-is-not-part-of-aem-wcm}

AEM Assets 고객만 사용할 수 있는 고유 기능은 다음과 같습니다.

1. 제목, 태그 및 설명 이외의 메타데이터를 추출하고 편집할 수 있습니다.
1. siteadmin 옆에 있는 두 번째 단추를 클릭하여 시작 화면에서 사용할 수 있는 AEM 자산 관리입니다.
1. 디지털 자산 관리와 관련된 모든 워크플로우 단계(AEM 자산 통합, AEM 자산 삭제, AEM 자산 하위 자산 처리, AEM 자산 메타데이터 추출)
1. 라이브러리(예: &quot;dam&quot; im package space 포함)

이러한 기능을 사용하려면 유효한 AEM Assets 라이선스가 필요합니다.

## AEM 자산을 개별 패키지로 사용할 수 있습니까? {#is-aem-assets-available-as-a-separate-package}

아니오. 모든 AEM 애플리케이션 및 Add-Ons는 설치 및 배포를 간소화하기 위해 모든 기능이 포함된 단일 패키지로 제공됩니다. 이는 패키지에 있는 모든 기능을 사용할 수 있는 권한이 있다는 것을 의미하지는 않습니다.

## 디지털 자산의 메타데이터를 편집하려고 합니다. AEM 자산이 필요합니까? {#i-want-to-edit-metadata-of-digital-assets-do-i-need-aem-assets}

제목, 설명 및 태그 이외의 메타데이터를 편집하려면 AEM 자산에 라이선스를 부여해야 합니다.

## 내 웹사이트에서 카테고리 조건부를 사용하고 싶다. AEM 자산이 필요합니까? {#i-want-to-use-the-category-predicate-on-my-website-do-i-need-aem-assets}

예. Geometrixx Press Center에서 사용되는 다른 모든 구성 요소와 함께 카테고리 조건자는 AEM Assets의 일부이며 AEM Assets 라이선스가 필요합니다.

## 가져올 때 이미지 크기를 자동으로 조정하려고 합니다. AEM 자산이 필요합니까? {#i-want-to-automatically-resize-images-upon-import-do-i-need-aem-assets}

예. 이미지 크기 조정 및 자동 워크플로우 기반 변환과 변환 관리 기능은 AEM Assets의 일부이며 AEM Assets 라이선스가 필요합니다.

## 사용자 정의된 이미지 구성 요소를 사용하여 이미지 크기를 조정하고 싶습니다. AEM 자산이 필요합니까? {#i-want-to-resize-images-using-a-customized-image-component-do-i-need-aem-assets}

이미지 구성 요소는 AEM WCM의 일부입니다. 이미지 구성 요소뿐만 아니라 AEM 자산에 의해 사용되는 그래픽 라이브러리는 AEM 플랫폼의 일부이며 AEM 자산 라이선스가 필요하지 않습니다.

## AEM 자산에 라이선스를 부여하지 않은 경우 사용자가 AEM 자산을 사용하지 못하도록 하려면 어떻게 해야 합니까? {#how-can-i-prevent-my-users-from-using-aem-assets-if-i-did-not-license-aem-assets}

AEM에서 모든 AEM 자산별 워크플로우, 구성 요소, 분류, 옵션 및 AEM 자산 관리자를 제거할 수 있습니다. 이렇게 하면 사용자가 라이선스가 부여되지 않은 AEM 자산 기능을 실수로 사용할 수 없습니다.

## 페이지에 이미지를 추가하고 이미지를 자르고 크기를 조정하려고 합니다. AEM 자산이 필요합니까? {#i-want-to-add-images-to-a-page-and-want-to-crop-and-resize-these-images-do-i-need-aem-assets}

이 경우 AEM 자산을 구매할 필요가 없습니다. 스마트 이미지 구성 요소를 사용하면 이미지를 페이지에 직접 업로드할 수 있으므로 미디어 라이브러리를 사용할 필요가 없습니다.

## AEM 자산과 미디어 라이브러리에서 사용할 수 있는 기능의 세부 목록 {#listoffeatures}

**AEM Assets**

* 컬렉션 및 라이트박스
* 고급 메타데이터 속성 및 관리
* Adobe Asset Link(Creative Cloud for enterprise에 연결)
* AEM Desktop App
* 처리 프로필
* InDesign Server 통합
* 자산 템플릿 및 카탈로그 제작 프레임워크
* Adobe Photoshop, Illustrator 및 InDesign 연결된 에셋
* 다국어 에셋 관리
* PIM 통합
* 권한 관리
* Camera RAW 지원
* 검색 패싯 관리 및 구성
* 사전 제작된 DAM 워크플로우(예: 사진 촬영)
* 자산 보고 및 분석:자산 통찰력
* 3D 자산 관리
* 연결된 자산
* 브랜드 포털
* 셀프 서비스 액세스
* 검색, 검색 및 다운로드
* 컬렉션 및 폴더 공유
* 관리 도구
* 스마트 태그
* 시각적 검색
* 자산 관리 UI

**미디어 라이브러리**

* 기본 메타데이터 속성
* 태그 관리
* 버전 제어
* 정적 표현물
* 프로젝트, 작업, 워크플로우 작성
* 활동 스트림(타임라인)
* 쿼리 빌더(API)
* Marketing Cloud 통합
* UI 사용자 정의 및 확장
* 주석 및 주석