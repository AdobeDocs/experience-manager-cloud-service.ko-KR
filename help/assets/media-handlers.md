---
title: 미디어 핸들러 및 워크플로우를 사용하여 자산 처리
description: 다양한 미디어 핸들러와 워크플로우에서 이를 사용하여 에셋에 대한 작업을 수행하는 방법에 대해 알아봅니다.
contentOwner: AG
translation-type: tm+mt
source-git-commit: f2e257ff880ca2009c3ad6c8aadd055f28309289

---


# 미디어 핸들러 및 워크플로우를 사용하여 자산 처리 {#processing-assets-using-media-handlers-and-workflows}

AEM(Adobe Experience Manager) 자산은 자산을 처리하기 위한 기본 워크플로우 및 미디어 핸들러 세트와 함께 제공됩니다. 워크플로우는 자산에서 실행할 일반 작업을 정의한 다음 축소판 생성 또는 메타데이터 추출 등의 미디어 핸들러에 특정 작업을 위임합니다.

특정 유형의 자산이 서버에 업로드될 때 자동으로 실행되도록 워크플로우를 정의할 수 있습니다. 처리 단계는 일련의 AEM Assets 미디어 핸들러에 대해 정의됩니다. AEM에서는 일부 [내장 핸들러를 제공하며,](#default-media-handlers) 추가 핸들러는 [명령줄 도구로](#creating-a-new-media-handler) 프로세스를 위임하여 [사용자 정의 개발](#command-line-based-media-handler)또는 정의될 수 있습니다.

미디어 처리기는 자산에 대한 특정 작업을 수행하는 AEM 자산 내의 서비스입니다. 예를 들어 MP3 오디오 파일이 AEM에 업로드되면 워크플로우는 메타데이터를 추출하고 축소판을 생성하는 MP3 핸들러를 트리거합니다. 미디어 핸들러는 일반적으로 워크플로우와 함께 사용됩니다. 대부분의 일반적인 MIME 유형은 AEM 내에서 지원됩니다. 워크플로우 확장/생성, 미디어 핸들러 확장/생성 또는 미디어 핸들러를 비활성화/활성화하여 자산에서 특정 작업을 수행할 수 있습니다.

>[!NOTE]
>
>AEM 자산에서 [지원하는 모든 포맷과 각 형식에 지원되는 기능에 대한 설명은 자산 지원 형식](file-format-support.md) 페이지를 참조하십시오.

## 기본 미디어 핸들러 {#default-media-handlers}

다음 미디어 핸들러는 AEM Assets 내에서 사용할 수 있으며 가장 일반적인 MIME 유형을 처리합니다.

<!-- TBD: Apply correct formatting once table is moved to MD.
-->

<table>
 <tbody>
  <tr>
   <td>처리기 이름</td>
   <td>서비스 이름(시스템 콘솔 내)</td>
   <td>지원되는 MIME 유형</td>
  </tr>
  <tr>
   <td>TextHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.TextHandler</p> </td>
   <td>text/plain</td>
  </tr>
  <tr>
   <td>PdfHandler</td>
   <td><p>com.day.cq.dam.handler.standard.pdf.PdfHandler</p> </td>
   <td><p>애플리케이션/pdf<br /> 애플리케이션/illustrator</p> </td>
  </tr>
  <tr>
   <td>JpegHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.JpegHandler</p> </td>
   <td>image/jpeg</td>
  </tr>
  <tr>
   <td>Mp3Handler</td>
   <td><p>com.day.cq.dam.handler.standard.mp3.Mp3Handler</p> </td>
   <td><p>audio/mpeg</p> </td>
  </tr>
  <tr>
   <td>ZipHandler</td>
   <td><p>com.day.cq.dam.handler.standard.zip.ZipHandler</p> </td>
   <td><p>application/java-archive</p> <p>application/zip</p> </td>
  </tr>
  <tr>
   <td>PictHandler</td>
   <td><p>com.day.cq.dam.handler.standard.pict.PictHandler</p> </td>
   <td><p>이미지/그림</p> </td>
  </tr>
  <tr>
   <td>StandardImageHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.StandardImageHandler</p> </td>
   <td><p>image/gif</p> <p>image/png</p> <p>애플리케이션/photoshop</p> <p>image/jpeg</p> <p>image/tiff</p> <p>image/x-ms-bmp</p> <p>image/bmp</p> </td>
  </tr>
  <tr>
   <td>MSOfficeHandler</td>
   <td>com.day.cq.dam.handler.standard.msoffice.MSOfficeHandler</td>
   <td>application/msword<br /> </td>
  </tr>
  <tr>
   <td>MSP 파섹</td>
   <td>com.day.cq.dam.handler.standard.msoffice.MSPowerPointHandler</td>
   <td>application/vnd.ms-powerpoint<br /> </td>
  </tr>
  <tr>
   <td>OpenOfficeHandler</td>
   <td>com.day.cq.dam.handler.standard.ooxml.OpenOfficeHandler</td>
   <td>application/vnd.openxmlformats-officedocument.wordprocessingml.document<br /> application/vnd.openxmlformats-office.spreadsheetml.sheet<br /> application/vnd.openxmlformats-officedocument.presentationml.presentation<br /><br /> </td>
  </tr>
  <tr>
   <td>EPubHandler</td>
   <td>com.day.cq.dam.handler.standard.epub.EPubHandler</td>
   <td>application/epub+zip</td>
  </tr>
  <tr>
   <td>GenericAssetHandler</td>
   <td><p>com.day.cq.dam.core.impl.handler.GenericAssetHandler</p> </td>
   <td>에셋에서 데이터를 추출할 다른 처리기가 없는 경우 폴백</td>
  </tr>
 </tbody>
</table>

모든 핸들러는 다음 작업을 수행합니다.

* 자산에서 사용 가능한 모든 메타데이터를 추출합니다.
* 자산에서 축소판 이미지 만들기

활성 미디어 핸들러를 볼 수 있습니다.

1. In your browser, navigate to `http://localhost:4502/system/console/components`.
1. 링크를 `com.day.cq.dam.core.impl.store.AssetStoreImpl`클릭합니다.
1. 모든 활성 미디어 핸들러가 있는 목록이 표시됩니다.

## 워크플로우에서 미디어 핸들러를 사용하여 자산 작업 수행 {#using-media-handlers-in-workflows-to-perform-tasks-on-assets}

미디어 처리기는 일반적으로 워크플로우와 함께 사용되는 서비스입니다.

AEM에는 자산을 처리하는 몇 가지 기본 워크플로우가 있습니다. 이를 보려면 워크플로우 콘솔을 열고 모델 **[!UICONTROL 탭을 클릭합니다]** .aem 자산으로 시작하는 워크플로우 제목은 자산별 제목입니다.

기존 워크플로우를 확장하고 특정 요구 사항에 따라 자산을 처리하기 위해 새로운 워크플로우를 만들 수 있습니다.

다음 예에서는 PDF 문서를 제외한 모든 자산에 대해 하위 **[!UICONTROL 자산이 생성되도록]** AEM 자산 동기화 워크플로우를 향상시키는 방법을 보여줍니다.

### 미디어 핸들러 비활성화/활성화 {#disabling-enabling-a-media-handler}

Apache Felix Web Management Console을 통해 미디어 핸들러를 비활성화하거나 활성화할 수 있습니다. 미디어 핸들러가 비활성화되면 해당 작업이 자산에 대해 수행되지 않습니다.

미디어 핸들러를 활성화/비활성화하려면:

1. In your browser, navigate to `https://<host>:<port>/system/console/components`.
1. 미디어 **[!UICONTROL 처리기의]** 이름 옆에 있는 비활성화를 클릭합니다. 예: `com.day.cq.dam.handler.standard.mp3.Mp3Handler`.
1. 페이지를 새로 고칩니다.비활성화되었음을 나타내는 아이콘이 미디어 처리기 옆에 표시됩니다.
1. 미디어 핸들러를 활성화하려면 미디어 **[!UICONTROL 핸들러의]** 이름 옆에 있는 활성화를 클릭합니다.

### 새 미디어 처리기 만들기 {#creating-a-new-media-handler}

새 미디어 유형을 지원하거나 자산에서 특정 작업을 실행하려면 새 미디어 핸들러를 만들어야 합니다. 이 섹션에서는 진행 방법에 대해 설명합니다.

#### 중요한 클래스 및 인터페이스 {#important-classes-and-interfaces}

구현을 시작하는 가장 좋은 방법은 대부분의 작업을 처리하고 적절한 기본 동작을 제공하는 제공된 추상 구현에서 상속하는 것입니다.Adobe `com.day.cq.dam.core.AbstractAssetHandler` 는

이 클래스는 이미 추상 서비스 설명자를 제공합니다. 따라서 이 클래스에서 상속하고 maven-sling-plugin을 사용하는 경우 inherit 플래그를 `true`로 설정해야 합니다.

다음 방법을 구현합니다.

* `extractMetadata()`:사용 가능한 모든 메타데이터를 추출합니다.
* `getThumbnailImage()`:전달된 자산에서 축소판 이미지를 만듭니다.
* `getMimeTypes()`:자산 MIME 형식을 반환합니다.

다음은 예제 템플릿입니다.

`package my.own.stuff; /** * @scr.component inherit="true" * @scr.service */ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the relevant parts } `

인터페이스와 클래스에는 다음이 포함됩니다.

* `com.day.cq.dam.api.handler.AssetHandler` 인터페이스:이 인터페이스는 특정 MIME 유형에 대한 지원을 추가하는 서비스에 대해 설명합니다. 이 인터페이스를 구현하려면 새 MIME 유형을 추가해야 합니다. 인터페이스에는 축소판을 만들고 메타데이터를 추출하기 위해 특정 문서를 가져오고 내보내는 방법이 포함되어 있습니다.
* `com.day.cq.dam.core.AbstractAssetHandler` class:이 클래스는 다른 모든 에셋 처리기 구현의 기초로 사용되고 있는 일반적인 기능을 제공합니다.
* `com.day.cq.dam.core.AbstractSubAssetHandler` 클래스:
   * 이 클래스는 다른 모든 에셋 처리기 구현의 기초가 되며 일반적으로 사용되는 기능뿐만 아니라 하위 에셋 추출에 일반적으로 사용되는 기능을 제공합니다.
   * 구현을 시작하는 가장 좋은 방법은 대부분의 작업을 처리하고 적절한 기본 동작을 제공하는 제공된 추상 구현에서 상속하는 것입니다.com.day.cq.dam.core.AbstractAssetHandler 클래스.
   * 이 클래스는 이미 추상 서비스 설명자를 제공합니다. 따라서 이 클래스에서 상속하고 maven-sling-plugin을 사용하는 경우 inherit 플래그를 true로 설정해야 합니다.

다음 방법을 구현해야 합니다.

* `extractMetadata()`:이 메서드는 사용 가능한 모든 메타데이터를 추출합니다.
* `getThumbnailImage()`:이 방법을 사용하면 전달된 자산에서 축소판 이미지가 만들어집니다.
* `getMimeTypes()`:이 메서드는 자산 MIME 형식을 반환합니다.

다음은 예제 템플릿입니다.

package my.own.stuff;/&amp;ast;&amp;ast;&amp;ast;@scr.component inherit=&quot;true&quot; &amp;ast;@scr.service &amp;ast;/ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the related parts }

