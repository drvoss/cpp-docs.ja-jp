---
title: メッセージ マップ クロス リファレンスの使い方
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.messages
helpviewer_keywords:
- windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
ms.openlocfilehash: 71c46e7c30eab414534012c2fe314999568d2bd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457799"
---
# <a name="how-to-use-the-message-map-cross-reference"></a>メッセージ マップ クロス リファレンスの使い方

エントリ\<memberFxn >、派生クラス用の独自のメンバー関数を記述[CWnd](../../mfc/reference/cwnd-class.md)クラス。 関数は任意の名前を指定します。 などの他の関数`OnActivate`、クラスのメンバー関数は`CWnd`します。 呼び出された場合にメッセージを渡す、 `DefWindowProc` Windows 関数。 Windows 通知メッセージを処理するには、オーバーライド、対応する`CWnd`派生クラスで関数。 関数は、基本クラスを基底クラスでオーバーライドされた関数を呼び出す必要があり、Windows は、メッセージに応答します。

すべてのケースに関数のプロトタイプを置く、 `CWnd`-派生クラスのヘッダー、およびコードに示すようメッセージ マップ エントリ。

次の用語が使用されます。

|用語|定義|
|----------|----------------|
|ID|任意のユーザー定義のメニュー項目の ID (WM_COMMAND メッセージ) またはコントロール ID (子ウィンドウの通知メッセージ)。|
|"message"と"wNotifyCode"|Windows は、WINDOWS で定義されている Id をメッセージです。H.|
|nMessageVariable|戻り値を格納する変数の名前、 `RegisterWindowMessage` Windows 関数。|

## <a name="see-also"></a>関連項目

[メッセージ マップ](../../mfc/reference/message-maps-mfc.md)

