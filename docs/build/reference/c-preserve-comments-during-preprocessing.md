---
title: /C (プリプロセス時のコメントの保持)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- /c
- VC.Project.VCCLWCECompilerTool.KeepComments
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
ms.openlocfilehash: b37e279af3995bd1d61c97dc88b49cdd95495c75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442602"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (プリプロセス時のコメントの保持)

プリプロセス時にコメントを保持します。

## <a name="syntax"></a>構文

```
/C
```

## <a name="remarks"></a>Remarks

このコンパイラ オプションが必要です、 **/E**、 **/P**、または **/EP**オプション。

次のコード サンプル ソース コードのコメントが表示されます。

```
// C_compiler_option.cpp
// compile with: /E /C /c
int i;   // a variable
```

このサンプルでは、次の出力が生成されます。

```
#line 1 "C_compiler_option.cpp"
int i;   // a variable
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、「[プロジェクトのプロパティの操作](../../ide/working-with-project-properties.md)」を参照してください。

1. **[C/C++]** フォルダーをクリックします。

1. をクリックして、**プリプロセッサ**プロパティ ページ。

1. 変更、**コメントを残す**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[コンパイラ オプションの設定](../../build/reference/setting-compiler-options.md)<br/>
[/E (stdout に前処理する)](../../build/reference/e-preprocess-to-stdout.md)<br/>
[/P (ファイルの前処理)](../../build/reference/p-preprocess-to-a-file.md)<br/>
[/EP (#line ディレクティブなしで stdout に前処理する)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)