---
title: 環境変数マクロ
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, environment variable macros
- environment variables, macros in NMAKE
- macros, environment-variable
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
ms.openlocfilehash: 4691f89f1886b40637a0800ee8a6a94e4b4e06c5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594299"
---
# <a name="environment-variable-macros"></a>環境変数マクロ

NMAKE は、マクロの定義のセッションの開始前に存在する環境変数を継承します。 オペレーティング システム環境変数が設定されている場合は、NMAKE マクロとして使用できます。 継承された名前は大文字に変換します。 継承は、前処理する前に発生します。 /E オプションを使用して、メイクファイルで同じ名前のすべてのマクロをオーバーライドする環境変数から継承されたマクロが発生します。

セッションで、環境変数マクロを再定義することができ、これが、対応する環境変数を変更します。 SET コマンドで環境変数を変更することもできます。 SET コマンドを使用して、セッションで環境変数を変更するのには変更されません、対応するマクロが。

例えば:

```
PATH=$(PATH);\nonesuch

all:
    echo %PATH%
```

変更する、この例では`PATH`、対応する環境変数を変更`PATH`; 追加`\nonesuch`をパスにします。

メイクファイルの正しい構文になる文字列として、環境変数が定義されている場合は、マクロは作成されませんし、警告は生成されません。 変数の値にドル記号 ($) が含まれている場合 (nmake の) はそのマクロ呼び出しの先頭として解釈されます。 マクロを使用すると、予期しない動作を可能性があります。

## <a name="see-also"></a>関連項目

[NMAKE の特殊マクロ](../build/special-nmake-macros.md)