---
title: AEM의 Assets 보기가 어떤 도움이 됩니까?
description: AEM에서 Assets 보기를 통해 얻을 수 있는 주요 이점에 대해 자세히 알아보십시오. Adobe은 마케팅 및 크리에이티브 전문가에게 권한을 부여하는 전문 지식을 사용하여 게임을 변화시킬 새로운 사용자 경험을 도입합니다.
mini-toc-levels: 3
exl-id: c27134f5-178c-4db1-a8e6-ec45d020f2b5
feature: Asset Management, Publishing, Collaboration, Asset Processing
role: User
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '1012'
ht-degree: 68%

---

# Assets 보기 소개 {#assets-view}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime 및 Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>Edge Delivery Services과 AEM Assets 통합</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>UI 확장성</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>새로 만들기</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Dynamic Media Prime 및 Ultimate 사용</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>모범 사례 검색</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>메타데이터 모범 사례</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>OpenAPI 기능이 포함된 Dynamic Media</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>AEM Assets 개발자 설명서</b></a>
        </td>
    </tr>
</table>

![Assets Essentials 배포](assets/banner-image.jpg)

실시간 콘텐츠 생성 및 게재가 필수적인 오늘날의 급변하는 디지털 중심 환경에서는 다운스트림 마케팅 속도를 위해 설계된 디지털 자산 관리(DAM) 경험이 무엇보다 중요합니다. Adobe은 마케팅 및 크리에이티브 전문가에게 권한을 부여하는 전문 지식을 사용하여 게임을 변화시킬 새로운 사용자 경험을 도입합니다. 이 워크플로 중심 접근 방식은 기업이 동적 디지털 자산을 처리하는 방식을 혁신하여 마케터가 자산을 찾고, 공동 작업하고, 개인화하고, 게재하는 데 효율성을 극대화하도록 합니다. 이처럼 간소화된 워크플로는 콘텐츠 속도를 가속화하고 마케팅 활동을 새로운 차원으로 끌어올립니다.

