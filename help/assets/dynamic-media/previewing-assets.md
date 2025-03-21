---
title: 자산 미리보기
description: 고객이 자신의 웹 브라우저에서 자산을 보는 방법을 볼 수 있도록 Dynamic Media에서 자산을 미리 보는 방법에 대해 알아봅니다.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 3928798d-352a-42a8-a544-7104fc9b3cf1
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '1274'
ht-degree: 3%

---

# 자산 미리보기{#previewing-assets}

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

미리보기 를 사용하여 업로드한 디지털 에셋을 고객이 자신의 웹 브라우저에서 볼 때 표시되는 방식을 확인할 수 있습니다. 자산에 할당된 기본 임베드된 교차 장치 뷰어가 미리보기에 사용됩니다.

뷰어는 다양한 설정 또는 &quot;사전 설정&quot;의 컬렉션입니다. 예를 들어, 사용자가 컴퓨터 화면 및 모바일 장치에서 리치 미디어 에셋을 보는 방법을 결정하는 뷰어 표시 크기, 확대/축소 동작, 색상 구성표, 테두리 및 글꼴입니다.

비디오, 스핀 세트 및 이미지 세트의 전용 미리 보기 기능을 사용하는 것 외에도 사용자가 만든 뷰어 사전 설정을 사용하여 에셋을 미리 볼 수도 있습니다. 또는 이미지 사전 설정을 사용하여 이미지 렌디션을 미리 봅니다.

* [이미지 사전 설정 적용](/help/assets/dynamic-media/image-presets.md)
* [뷰어 사전 설정 적용](/help/assets/dynamic-media/viewer-presets.md)

>[!NOTE]
>
>Adobe Experience Manager의 웹 페이지(사이트)를 사용하는 경우 **[!UICONTROL 편집]** 모드에서 자산을 미리 볼 수 없습니다. 대신 페이지의 오른쪽 상단에 있는 **[!UICONTROL 미리 보기]**&#x200B;를 선택하여 미리 보기 모드로 이동합니다.

사용자 인터페이스에서 뷰어 사전 설정을 활성화하거나 비활성화하려면 [뷰어 사전 설정 관리](/help/assets/dynamic-media/managing-viewer-presets.md)를 참조하십시오.

**에셋을 미리 보려면:**

