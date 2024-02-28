---
title: AEM SDK를 다시 시작하는 방법
description: AEM SDK를 다시 시작하는 우수 사례
role: Admin, Developer, User
feature: Adaptive Forms
source-git-commit: a0e2c0e3020d48b171645818b8e02dc33b50c2d5
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 2%

---


# AEM SDK 다시 시작

Java™ 프로세스를 중지한 후 AEM SDK를 다시 시작하면 가 AEM 개발 환경에서 일치하지 않아 다음과 같은 오류가 발생할 수 있습니다.

`javax.jcr.RepositoryException: Applying repoinit operation failed despite retry; set loglevel to DEBUG to see all exceptions. Last exception message was: Failed to set ACL (javax.jcr.ValueFormatException: Invalid type: 0) AclLine ALLOW {principals=[forms-xfa-writers], privileges=[jcr:modifyProperties]} restrictions=[rep:glob=[*/jcr:content/*], rep:itemNames=[xfaForm], fd:condition=[xfaForm, 1]]`

![Restart-aem-sdk-error](/help/forms/assets/restart-sdk-error.png)

## 솔루션

AEM SDK를 다시 시작하려면 활성 명령 창으로 이동한 다음 키를 누릅니다 `Ctrl + C` sdk를 다시 시작하는 명령입니다.

SDK를 다시 시작하려면 &#39;Ctrl + C&#39; 명령을 사용하는 것이 좋습니다. Java™ 프로세스 중지와 같은 대체 방법을 사용하여 AEM SDK를 다시 시작하면 AEM 개발 환경이 일치하지 않을 수 있습니다.

## 참고 항목

* [AEM Forms을 위한 로컬 개발 환경 설정](/help/forms/setup-local-development-environment.md)
* [적응형 Forms 핵심 구성 요소 활성화](/help/forms/enable-adaptive-forms-core-components.md)
