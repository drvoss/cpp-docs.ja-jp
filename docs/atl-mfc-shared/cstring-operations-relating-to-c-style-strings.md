---
title: "C スタイルの文字列に関連する CString の操作方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "キャスト (CString オブジェクトを)"
  - "CString オブジェクト, 基本操作"
  - "C スタイルの文字列"
  - "MFC [C++], 文字列処理クラス"
  - "null 値, null で終わる文字列の変換"
  - "標準ランタイム ライブラリ文字列関数"
  - "string 引数"
  - "文字列変換 [C++], C スタイルの文字列"
  - "文字列関数"
  - "文字列 [C++], CString クラス"
  - "文字列 [C++], C で"
  - "文字列 [C++], 文字列操作"
ms.assetid: 5048de8a-5298-4891-b8a0-c554b5a3ac1b
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# C スタイルの文字列に関連する CString の操作方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CString](../atl-mfc-shared/using-cstring.md) オブジェクトには文字列データが含まれます。  `CString` は、クラス テンプレート [CStringT](../atl-mfc-shared/reference/cstringt-class.md) で定義されている[メソッドと演算子](../atl-mfc-shared/reference/cstringt-class.md)のセットを継承して、文字列データを操作します  \(`CString` は、`CString` でサポートされる種類の文字データを操作するように `CStringT` を特化させた `typedef` です\)。  
  
 `CString` は文字データを C スタイルの null で終わる文字列として内部的に格納しません。  代わりに、`CString` は文字データの長さを追跡して、より安全にデータとそれに必要な領域を監視できるようにします。  
  
 `CString` は C スタイルの文字列を受け入れ、C スタイルの文字列として文字データにアクセスする方法を提供します。  このトピックの次のセクションで、`CString` オブジェクトを C スタイルの null で終わる文字列と同じように使用する方法について説明します。  
  
-   [C スタイルの null で終わる文字列への変換](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)  
  
