---
title: "浮動小数点値の切り捨て | Microsoft Docs"
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
- floating-point numbers, truncation
ms.assetid: 051a6e22-c636-4af8-9ac4-40160f4affca
caps.latest.revision: 6
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
ms.openlocfilehash: 795b8a21f3f4113eab7ebe78fea6117255df8b22
ms.contentlocale: ja-jp
ms.lasthandoff: 05/18/2017

---
# <a name="truncation-of-floating-point-values"></a>浮動小数点値の切り捨て
**ANSI 3.2.1.4** 浮動小数点数をより狭い浮動小数点数に変換するときの切り捨てまたは丸めの方向  
  
 アンダーフローが発生すると、浮動小数点変数の値はゼロに丸められます。 オーバーフローは、指定した最適化に応じて、実行時エラーが発生する場合も、予測不可能な値が生成される場合もあります。  
  
## <a name="see-also"></a>関連項目  
 [浮動小数点演算](../c-language/floating-point-math.md)