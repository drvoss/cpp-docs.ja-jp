---
title: OnCmdMsg ハンドラー
ms.date: 11/04/2016
f1_keywords:
- OnCmdMsg
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
ms.openlocfilehash: 37b3d5ffa3e6492c8c00b8b22eba58d09fad51f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643171"
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg ハンドラー

各コマンド ターゲットを呼び出すコマンドのルーティングを実現する、`OnCmdMsg`次のコマンド ターゲット シーケンス内のメンバー関数。 コマンドの使用対象`OnCmdMsg`コマンドを処理できるかどうかを判断し、処理できない場合は、別のコマンド ターゲットにルーティングします。

コマンド ターゲット クラスごとのオーバーライド、`OnCmdMsg`メンバー関数。 上書きは、次のターゲットを特定する各クラスのルート コマンドを使用できます。 フレーム ウィンドウでは、たとえば、常にコマンドをルーティングする現在の子ウィンドウまたはビューの表に示すように[標準のコマンド ルート](../mfc/command-routing.md)します。

既定の`CCmdTarget`の実装`OnCmdMsg`コマンド ターゲット クラスのメッセージ マップを使用して受信する各コマンド メッセージのハンドラー関数の検索-標準的なメッセージを検索することと同じ方法でします。 一致が見つかると、ハンドラーを呼び出します。 メッセージ マップの検索については[方法、フレームワークのメッセージ マップ検索](../mfc/how-the-framework-searches-message-maps.md)します。

## <a name="see-also"></a>関連項目

[フレームワークがハンドラーを呼び出す方法](../mfc/how-the-framework-calls-a-handler.md)

