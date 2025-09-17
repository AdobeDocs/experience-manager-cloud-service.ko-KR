---
title: AEM Assets 및 Forms의 문제 해결
description: 업로드, 메타데이터, 검색, 게재, 양식 작성, 제출 및 통합과 같은 주요 영역에 대한 문서 링크를 사용하여 일반적인 AEM Assets 및 Forms 문제를 해결합니다.
hidefromtoc: true
hide: true
source-git-commit: 5074e777c68c51955b9ad8f055e04067163b9596
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 1%

---


# AEM Assets 및 Forms 문제 해결 {#troubleshoot-aem-assets-forms}

AEM as a Cloud Service은 AEM Assets을 통해 디지털 자산 관리를 위한 포괄적인 솔루션을 제공하며 AEM Forms을 통해 강력한 양식 생성 기능을 제공합니다. 두 서비스 모두 클라우드 기반의 PaaS 솔루션과 AI/ML과 같은 차세대 스마트 기능을 제공하며, 항상 최신 상태를 유지하고 항상 사용 가능하며 항상 학습하는 시스템 내에 있습니다.

그러나 복잡한 엔터프라이즈 환경에서는 여러 영역에 걸쳐 다양한 기술적 문제가 발생할 수 있습니다.

이 포괄적인 문제 해결 안내서는 AEM Assets 및 Forms 모두에 대한 체계적인 진단 접근 방식, 분류된 솔루션 및 단계별 해결 경로를 제공합니다. 각 섹션에는 빠른 참조 안내서, 자세한 문제 해결 방법론 및 광범위한 리소스 링크가 포함되어 있어 문제를 효율적으로 해결하고 AEM Cloud Service 환경을 최적화할 수 있습니다.

## AEM Assets 문제 해결 {#aem-assets-troubleshooting}

AEM Assets은 여러 경험에서 디지털 자산을 관리, 구성 및 제공하는 방법을 간소화합니다. 그러나 에셋 업로드, 메타데이터, 통합 또는 전달에 영향을 주는 문제가 발생할 수 있습니다. 이 문서에서는 일반적인 AEM Assets 문제를 진단하고 해결하는 데 도움이 되는 문제 해결 단계를 제공합니다. 여기에서 설명하는 지침에 따라 워크플로우를 효율적으로 복원하고 에셋이 채널 전체에서 액세스 가능하고 정확하며 사용 가능한 상태로 유지되도록 할 수 있습니다.

### 에셋 처리 및 렌디션 {#asset-processing-renditions-issues}

<table>
  <tbody>
  <tr>
    <td><strong>업로드 및 처리</strong></td>
    <td><strong>렌디션</strong></td>
    <td><strong>PDF 및 텍스트 추출</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26610">AEM as a Cloud Service의 대용량 MP4 파일에 대한 자산 처리 실패</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26639">DAM 표현물이 원본 파일과 일치하지 않음</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26785">AEM은 10만 개의 토큰 후 큰 PDF에서 추출된 텍스트를 자릅니다</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-23916">ZIP 압축 업로드가 있는 TIFF 파일은 렌디션을 생성하지 않습니다</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26233">이미지가 AEM as a Cloud Service에서 썸네일 변환을 표시하지 않음</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25518">AEM as a Cloud Service의 큰 PDF에 대한 텍스트 추출 제한 사항</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-21865">자산 폴더를 AEM Assets 웹 UI로 드래그 앤 드롭하지 못했습니다</a></td>
    <td></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26528">자산 회전 문제로 인해 후속 회전이 표시되지 않습니다.</a></td>
  </tr>
  <tr>
  <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26450">Photoshop Firefly API 통합에 대한 단일 파트 자산 업로드 제한 늘리기</a></td>
  <td></td>
  <td></td>
  </tr>
  </tbody>
</table>

### Dynamic Media {#dynamic-media-issues}

<table>
  <tbody>
  <tr>
    <td><strong>비디오</strong></td>
    <td><strong>스핀 세트 및 스마트 자르기</strong></td>
    <td><strong>게재 및 설정</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26533">AEM의 비디오 업로드, 처리 및 렌더링 문제 해결</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26715">스핀 세트가 처리 상태에서 중단됨</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-17628">자산에 대한 Dynamic Media URL 변경</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26677">Dynamic Media와 DAM 카드 보기 간에 비디오 썸네일 불일치</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26873">AEM as a Cloud Service에서 생성되지 않는 스마트 자르기 렌디션</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26367">AEM 6.5에서 스마트 자르기와 관련된 손상된 이미지 문제</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26610">AEM Dynamic Media의 에셋 처리 실패</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26637">TIFF 표현물의 배경색 문제</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25294">Dynamic Media 일반 설정 페이지가 열리지 않음</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26197">Dynamic Media를 사용하여 비디오 파일의 오디오 문제 해결</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25885">Dynamic Media의 자산 동기화 실패</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26461">환경 간 자산 이름 불일치 해결</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26871">낮은 환경에서 Dynamic Media 비디오 플레이어가 작동하지 않음</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25471">Dynamic Media 동기화 사용자 권장 사항</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26902">API를 사용하여 Dynamic Media에서 자산 및 메타데이터 내보내기</a></td>
  </tr>
  </tbody>
</table>

### 메타데이터, 태깅 및 공유 {#metadata-tagging-sharing-issues}

