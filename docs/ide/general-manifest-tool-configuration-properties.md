---
title: マニフェスト ツールの構成プロパティ (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCManifestTool.MergeRulesFile
- VC.Project.VCManifestTool.UseUnicodeResponseFiles
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.UseFAT32Workaround
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
ms.assetid: b99368a5-6819-482c-a06e-f2409290cfd1
ms.openlocfilehash: 5706a67ac3f6be7a916d6f4f0ee8ccfafdfb9475
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565218"
---
# <a name="general-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>[全般] ([&lt;プロジェクト名&gt; プロパティ ページ] ダイアログ ボックス - [構成プロパティ] - [マニフェスト ツール])

このダイアログ ボックスを使用して、[Mt.exe](https://msdn.microsoft.com/library/aa375649) の全般オプションを指定します。

このプロパティ ページ ダイアログ ボックスにアクセスするには、自分のプロジェクトまたはプロパティ シートのプロパティ ページを開きます。 **[構成プロパティ]** の下で **[マニフェスト ツール]** ノードを展開して、**[全般]** を選択します。

## <a name="uielement-list"></a>UIElement の一覧

- **著作権情報の非表示**

   **[はい (/nologo)]** の場合、マニフェスト ツールを起動したとき、Microsoft の標準的な著作権情報が隠されます。 ビルド プロセスの一部として、あるいはビルド環境から mt.exe を実行するとき、ログ ファイルに不要な出力を表示しない場合、このオプションを使用します。

- **詳細出力**

   **[はい (/verbose)]** の場合、マニフェスト生成中、追加のビルド情報が表示されます。

- **アセンブリ ID**

   [\<assemblyIdentity> 要素](/visualstudio/deployment/assemblyidentity-element-clickonce-application)の属性を ID 文字列を指定するには、/identity オプションを使用します。 ID 文字列は `name` 属性の値で始まり、後ろに*属性* = *値*のペアが続きます。 ID 文字列の属性はコンマで区切られます。

   ID 文字列の例は次のようになります。

   `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="see-also"></a>参照

[ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest)<br>
[[マニフェスト ツール] プロパティ ページ](../ide/manifest-tool-property-pages.md)<br>
[プロジェクトのプロパティの操作](../ide/working-with-project-properties.md)