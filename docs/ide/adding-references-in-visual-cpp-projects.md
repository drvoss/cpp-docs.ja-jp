---
title: Visual C++ プロジェクトへの参照の追加
ms.date: 11/04/2016
f1_keywords:
- VC.Project.References
helpviewer_keywords:
- Add References Dialog Box (C++)
- .NET Framework (C++), Add References Dialog Box
ms.assetid: 12b8f571-0f21-40b3-9404-5318a57e9cb5
ms.openlocfilehash: c50a726b0e5b6e175bd7256ab5a5d93d6b172601
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583798"
---
# <a name="adding-references-in-visual-c-projects"></a>Visual C++ プロジェクトへの参照の追加

プログラムでは、DLL、Windows ランタイム コンポーネント、拡張 SDK、COM コンポーネント、.NET アセンブリなど、他のバイナリの API を呼び出すことは非常に一般的です。 プログラムが他のバイナリを検索する方法は、プロジェクトの種類とバイナリの種類の両方に応じて決まります。

ネイティブの C++ プロジェクトでは、ソリューション内の別のプロジェクトで生成されたものではないネイティブ DLL または COM コンポーネントを使用する場合、LoadLibrary または CoCreateInstance を使用してバイナリへのパスを指定するか、適切に定義された特定の場所をシステムに検索させてこれを見つけます。

UWP プロジェクトまたは C++/CLI プロジェクトなど、他の種類プロジェクトの場合、またはバイナリがソリューション内の別のプロジェクトから生成された場合は、 *参照* をアセンブリ、コンポーネント、またはプロジェクトに追加します。   基本的に言って参照とは、プログラムがバイナリを見つけて、これと通信できるようにするデータ セットのことです。       参照を追加すると、Visual Studio が下位レベルの詳細を処理します。 C++ プロジェクトから .NET Framework アセンブリ (C++/CLI のみ)、COM コンポーネント、共有プロジェクトを含むソリューション内の他のプロジェクト、または接続されたサービスへの参照を設定するには、**[ソリューション エクスプローラー]** で **[参照]** ノードを右クリックして **[参照マネージャー]** を表示します。 参照マネージャーの表示内容は、プロジェクトの種類によって異なります。

ネイティブの C++ プロジェクト (ATL) では、 *参照* の概念が適用されるのはソリューション内の他のプロジェクト (共有プロジェクトを含む) だけであるため、 **[参照マネージャー]** にはそれしか表示されません。

![Visual C&#43;&#43; 参照マネージャー &#40;ATL プロジェクト&#41;](../ide/media/visual-c---reference-manager--atl-projects-.png "Visual C++ 参照マネージャー (ATL プロジェクト)")

C++/CLI またはユニバーサル Windows プラットフォームのプロジェクトでは、ソリューション内の他のプロジェクトだけでなく、さらに多くの種類のバイナリに参照の概念が適用されます。  これらのものがすべて **[参照マネージャー]** を表示します。

## <a name="reference-properties"></a>参照のプロパティ

参照には種類に従ってそれぞれプロパティがあります。 プロパティを表示するには、ソリューション エクスプローラーで参照を選んで **Alt + Enter**キーを押すか、右クリックして **[プロパティ]** を選びます。 読み取り専用のプロパティと、変更できるプロパティがあります。 ただし、通常はこれらのプロパティを手動で変更する必要はありません。

### <a name="activex-reference-properties"></a>ActiveX 参照のプロパティ

ActiveX 参照のプロパティは、COM コンポーネントへの参照に対してのみ使用できます。 これらのプロパティは、 **[参照]** ウィンドウで COM コンポーネントが選択されている場合にのみ表示されます。 プロパティは修正できません。

- **コントロールの完全なパス**

   参照先のコントロールのディレクトリ パスが表示されます。

- **コントロールの GUID**

   ActiveX コントロールの GUID が表示されます。

- **コントロールのバージョン**

   参照先の ActiveX コントロールのバージョンが表示されます。

- **タイプ ライブラリ名**

   参照されているタイプ ライブラリ名が表示されます。

- **ラッパー ツール**

   参照先の COM ライブラリまたは ActiveX コントロールからの相互運用機能アセンブリをビルドするために使用するツールが表示されます。

### <a name="assembly-reference-properties"></a>アセンブリ参照のプロパティ

アセンブリ参照のプロパティは C++/CLI プロジェクトの .NET Framework アセンブリへの参照でのみ使用できます。 これらのプロパティは、**[参照]** ウィンドウで .NET Framework アセンブリが選択されている場合のみ表示されます。 プロパティは修正できません。

- **相対パス**

   プロジェクト ディレクトリから参照するアセンブリへの相対パスが表示されます。

### <a name="build-properties"></a>ビルド プロパティ

次のプロパティは、さまざまな種類の参照で使用できます。 参照付きでビルドする方法をこれらのプロパティにより指定できます。

- **ローカルにコピー**

   ビルド時に、参照するアセンブリをターゲットの場所に自動的にコピーするかどうかを指定します。

- **ローカル サテライト アセンブリにコピー**

   ビルド時に、参照するアセンブリのサテライト アセンブリをターゲットの場所に自動的にコピーするかどうかを指定します。 **[ローカルにコピー]** が **true** の場合にのみ使用します。

- **参照アセンブリの出力**

   このアセンブリがビルド処理で使用されることを指定します。 **true** の場合、ビルド時にコンパイラのコマンド ラインでアセンブリが使用されます。

### <a name="project-to-project-reference-properties"></a>プロジェクト間参照プロパティ

次のプロパティは、 *[参照]* ウィンドウで選んだプロジェクトから、同じソリューション内の別のプロジェクトへの **プロジェクト間参照** を定義します。 詳細については、「[プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)」を参照してください。

- **ライブラリ依存関係のリンク**

   このプロパティが **True**の場合、プロジェクト システムは、独立プロジェクトから生成される依存プロジェクトである .lib ファイルにリンクされます。 通常は **True**を指定します。

- **プロジェクト識別子**

   独立したプロジェクトを一意に識別します。 プロパティの値は、変更できない内部システムの GUID です。

- **ライブラリ依存関係の入力の使用**

   このプロパティが **False**の場合、プロジェクト システムは、独立プロジェクトから生成されるライブラリの依存プロジェクトである .lib ファイルにリンクされません。 そのため、この値はインクリメンタル リンクを無効にします。 依存プロジェクトが多い場合、アプリケーションのビルドには時間がかかるため、通常は **False** を指定します。

### <a name="reference-properties"></a>参照のプロパティ

次のプロパティは COM および .NET のアセンブリ参照のものであり、変更できません。

- **アセンブリ名**

   参照するアセンブリのアセンブリ名が表示されます。

- **カルチャ**

   選択された参照のカルチャが表示されます。

- **説明**

   選択された参照の説明が表示されます。

- **完全パス**

   参照されたアセンブリのディレクトリ パスが表示されます。

- **ID**

   .NET Framework アセンブリでは、完全なパスが表示されます。 COM コンポーネントでは、GUID が表示されます。

- **ラベル**

   参照のラベルが表示されます。

- **Name**

   参照名が表示されます。

- **公開キー トークン**

   参照されたアセンブリを識別するための公開キー トークンが表示されます。

- **厳密な名前**

   参照が厳密な名前を持つ場合は`true` です。 厳密な名前を持つアセンブリは、一意にバージョン管理されます。

- **Version**

   参照アセンブリのバージョンが表示されます。

## <a name="see-also"></a>参照

[プロパティ ページ](../ide/property-pages-visual-cpp.md)<br>
[プロジェクトのプロパティの操作](../ide/working-with-project-properties.md)