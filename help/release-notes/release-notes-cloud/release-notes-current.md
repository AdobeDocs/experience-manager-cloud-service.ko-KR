---
title: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
description: ' [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보'
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 6b38601e9bd29c71e5f70b46d2fa55a928851adc
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 41%

---

# [!DNL Adobe Experience Manager] as a Cloud Service 최신 릴리스 정보 {#release-notes}

다음 섹션에서는 [!DNL Experience Manager] as a Cloud Service의 최신 버전 기능 릴리스 정보에 대해 간략히 소개합니다.

>[!NOTE]
>
>여기에서 2021, 2022 버전 등 이전 버전의 릴리스 정보로 이동할 수 있습니다.
>
>[!DNL Experience Manager] as a Cloud Service의 향후 기능 활성화에 대해 알아보려면 [Experience Manager 릴리스 로드맵](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=ko-KR)을 살펴보십시오.

>[!NOTE]
>
>릴리스와 직접적으로 관련되지 않는 설명서 업데이트의 세부 정보는 [설명서 업데이트](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html)를 참조하십시오.

## 릴리스 일자 {#release-date}

의 릴리스 날짜 [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 현재 기능 릴리스(2023.4.0)는 2023년 6월 7일입니다. 다음 기능 릴리스(2023.6.0)는 2023년 6월 29일에 예정되어 있습니다.

## 릴리스 비디오 {#release-video}

2023년 4월 릴리스 개요 비디오를 통해 2023.4.0 릴리스에 추가된 기능에 대한 간단한 요약을 살펴보십시오:

>[!VIDEO](https://video.tv.adobe.com/v/3418681/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### [!DNL Experience Manager Sites]의 새로운 기능 {#sites-features}

* 콘텐츠 조각을 JSON 오퍼로 AEM as a Cloud Service에서 Adobe Target으로 내보냅니다.
* 내부 캐싱 향상과 함께 GraphQL 페이지 매김 및 정렬에 대한 지원은 이제 복잡한 GraphQL 쿼리 및 필터를 사용하여 AEM에서 대규모 콘텐츠 세트를 가져올 때 분리된 클라이언트 애플리케이션의 성능을 개선하는 데 도움이 됩니다.

### 의 새로운 기능 [!DNL Experience Manager Sites] 전치사 {#prerelease-sites}

* 이제 콘텐츠 조각 및 해당 참조를 게시자에 게시할 수 있습니다. [AEM 미리보기 서비스](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments.html?lang=en#access-preview-service) 사용 [콘텐츠 조각 콘솔](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=en)를 활성화하면 사용자가 라이브로 전환되기 전에 분리된 미리보기 애플리케이션에서 최종 경험을 미리 볼 수 있습니다.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### [!DNL Assets]의 새로운 기능 {#assets-features}

* WebP 이미지에 대한 지원이 추가되어 자동으로 메타데이터를 추출하고 썸네일 및 사용자 정의 렌디션을 생성합니다. 이제 이러한 파일에 대해 스마트 태그 기능도 지원됩니다. Dynamic Media 기능은 WebP에서 입력 형식으로 지원되지 않습니다.

* [향상된 검색 경험](/help/assets/search-assets.md#aftersearch) - 이제 검색 결과에 표시되는 에셋에서 다음 작업을 빠르게 수행할 수 있습니다.

   * 워크플로우 만들기
   * 새 버전 만들기
   * 에셋 연결 또는 연결 해제

      이러한 작업을 수행하기 위해 에셋 위치로 이동하여 에셋 위치의 속성을 볼 필요가 없습니다.

* 색상 검색 패싯 유용성 개선 사항 - 이제 색상 값에 대한 입력 필드를 편집할 수 있으며 색상 피커를 종료할 때만 검색 결과가 업데이트됩니다.

* 새로운 프로토콜(DASH - Dynamic Adaptive Streaming over HTTP)이 Dynamic Media 비디오 게재(CMAF 활성화)에서 적응형 스트리밍을 위해 시작되었습니다.
   * 적응형 스트리밍(DASH/HLS)은 비디오에 대한 더 나은 최종 사용자 시청 경험 보장
   * DASH는 적응형 비디오 스트리밍을 위한 국제 표준 프로토콜이며 업계에서 널리 채택되고 있음
   * 지원 티켓을 통해 모든 지역에서 사용 가능

* Dynamic Media _스냅샷_ - 테스트 이미지 또는 Dynamic Media URL을 실험하여 다양한 이미지 수정자의 출력을 확인하고, 파일 크기(WebP 및 AVIF 전달), 네트워크 대역폭 및 장치 픽셀 비율에 대해 스마트 이미징을 최적화합니다. 다음을 참조하십시오 [Dynamic Media 스냅샷](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot.html).

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### [!DNL Forms] 프리릴리스에서 사용 가능한 새로운 기능 {#new-features-available-in-channel}

* **[적응형 양식을 Microsoft SharePoint 및 Microsoft OneDrive에 제출](/help/forms/configuring-submit-actions.md)**: 비즈니스 사용자 민첩성을 개선하여 새로운 양식을 빠르게 시작하고, Microsoft SharePoint 사이트 또는 OneDrive 폴더와 같이 일상적으로 사용하는 도구에 제출된 데이터를 저장합니다.

### [!DNL Forms] 프리릴리스의 기능 {#prerelease-features-forms}

* [향상된 Adobe Acrobat Sign 통합 및 규정 준수](/help/forms/adobe-sign-integration-adaptive-forms.md): 이제 AEM Forms을 Adobe Acrobat Sign for Government와 통합하여 정부 관련 계정(정부 부서 및 기관)에 대한 적응형 양식 제출을 통해 전자 서명에 대한 고급 수준의 규정 준수 및 보안을 제공합니다.

   Adobe Acrobat Sign for Government와의 통합을 통해 파트너와 정부 고객은 적응형 Forms의 전자 서명을 사용하여 가장 미션 크리티컬하고 민감한 업무 라인을 수행할 수 있습니다. 이러한 추가적인 보안 계층을 통해 모든 전자 서명은 FedRAMP Moderate 규정을 완벽하게 준수할 수 있으므로 정부 고객이 안심할 수 있습니다.

* [AEM Sites 편집기 내의 적응형 Forms](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md): 이제 AEM Sites 편집기를 사용하여 여러 양식을 신속하게 만들고 사이트 페이지에 추가할 수 있습니다. 이 기능을 통해 콘텐츠 작성자는 동적 동작, 유효성 검사, 데이터 통합, 기록 문서 생성 및 비즈니스 프로세스 자동화를 비롯한 적응형 양식 구성 요소의 기능을 사용하여 Sites 페이지 내에서 매끄러운 데이터 캡처 경험을 만들 수 있습니다. 다음과 같은 작업을 수행할 수 있습니다.

   * 양식 구성 요소를 AEM Sites 편집기 또는 경험 조각의 적응형 Forms 컨테이너 구성 요소로 끌어다 놓아 적응형 양식을 만드십시오.
   * AEM Sites 편집기 내의 적응형 Forms 마법사를 사용하여 임의의 Sites 페이지와 독립적인 양식을 만들 수 있으므로 여러 페이지에서 그러한 양식을 자유롭게 재사용할 수 있습니다.
   * 사이트 페이지에 여러 양식을 추가하여 사용자 경험을 간소화하고 유연성을 높일 수 있습니다.

      >[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

* 규칙 편집기의 사용자 지정 오류 처리기를 사용하여 오류 처리 개선: 이제 외부 서비스에서 반환된 오류에 대한 응답으로 사용자 지정 함수(클라이언트 라이브러리 사용)를 호출하고 최종 사용자에게 맞춤 응답을 제공하거나 서비스에서 반환된 오류에 대해 특정 작업을 수행할 수 있습니다. 예를 들어 특정 오류 코드에 대해 백엔드에서 사용자 지정 워크플로우를 호출하거나 서비스가 중단되었음을 고객에게 알릴 수 있습니다.

   이렇게 하면 OOTB 오류 핸들러와 역호환되며 유연성과 제어력이 향상된 표준 기반 오류 응답을 도입하여 전반적인 오류 처리 기능을 향상시킬 수 있습니다.

## Headless 적응형 양식 얼리 어답터 프로그램 {#forms-early-adopter}

Headless 적응형 양식을 사용하여 개발자가 기존의 그래픽 사용자 인터페이스가 아닌 API를 통해 액세스하고 상호 작용할 수 있는 대화형 양식을 만들고, 게시하고, 관리할 수 있습니다. Headless 적응형 양식은 다음에 도움이 됩니다.

* 선택한 프로그래밍 언어로 고품질 다중 채널 양식 작성
* 양식을 데스크탑 및 모바일 앱, 웹 사이트 및 채팅 애플리케이션에 기본적으로 통합
* 양식 애플리케이션과 함께 독점 UI 구성 요소 재사용
* Adobe Experience Manager Forms의 기능 활용

다음으로 이메일을 보낼 수 있습니다. `aem-forms-headless@adobe.com` 얼리어답터 프로그램에 참여하려면 공식 이메일 ID에서 을(를) 전송하십시오.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### 새로운 기능 {#what-is-new-foundation}

* 추가 게시 영역: 사이트 고객은 기본 영역 외에 최대 3개의 게시 영역에 라이선스를 부여할 수 있습니다. 트래픽이 추가 게시 팜으로 라우팅되므로 특정 요청에 대한 지연 시간이 줄어들고 지역 중단에 대한 복원력이 향상됩니다. 라이선싱에 대한 자세한 내용은 Adobe 계정 관리자에게 문의하십시오 [추가 게시 영역](/help/operations/additional-publish-regions.md) 을 참조하십시오.

## 유지 관리 릴리스 정보 {#maintenance}

[ 여기](/help/release-notes/maintenance/latest.md)에서 최신 유지 관리 릴리스 정보를 확인할 수 있습니다.

## Cloud Manager {#cloud-manager}

[여기](/help/implementing/cloud-manager/release-notes/current.md)에서 Cloud Manager 월별 릴리스의 전체 목록을 찾을 수 있습니다.

## 마이그레이션 도구 {#migration-tools}

[여기](/help/journey-migration/release-notes/release-notes-migration-tools-current.md)에서 마이그레이션 도구의 전체 목록을 찾을 수 있습니다.