인터페이스와 클래스에는 다음이 포함됩니다.

* `com.day.cq.dam.api.handler.AssetHandler` 인터페이스:이 인터페이스는 특정 MIME 유형에 대한 지원을 추가하는 서비스에 대해 설명합니다. 이 인터페이스를 구현하려면 새 MIME 유형을 추가해야 합니다. 인터페이스에는 축소판을 만들고 메타데이터를 추출하기 위해 특정 문서를 가져오고 내보내는 방법이 포함되어 있습니다.
* `com.day.cq.dam.core.AbstractAssetHandler` class:이 클래스는 다른 모든 에셋 처리기 구현의 기초로 사용되고 있는 일반적인 기능을 제공합니다.
* `com.day.cq.dam.core.AbstractSubAssetHandler` class:이 클래스는 다른 모든 에셋 처리기 구현의 기초가 되며 일반적으로 사용되는 기능뿐만 아니라 하위 에셋 추출에 일반적으로 사용되는 기능을 제공합니다.

<!--
#### Example: create a specific Text Handler {#example-create-a-specific-text-handler}

In this section, you will create a specific Text Handler that generates thumbnails with a watermark.

Proceed as follows:

Refer to [Development Tools](../sites-developing/dev-tools.md) to install and set up Eclipse with a Maven plugin and for setting up the dependencies that are needed for the Maven project.

