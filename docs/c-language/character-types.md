---
title: "文字型 | Microsoft Docs"
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
- character data types [C]
- types [C], character
ms.assetid: d3ca8cda-c0d7-43af-9472-697e8ef015ce
caps.latest.revision: 7
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
ms.openlocfilehash: f0f8639e90787ddcc90b7a302f226d305f29dce1
ms.contentlocale: ja-jp
ms.lasthandoff: 05/18/2017

---
# <a name="character-types"></a>文字型
前に文字 **L** が付かない整数の文字定数には、`int` 型があります。 単一の文字を含む整数の文字定数の値は整数として解釈される文字の数値です。 たとえば、文字 `a` の数値は、10 進形式では 97 で、16 進形式では 61 です。  
  
 構文上、"ワイド文字定数" は、文字 **L** がプレフィックスとして付けられている文字定数です。ワイド文字定数は、`wchar_t` 型 (STDDEF.H ヘッダー ファイルで定義されている整数型) を持ちます。 例:  
  
```  
char    schar =  'x';   /* A character constant          */  
wchar_t wchar = L'x';   /* A wide-character constant for   
                            the same character           */  
```  
  
 ワイド文字定数は、16 ビット幅で、拡張実行文字セットのメンバーを指定します。 これにより、`char` 型で表すには大きすぎる文字をアルファベットで表現することができます。 ワイド文字の詳細については、「[マルチバイト文字とワイド文字](../c-language/multibyte-and-wide-characters.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [C 文字定数](../c-language/c-character-constants.md)