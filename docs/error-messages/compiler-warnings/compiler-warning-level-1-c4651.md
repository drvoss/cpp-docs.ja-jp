---
title: コンパイラの警告 (レベル 1) C4651
ms.date: 11/04/2016
f1_keywords:
- C4651
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
ms.openlocfilehash: 01e2472a547e73eda5fcc56952949a0d9611029f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434776"
---
# <a name="compiler-warning-level-1-c4651"></a>コンパイラの警告 (レベル 1) C4651

'定義' プリコンパイル済みヘッダーに定義されていますが、現在のコンパイルではありません。

プリコンパイル済みヘッダーが生成されたときに、このコンパイルではなく、定義が指定されました。

プリコンパイル済みのヘッダー内で、コードの残りの部分ではなく、定義が有効になります。

プリコンパイル済みヘッダーがで指定してビルドされている場合、コンパイラで/Yu コンパイルは指定していない場合にこの警告が生成されます。  /Yu コマンドラインに指定してを追加するには、この警告が解決されます。