-   [標準ランタイム ライブラリ文字列関数の操作](#_core_working_with_standard_run.2d.time_library_string_functions)  
  
-   [CString の内容の直接変更](#_core_modifying_cstring_contents_directly)  
  
-   [可変個の引数のある関数での CString オブジェクトの使用](#_core_using_cstring_objects_with_variable_argument_functions)  
  
-   [CString 仮パラメーターの指定](#_core_specifying_cstring_formal_parameters)  
  
##  <a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a> C スタイルの null で終わる文字列としての CString の使用  
 `CString` オブジェクトを C スタイルの文字列として使用するには、オブジェクトを `LPCTSTR` にキャストします。  次の例では、`CString` は読み取り専用で C スタイルの null で終わる文字列へのポインターを返します。  `strcpy` 関数は、C スタイルの文字列のコピーを変数 `myString` に入れます。  
  
```  
CString aCString = "A string";  
char myString[256];  
strcpy(myString, (LPCTSTR)aCString);  
  
```  
  
 `CString` メソッド \(`SetAt` など\) を使用して、文字列オブジェクトの個々の文字を変更できます。  ただし、`LPCTSTR` は一時的なポインターであり、`CString` に対して変更が行われると無効になります。  `CString` がスコープから外れ、自動的に削除されることもあります。  `CString` オブジェクトを使用するたびに、オブジェクトの新しい `LPCTSTR` ポインターを取得することをお勧めします。  
  
 場合によっては、直接変更するために `CString` データのコピーが必要になる場合があります。  より安全な関数 `strcpy_s` \(または Unicode\/MBCS との移植性がある `_tcscpy_s`\) を使用して、`CString` オブジェクトを別のバッファーにコピーします。  次の例に示すように、ここで文字を安全に変更できます。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#189](../atl-mfc-shared/codesnippet/CPP/cstring-operations-relating-to-c-style-strings_1.cpp)]  
  
> [!NOTE]
>  `strcpy_s` \(または Unicode\/MBCS との移植性がある `_tcscpy_s`\) に対する 3 つ目の引数には、`const``wchar_t*` \(Unicode\) または `const``char*` \(ANSI\) のいずれかを指定します。  前述の例では、この引数に `CString` を渡しています。  C\+\+ コンパイラは `CString` クラス用に定義されている変換関数を自動的に適用します。この関数は `CString` を `LPCTSTR` に変換します。  ある型から別の型へのキャスト操作を定義する機能は、C\+\+ の最も有効な機能の 1 つです。  
  
##  <a name="_core_working_with_standard_run.2d.time_library_string_functions"></a> 標準ランタイム ライブラリ文字列関数の操作  
 `strcmp` などの標準 C ランタイム ライブラリ文字列関数 \(または Unicode\/MBCS との移植性がある `_tcscmp`\) を使用して検討対象の文字列操作を実行するために、`CString` メソッドを検索できる必要があります。  
  
 C ランタイム文字列関数を使用する必要がある場合は、「C スタイルの null で終わる文字列への変換」を参照してください。 `CString` オブジェクトを同等の C スタイルの文字列バッファーにコピーし、そのバッファーに対して操作を実行してから、結果の C スタイルの文字列を `CString` オブジェクトに割り当てることができます。  
  
##  <a name="_core_modifying_cstring_contents_directly"></a> CString の内容の直接変更  
 ほとんどの場合、`CString` オブジェクトの内容を変更するか、または `CString` を C スタイルの文字列に変換するには、`CString` メンバー関数を使用する必要があります。  
  
 場合によっては、`CString` の内容を直接変更する方が合理的であることがあります。たとえば、文字バッファーを必要とするオペレーティング システム関数を使用する場合などです。  
  
 `GetBuffer` メソッドと `ReleaseBuffer` メソッドでは、`CString` オブジェクトの内部文字バッファーへのアクセスが提供され、これを使用して直接変更できます。  次の手順では、このような目的でこれらの関数を使用する方法を示します。  
  
#### GetBuffer と ReleaseBuffer を使用して CString オブジェクトの内部文字バッファーにアクセスするには  
  
1.  `CString` オブジェクトの `GetBuffer` を呼び出して、必要なバッファーの長さを指定します。  
  
2.  `GetBuffer` によって返されたポインターを使用して、`CString` オブジェクトに直接文字を書き込みます。  
  
3.  `CString` オブジェクトの `ReleaseBuffer` を呼び出して、文字列の長さなどのすべての内部的な `CString` 状態情報を更新します。  `CString` オブジェクトの内容を直接変更した後、先に `ReleaseBuffer` を呼び出してから、その他の `CString` メンバー関数を呼び出す必要があります。  
  
##  <a name="_core_using_cstring_objects_with_variable_argument_functions"></a> 可変個の引数のある関数での CString オブジェクトの使用  
 一部の C 関数は、可変個の引数を受け取ります。  主な例として `printf_s` があります。  この種類の関数の宣言方法では、コンパイラは引数の型がわからず、それぞれの引数で実行する変換操作を決定できません。  そのため、可変個の引数を受け取る関数に `CString` オブジェクトを渡す場合は、明示的な型キャストを使用することが重要です。  
  
 引数が可変個である関数で `CString` オブジェクトを使用するには、次の例に示すように、`CString` を `LPCTSTR` 文字列に明示的にキャストします。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#190](../atl-mfc-shared/codesnippet/CPP/cstring-operations-relating-to-c-style-strings_2.cpp)]  
  
##  <a name="_core_specifying_cstring_formal_parameters"></a> CString 仮パラメーターの指定  
 文字列引数を必要とするほとんどの関数では、`CString` の代わりに文字への `const` ポインター \(`LPCTSTR`\) として、関数プロトタイプの仮パラメーターを指定することをお勧めします。  仮パラメーターが文字への `const` ポインターとして指定されている場合、`TCHAR` 配列、リテラル文字列 \[`"hi there"`\]、または `CString` オブジェクトのいずれかにポインターを渡すことができます。  `CString` オブジェクトは、自動的に `LPCTSTR` に変換されます。  `LPCTSTR` を使用できる場所であればどこでも、`CString` オブジェクトを使用できます。  
  
 また、引数が変更されない場合は、仮パラメーターを定数文字列参照 \(`const``CString&`\) として指定することもできます。  文字列が関数で変更される場合は、`const` 修飾子を省略します。  既定の null 値が必要な場合は、次に示すように、これを null 文字列 \[`""`\] に初期化します。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#191](../atl-mfc-shared/codesnippet/CPP/cstring-operations-relating-to-c-style-strings_3.cpp)]  
  
 ほとんどの関数の結果では、単に値で `CString` オブジェクトを返すことができます。  
  
## 参照  
 [文字列](../atl-mfc-shared/strings-atl-mfc.md)   
 [CString 引数の渡し方](../atl-mfc-shared/cstring-argument-passing.md)