---
title: コンパイラ エラー C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: f643b7d8c035b4d1d7d8806feb5b121cf76d7796
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651910"
---
# <a name="compiler-error-c2698"></a>コンパイラ エラー C2698

使用して、宣言には、' 1' の宣言は、既存の using 宣言用と共存できません ' 2' の宣言

作成したら、[宣言を使用して](../../cpp/using-declaration.md)すべてを使用して、データ メンバー関数のみをオーバー ロードできるよう、同じ名前を使用して、同じスコープ内宣言は許可されませんが。

次の例では、C2698 が生成されます。

```
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```