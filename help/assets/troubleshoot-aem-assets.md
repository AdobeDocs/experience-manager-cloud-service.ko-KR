---
title: AEM Assets의 문제 해결
description: 업로드, 메타데이터, 검색, 게재 등과 같은 주요 AEM Assets s=영역에 대한 문서 링크를 사용하여 일반적인 AEM Assets 문제를 해결합니다.
hidefromtoc: true
hide: true
source-git-commit: c8f1c40e4300b26141cc394a9208641769da1f1e
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---


# AEM Assets 문제 해결 {#troubleshoot-aem-assets}

AEM Assets as a Cloud Service은 비즈니스를 위한 클라우드 기반의 PaaS 솔루션을 제공하여 Digital Asset Management 및 Dynamic Media 작업을 수행할 뿐만 아니라 AI/ML과 같은 차세대 스마트 기능도 사용합니다. 시스템 내에서 항상 최신 상태를 유지하고 항상 사용 가능하며 항상 학습하는 모든 것이 가능합니다.

그러나 에셋 업로드, 메타데이터, 검색 또는 게재 및 기타 AEM Assets 키 영역에 영향을 주는 문제가 발생할 수 있습니다. 이 문서에서는 이러한 일반적인 AEM Assets 문제를 진단하고 해결하는 데 도움이 되는 문제 해결 단계를 제공합니다.

<table>
  <tbody>
  <tr>
    <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-27140">AEM의 에셋 다운로드 ZIP 파일에 렌디션이 없음</a> </td>
    <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26616">콘텐츠 조각이 AEM Assets 라이선스에 포함되지 않음</a> </td>
    <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26928">읽기 액세스에도 불구하고 Assets 보기에서 댓글이 제한됩니다</a> </td> 
    </tr>
    <tr>
    <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26715">(Dynamic Media) 스핀 세트가 AEM Dynamic Media의 처리 상태에서 중단됨</a> </td>
    <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26639">AEM의 원본 파일과 일치하지 않는 DAM(디지털 에셋 관리) 표현물</a> </td>
    <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26873">AEMaaCS에서 스마트 자르기 렌디션이 생성되지 않음</a> </td> 
    </tr>
    <tr>
    <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26533">(Dynamic Media) AEM에서 비디오 업로드, 처리 및 렌더링 문제 해결</a> </td>
    <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26922">(Asset Link) InDesign을 사용할 때 Adobe Asset Link가 링크를 액세스할 수 없는 상태로 둡니다.</a> </td>
    <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26677">AEMaaCS에서 Dynamic Media와 DAM 카드 보기 간에 비디오 썸네일이 일치하지 않습니다</a> </td> 
    </tr>
    <tr>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26610">AEM as a Cloud Service의 대용량 MP4 파일에 대한 자산 처리 실패</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26871">(Dynamic Media) Dynamic Media 비디오 플레이어가 낮은 환경에서 작동하지 않음</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26103">(OpenAPI가 있는 Dynamic Media) IMS 사용자 그룹을 기반으로 Open API를 사용하여 Dynamic Media에 대한 제한된 Assets 액세스를 활성화합니다</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-23916">ZIP 압축 형식의 Tiff 파일을 AEM Assets에 업로드할 때 렌디션이 생성되지 않습니다</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26785">AEM은 10만 개의 토큰 후 큰 PDF에서 추출된 텍스트를 자릅니다</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-17628">(Dynamic Media) DM Assets에 대한 Dynamic Media URL 변경</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26655">AEMaaCS에서 관리자가 아닌 사용자에 대한 메타데이터 스키마 가시성 문제 해결</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26637">(Dynamic Media) Dynamic Media에서 TIFF 이미지 표현물에 대한 배경색 변경 문제</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26528">AEMaaCS Asset 회전 문제로 인해 이후 순환이 표시되지 않음</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26367">(Dynamic Media) Adobe Experience Manager 6.5 Dynamic Media에서 스마트 자르기로 손상된 이미지 문제 해결</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26450">Photoshop Firefly API 통합에 대한 단일 파트 자산 업로드 제한 늘리기</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26461">(Dynamic Media) PDF 파일에 대한 AEM 환경 간의 Dynamic Media 에셋 이름 불일치 해결</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26233">특정 이미지에는 Adobe Experience Manager(AEM) as a Cloud Service - 에셋의 썸네일 변환이 표시되지 않습니다</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25294">(Dynamic Media) Dynamic Media 일반 설정 페이지가 열리지 않습니다</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26197">(Dynamic Media) AEM에서 Dynamic Media를 사용하여 비디오 파일의 오디오 문제를 해결합니다</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25925">AEM as a Cloud Service에서 새로 업로드한 자산에 대한 자동 태그 지정</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25889">AEM에서 JWT를 OAuth로 마이그레이션한 후 스마트 태그 기능이 작동하지 않음</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25903">AEM Managed Services의 공유 링크 문제 해결</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25607">(Dynamic Media) AEM Dynamic Media의 에셋 처리 실패</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25885">(Dynamic Media) Adobe Experience Manager(AEM) Dynamic Media의 자산 동기화 실패</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25829">AEM as a Cloud Service에서 비디오 자산에 대한 사용자 지정 썸네일 업데이트</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25828">Adobe Experience Manager(AEM) Assets의 이미지 메타데이터 불일치</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-21865">자산 폴더를 AEM Assets 웹 UI로 드래그 앤 드롭하지 못했습니다</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25525">(Dynamic Media) AEM as a Cloud Service의 자산 처리 문제 해결</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25518">Adobe Experience Manager as a Cloud Service의 큰 PDF에 대한 텍스트 추출 제한 사항</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25562">(Asset Link) InDesign에서 Adobe Experience Manager(AEM) 자산 링크 연결 문제 해결</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25506">(Asset Link) Adobe Asset Link 플러그인 네트워크 오류: 서버에 연결할 수 없습니다</a></td>
</tr>
<tr>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-25471">(Dynamic Media) Dynamic Media 동기화 사용자 권장 사항</a></td>
  <td><a href="https://experienceleague.adobe.com/ko/docs/experience-cloud-kcs/kbarticles/ka-26902">(Dynamic Media) API를 사용하여 Dynamic Media에서 자산 및 메타데이터 내보내기</a></td>
  <td></td>
</tr>

</tbody>
  <table>


