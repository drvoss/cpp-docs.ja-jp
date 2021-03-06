---
title: __vmx_vmptrld
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmptrld
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
ms.openlocfilehash: 4f74a69bf0a4a780834dc9669c1266c82f7038e6
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51325921"
---
# <a name="vmxvmptrld"></a>__vmx_vmptrld

**Microsoft 固有の仕様**

現在の仮想マシンの制御構造 (VMCS) を指定したアドレスからポインターを読み込みます。

## <a name="syntax"></a>構文

```
int __vmx_vmptrld(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>パラメーター

*VmcsPhysicalAddress*<br/>
[in]VMCS ポインターが格納されているアドレスです。

## <a name="return-value"></a>戻り値

0<br/>
操作が成功しました。

1<br/>
現在 VMCS の `VM-instruction error field` で有効な拡張状態が発生したため、操作は失敗しました。

2<br/>
有効な状態がないため操作は失敗しました。

## <a name="remarks"></a>Remarks

VMCS ポインターは、64 ビットの物理アドレスです。

`__vmx_vmptrld` 関数は `VMPTRLD` マシン語命令と同じです。 この関数は、ホストの仮想マシンのモニターと、ゲスト オペレーティング システムとそのアプリケーションとの対話をサポートします。 詳細については、検索、ドキュメント、「Intel 仮想化技術仕様 ia-32 Intel アーキテクチャ向け、」で番号 C97063-002、文書化、 [Intel Corporation](https://software.intel.com/articles/intel-sdm)サイト。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__vmx_vmptrld`|X64|

**ヘッダー ファイル** \<intrin.h >

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)