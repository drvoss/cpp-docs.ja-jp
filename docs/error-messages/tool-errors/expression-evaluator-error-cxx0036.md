---
title: 式エバリュエーター エラー CXX0036
ms.date: 11/04/2016
f1_keywords:
- CXX0036
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
ms.openlocfilehash: d7961d92760cc5ac325b4bc9f187d4ee2298479a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576806"
---
# <a name="expression-evaluator-error-cxx0036"></a>式エバリュエーター エラー CXX0036

コンテキストが正しくありません {...} specification

このメッセージは、コンテキスト演算子の使用中のいくつかのエラーのいずれかで生成されることができます (**{}**)。

- コンテキスト演算子の構文 (**{}**) 指定されました。

   コンテキスト演算子の構文です。

     {*関数*、*モジュール*、*dll*}*式*

   コンテキストを指定しますこの*式*します。 コンテキスト演算子は、型キャストと同じ優先順位と使用状況が。

   末尾のコンマは省略できます。 いずれか*関数*、*モジュール*、または*dll*リテラルのコンマを含む名前全体をかっこで囲む必要があります。

- 関数名の綴りが間違って、または、指定されたモジュールまたはダイナミック リンク ライブラリに存在しません。

   C は大文字小文字を区別する言語のため*関数*ソースで定義されている大文字小文字の区別で指定する必要があります。

- モジュールまたは DLL が見つかりませんでした。

   指定されたモジュールまたは DLL の完全なパス名を確認します。

このエラーは、can0036 と同じものと同じです。