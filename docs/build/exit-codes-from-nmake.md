---
title: NMAKE で返される終了コード
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
ms.openlocfilehash: 08aceadf107112b446844b09fad24a11fbe7a731
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499594"
---
# <a name="exit-codes-from-nmake"></a>NMAKE で返される終了コード

NMAKE では、次の終了コードが返されます。

|コード|説明|
|----------|-------------|
|0|エラー (場合によっては警告)|
|1|(/K を使用する場合にのみを発行する) 不完全なビルド|
|2|プログラム エラー: 次のいずれかの原因として考えられます。|
||-メイクファイルに構文エラー|
||-コマンドからのエラーまたは終了コード|
||-ユーザーにより中断|
|4|システム エラー: メモリ不足|
|255|ターゲットが最新でない (/Q を使用する場合にのみ発行)|

## <a name="see-also"></a>関連項目

[NMAKE の実行](../build/running-nmake.md)