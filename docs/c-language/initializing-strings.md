---
title: "文字列の初期化 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- character arrays, initializing
- strings [C++], initializing
- initializing arrays, strings
ms.assetid: 0ab8079d-d0d3-48f9-afd1-36a7bb439b29
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: c1bf614544f008910a86e8281cb775c1d7734b0d
ms.contentlocale: ja-jp
ms.lasthandoff: 05/18/2017

---
# <a name="initializing-strings"></a>文字列の初期化
文字列リテラル (またはワイド文字列リテラル) で、文字 (またはワイド文字) の配列を初期化できます。 例:  
  
```  
char code[ ] = "abc";  
```  
  
 文字の 4 要素配列として `code` を初期化します。 4 番目の要素は、すべての文字列リテラルを終了する null 文字です。  
  
 識別子リストの長さは、初期化される識別子の数と同じだけです。 文字列より短い配列サイズを指定すると、余分な文字は無視されます。 たとえば、次の宣言では、`code` を 3 要素の文字配列として初期化します。  
  
```  
char code[3] = "abcd";  
```  
  
 初期化子の最初の 3 文字だけが `code` に割り当てられます。 文字 `d` と文字列の終端の null 文字は破棄されます。 このため、終端文字なし文字列 (つまり、終端を示す 0 値のない文字列) が作成され、この条件を示す診断メッセージが生成されることに注意してください。  
  
 次の宣言  
  
```  
char s[] = "abc", t[3] = "abc";  
```  
  
 は次の宣言と同じです。  
  
```  
char s[]  = {'a', 'b', 'c', '\0'},   
     t[3] = {'a', 'b', 'c' };  
```  
  
 文字列が指定された配列のサイズよりも短い場合、配列内の残りの要素は 0 に初期化されます。  
  
 **Microsoft 固有の仕様**  
  
 Microsoft C では、文字列リテラルは最長 2048 バイトです。  
  
 **Microsoft 固有の仕様はここまで**  
  
## <a name="see-also"></a>関連項目  
 [初期化](../c-language/initialization.md)