---
title: コンパイラの警告 (レベル 4) C4629
ms.date: 11/04/2016
f1_keywords:
- C4629
helpviewer_keywords:
- C4629
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
ms.openlocfilehash: db3f4201dbf5ff925449b0924d08a43ee4283b3e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651790"
---
# <a name="compiler-warning-level-4-c4629"></a>コンパイラの警告 (レベル 4) C4629

digraph が使用されました。文字のシーケンス 'digraph' はトークン 'char' として解釈されます。(これが意図でない場合は、2 文字の間にスペースを挿入してください)

コンパイラで [/Za](../../build/reference/za-ze-disable-language-extensions.md)を使用すると、digraph の検出時に警告が表示されます。

次の例では C4629 が生成されます。

```
// C4629.cpp
// compile with: /Za /W4
int main()
<%   // C4629 <% digraph for {
}
```