---
title: 複数の記述ブロックのターゲット
ms.date: 11/04/2016
helpviewer_keywords:
- description blocks
- blocks, multiple description
- multiple description blocks
ms.assetid: 8618dcd9-c11d-4562-91a7-0c904ed438a8
ms.openlocfilehash: 5b441aab729beed771a6f3bce34e9555f490352d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647786"
---
# <a name="targets-in-multiple-description-blocks"></a>複数の記述ブロックのターゲット

別のコマンドを使用して 1 つ以上の記述ブロック内のターゲットを更新するには、ターゲットとの依存オブジェクト間の 2 つの連続するコロン (:) を指定します。

```
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

## <a name="see-also"></a>関連項目

[ターゲット](../build/targets.md)