After you perform the following procedure, when you upload a txt file into AEM, the file's metadata are extracted and two thumbnails with a watermark are generated.

1. In Eclipse, create `myBundle` Maven project:

    1. In the Menu bar, click **[!UICONTROL File > New > Other]**.
    1. In the dialog, expand the Maven folder, select Maven Project and click **[!UICONTROL Next]**.
    1. Check the Create a simple project box and the Use default Workspace locations box, then click **[!UICONTROL Next]**.
    1. Define the Maven project:

        * Group Id: com.day.cq5.myhandler
        * Artifact Id: myBundle
        * Name: My AEM bundle
        * Description: This is my AEM bundle

    1. Click **[!UICONTROL Finish]**.

1. Set the Java Compiler to version 1.5:

    1. Right-click the `myBundle` project, select Properties.
    1. Select Java Compiler and set following properties to 1.5:

        * Compiler compliance level
        * Generated .class files compatibility
        * Source compatibility

    1. Click **[!UICONTROL OK]**. In the dialog window, click Yes.

1. Replace the code in the pom.xml file with the following code:

1. Create the package `com.day.cq5.myhandler` that contains the Java classes under `myBundle/src/main/java`:

    1. Under myBundle, right-click `src/main/java`, select New, then Package.
    1. Name it `com.day.cq5.myhandler` and click Finish.

