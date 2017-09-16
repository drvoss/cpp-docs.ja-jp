---
title: "コンパイラ エラー C3211 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3211
dev_langs:
- C++
helpviewer_keywords:
- C3211
ms.assetid: 85e33fed-3b59-4315-97e6-20d31c6a985a
caps.latest.revision: 6
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
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: bba7dc1f5001b199d0789d681a9f9ad01cdabee2
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3211"></a>コンパイラ エラー C3211
'explicit specialization': 明示的特殊化は、部分的特殊化の構文を使用しています。代わりに、テンプレート <> を使用してください  
  
 明示的特殊化の形式が正しくありません。  
  
 次の例では C3211 が生成されます。  
  
```  
// C3211.cpp  
// compile with: /LD  
template<class T>  
struct s;  
  
template<class T>  
// use the following line instead  
// template<>  
struct s<int>{};   // C3211  
```