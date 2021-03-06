---
title: コマンド ライン パラメーターの処理
ms.date: 11/04/2016
helpviewer_keywords:
- _spawn functions
- command line, processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line, processing arguments
- suppressing environment processing
- _exec function
ms.assetid: c20fa11d-b35b-4f3e-93b6-2cd5a1c3c993
ms.openlocfilehash: 9f7bc78c20aee4b91bf00fefd2615ba1a6611010
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623601"
---
# <a name="customizing-c-command-line-processing"></a>コマンド ライン パラメーターの処理

プログラムがコマンド ラインの引数を受け取らない場合は、コマンド ライン処理を実行するライブラリ ルーチンの使用を制約することで、領域を節約できます。 このルーチンは、「[ワイルドカード引数の展開](../c-language/expanding-wildcard-arguments.md)」で説明されているように、**_setargv** (ワイド文字環境では **_wsetargv**) と呼ばれます。 使用を抑制するには、**main** 関数を含むファイルの中に何も実行しないルーチンを定義し、**_setargv** (ワイド文字環境の場合は **_wsetargv**) という名前を付けます。 これにより、**_setargv** または **_wsetargv** の呼び出しが **_setargv** または **_wsetargv** の定義によって満たされるため、ライブラリ バージョンは読み込まれません。

同様に、`envp` 引数を使用して環境テーブルにアクセスしない場合は、環境処理ルーチンである **_setenvp** (または **_wsetenvp**) の代わりに独自の空ルーチンを指定できます。

プログラムが C ランタイム ライブラリ ルーチンの **_spawn** または **_exec** ファミリを呼び出す場合、起動元のプロセスから新しいプロセスに環境を渡すためにこのルーチンが使用されているので、環境処理ルーチンを抑制しないでください。

## <a name="see-also"></a>参照

[main 関数とプログラム実行](../c-language/main-function-and-program-execution.md)