---
title: __readpmc
ms.date: 11/04/2016
f1_keywords:
- __readpmc
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
ms.openlocfilehash: 059d9344fa329e69666abaca4d73122ab29f8d2a
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326434"
---
# <a name="readpmc"></a>__readpmc

**Microsoft 固有の仕様**

生成、`rdpmc`命令で指定されたカウンターの監視パフォーマンスの読み取りが`counter`します。

## <a name="syntax"></a>構文

```
unsigned __int64 __readpmc(
   unsigned long counter
);
```

#### <a name="parameters"></a>パラメーター

*counter*<br/>
[in]パフォーマンス カウンターを読み取る。

## <a name="return-value"></a>戻り値

指定したパフォーマンス カウンターの値。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__readpmc`|x86、x64|

**ヘッダー ファイル** \<intrin.h >

## <a name="remarks"></a>Remarks

この組み込みはカーネル モードでのみ、使用可能なルーチンは組み込みとして使用できるのみです。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)