1. Create the Java class `MyHandler`:

    1. In Eclipse, under `myBundle/src/main/java`, right-click the `com.day.cq5.myhandler` package, select New, then Class.
    1. In the dialog window, name the Java Class MyHandler and click Finish. Eclipse creates and opens the file MyHandler.java.
    1. In `MyHandler.java` replace the existing code with the following and then save the changes:

   ```java
   package com.day.cq5.myhandler;
   import java.awt.Color;
   import java.awt.Rectangle;
   import java.awt.image.BufferedImage;
   import java.io.IOException;
   import java.io.InputStream;
   import java.io.InputStreamReader;
   import javax.jcr.Node;
   import javax.jcr.RepositoryException;
   import javax.jcr.Session;
   import org.apache.commons.io.IOUtils;
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   import com.day.cq.dam.api.metadata.ExtractedMetadata;
   import com.day.cq.dam.core.AbstractAssetHandler;
   import com.day.image.Font;
   import com.day.image.Layer;
   import com.day.cq.wcm.foundation.ImageHelper;

   /**
    * The <code>MyHandler</code> can extract text files
    * @scr.component inherit="true" immediate="true" metatype="false"
    * @scr.service
    *
    **/

   public class MyHandler extends AbstractAssetHandler {
    /** * Logger instance for this class. */
    private static final Logger log = LoggerFactory.getLogger(MyHandler.class);
    /** * Music icon margin */
    private static final int MARGIN = 10;
    /** * @see com.day.cq.dam.api.handler.AssetHandler#getMimeTypes() */
    public String[] getMimeTypes() {
     return new String[] {"text/plain"};
    }

    public ExtractedMetadata extractMetadata(Node asset) {
     ExtractedMetadata extractedMetadata = new ExtractedMetadata();
     InputStream data = getInputStream(asset);
     try {
      // read text data
      InputStreamReader reader = new InputStreamReader(data);
      char[] buffer = new char[4096];
      String text = "";
      while (reader.read(buffer) != -1) {
       text += new String(buffer);
      }
      reader.close();
      long wordCount = this.wordCount(text);
      extractedMetadata.setProperty("text", text);
      extractedMetadata.setMetaDataProperty("Word Count",wordCount);
      setMimetype(extractedMetadata, asset);
     } catch (Throwable t) {
      log.error("handling error: " + t.toString(), t);
     } finally {
      IOUtils.closeQuietly(data);
     }
     return extractedMetadata; }
    // ----------------------< helpers >----------------------------------------
    protected BufferedImage getThumbnailImage(Node node) {
     ExtractedMetadata metadata = extractMetadata(node);
     final String text = (String) metadata.getProperty("text");
     // create text layer
     final Layer layer = new Layer(500, 600, Color.WHITE);
     layer.setPaint(Color.black);
     Font font = new Font("Arial", 12);
     String displayText = this.getDisplayText(text, 600, 12);
     if(displayText!=null && displayText.length() > 0) {
      // commons-gfx Font class would throw IllegalArgumentException on empty or null text
      layer.drawText(10, 10, 500, 600, displayText, font, Font.ALIGN_LEFT, 0, 0);
     }
     // create watermark and merge with text layer
     Layer watermarkLayer;
     try {
      final Session session = node.getSession();
      watermarkLayer = ImageHelper.createLayer(session, "/content/dam/geometrixx/icons/certificate.png");
      watermarkLayer.setX(MARGIN);
      watermarkLayer.setY(MARGIN);
      layer.merge(watermarkLayer);
     } catch (RepositoryException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
     } catch (IOException e) {
      // TODO Auto-generated catch block
      e.printStackTrace(); }
     layer.crop(new Rectangle(510, 600));
     return layer.getImage(); }
    // ---------------< private >-----------------------------------------------
    /**
     * This method cuts lines if the text file is too long..
     * * @param text
     * * text to check
     * * @param height
     * * text box height (px)
     * * @param fontheight
     * * font height (px)
     * * @return the text which will fit into the box
     */
    private String getDisplayText(String text, int height, int fontheight) {
     String trimmedText = text.trim();
     int numOfLines = height / fontheight;
     String lines[] = trimmedText.split("\n");
     if (lines.length <= numOfLines) {
      return trimmedText;
     } else {
      String cuttetText = "";
      for (int i = 0; i < numOfLines; i++) {
       cuttetText += lines[i] + "\n";
      }
      return cuttetText;
     }
    }
    /**
     * * This method counts the number of words in a string
     * * @param text the String whose words would like to be counted
     * * @return the number of words in the string
     * */
    private long wordCount(String text) {
     // We need to keep track of the last character, if we have two white spaces in a row we dont want to double count
     // The starting of the document is always a whitespace
     boolean prevWhiteSpace = true;
     boolean currentWhiteSpace = true;
     char c; long numwords = 0;
     int j = text.length();
     int i = 0;
     while (i < j) {
      c = text.charAt(i++);
      if (c == 0) { break; }
      currentWhiteSpace = Character.isWhitespace(c);
      if (currentWhiteSpace && !prevWhiteSpace) { numwords++; }
      prevWhiteSpace = currentWhiteSpace;
     }
     // If we do not end with a white space then we need to add one extra word
     if (!currentWhiteSpace) { numwords++; }
     return numwords;
    }
   }
   ```

