---
title: コンパイラ エラー C2504
ms.date: 11/04/2016
f1_keywords:
- C2504
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
ms.openlocfilehash: 8f428699aa14cbd1f021a57ed8dcabefa8b24c16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444392"
---
# <a name="compiler-error-c2504"></a>コンパイラ エラー C2504

'class': 基底クラスが定義されていません

基底クラスが宣言が定義されていることはありません。  以下の原因が考えられます。

1. インクルード ファイルがありません。

1. 外部の基本クラスの宣言[extern](../../cpp/using-extern-to-specify-linkage.md)します。

次の例では、C2504 が生成されます。

```
// C2504.cpp
// compile with: /c
class A;
class B : public A {};   // C2504
```

わかりました

```
class C{};
class D : public C {};
```