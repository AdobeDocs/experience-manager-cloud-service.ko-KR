---
title: 컨텐츠 전송 도구 사용
description: 컨텐츠 전송 도구 사용
exl-id: a19b8424-33ab-488a-91b3-47f0d3c8abf5
source-git-commit: 5b569ab1b1cca7e5ec46b872f8726fddfc8b8d14
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 57%

---

# 컨텐츠 전송 도구 사용 {#using-content-transfer-tool}

## 게시 인스턴스에서 컨텐츠 전송 도구 실행 {#running-ctt-on-publish}

컨텐츠를 게시 인스턴스로 이동하는 동안 컨텐츠를 대상 게시 인스턴스로 이동하기 위해 CTT를 소스 게시 인스턴스에 설치하는 것이 좋습니다. 아래 설명된 대로 권장되는 방법을 따르십시오.

* 작성자 인스턴스에서 사용한 것과 동일한 버전의 CTT를 사용합니다.

* 단일 게시 노드만 마이그레이션해야 합니다. 추출 작업을 시작하기 전에 로드 밸런서에서 제거해야 합니다.

* 마이그레이션 세트를 만들 때 작성 AEMaaCS 환경의 URL을 사용합니다.

* 게시하기 위해 수집하는 동안 게시 계층의 크기가 조정되지 않습니다(작성자와 다름). 따라서 다음과 같은 쓰기 작업을 시작하지 마십시오.

   * AEM AaCS 작성자에서 해당 환경의 게시로 컨텐츠 배포
   * 게시 인스턴스 간 사용자 동기화


## 문제 해결 {#troubleshooting}

### Blob ID가 누락됨 {#missing-blobs}

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


### UI 동작 {#ui-behavior}

사용자는 컨텐츠 전송 도구에 대한 UI(사용자 인터페이스)에서 다음과 같은 동작 변경 사항을 볼 수 있습니다.

* 컨텐츠 전송 도구 UI의 아이콘이 이 안내서에 표시된 스크린샷과 다르거나 소스 AEM 인스턴스의 버전에 따라 전혀 표시되지 않을 수 있습니다.
