---
title: naked 関数
ms.date: 11/04/2016
helpviewer_keywords:
- naked functions
- functions [C++], naked
- prolog code
- epilog code
ms.assetid: 2543c8af-00d4-4a2a-8a87-e746da1f9929
ms.openlocfilehash: 250a47157e915dfe2f2a9e5f6d912bbf83334d55
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430376"
---
# <a name="naked-functions"></a>naked 関数

**Microsoft 固有の仕様**

`naked` ストレージ クラス属性は C 言語への Microsoft 固有の拡張機能です。 `naked` ストレージ クラス属性を指定して宣言されている関数に対して、コンパイラは、プロローグ コードおよびエピローグ コードを含まないコードを生成します。 この機能を使用して、プロローグとエピローグのコード シーケンスをインライン アセンブラー コードで独自に記述できます。 naked 関数は、仮想デバイス ドライバーの記述用に特に便利です。

`naked` 属性は関数の定義だけに関連し、型修飾子ではないため、naked 関数は「[拡張ストレージ クラス属性](../c-language/c-extended-storage-class-attributes.md)」で説明されている拡張属性構文を使用します。

次の例では、`naked` 属性を使用して関数を定義します。

```
__declspec( naked ) int func( formal_parameters )
{
   /* Function body */
}
```

または、次のようにします。

```
#define Naked   __declspec( naked )

Naked int func( formal_parameters )
{
   /* Function body */
}
```

`naked` 属性は、関数のプロローグとエピローグのコード シーケンスをコンパイラが生成するかどうかにのみ影響を与えます。 このような関数を呼び出すために生成されるコードには影響を与えません。 したがって、`naked` 属性は関数の型の一部と見なされず、関数ポインターは `naked` 属性を持つことができません。 さらに、`naked` 属性は、データ定義に適用できません。 たとえば、次のコードはエラーになります。

```
__declspec( naked ) int i;  /* Error--naked attribute not */
                            /* permitted on data declarations. */
```

`naked` 属性は、関数定義にだけ関連し、関数のプロトタイプでは指定できません。 次の宣言はコンパイル エラーになります。

```
__declspec( naked ) int func();   /* Error--naked attribute not */
                     /* permitted on function declarations.    */   \
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[C 関数の定義](../c-language/c-function-definitions.md)