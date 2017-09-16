---
title: "_byteswap_uint64、_byteswap_ulong、_byteswap_ushort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_byteswap_uint64"
  - "_byteswap_ulong"
  - "_byteswap_ushort"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "byteswap_ulong"
  - "_byteswap_ulong"
  - "byteswap_uint64"
  - "_byteswap_ushort"
  - "_byteswap_uint64"
  - "byteswap_ushort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_byteswap_uint64 関数"
  - "_byteswap_ulong 関数"
  - "_byteswap_ushort 関数"
  - "バイトのスワッピング"
  - "バイト, スワップ"
  - "byteswap_uint64 関数"
  - "byteswap_ulong 関数"
  - "byteswap_ushort 関数"
  - "スワップ (バイトを)"
ms.assetid: 83bda211-f02f-4cf0-8a78-d6de1f175970
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _byteswap_uint64、_byteswap_ulong、_byteswap_ushort
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

整数のバイト順序を反転させます。  
  
## 構文  
  
```  
unsigned short _byteswap_ushort (  
   unsigned short val  
);  
unsigned long _byteswap_ulong (  
   unsigned long val  
);  
unsigned __int64 _byteswap_uint64 (  
   unsigned __int64 val  
);  
```  
  
#### パラメーター  
 `val`  
 バイト順を反転する整数。  
  
## 必要条件  
  
|ルーチン|必須ヘッダー|  
|----------|------------|  
|`_byteswap_ushort`|\<stdlib.h\>|  
|`_byteswap_ulong`|\<stdlib.h\>|  
|`_byteswap_uint64`|\<stdlib.h\>|  
  
 互換性の詳細については、「C ランタイム ライブラリ」の「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。  
  
## 使用例  
  
```  
// crt_byteswap.c  
#include <stdlib.h>  
  
int main()  
{  
   unsigned __int64 u64 = 0x0102030405060708;  
   unsigned long ul = 0x01020304;  
  
   printf("byteswap of %I64x = %I64x\n", u64, _byteswap_uint64(u64));  
   printf("byteswap of %Ix = %Ix", ul, _byteswap_ulong(ul));  
}  
```  
  
  **102030405060708 \= 807060504030201 の byteswap**  
**1020304 \= 4030201 の byteswap**   
## 参照  
 [カテゴリ別ランタイム ルーチン](../../c-runtime-library/run-time-routines-by-category.md)