---
title: NMAKE の致命的なエラー U1064
ms.date: 11/04/2016
f1_keywords:
- U1064
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
ms.openlocfilehash: 71213391032989e5faf8889761b29194928125a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463363"
---
# <a name="nmake-fatal-error-u1064"></a>NMAKE の致命的なエラー U1064

見つかりません。 メイクファイルと指定されたターゲットがありません。

NMAKE のコマンド ラインはメイクファイルまたはターゲットを指定しなかったし、現在のディレクトリにメイクファイルをという名前のファイルが含まれていません。

NMAKE では、メイクファイルまたはコマンド ライン ターゲット (または両方) が必要です。 Nmake メイクファイルを使用できるようにするには、/F オプションを指定するか、現在のディレクトリにメイクファイルをという名前のファイルを配置します。 NMAKE は、メイクファイルが指定されていない場合は、推論規則を使用して、コマンドラインのターゲットを作成できます。