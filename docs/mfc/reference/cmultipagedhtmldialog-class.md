---
title: CMultiPageDHtmlDialog クラス
ms.date: 11/04/2016
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
ms.openlocfilehash: 680c485241b7a377d1c6f0ec2785dbbade01ed3f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443552"
---
# <a name="cmultipagedhtmldialog-class"></a>CMultiPageDHtmlDialog クラス

マルチページ ダイアログは、複数の HTML ページを順番に表示し、各ページのイベントを処理します。

## <a name="syntax"></a>構文

```
class CMultiPageDHtmlDialog : public CDHtmlDialog
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|マルチページ (ウィザード スタイル) DHTML ダイアログ オブジェクトを構築します。|
|[CMultiPageDHtmlDialog:: ~ 関数](#cmultipagedhtmldialog__~cmultipagedhtmldialog)|マルチページ DHTML ダイアログ オブジェクトを破棄します。|

## <a name="remarks"></a>Remarks

これを行うためのメカニズムは、 [DHTML および URL イベント マップ](dhtml-event-maps.md)イベントのマップ ページごとに埋め込みが含まれています。

## <a name="example"></a>例

このマルチページのダイアログ ボックスは、簡単なウィザードのような機能を定義する 3 つの HTML リソースを想定しています。 最初のページには、 **[次へ]** ボタンをクリックし、2 番目、 **Prev**と **[次へ]** ボタン、および 3 番目、 **Prev**ボタン。 ハンドラー関数を呼び出すボタンが押されたとき[CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource)適切な新しいページを読み込みます。

(CMyMultiPageDlg.h) で、クラス宣言の関連部分:

[!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]

クラスの実装 (CMyMultipageDlg.cpp) 内の関連部分:

[!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)

`CMultiPageDHtmlDialog`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdhtml.h

##  <a name="cmultipagedhtmldialog"></a>  CMultiPageDHtmlDialog::CMultiPageDHtmlDialog

マルチページ (ウィザード スタイル) DHTML ダイアログ オブジェクトを構築します。

```
CMultiPageDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID = NULL,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog();
```

### <a name="parameters"></a>パラメーター

*lpszTemplateName*<br/>
ダイアログ ボックスのテンプレート リソースの名前を表す null で終わる文字列。

*szHtmlResID*<br/>
HTML のリソースの名前を表す null で終わる文字列。

*pParentWnd*<br/>
親またはオーナー ウィンドウ オブジェクトへのポインター (型の[CWnd](../../mfc/reference/cwnd-class.md)) ダイアログ オブジェクトが属しています。 NULL の場合、ダイアログ オブジェクトの親ウィンドウは、アプリケーションのメイン ウィンドウに設定されます。

*nIDTemplate*<br/>
ダイアログ ボックスのテンプレート リソースの ID 番号が含まれています。

*nHtmlResID*<br/>
HTML リソースの ID 番号が含まれています。

##  <a name="_dtorcmultipagedhtmldialog"></a>  CMultiPageDHtmlDialog:: ~ 関数

マルチページ DHTML ダイアログ オブジェクトを破棄します。

```
virtual ~CMultiPageDHtmlDialog();
```

## <a name="see-also"></a>関連項目

[CDHtmlDialog クラス](../../mfc/reference/cdhtmldialog-class.md)
