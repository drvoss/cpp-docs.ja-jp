---
title: コンパイラ エラー C3893
ms.date: 11/04/2016
f1_keywords:
- C3893
helpviewer_keywords:
- C3893
ms.assetid: 90d52eae-6ef2-4db1-b7ad-92f9e8b140fb
ms.openlocfilehash: 45a140d3fd5f510ee2434950ca3c4b47c0756d75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447232"
---
# <a name="compiler-error-c3893"></a>コンパイラ エラー C3893

'var': initonly データ メンバーの左辺値の使用は、クラス 'type_name' のインスタンス コンス トラクターでのみ使用できます。

静的[initonly](../../dotnet/initonly-cpp-cli.md)データ メンバーは、静的コンス トラクターで取得された、アドレスを持つことができますのみです。

インスタンス (静的ではない) initonly データ メンバーは、取得されたインスタンス (静的ではない) コンス トラクターで、アドレスだけを設定できます。

次の例では、C3893 が生成されます。

```
// C3893.cpp
// compile with: /clr
ref struct Y1 {
   Y1() : data_var(0) {
      int% i = data_var;   // OK
   }
   initonly int data_var;
};

int main(){
   Y1^ y= gcnew Y1;
   int% i = y->data_var;   // C3893
}
```