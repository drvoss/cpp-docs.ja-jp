---
title: __incfsbyte、__incfsword、__incfsdword
ms.date: 11/04/2016
f1_keywords:
- __incfsword
- __incfsbyte_cpp
- __incfsbyte
- __incfsdword
- __incfsword_cpp
- __incfsdword_cpp
helpviewer_keywords:
- __incfsword intrinsic
- __incfsdword intrinsic
- __incfsbyte intrinsic
ms.assetid: 820457fb-e35e-42d3-bcb6-725da3281c64
ms.openlocfilehash: f9f0bef89b32e1901c2f6b173baa90153b25a71d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577893"
---
# <a name="incfsbyte-incfsword-incfsdword"></a>__incfsbyte、__incfsword、__incfsdword

**Microsoft 固有の仕様**

先頭の相対オフセットで指定されたメモリ位置に追加する値を 1 つ、`FS`セグメント。

## <a name="syntax"></a>構文

```
void __incfsbyte(
   unsigned long Offset
);
void __incfsword(
   unsigned long Offset
);
void __incfsdword(
   unsigned long Offset
);
```

#### <a name="parameters"></a>パラメーター

*オフセット*<br/>
[in]先頭からのオフセット`FS`します。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__incfsbyte`|x86|
|`__incfsword`|x86|
|`__incfsdword`|x86|

## <a name="remarks"></a>Remarks

これらの組み込みはカーネル モードで使用可能なのみとルーチンは組み込みとしてのみです。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__addfsbyte, \__addfsword, \__addfsdword](../intrinsics/addfsbyte-addfsword-addfsdword.md)<br/>
[_ _readfsbyte、 \__readfsdword、 \__readfsqword、 \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)<br/>
[_ _writefsbyte、 \__writefsdword、 \__writefsqword、 \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)<br/>
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)