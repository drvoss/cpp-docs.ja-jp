---
title: "数値演算定数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.constants
dev_langs:
- C++
helpviewer_keywords:
- M_PI constant
- M_PI_2 constant
- math constants
- M_2_PI constant
- M_1_PI constant
- M_E constant
- USE_MATH_DEFINES constant
- M_LOG2E constant
- M_LOG10E constant
- M_LN10 constant
- M_SQRT1_2 constant
- _USE_MATH_DEFINES constant
- M_PI_4 constant
- constants, math
- M_2_SQRTPI constant
- M_SQRT2 constant
- M_LN2 constant
ms.assetid: db533c3f-6ae8-4520-9d35-c8fabbef3529
caps.latest.revision: 8
author: corob-msft
ms.author: corob
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
ms.openlocfilehash: 04e5bacf91207b71f083fce106335eb47254f355
ms.contentlocale: ja-jp
ms.lasthandoff: 05/18/2017

---
# <a name="math-constants"></a>数値演算定数
## <a name="syntax"></a>構文  
  
```  
#define _USE_MATH_DEFINES // for C++  
#include <cmath>  
  
#define _USE_MATH_DEFINES // for C  
#include <math.h>  
```  
  
## <a name="remarks"></a>コメント  
 指定された式の値として、次のシンボルが定義されています。  
  
|シンボル|式|値|  
|------------|----------------|-----------|  
|M_E|e|2.71828182845904523536|  
|M_LOG2E|log2(e)|1.44269504088896340736|  
|M_LOG10E|log10(e)|0.434294481903251827651|  
|M_LN2|ln(2)|0.693147180559945309417|  
|M_LN10|ln(10)|2.30258509299404568402|  
|M_PI|pi|3.14159265358979323846|  
|M_PI_2|pi/2|1.57079632679489661923|  
|M_PI_4|pi/4|0.785398163397448309616|  
|M_1_PI|1/pi|0.318309886183790671538|  
|M_2_PI|2/pi|0.636619772367581343076|  
|M_2_SQRTPI|2/sqrt(pi)|1.12837916709551257390|  
|M_SQRT2|sqrt(2)|1.41421356237309504880|  
|M_SQRT1_2|1/sqrt(2)|0.707106781186547524401|  
  
 数値演算定数は標準 C/C++ では定義されていません。 これらを使用するには、最初に `_USE_MATH_DEFINES` を定義してから、cmath または math.h をインクルードする必要があります。  
  
 リリース モードでプロジェクトをビルドする場合は、ファイル ATLComTime.h に math.h が含まれます。 ATLComTime.h をインクルードしているプロジェクトで 1 つまたは複数の数値演算定数を使用する場合は、ATLComTime.h をインクルードする前に `_USE_MATH_DEFINES` を定義する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [グローバル定数](../c-runtime-library/global-constants.md)