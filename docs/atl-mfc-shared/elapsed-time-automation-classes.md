---
title: '経過時間: オートメーション クラス'
ms.date: 11/04/2016
helpviewer_keywords:
- adding dates
- calculating dates and times
- dates, calculating intervals
- elapsed time, calculating in Automation
- Automation classes, elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: 26b34b37-c10e-4b91-82c3-1dc5ffb5361f
ms.openlocfilehash: fbd01a4e7268456af342293d77ef74d372d2e639
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583912"
---
# <a name="elapsed-time-automation-classes"></a>経過時間: オートメーション クラス

この手順は、2 つの差を計算する方法を示しています。`CTime`オブジェクトを取得、`CTimeSpan`結果。

## <a name="to-calculate-elapsed-time"></a>経過時間を計算するには

1. 2 つ作成`COleDateTime`オブジェクト。

1. 1 つの設定、`COleDateTime`オブジェクトを現在の時刻。

1. いくつかの時間のかかるタスクを実行します。

1. 他の設定`COleDateTime`オブジェクトを現在の時刻。

1. 2 つの時刻の差を取得します。

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

## <a name="see-also"></a>関連項目

[日付と時刻: オートメーション サポート](../atl-mfc-shared/date-and-time-automation-support.md)
