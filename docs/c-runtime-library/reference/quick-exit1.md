---
title: "quick_exit1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "quick_exit"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "quick_exit"
  - "process/quick_exit"
  - "stdlib/quick_exit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "quick_exit 関数"
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# quick_exit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通常のプログラムが終了するようにします。  
  
## 構文  
  
```  
__declspec(noreturn) void quick_exit(  
    int status  
);  
```  
  
#### パラメーター  
 状態  
 ホスト環境に戻るためのステータス コード。  
  
## 戻り値  
 `quick_exit` 関数は、その呼び出し元に戻ることができません。  
  
## 解説  
 `quick_exit` 関数は、通常のプログラムが終了するようにします。 これは、`atexit`、`_onexit`、またはシグナル ハンドラー \(`signal` 関数によって登録された\) によって登録された関数を呼び出しません。`quick_exit` が複数回呼び出される場合、または`exit` 関数も呼び出される場合、動作は定義されません。  
  
 関数が登録されたときに既に呼び出されている関数を除き、`quick_exit` 関数は、後入れ先出し \(LIFO\) という順序で、`at_quick_exit` によって登録される関数を呼び出します。[longjmp](../../c-runtime-library/reference/longjmp.md) 呼び出しが、関数の呼び出しを終了する登録済み関数を呼び出している間に呼び出される場合、動作は定義されません。  
  
 登録された関数が呼び出された後、`quick_exit` は、`status` 値を使用してコントロールをホスト環境に返すことにより、`_Exit` を呼び出します。  
  
## 必要条件  
  
|ルーチン|必須ヘッダー|  
|----------|------------|  
|`quick_exit`|\<process.h\> または \<stdlib.h\>|  
  
 互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。  
  
## 参照  
 [プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [\_exec、\_wexec 系関数](../../c-runtime-library/exec-wexec-functions.md)   
 [終了、\_Exit、\_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [\_onexit、\_onexit\_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_spawn 系関数と \_wspawn 系関数](../Topic/_spawn,%20_wspawn%20Functions.md)   
 [system、\_wsystem](../../c-runtime-library/reference/system-wsystem.md)