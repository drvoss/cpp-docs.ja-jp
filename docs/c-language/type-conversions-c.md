---
title: "型変換 | Microsoft Docs"
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
- conversions, type
- type conversion
- converting types
- integral promotions
- type casts, when performed
ms.assetid: d130ee7c-03c3-48f4-af7b-1fdba0d3b086
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
ms.openlocfilehash: b2d02ad9494bce2c1d9a0e94cd87c9327526e2f3
ms.contentlocale: ja-jp
ms.lasthandoff: 05/18/2017

---
# <a name="type-conversions-c"></a>型変換 (C)
型変換は、指定された演算子と、オペランドまたは演算子の型に依存します。 次の場合に型変換が実行されます。  
  
-   ある型の値が異なる型の変数に代入されるとき、または演算子が演算を実行する前にオペランドの型を変換するとき  
  
-   ある型の値が異なる型に明示的にキャストされるとき  
  
-   値が関数に引数として渡されるとき、または型が関数から戻されるとき  
  
 文字、短整数、整数ビット フィールド (符号付きと符号なし)、または列挙型のオブジェクトは、整数が使用できる場所であれば式内のどこででも使用できます。 `int` が元の型のすべての値を表すことができる場合、値は `int` に変換されます。それ以外の場合は `unsigned int` に変換されます。 このプロセスを "整数の上位変換" といいます。 整数の上位変換では値が保持されます。 つまり、上位変換後の値が上位変換前と同じであることが保証されます。 詳細については、「[通常の算術変換](../c-language/usual-arithmetic-conversions.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [式と代入](../c-language/expressions-and-assignments.md)