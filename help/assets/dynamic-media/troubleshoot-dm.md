---
title: Dynamic Media 문제 해결
description: Dynamic Media 사용 시 문제 해결 팁.
role: Administrator,Business Practitioner
exl-id: 3e8a085f-57eb-4009-a5e8-1080b4835ae2
source-git-commit: e94289bccc09ceed89a2f8b926817507eaa19968
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 2%

---

# Dynamic Media 문제 해결 {#troubleshooting-dynamic-media-scene-mode}

다음 항목에서는 Dynamic Media의 문제 해결에 대해 설명합니다.

## 새 Dynamic Media 구성 {#new-dm-config}

[새 Dynamic Media 구성 문제 해결](/help/assets/dynamic-media/config-dm.md#troubleshoot-dm-config)을 참조하십시오.

## 일반(모든 자산) {#general-all-assets}

다음은 모든 자산에 대한 일반적인 팁과 트릭입니다.

### 자산 동기화 상태 속성 {#asset-synchronization-status-properties}

다음 자산 속성을 CRXDE Lite에서 검토하여 Adobe Experience Manager에서 Dynamic Media으로 성공적으로 자산을 동기화할 수 있습니다.

| **속성** | **예** | **설명** |
|---|---|---|
| `<object_node>/jcr:content/metadata/dam:scene7ID` | **`a|364266`** | 노드가 Dynamic Media에 연결되어 있다는 일반 표시기입니다. |
| `<object_node>/jcr:content/metadata/dam:scene7FileStatus` | **** PublishComplete 또는 오류 텍스트 | Dynamic Media에 자산 업로드 상태. |
| `<object_node>/jcr:content/metadata/dam:scene7File` | **myCompany/myAssetID** | Dynamic Media의 원격 자산에 대한 URL을 생성하려면 채워야 합니다. |
| `<object_node>/jcr:content/dam:lastSyncStatus` | **** 후임자가  **실패했습니다.`<error text>`** | 세트(스핀 세트, 이미지 세트 등), 이미지 사전 설정, 뷰어 사전 설정, 자산에 대한 이미지 맵 업데이트 또는 편집된 이미지의 동기화 상태. |

### 동기화 로깅 {#synchronization-logging}

동기화 오류 및 문제가 `error.log`(Experience Manager 서버 디렉토리 `/crx-quickstart/logs/`)에 기록됩니다. 대부분의 문제의 근본 원인을 파악하는 데 충분한 로깅을 사용할 수 있지만 자세한 정보를 수집하기 위해 Sling Console([https://localhost:4502/system/console/slinglog](https://localhost:4502/system/console/slinglog))을 통해 `com.adobe.cq.dam.ips` 패키지의 DEBUG에 대한 로깅을 늘릴 수 있습니다.

### 버전 제어 {#version-control}

기존 Dynamic Media 자산을 바꿀 때(동일한 이름 및 위치) 자산을 유지하거나 버전을 교체/만들 수 있습니다.

* 두 자산을 모두 유지하면 게시된 자산 URL에 대한 고유한 이름이 있는 자산이 만들어집니다. 예를 들어 `image.jpg`은 원래 자산이고 `image1.jpg`은 새로 업로드된 자산입니다.

* Dynamic Media에서는 버전 만들기가 지원되지 않습니다. 새 버전은 게재의 기존 자산을 대체합니다.

## 이미지 및 세트 {#images-and-sets}

이미지 및 세트에 문제가 있는 경우 다음 문제 해결 지침을 참조하십시오.

<table>
 <tbody>
  <tr>
   <td><strong>문제</strong></td>
   <td><strong>디버그 방법</strong></td>
   <td><strong>솔루션</strong></td>
  </tr>
  <tr>
   <td>자산 세부 사항 보기의 복사 URL/포함 단추에 액세스할 수 없습니다</td>
   <td>
    <ol>
     <li><p>CRX/DE로 이동합니다.</p>
      <ul>
       <li>JCR <code>/etc/dam/presets/viewer/&lt;preset&gt; has lastReplicationAction</code>에 사전 설정이 정의되어 있는지 확인합니다. 이 위치는 Experience Manager 6.x에서 6.4로 업그레이드하고 마이그레이션을 옵트아웃한 경우에 적용됩니다. 그렇지 않으면 위치가 <code>/conf/global/settings/dam/dm/presets/viewer</code>입니다.</li>
       <li>JCR의 자산이 메타데이터 아래에 <code>dam:scene7FileStatus</code><strong> </strong>이 <code>PublishComplete</code>로 표시되는지 확인합니다.</li>
      </ul> </li>
    </ol> </td>
   <td><p>페이지를 새로 고치거나 다른 페이지로 이동한 다음 다시 돌아오십시오(사이드 레일 JSP는 다시 컴파일해야 함)</p> <p>작동하지 않는 경우:</p>
    <ul>
     <li>자산을 게시합니다.</li>
     <li>자산을 다시 업로드하고 게시합니다.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>회전 핫스팟은 슬라이드 간에 전환한 후 이동합니다</td>
   <td><p>모든 슬라이드의 크기가 동일한지 확인합니다.</p> </td>
   <td><p>회전판에 대해 크기가 같은 이미지만 사용합니다.</p> </td>
  </tr>
  <tr>
   <td>Dynamic Media 뷰어에서 이미지가 미리 표시되지 않음</td>
   <td><p>메타데이터 속성(CRXDE Lite)에서 자산에 <code>dam:scene7File</code>이 포함되어 있는지 확인합니다</p> </td>
   <td><p>모든 자산의 처리가 완료되었는지 확인합니다.</p> </td>
  </tr>
  <tr>
   <td>업로드된 자산이 자산 선택기에 표시되지 않습니다</td>
   <td><p>자산에 속성 <code>jcr:content</code> &gt; <strong><code>dam:assetState</code></strong> = <code>processed</code> (CRXDE Lite)이 있는지 확인합니다.</p> </td>
   <td><p>모든 자산의 처리가 완료되었는지 확인합니다.</p> </td>
  </tr>
  <tr>
   <td>카드 보기의 배너에 자산 처리가 시작되지 않은 경우 <strong>새로운</strong>이 표시됩니다</td>
   <td>자산 <code>jcr:content</code> &gt; <code>dam:assetState</code> = <code>unprocessed</code>이 워크플로우에서 선택하지 않은 경우 선택합니다.</td>
   <td>워크플로우가 자산을 선택할 때까지 기다립니다.</td>
  </tr>
  <tr>
   <td>이미지 또는 집합에 뷰어 URL 또는 포함 코드가 표시되지 않습니다</td>
   <td>뷰어 사전 설정이 게시되었는지 확인합니다.</td>
   <td><p><strong>도구</strong> &gt; <strong>자산</strong> &gt; <strong>뷰어 사전 설정</strong>으로 이동하여 뷰어 사전 설정을 게시합니다.</p> </td>
  </tr>
 </tbody>
</table>

## 비디오 {#video}

비디오에 문제가 있는 경우 다음 문제 해결 지침을 참조하십시오.

<table>
 <tbody>
  <tr>
   <td><strong>문제</strong></td>
   <td><strong>디버그 방법</strong></td>
   <td><strong>솔루션</strong></td>
  </tr>
  <tr>
   <td>비디오를 미리 볼 수 없습니다.</td>
   <td>
    <ul>
     <li>폴더에 비디오 프로필이 할당되어 있는지 확인합니다(지원되지 않는 파일 형식인 경우). 지원되지 않는 경우에는 이미지만 표시됩니다.</li>
     <li>비디오 프로필에는 AVS 세트를 생성하려면 둘 이상의 인코딩 사전 설정이 포함되어야 합니다(단일 인코딩은 MP4 파일에 대한 비디오 컨텐츠로 처리됨).지원되지 않는 파일의 경우 처리되지 않은 것으로 처리됨).</li>
     <li>메타데이터에서 <code>dam:scene7File</code> 의 <code>dam:scene7FileAvs</code> 을 확인하여 비디오 처리가 완료되었는지 확인합니다.</li>
    </ul> </td>
   <td>
    <ol>
     <li>폴더에 비디오 프로필을 지정합니다.</li>
     <li>둘 이상의 인코딩 사전 설정을 포함하도록 비디오 프로필을 편집합니다.</li>
     <li>비디오가 처리를 완료할 때까지 기다립니다.</li>
     <li>비디오를 다시 로드하기 전에 Dynamic Media 인코딩 비디오 워크플로우가 실행되고 있지 않은지 확인하십시오.<br/> </li>
     <li>비디오를 다시 업로드합니다.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>비디오가 인코딩되지 않음</td>
   <td>
    <ul>
     <li>Dynamic Media Cloud Service이 구성되어 있는지 확인합니다.</li>
     <li>비디오 프로필이 업로드 폴더와 연결되어 있는지 확인합니다.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Cloud Services 아래의 Dynamic Media 구성이 제대로 설정되었는지 확인합니다.</li>
     <li>폴더에 비디오 프로필이 있는지 확인합니다. 또한 비디오 프로필을 확인합니다.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>비디오 처리에 시간이 너무 오래 걸립니다</td>
   <td><p>비디오 인코딩이 계속 진행 중인지 또는 실패 상태가 되었는지 확인하려면:</p>
    <ul>
     <li>비디오 상태 <code>https://localhost:4502/crx/de/index.jsp#/content/dam/folder/videomp4/jcr%3Acontent</code> 확인 <code>dam:assetState</code></li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td>비디오 표현물이 없습니다.</td>
   <td><p>비디오가 업로드되지만 인코딩된 변환이 없는 경우:</p>
    <ul>
     <li>폴더에 비디오 프로필이 할당되어 있는지 확인합니다.</li>
     <li>메타데이터에서 <code>dam:scene7FileAvs</code> 을 확인하여 비디오 처리가 완료되었는지 확인합니다.</li>
    </ul> </td>
   <td>
    <ol>
     <li>폴더에 비디오 프로필을 지정합니다.</li>
     <li>비디오가 처리를 완료할 때까지 기다립니다.<br /> </li>
    </ol> </td>
  </tr>
 </tbody>
</table>

## 뷰어 {#viewers}

뷰어에 문제가 있는 경우 다음 문제 해결 지침을 참조하십시오.

<table>
 <tbody>
  <tr>
   <td><strong>문제</strong></td>
   <td><strong>디버그 방법</strong></td>
   <td><strong>솔루션</strong></td>
  </tr>
  <tr>
   <td>뷰어 사전 설정이 게시되지 않음</td>
   <td><p>샘플 관리자 진단 페이지로 진행합니다. <code>https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code></p> <p>계산된 값을 관찰합니다. 올바르게 작동하면 다음을 볼 수 있습니다.</p> <p><code>_DMSAMPLE status: 0 unsyced assets - activation not necessary
       _OOTB status: 0 unsyced assets - 0 unactivated assets</code></p> <p><strong>참고</strong>:뷰어 자산을 동기화할 Dynamic Media 클라우드 설정을 구성한 후 약 10분이 걸릴 수 있습니다.</p> <p>활성화되지 않은 자산이 남아 있는 경우 <strong>활성화되지 않은 모든 자산 목록</strong> 단추 중 하나를 클릭하여 세부 사항을 확인합니다.</p> </td>
   <td>
    <ol>
     <li>관리 도구의 뷰어 사전 설정 목록으로 이동합니다. <code>https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code></li>
     <li>모든 뷰어 사전 설정을 선택한 다음 <strong>게시</strong>를 클릭합니다.</li>
     <li>샘플 관리자로 돌아가서 활성화되지 않은 자산 수가 이제 0임을 확인합니다.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>뷰어 사전 설정 아트웍은 자산 세부 정보에서 미리 보기에서 404를 반환하거나 URL/포함 코드 복사</td>
   <td><p>CRXDE Lite에서 다음을 수행합니다.</p>
    <ol>
     <li>Dynamic Media 동기화 폴더 내의 <code>&lt;sync-folder&gt;/_CSS/_OOTB</code> 폴더로 이동합니다(예: <code>/content/dam/_CSS/_OOTB</code>).</li>
     <li>문제가 있는 자산의 메타데이터 노드(예: <code>&lt;sync-folder&gt;/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png/jcr:content/metadata/</code>)를 찾습니다.</li>
     <li><code>dam:scene7*</code> 속성이 있는지 확인합니다. 자산이 동기화되고 게시되면 <code>dam:scene7FileStatus</code> 세트가 <strong>PublishComplete</strong>로 표시됩니다.</li>
     <li>다음 속성 및 문자열 리터럴의 값을 연결하여 Dynamic Media에서 직접 아트웍을 요청합니다
      <ul>
       <li><code>dam:scene7Domain</code></li>
       <li><code>"is/content"</code></li>
       <li><code>dam:scene7Folder</code></li>
       <li><code>&lt;asset-name&gt;</code></li>
       <li>예: <code>https://&lt;server&gt;/is/content/myfolder/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png</code></li>
      </ul> </li>
    </ol> </td>
   <td><p>샘플 자산 또는 뷰어 사전 설정 아트워크가 동기화되거나 게시되지 않은 경우 전체 복사/동기화 프로세스를 다시 시작합니다.</p>
    <ol>
     <li>다음으로 이동 <code>/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code>
     </li>
     <li>다음 작업을 순서대로 선택합니다.
      <ol>
       <li>동기화 폴더를 삭제합니다.</li>
       <li>사전 설정 폴더 삭제(<code>/conf</code> 아래).
       <li>DM 설정 비동기 작업을 트리거합니다.</li>
      </ol> </li>
     <li>Experience Manager 받은 편지함에서 성공적인 동기화 알림을 기다립니다.
     </li>
    </ol> </td>
  </tr>
 </tbody>
</table>
