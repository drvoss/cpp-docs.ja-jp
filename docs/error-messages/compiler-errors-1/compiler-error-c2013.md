---
title: コンパイラ エラー C2013
ms.date: 11/04/2016
f1_keywords:
- C2013
helpviewer_keywords:
- C2013
ms.assetid: 6b5c955c-53da-48ee-8533-64ef5b905173
ms.openlocfilehash: b279202b8b32197a99d230040207aa50bc100495
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618479"
---
# <a name="compiler-error-c2013"></a>コンパイラ エラー C2013

'>' がありません。

`#include` ディレクティブに終わりの山かっこがありません。 エラーを解決するには、終わりの山かっこを追加します。

次の例では C2013 が生成されます。

```
// C2013.cpp
#include <stdio.h    // C2013
```

考えられる解決方法:

```
// C2013b.cpp
// compile with: /c
#include <stdio.h>
```