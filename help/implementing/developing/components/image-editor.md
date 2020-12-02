---
title: 이미지 편집기
description: 이미지 편집기는 AEM의 핵심 부분이며 구성 요소에서 활용하여 컨텐츠 작성자의 이미지 조작을 용이하게 할 수 있습니다.
translation-type: tm+mt
source-git-commit: 83c27daae4e8ae2ae6a8f115c9da9527971c6ecb
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 2%

---


# 이미지 편집기 {#image-editor}

이미지 편집기는 AEM의 핵심 부분이며 구성 요소에서 활용하여 컨텐츠 작성자의 이미지 조작을 용이하게 할 수 있습니다.

## 이미지 맵에 대한 상대 단위 {#relative-units-for-image-map}

이미지 편집기는 이미지 맵 영역을 절대 단위와 상대 단위 모두로 유지합니다. 상대 단위는 응답형 이미지 구성 요소의 클라이언트 쪽에서 이미지 맵(이미지 크기 기준)의 크기를 동적으로 조정하기 위해 데이터 속성으로 제공되는 경우 유용합니다.

### imageMap 속성 {#imagemap-property}

이미지 맵 좌표는 이미지 편집기에서 `imageMap` 속성으로 JCR에 유지됩니다. 다음 형식이 있습니다.

이 등록 정보에는 다음과 같은 맵 영역이 저장됩니다.

`[area1][area2][...]`

영역 포맷:

`[SHAPE(COORDINATES)"HREF"|"TARGET"|"ALT"|(RELATIVE_COORDINATES)]`

예:

`[rect(0,0,10,10)"https://www.adobe.com"|"_self"|"alt"|(0,0,0.8,0.8)]`
`[circle(10,10,10)"https://www.adobe.com"|"_self"|"alt"|(0.8,0.8,0.8)]`

## SVG 이미지 지원 {#support-for-svg-images}

SVG(Scalable Vector Graphics)는 이미지 편집기에서 지원됩니다.

* DAM에서 SVG 에셋을 드래그 앤 드롭하고 로컬 파일 시스템에서 SVG 파일 업로드를 업로드할 수 있습니다.

## MIME 유형으로 플러그인 활성화 {#enabling-plugins-by-mime-type}

특정 MIME 유형에 대해서는 서버측 처리에서 지원되지 않기 때문에 작성 작업을 제한해야 합니다. 예를 들어 SVG 이미지 편집은 허용되지 않을 수 있습니다.

이미지 편집기의 플러그인은 개별 플러그인의 구성 노드에서 `supportedMimeTypes` 속성을 설정하여 MIME 유형에 따라 선택적으로 활성화할 수 있습니다.

### 예 {#example}

예를 들어 자르기 기능은 GIF, JPEG, PNG, WEBP 및 TIFF 이미지만 허용됩니다.

그런 다음 `supportedMimeTypes` 속성을 이미지 구성 요소의 `cq:editConfig` 노드에 있는 플러그인의 구성 노드에서 허용되는 MIME 유형의 문자열로 설정해야 합니다.

`/apps/core/wcm/components/image/v2/image/cq:editConfig`

```xml
 jcr:primaryType="cq:EditConfig">
     <cq:dropTargets jcr:primaryType="nt:unstructured">
         <image ...>
            ...
         </image>
     </cq:dropTargets>
     <cq:inplaceEditing
         jcr:primaryType="cq:InplaceEditingConfig"
         active="{Boolean}true"
         editorType="image">
         <config jcr:primaryType="nt:unstructured">
             <plugins jcr:primaryType="nt:unstructured">
                 <crop
                     jcr:primaryType="nt:unstructured"
                     supportedMimeTypes="[image/gif,image/jpeg,image/png,image/webp,image/tiff]"
                     features="*">
                     <aspectRatios jcr:primaryType="nt:unstructured">
                        ...
                     </aspectRatios>
                 </crop>
                 ...
             </plugins>
             <ui jcr:primaryType="nt:unstructured">
                 ...
             </ui>
         </config>
     </cq:inplaceEditing>
 </jcr:root>
```
