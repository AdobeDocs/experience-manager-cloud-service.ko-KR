---
title: 에셋 처리를 위한 에셋 마이크로서비스 구성 및 사용
description: 클라우드 기반의 에셋 마이크로 서비스를 구성 및 사용하여 에셋을 규모에 맞게 처리하는 방법을 살펴볼 수 있습니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9c5dd93be316417014fc665cc813a0d83c3fac6f
workflow-type: tm+mt
source-wordcount: '1861'
ht-degree: 1%

---


# 자산 마이크로서비스 사용 시작 {#get-started-using-asset-microservices}

<!--
* Current capabilities of asset microservices offered. If workers have names then list the names and give a one-liner description. (The feature-set is limited for now and continues to grow. So will this article continue to be updated.)
* How to access the microservices. UI. API. Is extending possible right now?
* Detailed list of what file formats and what processing is supported by which workflows/workers process.
* How/where can admins check what's already configured and provisioned.
* How to create new config or request for new provisioning/purchase.

* [DO NOT COVER?] Exceptions or limitations or link back to lack of parity with AEM 6.5.
-->

에셋 마이크로서비스는 클라우드 서비스를 사용하여 자산을 확장 가능하고 탄력적으로 처리할 수 있습니다. Adobe는 다양한 자산 유형 및 처리 옵션을 적절하게 처리하기 위해 서비스를 관리합니다.

자산 처리는 기본 설정을 제공하고 관리자가 보다 구체적인 자산 처리 구성을 추가할 수 있도록 **[!UICONTROL 해주는 처리]**&#x200B;프로필의 구성에 따라 다릅니다. 관리자는 사용자 정의 옵션을 포함하여 사후 처리 워크플로우의 구성을 만들고 유지 관리할 수 있습니다. 사용자 정의 워크플로우를 통해 확장 및 사용자 정의

에셋 마이크로서비스를 사용하면 이전 버전의 Experience Manager에서 가능한 것보다 더 많은 포맷을 즉시 포함하는 [다양한 파일 유형을](/help/assets/file-format-support.md) 처리할 수 있습니다. 예를 들어 이전에는 ImageMagick과 같은 타사 솔루션이 필요했던 PSD 및 PSB 포맷의 축소판 추출을 수행할 수 있습니다.

<!-- Proposed DRAFT diagram for asset microservices flow - see section "asset-microservices-flow.png (asset-microservices-configure-and-use.md)" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![자산](assets/asset-microservices-flow.png "처리에 대한 고급 보기자산 처리에 대한 고급 보기")

>[!NOTE]
>
>여기에 설명된 자산 처리는 이전 버전의 Experience Manager에 있는 `DAM Update Asset` 워크플로우 모델을 대체합니다. 대부분의 표준 변환 생성 및 메타데이터 관련 단계는 에셋 마이크로 서비스 처리로 대체되며, 나머지 단계는 처리 후 워크플로우 구성으로 대체할 수 있습니다.

## 자산 처리 시작 {#get-started}

자산 마이크로서비스를 사용한 자산 처리는 기본 구성으로 미리 구성되므로 시스템에 필요한 기본 변환을 사용할 수 있습니다. 또한 메타데이터 추출 및 텍스트 추출 작업을 사용할 수 있습니다. 사용자는 에셋을 즉시 업로드하거나 업데이트할 수 있으며 기본 처리는 기본적으로 사용할 수 있습니다.

특정 변환 생성 또는 자산 처리 요구 사항에 대해 AEM 관리자가 추가 [!UICONTROL 처리 프로필을 만들 수 있습니다]. 사용자는 특정 폴더에 하나 이상의 사용 가능한 프로필을 할당하여 추가 처리를 수행할 수 있습니다. 예를 들어 웹, 모바일 및 태블릿별 변환을 생성합니다. 다음 비디오에서는 처리 프로필을 만들고 적용하는 방법 [!UICONTROL 과] 만들어진 표현물에 액세스하는 방법을 보여 줍니다.