<table>
  <tbody>
  <tr>
    <td><strong>메타데이터</strong></td>
    <td><strong>스마트 태그</strong></td>
    <td><strong>액세스 및 공유</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25828">AEM Assets의 이미지 메타데이터 불일치</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25925">새로 업로드한 자산의 자동 태그 지정</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26928">읽기 액세스에도 불구하고 Assets 보기에서 댓글 달기가 제한됨</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26655">관리자가 아닌 사용자에 대한 메타데이터 스키마 가시성 문제 해결</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25889">JWT에서 OAuth로 마이그레이션 후 스마트 태그가 작동하지 않음</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25903">AEM Managed Services의 공유 링크 문제 해결</a></td>
  </tr>

</tbody>
</table>

### 통합 및 액세스 {#integrations-access}

<table>
  <tbody>
    <tr>
      <td><strong>Asset Link</strong></td>
      <td><strong>라이선스 및 사용자 지정</strong></td>
    </tr>
    <tr>
      <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26922">Adobe Asset Link는 InDesign에서 액세스할 수 없는 링크를 유지합니다.</a></td>
      <td>
        <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26616">콘텐츠 조각이 AEM Assets 라이선스에 포함되지 않음</a><br>
        </td>
    </tr>
    <tr>
      <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25562">InDesign의 AEM Asset Link 연결 문제 해결</a></td>
      <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25525">AEM as a Cloud Service의 자산 처리 문제 해결</a></td>
    </tr>
    <tr>
      <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25506">Adobe Asset Link 플러그인 네트워크 오류: 서버에 연결할 수 없음</a></td>
      <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25829">AEM as a Cloud Service에서 비디오 자산에 대한 사용자 지정 썸네일 업데이트</a>
      </td>
    </tr>
  </tbody>
</table>




## AEM Forms 문제 해결 {#aem-forms-troubleshooting}

AEM Forms as a Cloud Service은 강력한 양식 생성 및 관리 기능을 제공합니다. 그러나 설치, 구성, 양식 작성 또는 제출 프로세스 중에 문제가 발생할 수 있습니다. 이 섹션에서는 일반적인 AEM Forms 문제에 대한 포괄적인 문제 해결 지침을 제공합니다.

### 설치 및 구성 문제

<table>
  <tbody>
  <tr>
    <td><strong>설정 및 구성</strong></td>
    <td><strong>양식 작성 문제</strong></td>
    <td><strong>성능 및 캐싱</strong></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-installation-and-configuration.md">Forms 옵션을 탐색에서 사용할 수 없음</a></td>
    <td><a href="/help/forms/form-creation-failing.md">템플릿 게시 후 양식 작성 실패</a></td>
    <td><a href="/help/forms/troubleshooting-caching-performance.md">적응형 Forms 캐싱 문제</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-installation-and-configuration.md#build-pipeline-fails">파이프라인 빌드 실패</a></td>
    <td><a href="/help/forms/form-creation-failing.md#cause-form-creation-fails">템플릿 게시 시퀀스 문제</a></td>
    <td><a href="/help/forms/troubleshooting-caching-performance.md#images-videos-not-invalidated">Dispatcher 캐시 무효화 문제</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-installation-and-configuration.md#bundles-inactive-state">번들 활성화 문제</a></td>
    <td><a href="/help/forms/known-issues.md">알려진 양식 생성 제한 사항</a></td>
    <td><a href="/help/forms/troubleshooting-caching-performance.md#cdn-caching-stops-working-after-300-seconds">CDN 캐싱 실패</a></td>
  </tr>
  </tbody>
</table>

### 양식 제출 및 통합 문제

<table>
  <tbody>
  <tr>
    <td><strong>Edge Delivery Services</strong></td>
    <td><strong>사용자 지정 제출 액션</strong></td>
    <td><strong>통합 문제</strong></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-403-forbidden-edge-delivery-form-submission.md">403 양식 제출에서 금지된 오류</a></td>
    <td><a href="/help/forms/custom-submit-action-troubleshooting.md">사용자 지정 제출 액션의 502 오류</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27434">DRM-SAML 리디렉션 실패</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-403-forbidden-edge-delivery-form-submission.md#cors-issues">CORS 구성 문제</a></td>
    <td><a href="/help/forms/custom-submit-action-troubleshooting.md#resolution">처리되지 않은 예외 처리</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27075">AEM Sites에서 제출 버튼이 비활성화됨</a></td>
  </tr>
  <tr>
    <td><a href="/help/forms/troubleshooting-403-forbidden-edge-delivery-form-submission.md#referrer-filter-issues">레퍼러 필터 구성</a></td>
    <td><a href="/help/forms/custom-submit-action-for-adaptive-forms-based-on-core-components.md">사용자 지정 작업에 대한 우수 사례</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26532">업그레이드 후 숨겨진 필드 가시성</a></td>
  </tr>
  </tbody>
</table>

### Designer 및 개발 문제

<table>
  <tbody>
  <tr>
    <td><strong>AEM Forms Designer</strong></td>
    <td><strong>개발 환경</strong></td>
    <td><strong>버전 및 호환성</strong></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26558">업그레이드 후 Designer 6.5가 열리지 않음</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27089">로케이터가 JDK 8/11로 시작하지 못했습니다.</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26862">AEM Forms(AEMFD) 패키지 버전 표시 문제</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-21018">PDF Generator JPEG 2000 오류</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-22689">JBoss 로그 경로 구성</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26846">Windows에서 잘못된 버전 번호</a></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27406">PDF 출력에 버튼 누락</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-18084">Configuration Manager 업그레이드 오류</a></td>
    <td><a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-17339">색인 손상 해결 방법</a></td>
  </tr>
  </tbody>
</table>



