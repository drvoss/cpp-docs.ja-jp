---
title: "ステートメントの概要 | Microsoft Docs"
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
ms.assetid: ce45d2fe-ec0e-459f-afb1-80ab6a7f0239
caps.latest.revision: 8
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: ba6aad3546a185958bf07432b377882645c3da7f
ms.contentlocale: ja-jp
ms.lasthandoff: 02/24/2017

---
# <a name="summary-of-statements"></a>ステートメントの概要
*statement*:  
 *labeled-statement*  
  
 *compound-statement*  
  
 *expression-statement*  
  
 *selection-statement*  
  
 *iteration-statement*  
  
 *jump-statement*  
  
 *try-except-statement* /* Microsoft 固有の仕様 \*/  
  
 *try-finally-statement* /* Microsoft 固有の仕様 \*/  
  
 *jump-statement*:  
 **goto**  *identifier*  **;**  
  
 **continue ;**  
  
 **break ;**  
  
 **return**  *expression*opt**;**  
  
 *compound-statement*:  
 **{**  *declaration-list*opt*statement-list*opt**}**  
  
 *declaration-list*:  
 *declaration*  
  
 *declaration-list declaration*  
  
 *statement-list*:  
 *statement*  
  
 *statement-list statement*  
  
 *expression-statement*:  
 *expression*opt**;**  
  
 *iteration-statement*:  
 **while (**  *expression*  **)**  *statement*  
  
 **do**  *statement*  **while (**  *expression*  **) ;**  
  
 **for (**  *expression*opt**;** *expression*opt**;** *expression*opt**)** *statement*  
  
 *selection-statement*:  
 **if (**  *expression*  **)**  *statement*  
  
 **if (**  *expression*  **)**  *statement*  **else**  *statement*  
  
 **switch (**  *expression*  **)**  *statement*  
  
 *labeled-statement*:  
 *identifier*  **:**  *statement*  
  
 **case**  *constant-expression*  **:**  *statement*  
  
 **default :**  *statement*  
  
 *try-except-statement*:   /\* Microsoft 固有の仕様 \*/  
 **__try**  *compound-statement*  
  
 **__except (**  *expression*  **)**  *compound-statement*  
  
 *try-finally-statement*:   /\* Microsoft 固有の仕様 \*/  
 **__try**  *compound-statement*  
  
 **__finally**  *compound-statement*  
  
## <a name="see-also"></a>関連項目  
 [句の構造文法](../c-language/phrase-structure-grammar.md)