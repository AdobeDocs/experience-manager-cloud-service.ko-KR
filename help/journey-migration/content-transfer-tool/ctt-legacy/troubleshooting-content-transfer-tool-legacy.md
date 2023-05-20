---
title: 컨텐츠 전송 도구 문제 해결(이전)
description: 콘텐츠 전송 도구 문제 해결
hide: true
hidefromtoc: true
exl-id: b99f8f2b-b1b7-4ec1-b1d2-0efe83e17e91
source-git-commit: 22bbf15e33ab3d5608dc01ed293bb04b07cb6c8c
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 94%

---

# 컨텐츠 전송 도구 문제 해결(이전) {#troubleshoot-content-transfer-tool}


## Blob ID가 누락됨 {#missing-blobs}

아래에 언급했듯이 보고된 Blob ID가 누락된 경우 기존 저장소에서 일관성 검사를 실행하고 누락된 Blob를 복원해야 합니다.
`ERROR o.a.j.o.p.b.AbstractSharedCachingDataStore - Error retrieving record [ba45c53f8b687e7056c85dceebf8156a0e6abc7e]`

다음 명령이 실행됩니다.

>[!NOTE]
>
>`--verbose` 플래그는 BLOB을 참조하는 노드 경로를 보고하는 데 필요합니다.

**저장소 AEM 6.5(Oak 1.8 이하)의 경우**

```shell
java -jar oak-run.jar datastorecheck --consistency --store [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds] <DATASTORE_CFG> --verbose <OUT_DIR> --dump
```

**Oak 1.10 이상이 있는 저장소의 경우**

```shell
java -jar oak-run.jar datastore --check-consistency [<SEGMENT_STORE_PATH>|<MONGO_URI>] --[s3ds|fds|azureds] <DATASTORE_CFG> --out-dir <OUT_DIR> --work-dir <TEMP_DIR> --verbose
```

자세한 내용은 [Oak 실행 가능 Jar](https://github.com/apache/jackrabbit-oak/tree/trunk/oak-run)를 참조하십시오.

일관성을 위해 위에 지정된 *OUT_DIR*&#x200B;에 생성된 파일에서 경로에 바이너리가 누락되고, 백업에서 복원, 경로 삭제, 색인 재지정 등과 같은 적절한 조치를 취했는지 확인할 수 있습니다. 


## UI 동작 {#ui-behavior}

사용자는 컨텐츠 전송 도구에 대한 UI(사용자 인터페이스)에서 다음과 같은 동작 변경 사항을 볼 수 있습니다.

* 컨텐츠 전송 도구 UI의 아이콘이 이 안내서에 표시된 스크린샷과 다르거나 소스 AEM 인스턴스의 버전에 따라 전혀 표시되지 않을 수 있습니다.
