---
title: raw_interfaces_only
ms.date: 11/04/2016
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: c07401036261b9f93bb2c07dcf3aff1ecf72e2fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519354"
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**C++ 固有の仕様**

エラー処理ラッパー関数の生成を抑制し、[プロパティ](../cpp/property-cpp.md)そのラッパー関数を使用して宣言します。

## <a name="syntax"></a>構文

```
raw_interfaces_only
```

## <a name="remarks"></a>Remarks

**Raw_interfaces_only**属性も削除する非プロパティ関数の名前付けで使用される既定のプレフィックスをによりします。 通常、プレフィックスは**raw _** します。 この属性を指定すると、タイプ ライブラリの関数名が直接使用されます。

この属性を使用することで、タイプ ライブラリの低水準の内容のみを公開できます。

**END C 固有の仕様**

## <a name="see-also"></a>関連項目

[#import の属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)