---
title: ストアド プロシージャの使用
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
ms.openlocfilehash: 2c0c1c71103384439d0b7b94f942e1b5a6d9e651
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536158"
---
# <a name="using-stored-procedures"></a>ストアド プロシージャの使用

ストアド プロシージャは、データベースに格納されている実行可能オブジェクトです。 ストアド プロシージャの呼び出しは、SQL コマンドの呼び出しに似ています。 (実行またはクライアント アプリケーション内のステートメントを準備する) 代わりに、データ ソースでストアド プロシージャを使用するより高いパフォーマンス、ネットワーク オーバーヘッドの削減、および一貫性の向上、および精度を含め、いくつかの利点が提供することができます。

ストアド プロシージャは (0 を含む) の任意の数が入力または出力パラメーターおよび戻り値を渡すことができます。 特定のデータ値またはパラメーター マーカーを使用して、ハード コード パラメーターの値ことができます (疑問符 '?')。

> [!NOTE]
>  CLR の SQL Server と Visual C を使用して作成されたストアド プロシージャをコンパイルする必要があります、`/clr:safe`コンパイラ オプション。

OLE DB provider for SQL Server (SQLOLEDB) には、ストアド プロシージャの使用データを返す、次のメカニズムがサポートされています。

- すべて**選択**プロシージャ内のステートメントは結果セットを生成します。

- プロシージャは、出力パラメーターを使用してデータを返すことができます。

- プロシージャは、整数のリターン コードを持つことができます。

> [!NOTE]
> 併用できませんストアド プロシージャ、OLE DB provider for Jet そのプロバイダーがストアド プロシージャをサポートしていないため、クエリ文字列では、定数のみが許可されています。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレートの操作](../../data/oledb/working-with-ole-db-consumer-templates.md)