>[!VIDEO](https://video.tv.adobe.com/v/29832?quality=9)

기존 프로필을 변경하려면 자산 마이크로서비스에 대한 [구성을 참조하십시오](#configure-asset-microservices).
사용자 지정 요구 사항에 맞는 사용자 지정 처리 프로필을 만들려면 다른 시스템과 통합하라고 [하십시오](#post-processing-workflows).

## 에셋 마이크로서비스 구성 {#configure-asset-microservices}

자산 마이크로서비스를 구성하려면 관리자가 도구 > 자산 > 처리 프로필에서 구성 사용자 인터페이스를 사용할 **[!UICONTROL 수 있습니다]**.

### 기본 구성 {#default-config}

기본 구성으로 표준 처리 프로필만 구성됩니다. 표준 처리 프로필은 사용자 인터페이스에 표시되지 않으며 수정할 수 없습니다. 업로드된 자산을 처리하기 위해 항상 실행합니다. 표준 처리 프로필은 Experience Manager에 필요한 모든 기본 처리가 모든 자산에 대해 완료되도록 합니다.

<!-- ![processing-profiles-standard](assets/processing-profiles-standard.png) -->

표준 처리 프로필은 다음 처리 구성을 제공합니다.

* 에셋 사용자 인터페이스에 사용되는 표준 축소판(48, 140 및 319px)
* 대규모 미리 보기(웹 변환 - 1280px)
* 메타데이터 추출
* 텍스트 추출

### 지원되는 파일 형식 {#supported-file-formats}

에셋 마이크로서비스는 변환을 생성하거나 메타데이터를 추출하는 기능 측면에서 다양한 파일 형식을 지원합니다. 전체 목록은 [지원되는](file-format-support.md) 파일 형식을 참조하십시오.

### 추가 처리 프로필 추가 {#processing-profiles}

만들기 작업을 사용하여 추가 처리 프로필을 추가할 **[!UICONTROL 수]** 있습니다.

각 처리 프로필 구성에는 변환 목록이 포함됩니다. 각 변환에 대해 다음을 지정할 수 있습니다.

* 변환 이름.
* 지원되는 변환 형식(예: JPEG, PNG 또는 GIF).
* 변환 너비 및 높이(픽셀 단위) 지정하지 않으면 원본 이미지의 전체 픽셀 크기가 사용됩니다.
* JPEG의 변환 품질을 백분율로 나타낸 것입니다.
* 프로필의 적용 가능성을 정의하는 MIME 유형이 포함되거나 제외됩니다.

![processing-profiles-adding](assets/processing-profiles-adding.png)

새 처리 프로필을 만들고 저장하면 구성된 처리 프로필 목록에 추가됩니다. 이러한 처리 프로필을 폴더 계층 구조의 폴더에 적용하여 자산 업로드 및 자산 처리를 효과적으로 수행할 수 있습니다.

<!-- Removed per cqdoc-15624 request by engineering.
 ![processing-profiles-list](assets/processing-profiles-list.png) -->

#### 변환 너비 및 높이 {#rendition-width-height}

변환 폭 및 높이 사양은 생성된 출력 이미지의 최대 크기를 제공합니다. 에셋 마이크로서비스는 폭과 높이가 각각 지정된 폭과 높이보다 크지 않은 가장 큰 변환을 생성하려고 시도합니다. 종횡비는 그대로 유지되며 원본과 동일합니다.

비어 있는 값은 자산 처리가 원본 픽셀 크기를 가정함을 의미합니다.

#### MIME 형식 포함 규칙 {#mime-type-inclusion-rules}

특정 MIME 유형의 자산이 처리되면 MIME 유형이 먼저 변환 사양에 대해 제외된 MIME 유형 값에 대해 검사됩니다. 해당 목록과 일치하는 경우 자산(차단 목록)에 대해 특정 변환이 생성되지 않습니다.

그렇지 않으면 MIME 유형이 포함된 MIME 유형에 대해 확인되며, MIME 유형이 목록과 일치하면 변환이 생성됩니다(허용 목록).

#### 특수 FPO 변환 {#special-fpo-rendition}

AEM의 큰 자산을 Adobe InDesign 문서로 가져올 때 크리에이티브 전문가는 자산을 [배치한 후 상당한 시간을 기다려야 합니다](https://helpx.adobe.com/indesign/using/placing-graphics.html). 반면 사용자는 InDesign을 사용할 수 없습니다. 크리에이티브 흐름을 가로막으며 사용자 경험에 부정적인 영향을 줍니다. Adobe는 InDesign 문서에서 작은 크기의 변환을 임시로 배치함으로써 나중에 전체 해상도 에셋으로 대체될 수 있습니다. Experience Manager은 배치 전용(FPO)에 사용되는 변환을 제공합니다. 이러한 FPO 변환은 파일 크기가 작지만 종횡비가 동일합니다.

처리 프로필에는 FPO(배치에만 해당) 변환이 포함될 수 있습니다. 처리 프로필에 맞게 설정해야 하는지 확인하려면 Adobe Asset Link [설명서를](https://helpx.adobe.com/kr/enterprise/using/manage-assets-using-adobe-asset-link.html) 참조하십시오. 자세한 내용은 [Adobe Asset Link 전체 설명서를 참조하십시오](https://helpx.adobe.com/kr/enterprise/using/adobe-asset-link.html).

## 에셋 마이크로서비스를 사용하여 에셋 처리 {#use-asset-microservices}

추가 사용자 정의 처리 프로필을 만들어 Experience Manager의 특정 폴더에 적용하여 이러한 폴더에 업로드되거나 업데이트된 자산에 대해 처리합니다. 기본 내장 표준 처리 프로필은 항상 실행되지만 사용자 인터페이스에 표시되지 않습니다. 사용자 지정 프로필을 추가하는 경우 두 프로필 모두 업로드된 자산을 처리하는 데 사용됩니다.

다음 방법 중 하나를 사용하여 폴더에 처리 프로필을 적용합니다.

* 관리자는 [ **[!UICONTROL 도구] > [자산] > [처리 프로필]**]에서 처리 프로필 정의를 선택하고 [폴더에 **[!UICONTROL 프로필 적용]]** 작업을 사용할 수 있습니다. 특정 폴더로 이동하여 선택한 다음 프로필의 적용을 확인할 수 있는 컨텐츠 브라우저가 열립니다.
* 사용자는 자산 사용자 인터페이스에서 폴더를 선택하고, **[!UICONTROL 속성]** 작업을 사용하여 폴더 속성 화면을 열고, **[!UICONTROL 처리 프로필]** 탭을 클릭하고, 팝업 목록에서 해당 폴더에 대해 올바른 처리 프로필을 선택할 수 있습니다. 변경 내용을 저장하려면 저장 및 **[!UICONTROL 닫기를 클릭합니다]**.

>[!NOTE]
>
>하나의 처리 프로필만 특정 폴더에 적용할 수 있습니다. 변환을 더 생성하려면 기존 처리 프로필에 변환 정의를 더 추가하십시오.

처리 프로필이 폴더에 적용되면, 이 폴더에 업로드되거나 업데이트되는 모든 새 자산 또는 하위 폴더의 모든 새 자산이 구성된 추가 처리 프로필을 사용하여 처리됩니다. 이 프로세스는 표준 기본 프로필 외에 추가로 사용됩니다. 폴더에 여러 개의 프로필을 적용하는 경우 업로드되거나 업데이트된 에셋은 이러한 각 프로필을 사용하여 처리됩니다.

>[!NOTE]
>
>폴더에 적용된 처리 프로필은 전체 트리에 대해 작동하지만 하위 폴더에 다른 프로필이 적용된 경우 오버로드할 수 있습니다. 에셋이 폴더에 업로드되면 Experience Manager은 포함된 폴더의 속성에 처리 프로필이 있는지 확인합니다. 적용되지 않으면 계층의 상위 폴더에서 적용할 처리 프로필이 선택됩니다.

사용자는 처리가 완료된 새로 업로드된 자산을 열고, 자산 미리 보기를 열고, 왼쪽 레일의 **[!UICONTROL 표현물]** 보기를 클릭하여 처리가 실제로 이루어졌는지 확인할 수 있습니다. 특정 자산의 유형이 MIME 유형 포함 규칙과 일치하는 처리 프로필의 특정 변환을 확인하고 액세스할 수 있어야 합니다.

![추가 표현물](assets/renditions-additional-renditions.png)

*그림: 상위 폴더에 적용된 처리 프로필로 생성된 두 개의 추가 표현물의 예.*

## 사후 처리 워크플로우 {#post-processing-workflows}

처리 프로필을 사용하여 얻을 수 없는 자산의 추가 처리가 필요한 경우 추가 사후 처리 워크플로우를 구성에 추가할 수 있습니다. 이를 통해 자산 마이크로 서비스를 사용하여 구성 가능한 처리 위에 완전히 사용자 정의된 처리를 추가할 수 있습니다.

사후 처리 워크플로우는 구성된 경우 마이크로서비스 처리가 완료된 후 AEM에서 자동으로 실행됩니다. 워크플로우 런터을 수동으로 추가하여 트리거할 필요가 없습니다. 이러한 예는 다음과 같습니다.

* 자산을 처리하는 사용자 정의 워크플로우 단계
* 제품 또는 프로세스 정보 등 외부 시스템의 자산에 메타데이터 또는 속성을 추가하는 통합
* 외부 서비스에서 수행한 추가 처리.

Experience Manager에 사후 처리 워크플로우 구성 추가는 다음 단계로 구성됩니다.

* 하나 이상의 워크플로우 모델을 만들 수 있습니다. 이 문서에는 *사후 처리 워크플로우 모델로*&#x200B;언급되어 있지만 일반 Experience Manager 워크플로우 모델입니다.
* 이러한 모델에 특정 워크플로우 단계를 추가합니다. 이 단계는 워크플로우 모델 구성에 따라 자산에 대해 실행됩니다.
* DAM [!UICONTROL 자산 업데이트 워크플로우 완료 프로세스] 추가 단계가 마지막에 표시됩니다. 이 단계를 추가하면 Experience Manager이 처리가 끝나는 시점을 알 수 있고 자산이 처리된 것으로 표시할 수 있으며, 즉 *새* 값이 자산에 표시됩니다.
* 경로(폴더 위치) 또는 정규 표현식을 통해 사후 처리 워크플로우 모델의 실행을 구성할 수 있는 사용자 지정 워크플로우 러너 서비스에 대한 구성을 만듭니다.

### 사후 처리 워크플로우 모델 만들기 {#create-post-processing-workflow-models}

사후 처리 워크플로우 모델은 일반적인 AEM 워크플로우 모델입니다. 다른 저장소 위치 또는 자산 유형에 대해 다른 처리가 필요한 경우 다른 모델을 생성합니다.

필요에 따라 처리 단계를 추가해야 합니다. 지원되는 모든 단계와 사용자 요구에 맞게 구현된 워크플로우 단계를 사용할 수 있습니다.

각 사후 처리 워크플로우의 마지막 단계가 올바른지 확인하십시오 `DAM Update Asset Workflow Completed Process`. 마지막 단계는 자산 처리가 완료되는 시기를 Experience Manager이 알 수 있도록 도와줍니다.

### 사후 처리 워크플로우 실행 구성 {#configure-post-processing-workflow-execution}

자산 마이크로서비스 처리가 완료된 후 시스템에서 업로드되거나 업데이트되는 자산에 대해 처리 후 워크플로우 모델을 실행하려면 사용자 지정 워크플로우 러너 서비스를 구성해야 합니다.

사용자 지정 Workflow Runner 서비스(`com.adobe.cq.dam.processor.nui.impl.workflow.CustomDamWorkflowRunnerImpl`)는 OSGi 서비스이며 구성에 대한 두 가지 옵션을 제공합니다.

* 경로별 사후 처리 워크플로우(`postProcWorkflowsByPath`): 다양한 저장소 경로에 따라 여러 워크플로우 모델을 표시할 수 있습니다. 패스와 모델은 콜론으로 구분해야 합니다. 단순 저장소 경로가 지원되며 경로의 워크플로우 모델에 매핑되어야 `/var` 합니다. 예: `/content/dam/my-brand:/var/workflow/models/my-workflow`.
* 식별 사후 처리 워크플로우(`postProcWorkflowsByExpression`): 서로 다른 정규 표현식을 기반으로 여러 워크플로우 모델을 나열할 수 있습니다. 표현식과 모델은 콜론으로 구분해야 합니다. 정규 표현식은 표현물이나 파일 중 하나를 지정하지 않고 자산 노드를 직접 가리켜야 합니다. 예: `/content/dam(/.*/)(marketing/seasonal)(/.*):/var/workflow/models/my-workflow`.

>[!NOTE]
>
>사용자 지정 워크플로우 러너의 구성은 OSGi 서비스의 구성입니다. OSGi 구성 [을 배포하는 방법에 대한 자세한 내용은 Experience Manager](/help/implementing/deploying/overview.md) 배포를 참조하십시오.
>AEM의 온프레미스 및 관리 서비스 배포와 달리 OSGi 웹 콘솔은 클라우드 서비스 배포에서 직접 사용할 수 없습니다.

사후 처리 워크플로우에서 사용할 수 있는 표준 워크플로우 단계에 대한 자세한 내용은 개발자 참조에서 [사후 처리 워크플로우의](developer-reference-material-apis.md#post-processing-workflows-steps) 워크플로우 단계를 참조하십시오.

## 모범 사례 및 제한 사항 {#best-practices-limitations-tips}

* 워크플로우를 설계할 때 모든 유형의 변환에 대한 요구 사항을 고려합니다. 나중에 변환의 필요성을 예측할 수 없는 경우 워크플로우에서 변환 생성 단계를 제거합니다. 나중에 변환을 일괄 삭제할 수 없습니다. 장기 사용 후 원치 않는 변환이 많은 저장 공간을 차지할 수 있습니다 [!DNL Experience Manager]. 개별 자산의 경우 사용자 인터페이스에서 변환을 수동으로 제거할 수 있습니다. 여러 자산의 경우 특정 표현물을 삭제하도록 사용자 [!DNL Experience Manager] 지정하거나 자산을 삭제하고 다시 업로드할 수 있습니다.
