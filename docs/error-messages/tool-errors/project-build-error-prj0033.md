---
title: プロジェクト ビルド エラー PRJ0033
ms.date: 11/04/2016
f1_keywords:
- PRJ0033
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
ms.openlocfilehash: e074ee18508271b56686aa16f9012085ed3bd77d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586213"
---
# <a name="project-build-error-prj0033"></a>プロジェクト ビルド エラー PRJ0033

カスタム ビルドの追加の依存関係 ' プロパティは、'macro_expansion' をファイル 'file' に含まれている 'macro' 評価を出すのステップします。

ファイルのカスタム ビルド ステップには、おそらくマクロ評価の問題により、追加の依存関係のエラーが含まれています。 このエラーにあるパス形式が正しくない、文字またはファイル パスでは無効な文字の組み合わせを含むもします。

このエラーを解決するのには、マクロを修正するか、パスの指定を修正します。 パスには、プロジェクト ディレクトリからの絶対パスを指定します。