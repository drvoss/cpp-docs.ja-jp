---
title: Visual C++ プロジェクトの種類
ms.date: 10/30/2017
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- Visual C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
ms.openlocfilehash: 456fdb5ec2025b3085332eced3a0c7f33e117918
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658017"
---
# <a name="visual-c-project-types"></a>Visual C++ プロジェクトの種類

プロジェクト テンプレートを使用して、基本的なプログラムの構造、メニュー、ツール バー、アイコン、参照、および作成するプロジェクトの種類に適した `#include` ステートメントを作成できます。 Visual Studio には、数種類の Visual C++ プロジェクト テンプレートが含まれ、これらのテンプレートの多くにはウィザードが用意されているため、プロジェクトを作成しながらカスタマイズを行うことができます。 プロジェクトを作成したらすぐにプロジェクトをビルドし、アプリケーションを実行できます。アプリケーションを開発しながら、断続的にビルドすることをお勧めします。

プロジェクトの作成にテンプレートを使用する必要はありませんが、多くの場合、テンプレートを使用した方が効率的です。用意されたプロジェクト ファイルおよび構造を修正する方が、初めから作成するよりも簡単なためです。

> [!NOTE]
> C++ プロジェクト テンプレートを使用して C 言語プロジェクトを作成できます。 生成されたプロジェクトで、.cpp ファイル名拡張子を持つファイルを検索して .c に変更します。 次に、プロジェクト (ソリューションではない) の **[プロジェクトのプロパティ]** ページで、 **[構成プロパティ]**、 **[C/C++]** の順に展開し、 **[詳細]** を選択します。 **[コンパイル言語の選択]** 設定を **[C コードとしてコンパイル (/TC)]** に変更します。

## <a name="project-templates"></a>プロジェクト テンプレート

Visual Studio に含まれるプロジェクト テンプレートは、製品のバージョンとインストールされているワークロードによって異なります。 C++ によるデスクトップ開発ワークロードをインストールした場合、Visual Studio には次の Visual C++ プロジェクト テンプレートが含まれます。

### <a name="windows-desktop"></a>Windows デスクトップ

|プロジェクト テンプレート|説明|
|----------------------|-----------------------------|
|[Windows コンソール アプリケーション](../windows/creating-a-console-application.md)|Windows コンソール アプリケーションを作成するためのプロジェクトです。|
|[Windows デスクトップ アプリケーション](../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|Windows デスクトップ (Win32) アプリケーションを作成するためのプロジェクトです。|
|[ダイナミック リンク ライブラリ](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|ダイナミック リンク ライブラリ (DLL) を作成するためのプロジェクトです。|
|[スタティック ライブラリ](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|スタティック ライブラリ (LIB) を作成するためのプロジェクトです。|
|Windows デスクトップ ウィザード|追加のオプションを使って Windows デスクトップ アプリケーションとライブラリを作成するためのウィザードです。|

### <a name="general"></a>全般

|プロジェクト テンプレート|説明|
|----------------------|-----------------------------|
|空のプロジェクト|アプリケーション、ライブラリ、DLL を作成するための空のプロジェクトです。 必要なコードやリソースを追加する必要があります。|
|[メイクファイル プロジェクト](../ide/creating-a-makefile-project.md)|外部のビルド システムを使用するためのプロジェクトです。|
|共有アイテム プロジェクト|複数のプロジェクト間でファイルを共有するために使われるプロジェクトです。|

### <a name="atl"></a>ATL

|プロジェクト テンプレート|説明|
|----------------------|-----------------------------|
|[ATL プロジェクト](../atl/reference/creating-an-atl-project.md)|Active Template Library を使用するプロジェクトです。|

### <a name="test"></a>テスト

|プロジェクト テンプレート|説明|
|----------------------|-----------------------------|
|[ネイティブ単体テスト プロジェクト](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|ネイティブ C++ 単体テストを含むプロジェクトです。|

### <a name="mfc"></a>MFC

MFC および ATL のサポート コンポーネントを Visual Studio のインストールに追加した場合、これらのプロジェクト テンプレートが Visual Studio に追加されます。

|プロジェクト テンプレート|説明|
|----------------------|-----------------------------|
|[MFC アプリケーション](../mfc/reference/creating-an-mfc-application.md)|Microsoft Foundation Class (MFC) ライブラリを使用するアプリケーションを作成するためのプロジェクトです。|
|[MFC ActiveX コントロール](../mfc/reference/creating-an-mfc-activex-control.md)|MFC ライブラリを使用する ActiveX コントロールを作成するためのプロジェクトです。|
|[MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md)|MFC ライブラリを使うダイナミックリンク ライブラリを作成するためのプロジェクトです。|

### <a name="windows-universal-apps"></a>Windows ユニバーサル アプリ

C++ Windows ユニバーサル プラットフォーム ツール コンポーネントを Visual Studio のインストールに追加した場合、これらのプロジェクト テンプレートが Visual Studio に追加されます。

C++ でのユニバーサル Windows アプリの概要については、「[ユニバーサル Windows アプリ (C++)](../windows/universal-windows-apps-cpp.md)」をご覧ください。

|プロジェクト テンプレート|説明|
|----------------------|-----------------------------|
|空のアプリケーション|定義済みのコントロールまたはレイアウトのない単一ページ ユニバーサル Windows プラットフォーム (UWP) アプリ用のプロジェクトです。|
|DirectX 11 アプリ|DirectX 11 を使用するユニバーサル Windows プラットフォーム アプリ用のプロジェクトです。|
|DirectX 12 アプリ|DirectX 12 を使用するユニバーサル Windows プラットフォーム アプリ用のプロジェクトです。|
|DirectX 11 および XAML アプリ|DirectX 11 と XAML を使用するユニバーサル Windows プラットフォーム アプリ用のプロジェクトです。|
|単体テスト アプリ|ユニバーサル Windows プラットフォーム (UWP) アプリ用の単体テスト アプリを作成するためのプロジェクトです。|
|[DLL]|ユニバーサル Windows プラットフォーム アプリまたはランタイム コンポーネントで使用できるネイティブ ダイナミック リンク ライブラリ (DLL) 用のプロジェクトです。|
|スタティック ライブラリ|ユニバーサル Windows プラットフォーム アプリまたはランタイム コンポーネントで使用できるネイティブ スタティック リンク ライブラリ (LIB) 用のプロジェクトです。|
|Windows ランタイム コンポーネント|ユニバーサル Windows プラットフォーム アプリが使用できる Windows ランタイム コンポーネント用のプロジェクトです。アプリを記述するプログラミング言語は問いません。|
|Windows アプリケーション パッケージ プロジェクト|デスクトップ アプリケーションのサイドロードまたは Microsoft ストアでの配布を可能にする UWP パッケージを作成するプロジェクトです。|

## <a name="todo-comments"></a>TODO コメント

プロジェクト テンプレートによって生成されたファイルの多くには TODO コメントが含まれています。このコメントは、独自のソース コードを作成できる場所を特定するのに役立ちます。 コードを追加する方法について詳しくは、「[コード ウィザードを使用した機能の追加](../ide/adding-functionality-with-code-wizards-cpp.md)」および「[リソース ファイルの操作](../windows/working-with-resource-files.md)」をご覧ください。

## <a name="see-also"></a>参照

[アプリケーション ウィザードを使用したデスクトップ プロジェクトの作成](../ide/creating-desktop-projects-by-using-application-wizards.md)
