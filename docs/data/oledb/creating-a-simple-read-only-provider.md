---
title: 単純な読み取り専用プロバイダーの作成
ms.date: 10/26/2018
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
ms.openlocfilehash: 2ac8e45ca06a5566923141adf5a22dc6710eeeab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432605"
---
# <a name="creating-a-simple-read-only-provider"></a>単純な読み取り専用プロバイダーの作成

使用する OLE DB プロバイダーを作成した場合、 **ATL プロジェクト ウィザード**と**ATL OLE DB プロバイダー ウィザード**をサポートするその他の機能を追加することができます。 送信してどのような条件下でコンシューマーにデータの種類を調べることで、プロバイダーのデザインを開始します。 これは、機能は、コマンド、トランザクション、およびその他の省略可能なオブジェクトをサポートするために必要かどうかを判断するは特に重要です。 実装とテスト、前もって優れたデザインが短縮されます。

2 つの部分では、例では、表示されます。

- 最初の部分に示す方法[単純な読み取り専用プロバイダーの作成](../../data/oledb/implementing-the-simple-read-only-provider.md)文字列のペアを読み取る。

- 2 番目の部分に示す方法[単純な読み取り専用プロバイダーの強化](../../data/oledb/enhancing-the-simple-read-only-provider.md)を追加して、`IRowsetLocate`インターフェイス。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダーの作成](../../data/oledb/creating-an-ole-db-provider.md)<br/>
