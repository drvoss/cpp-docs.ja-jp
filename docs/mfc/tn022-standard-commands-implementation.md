---
title: "TN022: 標準コマンドの実装 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.commands
dev_langs: C++
helpviewer_keywords:
- ID_PREV_PANE command [MFC]
- ID_APP_EXIT command [MFC]
- ID_NEXT_PANE command [MFC]
- ID_INDICATOR_REC command [MFC]
- ID_WINDOW_SPLIT command [MFC]
- ID_FILE_PRINT_PREVIEW command [MFC]
- ID_WINDOW_CASCADE command [MFC]
- ID_FILE_CLOSE command [MFC]
- ID_FILE_SAVE_COPY_AS command [MFC]
- ID_WINDOW_ARRANGE command [MFC]
- ID_EDIT_FIND command [MFC]
- ID_FILE_OPEN command [MFC]
- ID_FILE_PAGE_SETUP command [MFC]
- ID_OLE_VERB_FIRST command [MFC]
- ID_EDIT_UNDO command [MFC]
- ID_EDIT_CLEAR command [MFC]
- ID_INDICATOR_CAPS command [MFC]
- ID_HELP_INDEX command [MFC]
- commands [MFC], standard
- ID_FILE_PRINT_SETUP command [MFC]
- ID_DEFAULT_HELP command [MFC]
- ID_INDICATOR_SCRL command [MFC]
- ID_FILE_PRINT command [MFC]
- ID_INDICATOR_OVR command [MFC]
- ID_INDICATOR_KANA command [MFC]
- ID_EDIT_COPY command [MFC]
- ID_EDIT_REDO command [MFC]
- ID_EDIT_PASTE command [MFC]
- ID_OLE_INSERT_NEW command [MFC]
- ID_OLE_EDIT_LINKS command [MFC]
- ID_EDIT_PASTE_SPECIAL command [MFC]
- ID_INDICATOR_EXT command [MFC]
- ID_HELP_USING command [MFC]
- standard commands
- ID_VIEW_STATUS_BAR command [MFC]
- ID_FILE_SAVE_AS command [MFC]
- ID_EDIT_CLEAR_ALL command [MFC]
- ID_WINDOW_NEW command [MFC]
- ID_CONTEXT_HELP command [MFC]
- ID_EDIT_REPLACE command [MFC]
- ID_WINDOW_TILE_HORZ command [MFC]
- ID_APP_ABOUT command [MFC]
- TN022
- ID_VIEW_TOOLBAR command [MFC]
- ID_HELP command [MFC]
- ID_WINDOW_TILE_VERT command [MFC]
- ID_EDIT_CUT command [MFC]
- ID_FILE_UPDATE command [MFC]
- ID_EDIT_REPEAT command [MFC]
- ID_FILE_SAVE command [MFC]
- ID_EDIT_PASTE_LINK command [MFC]
- ID_EDIT_SELECT_ALL command [MFC]
- ID_FILE_NEW command [MFC]
- ID_INDICATOR_NUM command
ms.assetid: a7883b46-23f7-4870-ac3a-804aed9258b5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 05e5e927ebfcb1584913d6415349c473bde4463c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="tn022-standard-commands-implementation"></a>テクニカル ノート 22: 標準コマンドの実装
> [!NOTE]
>  次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。  
  
 ここでは、MFC 2.0 によって提供される標準のコマンドの実装について説明します。 読み取り[テクニカル ノート 21](../mfc/tn021-command-and-message-routing.md)最初ため、標準のコマンドの多くを実装するための機構について説明します。  
  
 この説明は、MFC アーキテクチャ、Api、および一般的なプログラミングに関する知識を前提とします。 文書化されているだけでなくドキュメントに未記載「の実装のみ」の Api が記述されています。 これは、機能または MFC のプログラムを作成する方法について学習を開始する場所ではありません。 一般的な情報について、および文書化された Api の詳細については、Visual C を参照してください。  
  
## <a name="the-problem"></a>問題を  
 MFC では、ヘッダー ファイル コマで多くの標準コマンド Id を定義します。H. これらのコマンドの framework のサポートが異なります。 Framework のクラスがこれらのコマンドを処理する場所と方法を理解することはできませんのみを表示するフレームワークの内部的な動作が標準の実装をカスタマイズおよび実装するためのいくつかの手法を学習する方法の有益な情報を提供コマンドのハンドラーを独自にします。  
  
## <a name="contents-of-this-technical-note"></a>このテクニカル ノートの内容  
 それぞれのコマンド ID は 2 つのセクションで説明します。  
  
-   タイトル: コマンド ID のシンボリック名 (たとえば、 **ID_FILE_SAVE**) (たとえば、「現在のドキュメントを保存する」など)、コロンで区切られたコマンドの目的で後にします。  
  
-   コマンド、および既定の実装では、どのようなクラスを記述する 1 つまたは複数の段落を実装します。  
  
 フレームワークの基本クラスのメッセージ マップには、ほとんどの既定のコマンドの実装が既に結び付けられています。 派生クラスで明示的に結び付けるを必要とするいくつかのコマンドの実装があります。 これらは、「注」の下で説明します。 AppWizard で適切なオプションを選択した場合は、生成された、スケルトン アプリケーションでのこれらの既定のハンドラーが接続されます。  
  
