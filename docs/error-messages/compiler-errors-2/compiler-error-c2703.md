---
title: コンパイラ エラー C2703
ms.date: 11/04/2016
f1_keywords:
- C2703
helpviewer_keywords:
- C2703
ms.assetid: 384295c3-643d-47ae-a9a6-865b3036aa84
ms.openlocfilehash: 363e3de497a7226a7c1dddd5769a047e6ea53e29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558298"
---
# <a name="compiler-error-c2703"></a>コンパイラ エラー C2703

無効な _leave ステートメント

A`__leave`ステートメントは内部である必要があります、`__try`ブロックします。

次の例では、C2703 が生成されます。

```
// C2703.cpp
int main() {
   __leave;   // C2703
   __try {
      // try the following line instead
      __leave;
   }
   __finally {}
}
```