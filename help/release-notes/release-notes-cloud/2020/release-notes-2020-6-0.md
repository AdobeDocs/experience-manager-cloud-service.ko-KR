---
title: Adobe Experience Manager as a Cloud Service 2020.6.0용 릴리스 노트
description: Experience Manager 2020.6.0용 릴리스 노트
exl-id: fd6ebe2b-6d98-498c-a45d-b9a9c34e6be7
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '1941'
ht-degree: 97%

---

# AEM as a Cloud Service 2020.6.0 릴리스 노트 {#release-notes}

이 페이지에서는 Experience Manager as a Cloud Service 2020.6.0 일반 릴리스 노트를 간략하게 설명합니다.

## 릴리스 날짜 {#release-date}

[!DNL Experience Manager] as a Cloud Service 2020.6.0의 출시일은 2020년 6월 4일입니다.

## AEM Sites의 새로운 기능 {#aem-sites}

AEM as a Cloud Service 릴리스 2020.6.0에 있는 AEM Sites의 새로운 기능과 업데이트에 대해 알려면 이 섹션을 따르십시오.

### 새로운 기능 {#whats-new-2020.6.0}

[핵심 구성 요소](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)의 릴리스 2.9.0은 이제 다음을 포함하여 AEM Sites의 일부로 사용할 수 있습니다.