Assets as a Cloud Service에 사용 가능한 사용자 기반 경험에 대한 자세한 내용은 [Assets as a Cloud Service 소개](/help/assets/overview.md#persona-based-experiences)를 참조하십시오.

## 자산 보기에 어떻게 액세스합니까? {#access-assets-view}

다음과 같은 방법으로 자산 보기에 액세스할 수 있습니다.
![내 작업 영역 개요](assets/assets-view.png)

<!--

* **Toggle in Admin view**

    * Log into [!DNL Experience Manager] using Cloud Manager.
    * Navigate to **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
    * Click the profile icon on the top right corner.
    * Click **[!UICONTROL Switch View]** from the **[!UICONTROL Profile Settings]** section.
    Repeat these steps to switch back to the Admin view.

* **Product Switcher**
    * Log into [!DNL Experience Manager] and click ![Product selector](assets/waffle-icon.svg).
    * Select **[!UICONTROL Experience Manager Assets]** to access the Assets view.
    * Select **[!UICONTROL Experience Manager]** to access the Admin view.

* **Quick Links** 
    * Log into experience.adobe.com.
    * Click **[!UICONTROL Experience Manager Assets]** to access the Assets view.
    * Click **[!UICONTROL Experience Manager Assets]** to access the Assets view.

    -->

## 자산 보기를 사용해야 하는 이유는 무엇입니까?

Assets 보기는 관리 보기에서 사용할 수 없는 다음과 같은 주요 이점을 제공합니다.

* [능률적인 경험을 제공하는 내 작업 영역 대시보드](#my-workspace-for-streamlined-experience)
* [효율성 향상을 위한 검색 중심 접근 방식](#search-first)
* [데이터 기반 의사 결정을 위한 인사이트](#insights-data)
* [공동 작업을 가속화하는 Adobe Photoshop Express 통합](#accelerate-collaboration)
* [조직의 계층 구조를 설정하기 위한 폴더 업로드](#folder-uploads)
* [효율적인 자산 관리를 위해 저장소 콘텐츠 구독](#subscribe-content)
* [관리자에게 더 나은 제어 기능을 제공하기 위한 자산 소프트 삭제](#soft-delete-assets)

### 능률적인 경험을 제공하는 내 작업 영역 대시보드 {#my-workspace-for-streamlined-experience}

여러 조직 역할의 다양한 요구 사항을 이해하는 디지털 자산 관리 솔루션을 소개합니다. 매끄러운 Assets 보기 보기를 통해 사용 편의성과 속도를 우선시하므로 시각적 호소력과 깔끔한 작업 공간에 대한 마케터의 선호도를 충족할 수 있습니다. 사용자 정의 가능한 사용자별 내 작업 영역 대시보드를 통해 마케터는 놀라운 효율성으로 자산을 빠르게 찾고, 미리 보고, 편집하고, 관리하고, 게재할 수 있습니다. 특정 자산을 검색하는 데 소모하는 끝없는 시간에 작별을 고하고, 필요한 모든 것을 간편하게 제공하는 능률적인 경험을 만나 보십시오.

![내 작업 영역 개요](assets/my-workspace-demo.gif)

[![안내서 참조](assets/see-the-guide-sm.png)](my-workspace-assets-view.md)

### 데이터 기반 의사 결정을 위한 인사이트 {#insights-data}

콘텐츠 속도에 보조를 맞추려면 실행 가능한 인사이트가 필수적입니다. Assets 보기는 My Workspace 내에 고급 통찰력을 제공하며 에셋 성능, 대상 사용 및 참여에 대한 중요한 데이터를 제공합니다. 마케터는 데이터 기반 의사 결정을 내리고, 콘텐츠 전략을 최적화하고, 다운스트림 게재를 개선하여 최적의 결과를 얻을 수 있습니다. 의미 있는 인사이트에 액세스할 수 있는 기업은 경쟁에서 앞서 나가고 우수한 결과를 창출할 수 있습니다.

![인사이트 개요](assets/insights-overview.gif)

[![안내서 참조](assets/see-the-guide-sm.png)](manage-reports-assets-view.md#view-live-statistics)

### 공동 작업을 가속화하는 Adobe Photoshop Express 통합 {#accelerate-collaboration}

새로운 환경은 내장된 Adobe Photoshop 기능, 버전 제어 및 주석 도구를 사용한 실시간 편집을 포함하여 강력한 공동 작업 기능 세트를 제공합니다. 이를 통해 디자인, 크리에이티브, 브랜딩 및 마케팅 팀 간에 원활한 공동 작업이 가능하여 병목 현상을 극복하고 마케팅 운영 프로세스를 가속화할 수 있습니다. 마케팅 담당자는 이제 프로젝트 게재를 가속화하고 전반적인 생산성을 높일 수 있는 강력한 도구를 자유롭게 사용할 수 있습니다.

Adobe Photoshop Express와 통합된 자산 보기의 기능을 이해하려면 이 비디오를 시청하십시오.

>[!VIDEO](https://video.tv.adobe.com/v/3420922)

[![안내서 참조](assets/see-the-guide-sm.png)](edit-images-assets-view.md)

Assets as a Cloud Service에 예정된 릴리스에는 [Adobe Express을 통한 Adobe Firefly 통합](https://firefly.adobe.com/?gclid=EAIaIQobChMIlZeKuNfj_wIVeyCtBh3e5g2cEAAYASAAEgL56_D_BwE&amp;sdid=JM4FW6VL&amp;mv=search&amp;mv2=paidsearch&amp;ef_id=EAIaIQobChMIlZeKuNfj_wIVeyCtBh3e5g2cEAAYASAAEgL56_D_BwE:G:s&amp;s_kwcid=AL!3085!3!652077237594!e!!g!!adobe%20firefly!19870733758!148140507838)도 포함됩니다.

### 조직의 계층 구조를 설정하기 위한 폴더 업로드 {#folder-uploads}

로컬 파일 시스템에 있는 폴더를 업로드하는 방식으로 자산 보기를 사용하여 조직의 폴더 구조를 빠르게 설정할 수 있습니다. 논리적 계층 구조를 유지하기 위해 루트 폴더 아래에 폴더를 만든 다음 자산을 해당 폴더에 수동으로 업로드할 필요가 없습니다. 루트 폴더 아래의 모든 폴더와 자산은 자동으로 Experience Manager Assets에 업로드됩니다.

![폴더 업로드](assets/folder-uploads.gif)

[![안내서 참조](assets/see-the-guide-sm.png)](add-delete-assets-view.md)

### 효율성 향상을 위한 검색 중심 접근 방식 {#search-first}

혁신적인 검색 기능으로 조직의 디지털 자산 라이브러리의 잠재력을 활용하십시오. 수많은 파일과 폴더를 수동으로 탐색하는 번거로움에 작별을 고할 수 있습니다. 모든 사용자는 멋진 마케팅 캠페인, 마음을 사로잡는 프레젠테이션 및 매력적인 콘텐츠를 만드는 데 필요한 완벽한 이미지, 비디오 또는 문서를 즉시 찾을 수 있습니다. 검색 첫 번째 엔진을 사용하면 정확한 키워드를 알지 못한 채 에셋 유형, 메타데이터, 스마트 태그 및 콘텐츠 자체도 손쉽게 탐색할 수 있습니다. Adobe의 검색 중심 방식으로 DAM의 미래를 수용하고 디지털 자산 라이브러리의 잠재력을 최대한 활용하십시오.

![검색 중심 방식](assets/search-first.gif)

### 효율적인 자산 관리를 위해 저장소 콘텐츠 구독 {#subscribe-content}

Assets 보기는 저장소에서 사용할 수 있는 에셋, 폴더 또는 컬렉션에서 수행된 작업을 모니터링하는 기능을 제공합니다. 알림을 받을 콘텐츠를 선택하고 구독해야 합니다. 구독한 콘텐츠 삭제, 구독한 콘텐츠 수정 등과 같은 이벤트 유형을 구성할 수도 있습니다. 그러면 해당 이벤트 유형에 대해서만 알림이 전송됩니다.

![알림 수신](assets/notifications.gif)

[![안내서 참조](assets/see-the-guide-sm.png)](manage-notifications-assets-view.md)

### 관리자에게 더 나은 제어 기능을 제공하기 위한 자산 소프트 삭제 {#soft-delete-assets}

자산 보기에서 사용할 수 있는 휴지통 폴더에는 루트 자산 폴더에서 삭제된 자산이 나열됩니다. 휴지통 폴더에서 자산을 선택하여 원래 위치로 복원하거나 영구적으로 삭제할 수 있습니다. 키워드를 지정하거나 표준 또는 사용자 정의 필터를 적용하여 휴지통 폴더 내에서 적절한 자산을 검색할 수도 있습니다.

![소프트 삭제](assets/soft-delete.gif)

[![안내서 참조](assets/see-the-guide-sm.png)](navigate-assets-view.md)

이러한 기능 외에도 자산 보기에서는 관리자 보기에서 사용할 수 없는 다음 기능을 수행할 수 있습니다.

* 로컬 파일 시스템에서 자산 저장소로 이름이 다른 새 버전의 자산을 업로드합니다. 업로드된 자산은 원래 자산과 동일한 이름의 새 버전으로 사용할 수 있습니다.

* 저장소 내에서 사용할 수 있는 에셋 및 폴더의 이름을 변경합니다.

Assets 보기는 워크플로우를 능률화하고, 공동 작업을 촉진하고, 에셋 전달을 가속화하기 위해 맞춤화되었습니다. 콘텐츠 속도를 수용하여 마케터는 디지털 에셋의 잠재력을 최대한 활용하고 이전과는 전혀 다른 창의력을 발휘할 수 있습니다.


다음 링크를 사용하여 Assets 보기를 빠르게 시작할 수 있습니다.

* [내 작업 영역](/help/assets/my-workspace-assets-view.md)
* [Assets 보기 사용 시작하기](/help/assets/get-started-assets-view.md)