1. Compile the Java class and create the bundle:

    1. Right-click the myBundle project, select **[!UICONTROL Run As]**, then **[!UICONTROL Maven Install]**.
    1. The bundle `myBundle-0.0.1-SNAPSHOT.jar` (containing the compiled class) is created under `myBundle/target`.

1. In CRX Explorer, create a new node under `/apps/myApp`. Name = `install`, Type = `nt:folder`.
1. Copy the bundle `myBundle-0.0.1-SNAPSHOT.jar` and store it under `/apps/myApp/install` (for example with WebDAV). The new text handler is now active in AEM.
1. In your browser, open the Apache Felix Web Management Console. Select the Components tab and disable the default text handler `com.day.cq.dam.core.impl.handler.TextHandler`.

-->

## 명령줄 기반 미디어 처리기 {#command-line-based-media-handler}

AEM을 사용하면 워크플로우 내에서 명령줄 도구를 실행하여 에셋(예: ImageMagick)을 변환하고 새 변환을 자산에 추가할 수 있습니다. AEM 서버를 호스팅하는 디스크에만 명령줄 도구를 설치하고 워크플로우에 프로세스 단계를 추가 및 구성해야 합니다. 호출된 프로세스를 `CommandLineProcess`사용하면 특정 MIME 유형에 따라 필터링하고 새 변환에 따라 여러 축소판을 만들 수도 있습니다.

