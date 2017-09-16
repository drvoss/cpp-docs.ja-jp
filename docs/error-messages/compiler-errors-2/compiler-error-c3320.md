---
title: "コンパイラ エラー C3320 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3320
dev_langs:
- C++
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: 4b4acfe97e38cf13e336b7c58ffc868c69cf7a09
ms.contentlocale: ja-jp
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3320"></a>コンパイラ エラー C3320
'type': 型には、モジュール 'name' プロパティと同じ名前を指定することはできません  
  
渡されたパラメーターと、エクスポートされたユーザー定義型 (UDT)、構造体、クラス、列挙型、または共用体の場合が同じ名前を持つことはできません、[モジュール](../../windows/module-cpp.md)属性の name プロパティです。  
  
## <a name="example"></a>例  
次の例では C3320 が生成されます。  
  
```cpp  
// C3320.cpp  
#include "unknwn.h"  
[module(name="xx")];  
  
[export] struct xx {   // C3320  
// Try the following line instead  
// [export] struct yy {  
   int i;  
};  
```