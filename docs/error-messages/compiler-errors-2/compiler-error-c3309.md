---
title: コンパイラ エラー C3309
ms.date: 11/04/2016
f1_keywords:
- C3309
helpviewer_keywords:
- C3309
ms.assetid: 75ee16e3-7d4e-4c41-b3cb-64e9849c3aab
ms.openlocfilehash: e66aa31982b018670684c8f12b05ba6f7347cd87
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598147"
---
# <a name="compiler-error-c3309"></a>コンパイラ エラー C3309

'macro_name': モジュール名をマクロ、またはキーワードにすることはできません

モジュール属性の名前プロパティに渡す値を、展開するプリプロセッサのシンボルにすることはできません。文字列リテラルにする必要があります。

次の例では C3309 が生成されます。

```
// C3309.cpp
#define NAME MyModule
[module(name="NAME")];   // C3309
// Try the following line instead
// [module(name="MyModule")];
[coclass]
class MyClass {
public:
   void MyFunc();
};

int main() {
}
```