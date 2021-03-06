---
title: OLE ドラッグ アンド ドロップおよびデータ転送クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
ms.openlocfilehash: 7520881314da9568f6130f5fe2ccf0a3e0e88e2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475185"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>OLE ドラッグ アンド ドロップおよびデータ転送クラス

これらのクラスは、OLE データ転送で使用されます。 これらは、アプリケーションによってクリップボードの使用方法やドラッグ アンド ドロップの間で転送されるデータを許可します。

[COleDropSource](../mfc/reference/coledropsource-class.md)<br/>
最初から最後までドラッグ アンド ドロップ操作を制御します。 このクラスは、ドラッグ操作の開始時と終了時に決定します。 カーソルからのフィードバックは、ドラッグ アンド ドロップ操作中にも表示されます。

[COleDataSource](../mfc/reference/coledatasource-class.md)<br/>
アプリケーションでは、データ転送のデータを提供するときに使用します。 `COleDataSource` オブジェクト指向クリップボード オブジェクトとして表示でした。

[COleDropTarget](../mfc/reference/coledroptarget-class.md)<br/>
ドラッグ アンド ドロップ操作の対象を表します。 A`COleDropTarget`オブジェクトは画面上のウィンドウに対応します。 すべてのデータにドロップし、実際のドロップ操作を実装をそのまま使用するかどうかが決定します。

[COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
受信側として使用される`COleDataSource`します。 `COleDataObject` オブジェクトによって格納されるデータにアクセスできるように、`COleDataSource`オブジェクト。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)

