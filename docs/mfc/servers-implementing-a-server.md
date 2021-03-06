---
title: 'サーバー : サーバーの実装'
ms.date: 11/04/2016
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
ms.openlocfilehash: a5c89ff1256d557ef417b9e53ce76bbf1b5d6196
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518962"
---
# <a name="servers-implementing-a-server"></a>サーバー : サーバーの実装

この記事では、ビジュアル編集サーバー アプリケーションの MFC アプリケーション ウィザードを作成するコードについて説明します。 アプリケーション ウィザードを使用していない場合、この記事では、サーバー アプリケーションを実装するコードを記述する必要があります、領域を示します。

新しいサーバー アプリケーションを作成するアプリケーション ウィザードを使用する場合の大量のサーバー固有のコードを提供します。 ビジュアル編集サーバーの機能を既存のアプリケーションに追加する場合は、アプリケーション ウィザードが必要なサーバー コードの残りの部分を追加する前に指定するコードを複製する必要があります。

アプリケーション ウィザードで提供されるサーバー コードは、いくつかのカテゴリに分類されます。

- サーバーのリソースを定義するには。

  - メニュー リソースをサーバーが、独自のウィンドウで埋め込みアイテムを編集するときに使用します。

  - メニューとツールバーのリソースを場所に、サーバーがアクティブなときに使用します。

  これらのリソースの詳細については、次を参照してください。[メニューとリソース: サーバーの変更点](../mfc/menus-and-resources-server-additions.md)します。

- 派生した item クラスを定義する`COleServerItem`します。 サーバーのアイテムの詳細については、次を参照してください。[サーバー: サーバー アイテム](../mfc/servers-server-items.md)します。

- ドキュメント クラスの基本クラスを変更する`COleServerDoc`します。 詳細については、次を参照してください。[サーバー: サーバー ドキュメントの実装](../mfc/servers-implementing-server-documents.md)します。

- 派生したフレーム ウィンドウ クラスを定義する`COleIPFrameWnd`します。 詳細については、次を参照してください。[サーバー: を実装する、インプレース フレーム Windows](../mfc/servers-implementing-in-place-frame-windows.md)します。

- Windows の登録データベースにサーバー アプリケーションのエントリを作成し、OLE システム、サーバーの新しいインスタンスを登録します。 このトピックでは、次を参照してください。[登録](../mfc/registration.md)します。

- 初期化とサーバー アプリケーションを起動します。 このトピックでは、次を参照してください。[登録](../mfc/registration.md)します。

詳細については、次を参照してください。 [COleServerItem](../mfc/reference/coleserveritem-class.md)、 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)、および[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)で、*クラス ライブラリ リファレンス*します。

## <a name="see-also"></a>関連項目

[サーバー](../mfc/servers.md)<br/>
[コンテナー](../mfc/containers.md)<br/>
[メニューとリソース (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[登録](../mfc/registration.md)

