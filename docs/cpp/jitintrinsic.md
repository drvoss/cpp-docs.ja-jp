---
title: jitintrinsic
ms.date: 11/04/2016
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
ms.openlocfilehash: 9e726413f0bbfbd9d6affa348777c995c51283a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519302"
---
# <a name="jitintrinsic"></a>jitintrinsic

64 ビット共通言語ランタイムにとって重要であると関数をマークします。 これは、Microsoft が提供するライブラリの特定の関数で使用されます。

## <a name="syntax"></a>構文

```
__declspec(jitintrinsic)
```

## <a name="remarks"></a>Remarks

**jitintrinsic** MODOPT を追加します (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) 関数のシグネチャにします。

ユーザーはこれを使用してから推奨されません **_ _declspec**修飾子は、予期しない結果として発生することができます。

## <a name="see-also"></a>関連項目

[__declspec](../cpp/declspec.md)<br/>
[キーワード](../cpp/keywords-cpp.md)