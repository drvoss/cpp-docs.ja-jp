---
title: 規則の定義
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
ms.openlocfilehash: 0e8356f57b85d503328bb282e2f9f785ac20fa4c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431166"
---
# <a name="defining-a-rule"></a>規則の定義

*Fromext*依存のファイルの拡張機能を表すと*toext*ターゲット ファイルの拡張子を表します。

```
.fromext.toext:
   commands
```

## <a name="remarks"></a>Remarks

拡張は、大文字小文字が区別されていません。 表すマクロを呼び出すことができる*fromext*と*toext*; マクロは、プリプロセス時に展開されます。 上記ピリオド (.) *fromext*行の先頭に置く必要があります。 コロン (:) は、スペースまたはタブの 0 個以上続きます。 これは、スペースまたはタブ、コマンドを指定するにはセミコロン (;)、番号記号 (#)、コメントを指定して、または改行文字によってのみ実行できます。 その他の空白は許可されません。 記述ブロックのように、コマンドが指定されます。

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

[規則の検索パス](../build/search-paths-in-rules.md)

## <a name="see-also"></a>関連項目

[推論規則](../build/inference-rules.md)