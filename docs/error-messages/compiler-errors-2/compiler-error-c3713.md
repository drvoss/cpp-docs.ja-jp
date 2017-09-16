---
title: "コンパイラ エラー C3713 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3713"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3713"
ms.assetid: 75c6b9b6-955b-49bd-9bc8-ced88b496a1f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# コンパイラ エラー C3713
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'メソッド': イベント ハンドラー メソッドは、ソース 'メソッド' と同じ関数パラメーターを含む必要があります。  
  
 ソース イベントのメソッドと同じパラメーターを使用しないイベント ハンドラーのメソッドを定義しています。  このエラーを解決するには、イベント ハンドラーのメソッドに、ソース イベントのメソッドと同じパラメーターを指定します。  
  
 次の例では警告 C3713 が生成されます。  
  
```  
// C3713.cpp  
// compile with: /c  
[event_source(native)]  
class CEventSrc {  
public:  
   __event void event1(int nValue);  
   // try the following line instead  
   // __event void event1();  
};  
  
[event_receiver(native)]  
class CEventRec {  
public:  
   void handler1() {}  
  
   void HookEvents(CEventSrc* pSrc) {  
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3713  
   }  
  
   void UnhookEvents(CEventSrc* pSrc) {  
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3713  
   }  
};  
```