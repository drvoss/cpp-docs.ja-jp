---
title: リソース コンパイラの致命的なエラー RW1025
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 8ecfc11f5cc991294d966a4b6c75d8da6669d5b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575683"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>リソース コンパイラの致命的なエラー RW1025

ここまでのヒープのメモリ不足

領域が多すぎるをしている可能性がありますのあるメモリに常駐するソフトウェアを確認します。 あるメモリの量を確認するには、CHKDSK プログラムを使用します。

大規模なリソース ファイルを作成する場合は、リソース スクリプトを 2 つのファイルに分割します。 2 つの .res ファイルを作成した後に、それらを結合するのに MS-DOS のコマンドラインを使用します。

```
copy first.res /b + second.res /b full.res
```