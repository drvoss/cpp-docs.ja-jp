---
title: "コンパイラ エラー C2270 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2270"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2270"
ms.assetid: b52c068e-0b61-42e7-b775-4d57b3ddcba0
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# コンパイラ エラー C2270
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 非メンバー関数が、メモリ モデル修飾子で宣言されています。  
  
 非メンバー関数が、[const](../../cpp/const-cpp.md)、[volatile](../../cpp/volatile-cpp.md)、または別のメモリ モデル修飾子で宣言されています。  
  
 次の例では警告 C2270 が生成されます。  
  
```  
// C2270.cpp  
// compile with: /c  
void func1(void) const;   // C2270, nonmember function  
  
void func2(void);  
  
class CMyClass {  
public:  
   void func2(void) const;  
};  
```