## <a name="naming-convention"></a>名前付け規約  
 標準のコマンドでは、可能な場合に使用することをお勧めする単純な名前付け規則に従います。 ほとんどの標準のコマンドは、アプリケーションのメニュー バーで標準的な場所に配置されます。 コマンドのシンボリック名は、「id _」は標準のポップアップ メニュー名のメニュー項目の名前で後に続くを開始します。 シンボリック名がアンダー スコアの単語区切りを大文字に変換します。 標準メニュー項目名がないコマンド、コマンドの論理名が定義されて id「_」で始まる (たとえば、 **ID_NEXT_PANE**)。  
  
 プレフィックス「id _」を使用すると、メニュー項目、ツール バー ボタン、またはその他のユーザー インターフェイス オブジェクトをコマンドにバインドするのによう設計されているコマンドを表します。 Id「_」のコマンドの処理コマンド ハンドラーを使用する必要があります、`ON_COMMAND`と`ON_UPDATE_COMMAND_UI`コマンド アーキテクチャを MFC のメカニズムです。  
  
 せずにコマンド アーキテクチャに準拠してメニュー固有のコードを有効にして、それらを無効にする必要があるメニュー項目に標準の「idm _」プレフィックスを使用することをお勧めします。 もちろん] メニューの [特定のコマンドの数を小さい MFC コマンド アーキテクチャを次により (ツールバーを使用) してから、コマンド ハンドラーのより強力なだけでなく、コマンド ハンドラー コードを再使用ためにがあります。  
  
## <a name="id-ranges"></a>ID の範囲  
 参照してください[テクニカル ノート 20](../mfc/tn020-id-naming-and-numbering-conventions.md) MFC 内の ID 範囲の使用の詳細についてはします。  
  
 MFC の標準のコマンドは、0 xefff に 0xE000 の範囲内で分類されます。 依存しないでください、これらの Id の特定の値に、ライブラリの将来のバージョンで変更される可能性があるためです。  
  
 アプリケーションは 0x8000 ~ 0 xdfff の範囲内でそのコマンドを定義する必要があります。  
  
## <a name="standard-command-ids"></a>標準コマンド Id  
 コマンド id ごとに、ファイルの確認ダイアログで使用されている標準的なメッセージ行のプロンプト文字列があります。RC します。 メニュー プロンプトの文字列 ID は、コマンド ID の場合と同様である必要があります。  
  
-   ID_FILE_NEW では、新しい/空のドキュメントを作成します。  
  
    > [!NOTE]
    >  これを接続する必要があります、 `CWinApp`-この機能を有効にするクラスのメッセージ マップを派生します。  
  
     `CWinApp::OnFileNew`アプリケーションのドキュメント テンプレートの数に応じて異なる方法でこのコマンドを実装します。 1 つだけを使用する必要がある場合`CDocTemplate`、 `CWinApp::OnFileNew` 、その種類だけでなく、適切なフレームとビュー クラスの新しいドキュメントを作成します。  
  
     1 つ以上を使用する必要がある場合`CDocTemplate`、`CWinApp::OnFileNew`ダイアログ ボックスでユーザーを促します (**AFX_IDD_NEWTYPEDLG**) を使用するどのドキュメントの種類を選択できるようにすることです。 選択した`CDocTemplate`ドキュメントを作成するために使用します。  
  
     1 つの一般的なカスタマイズ`ID_FILE_NEW`別およびドキュメントの種類をグラフィカルに選択を提供することです。 ここで実装できます独自**CMyApp::OnFileNew**の代わりに、メッセージ マップに配置および`CWinApp::OnFileNew`です。 基本クラス実装を呼び出す必要はありません。  
  
     別の一般的なカスタマイズ`ID_FILE_NEW`各タイプのドキュメントを作成するため、個々 のコマンドを提供することです。 ここで新しいコマンド Id、ID_FILE_NEW_CHART と ID_FILE_NEW_SHEET などを定義する必要があります。  
  
-   ID_FILE_OPEN では、既存のドキュメントが開きます。  
  
    > [!NOTE]
    >  これを接続する必要があります、 `CWinApp`-この機能を有効にするクラスのメッセージ マップを派生します。  
  
     `CWinApp::OnFileOpen`呼び出し元の非常に単純な実装を持つ**CWinApp::DoPromptFileName**続く`CWinApp::OpenDocumentFile`に開かれるファイルのファイルまたはパスの名前に置き換えます。 `CWinApp`実装ルーチン**DoPromptFileName**標準 FileOpen ダイアログを表示し、現在のドキュメント テンプレートから取得したファイル拡張子で塗りつぶします。  
  
     1 つの一般的なカスタマイズ`ID_FILE_OPEN`を開く ダイアログ ボックスをカスタマイズまたは追加のファイルのフィルターを追加します。 これをカスタマイズすることをお勧めを開く ダイアログ ボックス、および呼び出しと既定の実装を置き換える`CWinApp::OpenDocumentFile`ドキュメントのファイル名またはパス名にします。 基本クラスを呼び出す必要はありません。  
  
-   ID_FILE_CLOSE は、現在開いているドキュメントを閉じます。  
  
     **CDocument::OnFileClose**呼び出し`CDocument::SaveModified`を呼び出してが変更された場合は、ドキュメントを保存するユーザー入力を求める`OnCloseDocument`です。 行われるすべての終了ロジックで、ドキュメントの破棄を含む、`OnCloseDocument`ルーチンです。  
  
    > [!NOTE]
    >  **ID_FILE_CLOSE**から異なる方法では、機能、`WM_CLOSE`メッセージまたは**SC_CLOSE**ドキュメント フレーム ウィンドウに送信されるシステム コマンド。 ウィンドウを閉じると、最後のフレーム ウィンドウ、ドキュメントを表示する場合にのみ、ドキュメントが閉じられます。 使用してドキュメントを閉じる**ID_FILE_CLOSE**のみ閉じませんドキュメントが閉じられるすべてのフレーム ウィンドウ、ドキュメントを表示します。  
  
-   まずは、現在のドキュメントを保存します。  
  
     実装では、ヘルパー ルーチンを使用して**コマンドで**の両方で使用されている**OnFileSave**と**する**です。 前に保存されていない、ドキュメントを保存するかどうか (つまりがないパス名では、という名前の場合は、)、読み取り専用のドキュメントから読み込まれたか、 **OnFileSave**ロジックのように機能、 **ID_FILE_SAVE_AS**コマンドを新しいファイル名を指定するユーザーに確認します。 仮想関数を通じたファイルを開くと、保存を行って実際の処理が行われます`OnSaveDocument`です。  
  
     カスタマイズする一般的な理由は 2 つ**ID_FILE_SAVE**です。 ドキュメントを保存しないには、単純に削除、 **ID_FILE_SAVE**メニュー項目と、ユーザー インターフェイスからツール バー ボタンです。 また、ドキュメントをダーティしないことを確認 (つまり、呼び出すことはありません`CDocument::SetModifiedFlag`) フレームワークは、ドキュメントを保存するが発生することはありません。 ディスク ファイル以外の任意の場所に保存するドキュメントでは、その操作用の新しいコマンドを定義します。  
  
     場合、 `COleServerDoc`、 **ID_FILE_SAVE**ファイルを保存 (通常のドキュメント) およびファイルの更新 (埋め込まれたドキュメント) の両方に使用されます。  
  
     ドキュメント データがディスク ファイルに格納されているが、既定値を使用しない場合**CDocument**実装をシリアル化、オーバーライドする必要があります`CDocument::OnSaveDocument`の代わりに**OnFileSave**です。  
  
-   ID_FILE_SAVE_AS は、別のファイル名の下にある現在のドキュメントを保存します。  
  
     **CDocument::OnFileSaveAs**実装を使用して同じ**コマンドで**としてヘルパー ルーチン**OnFileSave**です。 **する**と同様にコマンドが処理された**ID_FILE_SAVE**ドキュメントには、保存する前にファイル名があるない場合。 **COleServerDoc::OnFileSaveAs**別個のファイルとして他のアプリケーションに埋め込まれている OLE オブジェクトを表すサーバー ドキュメントを保存するか、標準の文書のデータ ファイルを保存するロジックを実装します。  
  
     ロジックをカスタマイズする場合は**ID_FILE_SAVE**、カスタマイズすることはおそらく**ID_FILE_SAVE_AS**同様または名前を付けての操作では、ドキュメントには適用されません可能性があります。 不要な場合は、メニュー バーからメニュー項目を削除できます。  
  
-   ID_FILE_SAVE_COPY_AS は、新しい名前でコピー現在のドキュメントを保存します。  
  
     **COleServerDoc::OnFileSaveCopyAs**実装は非常に**CDocument::OnFileSaveAs**ドキュメント オブジェクト"にアタッチされていない"基になるファイルの保存後にする点を除いて、します。 つまり、メモリ内のドキュメントは、保存する前に"modified"が場合に、まだ"modified"です。 さらに、このコマンドでは、パス名またはドキュメントに保存されているタイトルには影響はありません。  
  
-   ID_FILE_UPDATE では、埋め込まれたドキュメントを保存するコンテナーに通知します。  
  
     `COleServerDoc::OnUpdateDocument`実装 notifiies 埋め込みを保存するか、コンテナーだけです。 コンテナーは、埋め込みオブジェクトを保存するために、適切な OLE Api を呼び出します。  
  
-   ID_FILE_PAGE_SETUP は、アプリケーション固有のページ セットアップ/レイアウト ダイアログを起動します。  
  
     現在、このダイアログの標準はなく、フレームワークには、このコマンドの既定の実装がありません。  
  
     このコマンドを実装する場合は、使用をお勧めするこのコマンドの id。  
  
-   ID_FILE_PRINT_SETUP は、標準的な印刷設定 ダイアログ ボックスを呼び出します。  
  
    > [!NOTE]
    >  これを接続する必要があります、 `CWinApp`-この機能を有効にするクラスのメッセージ マップを派生します。  
  
     このコマンドは、プリンターをカスタマイズし、印刷の設定には、少なくともユーザーができる標準の印刷設定 ダイアログを起動します。 このドキュメントまたはこのアプリケーションでドキュメントの最大すべてです。 コントロール パネルを使用して、システム全体の既定のプリンター設定を変更する必要があります。  
  
     `CWinApp::OnFilePrintSetup`非常に単純な実装を作成する、`CPrintDialog`オブジェクトと呼び出し元、**高める**関数を実装します。 これは、アプリケーションの既定のプリンター設定を設定します。  
  
     このコマンドをカスタマイズするための一般的な必要性は、ドキュメントの保存時に保存するか、ドキュメントごとプリンター設定できるようにするのにです。 これを行うには、メッセージ マップのハンドラーを追加する必要があります、 **CDocument**を作成するクラス、`CPrintDialog`オブジェクト、適切なプリンターの属性を持つ初期化 (通常**hDevMode**と**と**)、呼び出す、 **CPrintDialog::DoModal、**し、変更されたプリンターの設定を保存します。 堅牢に実装する必要があります見ての実装**高める**エラーを検出するのと**CWinApp::UpdatePrinterSelection**実用的な既定値を処理するため、システム全体のプリンターの変更を追跡します。  
  
-   現在のドキュメントの ID_FILE_PRINT 標準の印刷  
  
    > [!NOTE]
    >  これを接続する必要があります、 `CView`-この機能を有効にするクラスのメッセージ マップを派生します。  
  
     このコマンドは、現在のドキュメントを印刷したりより正確に、標準的な印刷ダイアログ ボックスを呼び出す、印刷、エンジンを実行する、印刷プロセスを起動します。  
  
     **CView::OnFilePrint**次のコマンドとメインの印刷ループを実装します。 仮想呼び出し`CView::OnPreparePrinting`印刷ダイアログ ボックスを持つユーザーのプロンプトにします。 プリンターへの出力を DC の準備、印刷の進行状況ダイアログを表示し (**AFX_IDD_PRINTDLG**)、し、送信、`StartDoc`をプリンターにエスケープします。 **CView::OnFilePrint**も、メイン ページ指向印刷ループが含まれています。 仮想呼び出し、各ページの`CView::OnPrepareDC`続けて、`StartPage`のエスケープと仮想呼び出し`CView::OnPrint`そのページに対してです。 完了したとき、仮想`CView::OnEndPrinting`が呼び出されると、印刷の進行状況ダイアログは閉じられます。  
  
     MFC の印刷のアーキテクチャは、印刷と印刷プレビューのさまざまな方法でフックするために設計されています。 通常どおり表示されます、さまざまな`CView`オーバーライド可能な関数の任意のページ指向の印刷タスクに適しています。 置換する必要がありますの非ページ指向の出力のプリンターを使用するアプリケーションの場合にのみ、 **ID_FILE_PRINT**実装します。  
  
-   ID_FILE_PRINT_PREVIEW 印刷プレビュー モードを開始、現在のドキュメントのです。  
  
    > [!NOTE]
    >  これを接続する必要があります、 `CView`-この機能を有効にするクラスのメッセージ マップを派生します。  
  
     **CView::OnFilePrintPreview**を文書化されたヘルパー関数を呼び出して印刷プレビュー モードを開始**CView::DoPrintPreview**です。 **CView::DoPrintPreview**と同様、印刷プレビュー ループのメインのエンジンは、 **OnFilePrint**印刷ループのメインのエンジンです。  
  
     他のパラメーターを渡すことによって、印刷プレビュー操作のさまざまな方法でカスタマイズできます**呼び出す**です。 参照してください[テクニカル ノート 30:](../mfc/tn030-customizing-printing-and-print-preview.md)、印刷プレビューの詳細の一部を説明するおよびそれをカスタマイズする方法です。  
  
-   **ID_FILE_MRU_FILE1**しています.**FILE16**ファイル MRU のコマンド Id の範囲`list`です。  
  
     **CWinApp::OnUpdateRecentFileMenu**更新コマンド UI ハンドラーの高度な用途の 1 つであるは、`ON_UPDATE_COMMAND_UI`メカニズムです。 メニュー リソースを ID を持つ 1 つのメニュー項目を定義する必要がありますのみ**ID_FILE_MRU_FILE1**です。 メニュー項目が最初に無効のままです。  
  
     MRU 一覧につれて、複数のメニュー項目が一覧に追加されます。 標準`CWinApp`実装の既定値は 4 つの最近使用したファイルの標準的な制限です。 既定値を変更するには呼び出すことによって`CWinApp::LoadStdProfileSettings`大きくまたは小さく値を使用します。 MRU 一覧は、アプリケーションに格納されます。INI ファイルです。 アプリケーションの一覧が読み込まれる`InitInstance`関数を呼び出す場合`LoadStdProfileSettings`と、アプリケーションの終了時に保存されます。 また MRU 更新コマンド UI ハンドラーは、[ファイル] メニューの表示の相対パスに絶対パスが変換されます。  
  
     **CWinApp::OnOpenRecentFile**は、`ON_COMMAND`実際のコマンドを実行するハンドラー。 MRU 一覧および呼び出しからファイル名を取得するだけ`CWinApp::OpenDocumentFile`ファイルを開くと、MRU 一覧の更新のすべての作業はどのです。  
  
     このコマンド ハンドラーのカスタマイズは推奨されません。  
  
-   ID_EDIT_CLEAR が現在の選択を解除します。  
  
     現在このコマンドの標準の実装ではありません。 それぞれにこれを実装する必要があります`CView`-クラスを派生します。  
  
     `CEditView`使用してこのコマンドの実装を提供`CEdit::Clear`です。 現在選択されていない場合は、コマンドが無効です。  
  
     このコマンドを実装する場合は、使用をお勧めするこのコマンドの id。  
  
-   ID_EDIT_CLEAR_ALL では、ドキュメント全体を消去します。  
  
     現在このコマンドの標準の実装ではありません。 それぞれにこれを実装する必要があります`CView`-クラスを派生します。  
  
     このコマンドを実装する場合は、使用をお勧めするこのコマンドの id。 MFC のチュートリアルのサンプルを参照して[SCRIBBLE](../visual-cpp-samples.md)実装例についてはします。  
  
-   ID_EDIT_COPY は、現在の選択範囲をクリップボードにコピーします。  
  
     現在このコマンドの標準の実装ではありません。 それぞれにこれを実装する必要があります`CView`-クラスを派生します。  
  
     `CEditView`このコマンドは、現在選択されているテキストをされているテキストを使用してとしてクリップボードにコピーの実装を提供`CEdit::Copy`です。 現在選択されていない場合は、コマンドが無効です。  
  
     このコマンドを実装する場合は、使用をお勧めするこのコマンドの id。  
  
-   ID_EDIT_CUT をクリップボードに現在の選択項目を切り取ります。  
  
     現在このコマンドの標準の実装ではありません。 それぞれにこれを実装する必要があります`CView`-クラスを派生します。  
  
     `CEditView`現在選択されているテキストを切り取り、クリップボードされているテキストを使用すると、このコマンドの実装を提供`CEdit::Cut`です。 現在選択されていない場合は、コマンドが無効です。  
  
     このコマンドを実装する場合は、使用をお勧めするこのコマンドの id。  
  
-   ID_EDIT_FIND 開始検索操作は、モードレスの検索 ダイアログ ボックスが表示されます。  
  
     現在このコマンドの標準の実装ではありません。 それぞれにこれを実装する必要があります`CView`-クラスを派生します。  
  
     `CEditView`このコマンドは、実装のヘルパー関数の実装を提供**OnEditFindReplace**を使用し、プライベート変数に、以前の検索と置換設定を格納します。 `CFindReplaceDialog`クラスは、ユーザー入力を求めるのモードレス ダイアログの管理に使用します。  
  
     このコマンドを実装する場合は、使用をお勧めするこのコマンドの id。  
  
-   ID_EDIT_PASTE は、現在のクリップボードの内容を挿入します。  
  
     現在このコマンドの標準の実装ではありません。 それぞれにこれを実装する必要があります`CView`-クラスを派生します。  
  
     `CEditView`このコマンドを使用して、選択したテキストを置き換える現在クリップボード データのコピーの実装を提供`CEdit::Paste`です。 ある場合、コマンドが無効になっているありません**エディット**をクリップボードにします。  
  
     **COleClientDoc**このコマンドの更新コマンド UI ハンドラーを提供するだけです。 クリップボードに埋め込み OLE アイテム/オブジェクトが含まれていない場合は、コマンドは無効になります。 実際に貼り付けを行うには実際のコマンドのハンドラーの作成を担当しています。 OLE アプリケーションでは、その他の形式を貼り付けることも場合、は、ビューまたはドキュメントでは、独自更新コマンド UI ハンドラーを指定する必要があります (つまり、どこかにする前に**COleClientDoc**コマンド ターゲットのルーティングで)。  
  
     このコマンドを実装する場合は、使用をお勧めするこのコマンドの id。  
  
     OLE の標準実装を置換するを使用して`COleClientItem::CanPaste`です。  
  
-   ID_EDIT_PASTE_LINK は、現在のクリップボードの内容からのリンクを挿入します。  
  
     現在このコマンドの標準の実装ではありません。 それぞれにこれを実装する必要があります`CView`-クラスを派生します。  
  
     `COleDocument`だけこのコマンドの更新コマンド UI ハンドラーを提供します。 クリップボードにリンク可能な OLE アイテム/オブジェクトが含まれていない場合は、コマンドは無効になります。 実際に貼り付けを行うには実際のコマンドのハンドラーの作成を担当しています。 OLE アプリケーションでは、その他の形式を貼り付けることも場合、は、ビューまたはドキュメントでは、独自更新コマンド UI ハンドラーを指定する必要があります (つまり、どこかにする前に`COleDocument`コマンド ターゲットのルーティングで)。  
  
     このコマンドを実装する場合は、使用をお勧めするこのコマンドの id。  
  
     OLE の標準実装を置換するを使用して`COleClientItem::CanPasteLink`です。  
  
-   ID_EDIT_PASTE_SPECIAL は、オプションの現在のクリップボードの内容を挿入します。  
  
     現在このコマンドの標準の実装ではありません。 それぞれにこれを実装する必要があります`CView`-クラスを派生します。 MFC では、このダイアログ ボックスは提供されません。  
  
     このコマンドを実装する場合は、使用をお勧めするこのコマンドの id。  
  
-   ID_EDIT_REPEAT には、最後の操作が繰り返されます。  
  
     現在このコマンドの標準の実装ではありません。 それぞれにこれを実装する必要があります`CView`-クラスを派生します。  
  
     `CEditView`最後の検索操作を繰り返し実行するには、このコマンドの実装を提供します。 最後の検索のプライベート変数が使用されます。 指定して検索を試行できない場合は、コマンドが無効です。  
  
     このコマンドを実装する場合は、使用をお勧めするこのコマンドの id。  
  
-   ID_EDIT_REPLACE 開始置換操作は、モードレスの置換 ダイアログが表示されます。  
  
     現在このコマンドの標準の実装ではありません。 それぞれにこれを実装する必要があります`CView`-クラスを派生します。  
  
     `CEditView`このコマンドは、実装のヘルパー関数の実装を提供**OnEditFindReplace**を使用し、プライベート変数に、以前の検索と置換設定を格納します。 `CFindReplaceDialog`を求めるメッセージがモードレスのダイアログを管理するクラスを使用します。  
  
     このコマンドを実装する場合は、使用をお勧めするこのコマンドの id。  
  
-   ID_EDIT_SELECT_ALL では、ドキュメント全体を選択します。  
  
     現在このコマンドの標準の実装ではありません。 それぞれにこれを実装する必要があります`CView`-クラスを派生します。  
  
     `CEditView`このコマンドは、ドキュメント内のすべてのテキストの選択の実装を提供します。 テキストを選択が存在しない場合は、コマンドが無効です。  
  
     このコマンドを実装する場合は、使用をお勧めするこのコマンドの id。  
  
-   ID_EDIT_UNDO には、最後の操作が元に戻します。  
  
     現在このコマンドの標準の実装ではありません。 それぞれにこれを実装する必要があります`CView`-クラスを派生します。  
  
     `CEditView`この実装を提供コマンドを使用して`CEdit::Undo`です。 場合、コマンドが無効になっている`CEdit::CanUndo`FALSE を返します。  
  
     このコマンドを実装する場合は、使用をお勧めするこのコマンドの id。  
  
-   ID_EDIT_REDO は、最後の操作をやり直します。  
  
     現在このコマンドの標準の実装ではありません。 それぞれにこれを実装する必要があります`CView`-クラスを派生します。  
  
     このコマンドを実装する場合は、使用をお勧めするこのコマンドの id。  
  
-   ID_WINDOW_NEW では、アクティブなドキュメントで別のウィンドウが開きます。  
  
     **CMDIFrameWnd::OnWindowNew**を現在のドキュメントの別のビューを含む別のフレームを作成する現在のドキュメントのドキュメント テンプレートを使用してこの強力な機能を実装します。  
  
     複数ドキュメント インターフェイス (MDI) のウィンドウ メニュー、ほとんどのコマンドと同様には、アクティブな MDI 子ウィンドウがない場合、コマンドは無効です。  
  
     このコマンド ハンドラーのカスタマイズは推奨されません。 その他のビューまたはフレーム ウィンドウを作成するコマンドを提供する場合は、独自のコマンドを開発することをお勧めします。 コードを複製する**CMDIFrameWnd::OnWindowNew**好みは、特定のフレームとビューの次のクラスに変更します。  
  
-   MDI ウィンドウの下部にアイコンを ID_WINDOW_ARRANGE を整列します。  
  
     `CMDIFrameWnd`実装のヘルパー関数でこの標準 MDI コマンドを実装して**OnMDIWindowCmd**です。 このヘルパーでは、コマンド Id を MDI ウィンドウのメッセージにマップされ、大量のコードを共有できるためです。  
  
     MDI ウィンドウ メニューのほとんどのコマンドと同様には、アクティブな MDI 子ウィンドウがない場合、コマンドは無効です。  
  
     このコマンド ハンドラーのカスタマイズは推奨されません。  
  
-   重なるように windows を ID_WINDOW_CASCADE 連鎖します。  
  
     `CMDIFrameWnd`実装のヘルパー関数でこの標準 MDI コマンドを実装して**OnMDIWindowCmd**です。 このヘルパーでは、コマンド Id を MDI ウィンドウのメッセージにマップされ、大量のコードを共有できるためです。  
  
     MDI ウィンドウ メニューのほとんどのコマンドと同様には、アクティブな MDI 子ウィンドウがない場合、コマンドは無効です。  
  
     このコマンド ハンドラーのカスタマイズは推奨されません。  
  
-   ID_WINDOW_TILE_HORZ タイル windows 水平方向にします。  
  
     このコマンドは`CMDIFrameWnd`と同じように**ID_WINDOW_CASCADE**操作のさまざまな MDI ウィンドウ メッセージを使用する以外、します。  
  
     アプリケーションの既定のタイルの向きを選択する必要があります。 いずれかに、ウィンドウの「並べて表示」メニュー項目の ID を変更することによってこれを行う**ID_WINDOW_TILE_HORZ**または**ID_WINDOW_TILE_VERT**です。  
  
-   ID_WINDOW_TILE_VERT タイル windows 垂直方向にします。  
  
     このコマンドは`CMDIFrameWnd`と同じように**ID_WINDOW_CASCADE**操作のさまざまな MDI ウィンドウ メッセージを使用する以外、します。  
  
     アプリケーションの既定のタイルの向きを選択する必要があります。 いずれかに、ウィンドウの「並べて表示」メニュー項目の ID を変更することによってこれを行う**ID_WINDOW_TILE_HORZ**または**ID_WINDOW_TILE_VERT**です。  
  
-   スプリッターを ID_WINDOW_SPLIT キーボード インターフェイスです。  
  
     `CView`このコマンドは、処理、`CSplitterWnd`実装します。 このコマンドは実装の機能を委任されているビューが分割ウィンドウの一部である場合は、`CSplitterWnd::DoKeyboardSplit`です。 これにより、スプリッターが利用できるキーボード分割分割ウィンドウの分割を解除するモードに配置されます。  
  
     このコマンドは、ビューが分割ウィンドウ内にない場合は無効です。  
  
     このコマンド ハンドラーのカスタマイズは推奨されません。  
  
-   ID_APP_ABOUT では、バージョン情報 ダイアログ ボックスを呼び出します。  
  
     アプリケーションについてボックスの標準の実装はありません。 既定 AppWizard で作成したアプリケーション、アプリケーションのカスタム ダイアログ クラスが作成され、についてボックスとして使用します。 AppWizard では、このコマンドを処理し、ダイアログを起動する単純なコマンド ハンドラーも書き込みます。  
  
     ほとんどの場合、このコマンドを実装します。  
  
-   ID_APP_EXIT は、アプリケーションを終了します。  
  
     **CWinApp::OnAppExit**送信することでこのコマンドを処理する、`WM_CLOSE`メッセージをアプリケーションのメイン ウィンドウにします。 標準の (の入力を求めてダーティ ファイルなど)、アプリケーションのシャット ダウンがによって処理される、`CFrameWnd`実装します。  
  
     このコマンド ハンドラーのカスタマイズは推奨されません。 オーバーライドする`CWinApp::SaveAllModified`または`CFrameWnd`クロージング ロジックをお勧めします。  
  
     このコマンドを実装する場合は、使用をお勧めするこのコマンドの id。  
  
-   ID_HELP_INDEX 一覧のヘルプから。HLP ファイルです。  
  
    > [!NOTE]
    >  これを接続する必要があります、 `CWinApp`-この機能を有効にするクラスのメッセージ マップを派生します。  
  
     `CWinApp::OnHelpIndex`このコマンドを簡単に呼び出すことによって処理`CWinApp::WinHelp`です。  
  
     このコマンド ハンドラーのカスタマイズは推奨されません。  
  
-   ヘルプを使用する方法のヘルプ ID_HELP_USING 表示します。  
  
    > [!NOTE]
    >  これを接続する必要があります、 `CWinApp`-この機能を有効にするクラスのメッセージ マップを派生します。  
  
     `CWinApp::OnHelpUsing`このコマンドを簡単に呼び出すことによって処理`CWinApp::WinHelp`です。  
  
     このコマンド ハンドラーのカスタマイズは推奨されません。  
  
-   ID_CONTEXT_HELP 入力 shift キーを押しながら F1 ヘルプ モードです。  
  
    > [!NOTE]
    >  これを接続する必要があります、 `CWinApp`-この機能を有効にするクラスのメッセージ マップを派生します。  
  
     `CWinApp::OnContextHelp`ヘルプ モードのカーソルを設定、モーダル ループを入力し、ユーザーに関するヘルプを表示するウィンドウを選択するを待って、このコマンドを処理します。 参照してください[テクニカル ノート 28:](../mfc/tn028-context-sensitive-help-support.md) MFC のヘルプの実装の詳細についてはします。  
  
     このコマンド ハンドラーのカスタマイズは推奨されません。  
  
-   現在のコンテキストに Id_help ヘルプ  
  
    > [!NOTE]
    >  これを接続する必要があります、 `CWinApp`-この機能を有効にするクラスのメッセージ マップを派生します。  
  
     `CWinApp::OnHelp`現在のアプリケーション コンテキストのヘルプ コンテキストを取得することによって、このコマンドを処理します。 F1 ヘルプの単純な処理は、メッセージ ボックスなどです。 参照してください[テクニカル ノート 28:](../mfc/tn028-context-sensitive-help-support.md) MFC の詳細については、実装をヘルプ参照します。  
  
     このコマンド ハンドラーのカスタマイズは推奨されません。  
  
-   コンテキストの既定のヘルプを ID_DEFAULT_HELP 表示  
  
    > [!NOTE]
    >  これを接続する必要があります、 `CWinApp`-この機能を有効にするクラスのメッセージ マップを派生します。  
  
     このコマンドは、通常`CWinApp::OnHelpIndex`です。  
  
     既定のヘルプとヘルプのキーワードを区別が必要な場合、別のコマンド ハンドラーを指定できます。  
  
-   ID_NEXT_PANE は次のペインに移動  
  
     `CView`このコマンドは、処理、`CSplitterWnd`実装します。 このコマンドは実装の機能を委任されているビューが分割ウィンドウの一部である場合は、 **CSplitterWnd::OnNextPaneCmd**です。 これにより、アクティブなビューが分割ウィンドウの次のペインに移動されます。  
  
     分割ウィンドウで、ビューがまたはに移動する次のペインがない場合は、このコマンドが無効です。  
  
     このコマンド ハンドラーのカスタマイズは推奨されません。  
  
-   ID_PREV_PANE は前のペインに移動  
  
     `CView`このコマンドは、処理、`CSplitterWnd`実装します。 このコマンドは実装の機能を委任されているビューが分割ウィンドウの一部である場合は、 **CSplitterWnd::OnNextPaneCmd**です。 これにより、アクティブなビューが分割ウィンドウの前のペインに移動されます。  
  
     分割ウィンドウで、ビューがまたはに移動する前のペインがない場合は、このコマンドが無効です。  
  
     このコマンド ハンドラーのカスタマイズは推奨されません。  
  
-   ID_OLE_INSERT_NEW 新しい OLE オブジェクトを挿入します。  
  
     現在このコマンドの標準の実装ではありません。 これを実装する必要があります、 `CView`-現在の選択範囲に新しい OLE アイテム/オブジェクトを挿入するクラスを派生します。  
  
     OLE のすべてのクライアント アプリケーションは、このコマンドを実装する必要があります。 AppWizard、オプションでは、OLE はスケルトンの実装を作成**OnInsertObject**を完了する必要があるビュー クラスにします。  
  
     MFC OLE サンプルを参照して[OCLIENT](../visual-cpp-samples.md)の例を次のコマンドを完全に実装します。  
  
-   ID_OLE_EDIT_LINKS 編集リンク  
  
     `COleDocument`標準の OLE へのリンク ダイアログの MFC に用意されている実装を使用してこのコマンドを処理します。 このダイアログ ボックスの実装は、`COleLinksDialog`クラスです。 現在のドキュメントにリンクが含まれていない場合、コマンドは無効です。  
  
     このコマンド ハンドラーのカスタマイズは推奨されません。  
  
-   ID_OLE_VERB_FIRST しています.OLE の動詞の最後の ID 範囲  
  
     `COleDocument`現在選択されている OLE 項目/オブジェクトでサポートされている動詞にこのコマンドの ID 範囲を使用します。 指定した OLE 項目/オブジェクトの種類は、0 個以上のカスタム動詞をサポートできるので、範囲があります。 アプリケーションのメニューには、1 つのメニュー項目の ID を持つをが**ID_OLE_VERB_FIRST**です。 プログラムを実行すると、メニューは、適切なメニュー動詞の説明 (または多くの動詞でポップアップ メニュー) で更新されます。 OLE のメニューの管理がによって処理される`AfxOleSetEditMenu`、このコマンドの更新コマンド UI ハンドラーで元に戻す。  
  
     この範囲内のコマンド ID のそれぞれを処理するための明示的なコマンド ハンドラーはありません。 **COleDocument::OnCmdMsg**をオーバーライドすることで、この範囲内のすべてのコマンド Id をトラップして、動詞の 0 から始まる数値に変換し、その動詞のサーバーを起動 (を使用して`COleClientItem::DoVerb`)。  
  
     カスタマイズまたはこのコマンドの ID 範囲の他の使用は推奨されません。  
  
-   ID_VIEW_TOOLBAR オンとオフをツールバーを切り替え  
  
     `CFrameWnd`ツールバーの表示状態を切り替えるには、このコマンドおよび更新コマンド UI ハンドラーを処理します。 ツールバーの子ウィンドウ ID とフレームの子ウィンドウである必要があります`AFX_IDW_TOOLBAR`です。 コマンド ハンドラーは、実際にツールバー ウィンドウの表示を切り替えます。 `CFrameWnd::RecalcLayout`新しい状態で、ツールバーで、フレーム ウィンドウを再描画に使用されます。 更新コマンド UI ハンドラーは、ツールバーが表示されるメニュー項目を確認します。  
  
     このコマンド ハンドラーのカスタマイズは推奨されません。 ツールバーを追加したい場合は、複製し、コマンド ハンドラーと、このコマンドの更新コマンド UI ハンドラーを変更するがします。  
  
-   ID_VIEW_STATUS_BAR がオンとオフ、ステータス バーを切り替えます  
  
     このコマンドは実装されて`CFrameWnd`と同じように**ID_VIEW_TOOLBAR**、他の子ウィンドウ ID を除く (**AFX_IDW_STATUS_BAR**) を使用します。  
  
## <a name="update-only-command-handlers"></a>更新専用のコマンド ハンドラー  
 いくつかの標準コマンド Id は、ステータス バーのインジケーターとして使用されます。 これらと同じ更新コマンド UI を使用して処理メカニズム アプリケーションのアイドル時間中に、現在の状態を表示します。 ユーザーが選択できないため (つまり、ステータス バー ペインをプッシュできません、) に意味がないし、`ON_COMMAND`のハンドラーをこれらのコマンド Id。  
  
-   **ID_INDICATOR_CAPS** : CAP ロック インジケーター。  
  
-   **ID_INDICATOR_NUM** : NUM lock インジケーター。  
  
-   **ID_INDICATOR_SCRL** : SCRL ロック インジケーター。  
  
-   **ID_INDICATOR_KANA** : かなロック インジケーター (日本語のシステムにのみ適用されます)。  
  
 これらの 3 つすべてがで実装された**すべて**、コマンド ID を使用して、適切な仮想キーにマップする実装ヘルパー。 一般的な実装を有効または無効になります (無効になっているウィンドウの状態 = なしテキスト)、`CCmdUI`仮想キーが現在ロックされているかどうかに依存するオブジェクト。  
  
 このコマンド ハンドラーのカスタマイズは推奨されません。  
  
-   **ID_INDICATOR_EXT: EXT**インジケーターの選択が終了します。  
  
-   **ID_INDICATOR_OVR: について**e**R**インジケーターを取る。  
  
-   **ID_INDICATOR_REC: REC**ording インジケーター。  
  
 現在これらのインジケーターの標準の実装ではありません。  
  
 これらのインジケーターを実装する場合は、使用をお勧めするこれらのインジケーターの Id と、ステータス バー内のインジケーターの順序を維持する (つまり、この順序で: EXT、CAP、NUM、SCRL、上書、推奨値)。  
  
## <a name="see-also"></a>参照  
 [番号順テクニカル ノート](../mfc/technical-notes-by-number.md)   
 [カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
