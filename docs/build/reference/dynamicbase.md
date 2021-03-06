---
title: /DYNAMICBASE
ms.date: 06/12/2018
f1_keywords:
- /dynamicbase
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
ms.openlocfilehash: fb8bfd4f4b11d14dbbc605f4366cf1cd5446a319
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430791"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

ランダムに再ベースできる読み込み時に Windows Vista で初めて提供された Windows のアドレス空間レイアウト randomization (ASLR) 機能を使用して実行可能イメージを生成するかどうかを指定します。

## <a name="syntax"></a>構文

> **/DYNAMICBASE****[: NO]**

## <a name="remarks"></a>Remarks

**/DYNAMICBASE**オプションのヘッダーを変更する、*実行可能イメージ*、.dll または .exe ファイルをアプリケーションが、読み込み時にランダムにリベースする必要があり、仮想アドレスが有効かどうかを示すためにヒープの仮想メモリの場所に影響を与える割り当てのランダム化スタック、およびその他のオペレーティング システムの割り当て。 **/DYNAMICBASE**オプションは、32 ビットと 64 ビットの両方のイメージに適用されます。 ASLR は、Windows Vista およびそれ以降のオペレーティング システムでサポートされます。 オプションは、以前のオペレーティング システムによって無視されます。

既定では、 **/DYNAMICBASE**を有効にします。 このオプションを無効にするには、 **/DYNAMICBASE:NO**します。 **/DYNAMICBASE**オプションが必要です、 [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)オプションに影響を与えます。

## <a name="see-also"></a>関連項目

- [EDITBIN オプション](../../build/reference/editbin-options.md)
- [Windows ISV Software Security Defenses](https://msdn.microsoft.com/library/bb430720.aspx)