1. **[!UICONTROL Experience Manager]**&#x200B;의 **[!UICONTROL 탐색]** 페이지에서 **[!UICONTROL Assets]**&#x200B;을 선택한 다음 **[!UICONTROL 파일]**&#x200B;을 선택하여 에셋에 액세스합니다.
1. 페이지의 오른쪽 상단 모서리 근처에 있는 **[!UICONTROL 보기]** 드롭다운 목록에서 **[!UICONTROL 목록 보기]**&#x200B;를 선택합니다.
1. (선택 사항) **[!UICONTROL Type]** 열을 사용하여 미리 보려는 유형별로 자산을 정렬합니다.
1. **[!UICONTROL 제목]** 열에서 미리 보려는 자산의 제목 이름(썸네일 이미지가 아님)을 선택합니다.
1. 선택한 에셋 유형에 따라 다음 중 하나를 수행합니다.

   <table>
    <tbody>
      <tr>
      <td><strong>선택한 자산 유형</strong><br /> </td>
      <td><strong>특정 렌디션에서 에셋을 미리 볼 수 있습니까?</strong></td>
      <td><strong>특정 뷰어에서 에셋을 미리 볼 수 있습니까?</strong></td>
      </tr>
      <tr>
      <td><p>3D</p> </td>
      <td>아니요</td>
      <td>예</td>
      <td><p><strong>차원 뷰어에서 3D 자산 미리 보기</strong></p>
      <ul>
      <li>페이지의 왼쪽 상단 모서리 근처에서 드롭다운 목록이 나타나도록 아이콘을 선택합니다. 목록에서 <strong>뷰어</strong>를 선택한 다음 차원 뷰어를 선택합니다.</li>
      <li>이미지를 원래 확대/축소 맵으로 되돌리려면 <strong>재설정</strong>을 선택합니다.</li>
      <li>디스플레이 장치에서 뷰어를 최대화하려면 <strong>전체 화면</strong>을(를) 선택하십시오.</li>
      </ul>
      <p><strong>3D 장면 탐색</strong></p>
      <ul>
      <li><p><strong>3D 카메라 돌리기</strong> - 3D 장면 및 개체 주변의 보기를 궤도 회전합니다.</p> 마우스: 마우스 왼쪽 단추 + 드래그.</p> Touch-screen: 키를 누른 채 끌기</p></li>
      <li><p><strong>카메라 패닝</strong> - 보기를 왼쪽, 오른쪽, 위쪽 및 아래쪽으로 패닝합니다.</p> 마우스: 마우스 오른쪽 단추 클릭 + 드래그.</p> Touch-screen: 두 손가락으로 누른 상태에서 드래그하십시오.</p></li>
      <li><p><strong>카메라 확대/축소</strong> - 3D 장면의 영역 안과 밖으로 이동하려면 카메라를 확대하십시오.</p> 마우스: 스크롤 휠입니다.</p> 터치 스크린: 손가락 핀치.</p></li>
      <li><p><strong>카메라를 가운데로 다시 맞춤</strong> - 3D 장면 및 개체 주위로 보기를 궤도 회전합니다.</p> 마우스: 두 번 클릭합니다.</p> Touch-screen: 두 번 선택합니다.</li></ul></td>
      </tr>
      <tr>
      <td><p>이미지</p> </td>
      <td>예</td>
      <td>예</td>
      <td><p><strong>특정 렌디션의 에셋 미리보기</strong></p>
        <ul>
        <li>페이지의 왼쪽 상단 모서리 근처에서 드롭다운 목록이 나타나도록 아이콘을 선택합니다. 목록에서 <strong>렌디션</strong>을 선택한 다음 미리 보려는 특정 렌디션을 선택합니다.</li>
        </ul> <p><strong>특정 뷰어에서 에셋 미리보기</strong></p>
        <ul>
        <li>페이지의 왼쪽 상단 모서리 근처에서 드롭다운 목록이 나타나도록 아이콘을 선택합니다. 목록에서 <strong>뷰어</strong>를 선택한 다음 에셋에 적용할 뷰어를 선택하십시오.</li>
        </ul><p><strong>+</strong> 및 <strong>-</strong>아이콘을 사용하여 선택한 이미지의 확대/축소를 각각 늘리거나 줄이십시오. 이미지를 원래 확대/축소로 되돌리려면 <strong>재설정</strong>을 선택합니다.<br>터치 스크린을 사용하는 경우 단계별로 확대할 이미지를 두 번 선택하십시오. 최대 확대/축소에 도달하면 이미지를 다시 두 번 선택하여 확대/축소 상태를 재설정합니다. 이미지를 드래그하여 패닝합니다.</p> </td>
      </tr>
      <tr>
      <td>멀티미디어</td>
      <td>예</td>
      <td>예</td>
      <td><p><strong>특정 렌디션의 에셋 미리보기</strong></p>
        <ul>
        <li>페이지의 왼쪽 상단 모서리 근처에서 드롭다운 목록이 나타나도록 아이콘을 선택합니다. 목록에서 <strong>렌디션</strong>을 선택한 다음 미리 보려는 특정 렌디션을 선택합니다.</li>
        </ul><p>미리 볼 더 높은 해상도의 비디오 렌디션을 선택하면 비디오가 잘려 보일 수 있습니다. 그 이유는 렌디션 미리 보기에서는 미리 보기에 사용되는 임베드된 뷰어의 모든 컨텍스트에서 고객이 볼 수 있는 정확한 해상도를 보여주기 때문입니다.</p><p>에셋 수준에서 응용 비디오 세트를 미리 볼 때 렌디션은 하나의 재생 경험으로 그룹화됩니다. 즉, 응용 비디오 크기가 보기에 알맞게 조정되고 시청 장치 및 연결 속도의 맥락에서 최상의 해상도를 사용하여 재생됩니다.<br /></p><p><strong>특정 뷰어에서 에셋 미리보기</strong></p>
        <ul>
        <li>페이지의 왼쪽 상단 모서리 근처에서 드롭다운 목록이 나타나도록 아이콘을 선택합니다. 목록에서 <strong>뷰어</strong>를 선택한 다음 에셋에 적용할 뷰어를 선택하십시오.</li>
        </ul> </td>
      </tr>
      <tr>
      <td>이미지 집합</td>
      <td>아니요</td>
      <td>예</td>
      <td><p><strong>특정 뷰어에서 에셋 미리보기</strong></p>
        <ul>
        <li>페이지의 왼쪽 상단 모서리 근처에서 드롭다운 목록이 나타나도록 아이콘을 선택합니다. 목록에서 <strong>뷰어</strong>를 선택한 다음 에셋에 적용할 뷰어를 선택하십시오.</li>
        </ul> <p><strong>+</strong> 및 <strong>- </strong> 아이콘을 사용하여 선택한 이미지의 확대/축소를 각각 늘리거나 줄이십시오. 이미지를 원래 확대/축소로 되돌리려면 <strong>재설정</strong>을 선택합니다.<br /> 터치 스크린을 사용하는 경우 단계적으로 확대할 이미지를 두 번 선택하십시오. 최대 확대/축소에 도달하면 이미지를 다시 두 번 선택하여 확대/축소 상태를 재설정합니다. 이미지를 드래그하여 패닝합니다.</p></td>
      </tr>
      <tr>
      <td>회전 집합</td>
      <td>아니요</td>
      <td>예</td>
      <td><p><strong>특정 뷰어에서 에셋 미리보기</strong></p>
        <ul>
        <li>페이지의 왼쪽 상단 모서리 근처에서 드롭다운 목록이 나타나도록 아이콘을 선택합니다. 목록에서 <strong>뷰어</strong>를 선택한 다음 에셋에 적용할 뷰어를 선택하십시오.</li>
        </ul><p><strong>+</strong> 및 <strong>- </strong> 아이콘을 사용하여 선택한 이미지의 확대/축소를 각각 늘리거나 줄이십시오. 이미지를 원래 확대/축소로 되돌리려면 <strong>재설정</strong>을 선택합니다.<br /> 터치 스크린을 사용하는 경우 단계적으로 확대할 이미지를 두 번 선택하십시오. 최대 확대/축소에 도달하면 이미지를 다시 두 번 선택하여 확대/축소 상태를 재설정합니다. 이미지를 드래그하여 패닝합니다.</p> </td>
      </tr>
      <tr>
      <td>혼합 미디어 집합</td>
      <td>아니요</td>
      <td>예</td>
      <td><p><strong>특정 뷰어에서 에셋 미리보기</strong></p>
        <ul>
        <li>페이지의 왼쪽 상단 모서리 근처에서 드롭다운 목록이 나타나도록 아이콘을 선택합니다. 목록에서 <strong>뷰어</strong>를 선택한 다음 에셋에 적용할 뷰어를 선택하십시오.</li>
        </ul> <p><strong>+</strong> 및 <strong>- </strong> 아이콘을 사용하여 선택한 이미지의 확대/축소를 각각 늘리거나 줄이십시오. 이미지를 원래 확대/축소로 되돌리려면 <strong>재설정</strong>을 선택합니다.<br /> 터치 스크린을 사용하는 경우 단계적으로 확대할 이미지를 두 번 선택하십시오. 최대 확대/축소에 도달하면 이미지를 다시 두 번 선택하여 확대/축소 상태를 재설정합니다. 이미지를 드래그하여 패닝합니다.</p> </td>
      </tr>
      <tr>
      <td>회전 메뉴 세트</td>
      <td>아니요</td>
      <td>예</td>
      <td><strong>특정 뷰어에서 자산을 미리 보려면</strong>
        <ul>
        <li>페이지의 왼쪽 상단 모서리 근처에서 드롭다운 목록이 나타나도록 아이콘을 선택합니다. 에셋에 적용할 뷰어를 선택합니다.</li>
        </ul> </td>
      </tr>
      <tr>
      <td>360 비디오<br /> </td>
      <td>예</td>
      <td>예</td>
      <td><p><strong>특정 렌디션의 에셋 미리보기</strong></p>
        <ul>
        <li>페이지의 왼쪽 상단 모서리 근처에서 드롭다운 목록이 나타나도록 아이콘을 선택합니다. <strong>렌디션</strong>을 선택한 다음 미리 보려는 렌디션을 선택합니다.</li>
        </ul> <p><strong>특정 뷰어에서 에셋 미리보기</strong></p>
        <ul>
        <li>페이지의 왼쪽 상단 모서리 근처에서 드롭다운 목록이 나타나도록 아이콘을 선택합니다. <strong>뷰어</strong>를 선택한 다음 에셋에 적용할 뷰어를 선택하십시오.</li>
        </ul> <p><strong>+</strong> 및 <strong>- </strong> 아이콘을 사용하여 선택한 이미지의 확대/축소를 각각 늘리거나 줄이십시오. 이미지를 원래 확대/축소로 되돌리려면 <strong>재설정</strong>을 선택합니다.<br /> 터치 스크린을 사용하는 경우 단계적으로 확대할 이미지를 두 번 선택하십시오. 최대 확대/축소에 도달하면 이미지를 다시 두 번 선택하여 확대/축소 상태를 재설정합니다. 이미지를 드래그하여 패닝합니다.</p> </td>
      </tr>
    </tbody>
    </table>
