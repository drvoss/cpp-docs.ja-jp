---
title: STUB
ms.date: 11/04/2016
f1_keywords:
- STUB
helpviewer_keywords:
- STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
ms.openlocfilehash: 95f8e1584bdd87f23e87c27418c0debca5c3181a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533719"
---
# <a name="stub"></a>STUB

仮想デバイス ドライバー (VxD) (WINNT で定義されている IMAGE_DOS_HEADER 構造体を含むファイル名を指定することができますを構築するモジュール定義ファイルで使用する場合。H) をクリックし、既定のヘッダーではなく、仮想デバイス ドライバー (VxD) で使用します。

```
STUB:filename
```

## <a name="remarks"></a>Remarks

指定するのと同じ方法*filename*では、 [/stub](../../build/reference/stub-ms-dos-stub-file-name.md)リンカー オプション。

スタブは VxD を構築する場合だけ、モジュール定義ファイルで有効です。

## <a name="see-also"></a>関連項目

[モジュール定義ステートメントに関する規則](../../build/reference/rules-for-module-definition-statements.md)