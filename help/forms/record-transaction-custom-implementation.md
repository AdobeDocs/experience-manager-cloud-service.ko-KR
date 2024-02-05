---
title: 사용자 지정 구현에 대한 트랜잭션 기록
description: TransactionRecorder API를 사용하여 트랜잭션으로 계상되지 않은 작업을 자동으로 기록합니다
feature: Adaptive Forms, Foundation Components
hide: true
hidefromtoc: true
source-git-commit: a1a87a27d73d7472ec02de37621123bbdd3876b4
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 1%

---

# 사용자 지정 구현에 대한 트랜잭션 기록 {#record-a-transaction-for-custom-implementations}

TransactionRecorder API를 사용하여 트랜잭션으로 계산되지 않은 작업을 자동으로 기록합니다.

사용자 지정 코드를 사용하여 PDF 양식을 제출할 수 있습니다. 또는 AEM Forms에서 제공하는 제출 방법 대신 사용자 지정 방법을 사용하여 양식을 제출합니다. 이전에 언급된 AEM Forms API의 모든 작업 및 사용자 지정 구현은 트랜잭션으로 계산되지 않습니다. AEM Forms에서 API 제공, [TransactionRecorder](https://javadoc.io/doc/com.adobe.aem/aem-forms-sdk-api/latest/com/adobe/aem/transaction/core/ITransactionRecorder.html)를 입력하여 트랜잭션으로 이러한 작업을 기록합니다.

트랜잭션을 기록하려면 [표준 sling 서블릿](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/store-and-retrieve-af-with-2fa/create-servlet.html?lang=en) 클라이언트에서 서블릿을 호출하여 트랜잭션을 기록합니다. AJAX 또는 기타 모든 표준 메서드를 사용하여 서블릿을 호출할 수 있습니다.

## 샘플 서버측 코드 {#sample-server-sided-code}

아래 샘플 코드를 사용하여 사용자 지정 OSGi 번들을 사용하여 Java™ 클래스에서 TransactionRecorder API를 실행할 수 있습니다.

```java
import com.adobe.aem.transaction.core.ITransactionRecorder;
import com.adobe.aem.transaction.core.model.TransactionRecord;
import com.adobe.aem.transaction.core.exception.TransactionException;
import com.adobe.aem.transaction.core.FormsTransactionConstants;

@Reference
private ITransactionRecorder transactionRecorder;

doPost (SlingHttpServletRequest request, SlingHttpServletResponse response) {
    transactionRecorder.startContext();
    TransactionRecord txRecord = extractTxRecordFromRequest(request); //extract transaction relevant data from request
    try {
        bool success = doBillableWork();
        if (success) {
            transactionRecorder.recordTransaction(txRecord);
        }
    } catch (Exception e) {
        //exception handling
    } finally {
        transactionRecorder.endContext();
    }
}

//Here, it is assumed that txInfo is passed in Stringified json form in the ajax call (in data parameter). You can pass txInfo from client in any way that you find suitable.
private TransactionRecord extractTxRecordFromRequest(SlingHttpServletRequest request) {
    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(request.getInputStream()));
    Map<String, Object> txDataMap = new HashMap<String, Object>();
    String txData = bufferedReader.readLine();
    JSONObject txInfo= new JSONObject(txData );
    try {
        String resourceType= txInfo.getString("resourceType");
        String transactionType = txInfo.getString("transactionType");
        Integer transactionCount = (Integer)txInfo.get("transactionCount");
        //Extract all the relevant tx record attributes similarly and pass them in Transaction Record constructor as per the java doc}
        return new TransactionRecord(transactionCount, transactionType, resourceType, ..);
    } catch (JSONException e) {
        //exception handling
    } finally {
        bufferedReader.close();
    }
}
```

## 샘플 클라이언트측 코드 {#sample-client-side-code}

아래 샘플 코드를 사용하여 가 있는 서블릿을 호출할 수 있습니다. `TransactionRecorder`API.

```javascript
$.ajax({
   type: 'POST',
   url: url, //servlet url
   contentType: 'application/json; UTF-8',
   data: JSON.stringify({transactionCount : 1,
                        transactionType: "SUBMIT",
                        resourceType: "FORM",
                        resourceSubType: "ADAPTIVE-FORM"}),
   success: successHandler,
   error: faultHandler
})
```

## 관련 문서 {#related-articles}

* [거래 보고서 청구 가능 API](/help/forms/transaction-reports-billable-apis.md)