다음 변환은 AEM Assets 내에서 자동으로 실행 및 저장할 수 있습니다.

* ImageMagick 및 Ghostscript를 사용한 [EPS](https://www.imagemagick.org/script/index.php) 및 [AI 변환](https://www.ghostscript.com/)
* FFmpeg를 사용한 FLV 비디오 [트랜스코딩](https://ffmpeg.org/)
* LAME를 사용한 MP3 [인코딩](http://lame.sourceforge.net/)
* SOX를 사용한 오디오 [처리](http://sox.sourceforge.net/)

>[!NOTE]
>
>Windows 이외의 시스템에서 FFMpeg 도구는 파일 이름에 작은 따옴표(&#39;)가 있는 비디오 자산에 대한 변환을 생성하는 동안 오류를 반환합니다. 비디오 파일 이름에 단일 견적이 포함된 경우 AEM에 업로드하기 전에 해당 견적을 제거하십시오.

이 `CommandLineProcess` 프로세스는 나열된 순서대로 다음 작업을 수행합니다.

* 지정된 경우 특정 MIME 유형에 따라 파일을 필터링합니다.
* AEM 서버를 호스팅하는 디스크에 임시 디렉토리를 만듭니다.
* 원본 파일을 임시 디렉토리로 스트리밍합니다.
* 단계의 인수로 정의된 명령을 실행합니다. AEM을 실행하는 사용자의 권한이 있는 임시 디렉터리 내에서 명령이 실행되고 있습니다.
* 결과를 AEM 서버의 변환 폴더로 다시 스트리밍합니다.
* 임시 디렉토리를 삭제합니다.
* 지정된 경우 이러한 변환에 따라 축소판을 만듭니다. 축소판의 수와 크기는 단계의 인수로 정의됩니다.

### ImageMagick 사용 예 {#an-example-using-imagemagick}

다음 예에서는 AEM 서버의 /content/dam에 mime-type gif 또는 tiff가 있는 자산이 추가될 때마다 역진행 이미지의 원본과 세 개의 추가 축소판(140x100, 48x48 및 10x250)이 함께 작성되도록 명령줄 프로세스 단계를 설정하는 방법을 보여 줍니다.

이렇게 하려면 ImageMagick을 사용합니다. ImageMagick은 비트맵 이미지를 작성, 편집 및 구성할 수 있는 무료 소프트웨어 패키지로, 일반적으로 명령줄에서 사용됩니다.

먼저 AEM 서버를 호스팅하는 디스크에 ImageMagick을 설치합니다.

1. ImageMagick 설치:imageMagick 설명서를 [참조하십시오](https://www.imagemagick.org/script/download.php).
1. 명령줄에서 변환을 실행할 수 있도록 도구를 설정합니다.
1. 도구가 제대로 설치되었는지 확인하려면 명령줄에서 다음 명령을 `convert -h` 실행하십시오.

   변환 도구의 가능한 모든 옵션이 포함된 도움말 화면이 표시됩니다.

   >[!NOTE]
   >
   >일부 버전의 Windows(예: Windows SE)에서는 변환 명령이 Windows 설치의 일부인 기본 변환 유틸리티와 충돌하므로 실행되지 않을 수 있습니다. 이 경우 이미지 파일을 축소판으로 변환하는 데 사용되는 ImageMagick 유틸리티의 전체 경로를 언급합니다. 예, `"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`.

1. 도구가 제대로 실행되는지 확인하려면 작업 디렉토리에 .jpg 이미지를 추가하고 명령줄에서 명령 변환을 실행합니다. `<image-name>.jpg -flip <image-name>-flipped.jpg`

   역진행 이미지가 디렉토리에 추가됩니다.

그런 다음 명령줄 프로세스 단계를 DAM 자산 업데이트 **[!UICONTROL 워크플로우에 추가합니다]** .

1. 워크플로우 **[!UICONTROL 콘솔로]** 이동합니다.
1. 모델 **[!UICONTROL 탭에서]** DAM 자산 **[!UICONTROL 업데이트]** 모델을편집합니다.
1. 웹이 활성화된 **[!UICONTROL 변환]** 단계의 설정을 다음과 같이 변경합니다.

   **인수**:

   `mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

1. 워크플로우를 저장합니다.

수정된 워크플로우를 테스트하려면 자산을 추가합니다 `/content/dam`.

1. 파일 시스템에서 원하는 .tiff 이미지를 가져옵니다. WebDAV를 사용하여 이름을 변경하여 `myImage.tiff` 복사하여 `/content/dam`붙여넣을 수 있습니다.
1. 예를 들어 CQ5 **[!UICONTROL DAM]** 콘솔로 이동합니다 `http://localhost:4502/libs/wcm/core/content/damadmin.html`.
1. 자산 myImage.tiff **[!UICONTROL 를]** 열고 역진행 이미지와 세 개의 축소판이 만들어졌는지 확인합니다.

#### CommandLineProcess 프로세스 단계 구성 {#configuring-the-commandlineprocess-process-step}

이 섹션에서는 CommandLineProcess의 **프로세스 인수를** 설정하는 방법에 대해 **설명합니다**.

프로세스 인수의 **값은** 쉼표로 구분해야 하며 공백으로 시작할 수 없습니다.

<table>
 <tbody>
  <tr>
   <td> 인수 형식</td>
   <td>설명</td>
  </tr>
  <tr>
   <td> mime:&lt;mime-type&gt;</td>
   <td><p>선택적 인수입니다. 자산이 인수 중 하나와 동일한 MIME 형식을 갖는 경우 프로세스가 적용됩니다.</p> <p>여러 MIME 형식을 정의할 수 있습니다.</p> </td>
  </tr>
  <tr>
   <td> tn:&lt;width&gt;:&lt;height&gt;</td>
   <td><p>선택적 인수입니다. 그러면 인수에 정의된 치수로 축소판이 만들어집니다.</p> <p>여러 축소판을 정의할 수 있습니다.<br /> </p> </td>
  </tr>
  <tr>
   <td> cmd:&lt;command&gt;</td>
   <td><p>실행할 명령을 정의합니다. 구문은 명령줄 도구에 따라 다릅니다.</p> <p>하나의 명령만 정의할 수 있습니다.</p> <p>다음 변수를 사용하여 명령을 만들 수 있습니다.<br/></p> <p><code>${filename}</code>:입력 파일의 이름(예: 'original.jpg'<br/><code>${file}</code>):입력 파일의 전체 경로 이름(예: '/tmp/cqdam0816.tmp/original.jpg'<br/><code>${directory}</code>:입력 파일의 디렉토리(예: '/tmp/cqdam0816.tmp').<br/> <code>${basename}</code>:입력 파일의 확장자가 없는 이름(예: 원본<br/><code>${extension}</code>:입력 파일의 확장자(예: JPG)<br/></p></td>
  </tr>
 </tbody>
</table>

예를 들어 ImageMagick이 AEM 서버를 호스팅하는 디스크에 설치되어 있고 CommandLineProcess를 구현으로 사용하여 프로세스 단계를 만드는 경우 **다음** 값을 프로세스 인수로 **지정합니다**.

`mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

그런 다음 워크플로우가 실행되면 이 단계는 이미지/gif 또는 mime:image/tiff가 있는 에셋에만 적용되며, 전환된 원본 이미지를 만들어 .jpg로 변환하고 크기가 작은 세 개의 축소판을 만듭니다.140x100, 48x48 및 10x250.

ImageMagick을 **사용하여 다음** 프로세스 인수를 사용하여 세 개의 표준 축소판을 만듭니다.

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=319x319 -thumbnail "319x319>" -background transparent -gravity center -extent 319x319 -write png:cq5dam.thumbnail.319.319.png -thumbnail "140x100>" -background transparent -gravity center -extent 140x100 -write cq5dam.thumbnail.140.100.png -thumbnail "48x48>" -background transparent -gravity center -extent 48x48 cq5dam.thumbnail.48.48.png`

ImageMagick을 **사용하여 웹** 지원 변환을 만들려면 다음 프로세스 인수를 사용합니다.

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=1280x1280 -thumbnail "1280x1280>" cq5dam.web.1280.1280.jpeg`

>[!NOTE]
>
>CommandLineProcess **단계는** 자산의 자산(유형 노드 `dam:Asset`) 또는 하위 요소에만 적용됩니다.