* [Adobe 클라이언트 데이터 레이어](https://github.com/adobe/adobe-client-data-layer)와 핵심 구성 요소 간의 통합
* 모든 구성 요소에 대해 구성 가능한 HTML ID 속성
* 새 진행률 표시줄 구성 요소
* 많은 버그 수정

### 버그 수정 {#sites-bug-fixes}

* 레이아웃 컨테이너를 복사하여 페이지에 다시 붙여넣으면 레이아웃 컨테이너 내의 구성 요소가 표시되지 않습니다.

* 레이아웃 구성 요소의 크기 조정 문제가 해결되었습니다.

* 라우팅 각도 전용 페이지 및 AEM/각도 페이지를 관리하는 기능이 추가되었습니다.

### 접근성 {#accessibility}

* 이제 아래쪽 화살표를 사용하여 탐색 모드로 탐색하는 동안 **페이지 만들기** 대화 상자의 Masonry 항목에 대해 내레이션 역할과 상태가 가능합니다.

* 사용자가 기본 컨텐츠로 건너뛸 수 있도록 탐색에 링크를 추가했습니다.

* 화면 판독기를 향상했습니다.

## AEM as a Cloud Service 기본 사항의 새로운 기능 {#foundations}

AEM 프로젝트 빌드 시간은 AEM 프로젝트 pom.xml의 모든 참조를 원격 저장소에 제거하여 개선됩니다 `https://downloads.experiencecloud.adobe.com/content/maven/public`.

해당 위치에서 이전에 호스팅된 AEM as a Cloud Service SDK API Jar은 이제 Maven의 기본 객체 저장소인 Maven Central에 있습니다.

## Cloud Manager의 새로운 기능 {#cloud-manager}

AEM as a Cloud Service 릴리스 2020.6.0에 있는 Cloud Manager의 새로운 기능과 업데이트에 대해 알려면 이 섹션을 따르십시오.

### 새로운 기능 {#what-is-new-cloud-manager}

* Cloud Manager의 *비즈니스 소유자* 역할의 사용자는 이제 랜딩 페이지(프로그램 카드의 빠른 작업 단추)나 프로그램 내에서 샌드박스 프로그램을 삭제할 수 있습니다.

   자세한 내용은 [샌드박스 프로그램 삭제](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html)를 참조하십시오.

* Cloud Manager의 *비즈니스 소유자* 또는 *배포 관리자* 역할의 샌드박스 프로그램 사용자는 이제 클라우드 관리자 UI를 통해 프로덕션 및 스테이지 환경 세트를 삭제할 수 있습니다. 이제 **프로그램 개요** 페이지와 **환경** 페이지의 환경 카드 모두에서 삭제 옵션을 사용할 수 있습니다 . 프로덕션 또는 스테이지에서 삭제 옵션을 선택하면 세트에 있는 다른 옵션도 삭제됩니다.

   자세한 내용은 [샌드박스 프로그램 삭제](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html)를 참조하십시오.

* 랜딩 페이지의 코치 표시를 사용하여 사용자에게 기본 탐색에 대해 알리고 지시합니다.

* **프로그램 개요** 페이지의 코치 표시의 내용을 참조하여 Cloud Manager 내의 기본 탐색에 대해 알리고 지시할 수 있습니다.

* 이제 **LEARN** 페이지를 Cloud Manager에서 사용할 수 있으며 위쪽 탐색을 통해 액세스할 수 있습니다. 이 페이지에는 Cloud Manager에서 할당된 역할과 관련하여 가장 자주 사용되는 워크플로우에 대한 사용자 학습을 돕는 리소스가 포함되어 있습니다.

* 이제 샌드박스 프로그램은 **프로그램 개요** 페이지의 프로그램 이름 옆에 있을 뿐 아니라 랜딩 페이지의 프로그램 카드에 표시될 **샌드박스** 배지로 식별됩니다.

* 이제 SysAdmin 역할의 사용자는 Cloud Manager에 대한 사용자 역할이나 권한을 관리할 수 있는 Admin Console의 위치에 클릭 한 번으로 액세스할 수 있습니다. 이제 **액세스 관리** 단추를 **프로그램 추가** 단추 옆에 있는 랜딩 페이지에서 사용할 수 있습니다.

   자세한 내용은 [SysAdmin 작업](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html#sysadmin-tasks)을 참조하십시오.

* 이제 SysAdmin 역할의 사용자는 Cloud Manager에서 직접 작성자 인스턴스에 한 번의 클릭으로 액세스할 수 있습니다.

   자세한 내용은 [작성자 인스턴스에 대한 액세스 관리](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html#manage-access-aem)를 참조하십시오.

* 이제 빌드 로그에는 생략된 컨텐츠 패키지를 포함하여 검색된 객체 목록이 포함됩니다.

* 빌드 단계에서 이제 생성된 모든 컨텐츠 패키지에 이름, 그룹 및 버전과 같은 모든 필수 속성이 포함되어 있는지 확인합니다.

* 빌드 단계에서 이제 빌드가 하나 이상의 컨텐츠 패키지를 생성했는지 확인합니다.

### 버그 수정 {#bug-fixes-cm}

* **프로그램 만들기** 대화 상자의 아이콘이 잘못 정렬된 경우가 있었습니다.

* AEM 릴리스 식별자가 **프로그램 개요** 페이지에 일관되게 표시되지 않았습니다.

* 프로덕션 파이프라인을 구성할 때 일부 고객은 **예약된 배포** 옵션을 볼 수 없었습니다.

### 알려진 문제 {#known-issues-cm}

* 샌드박스 프로그램 내의 환경은 특정 기간에 활동이 감지되지 않으면 최대 절전 모드로 전환됩니다. 이 상태는 Cloud Manager에서 관찰되지 않습니다. 하지만 개발자 콘솔을 통해 상태를 확인할 수 있습니다. 이 문제는 향후 릴리스에서 해결될 예정입니다.

* Cloud Manager에서 직접 개발자 콘솔로 연결되는 링크에는 샌드박스 프로그램 환경의 최대 절전 모드 해제/최대 절전 모드 해제 옵션이 표시되지 않습니다. 이 문제를 해결하려면 개발자 콘솔에서 `#release-cm-p1234-e5678` 패턴을 URL 끝에 추가합니다. 여기서 *1234*&#x200B;를 프로그램 ID이고 *5678*&#x200B;은 환경 ID입니다. 이 문제는 향후 릴리스에서 해결될 예정입니다.

## 의 새로운 기능[!DNL Adobe Experience Manager Assets] {#aem-assets}

**Adobe Sensei 기반의 향상된 스마트 태그를 위한 사용자 경험 가이드**

고급 스마트 태그를 사용하면 일반 스마트 태그 외에도 고급 태그 모델 기반의 이미지를 인식할 수 있도록 고급 태그 지정 모델을 교육할 수 있습니다.

이번 릴리스에는 고객별 태그의 세트에 대한 스마트 태그 교육을 설정하고, 자산에 대한 교육을 제공하는 가이드 방식의 새로운 사용자 경험이 포함되어 있으며, 이를 인식하여 향후 태그를 지정해야 합니다. 이제 경험이 보다 직관적이 됩니다.
고급 스마트 태그를 트레이닝하여 더욱 직관적인 스마트 태그 트레이닝을 받을 수 있습니다. 자세한 내용은 [자산에 스마트 태그를 추가하는 방법](/help/assets/smart-tags.md).

**3D 컨텐츠 수집, 미리 보기 및 전달 지원**

조직은 이제 AEM Assets 내에 3D 파일을 저장하고 사용할 수 있습니다. 사용자는 OBJ, STL, GLTF, GLB 파일 등 다양한 핵심 3D 파일을 업로드하고, 미리 보고 사용할 수 있습니다. 또한 다양한 URL 또는 뷰어를 사용하여 [!DNL Dynamic Media] 추가와 함께 3D 경험을 구성하고 전달할 수 있습니다. 여기에는 [!DNL Dynamic Media] 3D Experience Viewer, Sites 3D Viewer 구성 요소 및 3D 파일을 [!DNL Dynamic Media] (AR/VR)를 통해 전달하는 기능이 포함됩니다. [Dynamic Media에서 3D 자산 작업](/help/assets/dynamic-media/assets-3d.md)을 참조하십시오.

**Adobe XD를 위한 Adobe Asset Link 지원**

최신 릴리스에서 [!DNL Experience Manager Assets]는 [!DNL Adobe Asset Link] v29.3과 함께 릴리스된 새 [!DNL Adobe XD] 플러그인을 지원합니다. 통합을 통해 디자이너는 [!DNL Experience Manager] 애플리케이션을 종료하지 않고 디자인의 [!DNL Adobe XD]에서 자산에 액세스하고 이를 사용할 수 있습니다. [Adobe XD용 Adobe Asset Link 설명서](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link-for-xd.html)를 참조하십시오.

이번 릴리스를 통해 크리에이티브 사용자와 디자이너는 이제 [!DNL AEM Assets] , [!DNL Adobe Asset Link], [!DNL Adobe XD] 및 [!DNL Photoshop] 등의 다양한 Creative Cloud 데스크탑 앱에서 [!DNL Illustrator]를 사용하여 [!DNL InDesign]에서 관리하는 자산으로 작업할 수 있습니다.

**접근성 개선**

이제 WCAG(Web Content Accessibility Guidelines) v2.1 안내서를 준수하여 [!DNL Adobe Experience Manager Assets]에 더 쉽게 액세스할 수 있습니다. 다음 사용 사례 또는 인터페이스에 대한 접근성이 개선되었습니다.

사용자 인터페이스 요소는 화면 판독기 친화적이고, 키보드를 사용하여 액세스할 수 있으며, 더 나은 대비를 보여줍니다. 다음은 향상된 기능의 세부 목록입니다.

* [!UICONTROL 게시 관리] 페이지의 [!UICONTROL 옵션], [!UICONTROL 범위] 및 [!UICONTROL 워크플로우] 진행률 표시줄은 화면 판독기에서 진행률 표시줄로 읽지 않습니다. 대신 화면 판독기 사용자는 이러한 상태 표시기를 탭 목록으로 인식합니다. (CQ-4273015)

* 자산의 [!UICONTROL 속성] 페이지에서 태그를 추가할 때 사용자는 태그의 트리 구조를 탐색합니다. 화면 판독기 사용자가 트리 구조를 탐색할 때 아무 소리도 들리지 않으므로 트리 구조에 액세스할 수 없습니다. (CQ-4272964)

* 링크 공유 대화 상자의 검색 모드에서 탐색할 때 화면 판독기에서

   * 대화 상자가 로드되는 즉시 테이블 정보에 내레이션이 적용됩니다.
   * 나열된 모든 자동 제안 항목으로 이동할 수 없습니다.
   * [!UICONTROL 이메일 주소/검색 추가] 콤보 상자에 표시된 자동 제안에 내레이션이 적용되지 않습니다. (CQ-4294232)

* 이제 키보드를 사용하여 [!UICONTROL 메타데이터 스키마 편집기] 페이지와 해당 요소에 액세스할 수 있으며, 이러한 페이지는 화면 판독기에 친숙합니다. (CQ-4272953) 사용자는 NVDA 검색 모드에서 키보드를 사용하여 구성 요소를 드래그할 수 있습니다. (CQ-4296326)

* 자산 사용자 인터페이스에서 보기 설정은 키보드로 액세스할 수 없습니다. (CQ-4289038)

* 황색 등급 아이콘의 광도 비율은 3:1보다 작습니다. 이 기능은 시각 장애가 있거나 색상에 대한 인식이 없는 사용자에게 유용하지 않습니다. 별 등급은 자산 또는 카드 보기에서 탭에 표시됩니다.

* 일부 사용자 인터페이스 요소의 색상 및 대비가 업데이트되어 시력이 제한된 사용자 또는 색상을 인식하지 못하는 사용자가 이러한 사용자 인터페이스 요소를 구분할 수 있습니다. 예를 들어 자산 [!UICONTROL 속성] 또는 카드 보기에서 [!UICONTROL 고급] 탭의 [!UICONTROL 등급] 섹션에 있는 별 등급 아이콘 색상이 적절한 대비를 위해 변경되었습니다. (CQ-4295106)

* 이제 화면 판독기에서 콤보 상자의 목록 상자 팝업 메뉴 항목을 옵션 목록으로 읽을 수 있습니다(여러 페이지의 다양한 필드). (CQ-4294017)

* 자산에 워크플로우를 적용하려면 [!UICONTROL 타임라인]에 있는 V자 모양 화살표에 키보드로 액세스할 수 있습니다. (CQ-4289268)

* 사용자는 [!UICONTROL  기호를 사용하여 자산의 ]속성[!UICONTROL  페이지의 ]기본 사항[!UICONTROL  탭에 있는 ]태그`x` 필드에서 선택한 태그를 제거할 수 있습니다. 이제 화면 판독기에서 선택한 태그의 용도와 수를 알려줍니다(CQ-4273033).

* 읽기 전용 양식 필드는 키보드 사용에 중점을 둘 수 있습니다. 예를 들어, 자산의 [!UICONTROL 속성] 페이지에서 [!UICONTROL 기본 사항] 탭의 필드가 비활성화되어 있습니다. (CQ-4273031)

* 키보드를 사용하여 왼쪽 사이드바의 자산을 필터링하는 옵션에 액세스합니다. (CQ-4273018)

* 화면 판독기는 경로 필드 및 자산 [!UICONTROL 속성] 페이지의 [!UICONTROL 기본 사항] 탭에서 선택 항목 대화 상자를 여는 옵션 등의 다양한 콤보 상자 요소의 용도를 알려줍니다. (CQ-4273016)

* 비디오의 볼륨 컨트롤에는 키보드를 사용하여 액세스할 수 있습니다. (CQ-4272696)

* 자산 사용자 인터페이스에 있는 많은 작업 가능 옵션이 키보드를 사용할 때 포커스를 표시하지 않습니다. (CQ-4272694)

* 이제 화면 판독기 사용자는 키보드를 사용하여 목록 보기의 행을 선택할 수 있는 시기를 알 수 있습니다. 이 정보는 포인터를 행 위에 두면 표시됩니다. (CQ-4271824)

* 로그인 페이지의 사용자 이름 및 암호 필드와 같은 일부 양식 필드는 자리 표시자 값을 사용하여 액세스 가능한 레이블을 지정합니다. (CQ-4271716)

* 이제 키보드를 사용하여 링크 및 자산 페이지의 헤더 및 확대/축소 옵션, 폴더 탐색과 같은 옵션 등의 대화형 사용자 인터페이스 요소에 액세스할 수 있습니다. (CQ-4271412)

* 이제 [!DNL Adobe Experience Manager] Assets에서 검색한 모든 페이지의 제목이 고유합니다. (CQ-4271409)

**기타 개선 사항**

이 릴리스에서는 다음과 같은 기타 개선 사항이 제공됩니다.

* 자산 처리 프로필로 자산을 재처리할 수 있으므로 프로세스를 완전히 제어할 수 있습니다(전체 자산 처리 실행, 특정 처리 프로필 적용, 사후 처리 워크플로우 실행 여부 결정).
* 검색 쿼리는 기본 클러스터 인스턴스가 백그라운드에서 다시 시작되었을 때 결과를 빠르게 반환합니다(이러한 경우 초기 검색 실행이 더 오래 지속될 수 있음).
* 자산 인터페이스 및 검색 결과의 목록 보기에서 자산을 볼 때는 &#39;이름&#39;으로 정렬합니다. [자산 검색](/help/assets/search-assets.md#sort)을 참조하십시오.
* 자산 인터페이스 및 검색 결과의 목록 보기에서 자산을 볼 때 &#39;생성됨&#39;(날짜)으로 정렬합니다. [자산 검색](/help/assets/search-assets.md#sort)을 참조하십시오.
* 자산 마이크로서비스를 사용하여 EPS 파일을 이미지로 변환하도록 지원합니다.

### 버그 수정 {#assets-bug-fixes}

위의 새로운 기능 외에도 현재 릴리스는 고객의 피드백을 기반으로 [!DNL Assets]에 대해 다음과 같은 버그 수정을 제공합니다.

* MP3 음악 파일의 경우 DAM 미리 보기의 썸네일에 표시되는 재생 단추가 작동하지 않습니다. (CQ-4294731)
* 카드 보기에서 포인터를 가져가면 카드의 빠른 작업에 (자동) 초점이 맞춰져 화면 스크롤이 됩니다. (GRANITE-26895)
* 많은 검색 결과를 스크롤한 후 너무 많은 이미지를 표시하면 브라우저 충돌이 발생합니다. (GRANITE-26432)
* 자산을 다운로드할 때 이메일 옵션이 선택되어 있고 유효한 이메일 ID가 제공되더라도 다운로드 옵션을 사용할 수 없습니다. (CQ-4296535)
* 스마트 컬렉션으로 저장된 사용자 지정 필터는 자산에 제대로 적용되지 않습니다. (CQ-4294942)
* 여러 검색 및 색인 개선 사항 및 버그 수정을 통해 성능을 향상할 수 있습니다. (CQ-4286373)
* 자산에서 폴더 속성 탭에 액세스할 수 없으며 500 오류를 반환합니다. (CQ-4295701)
