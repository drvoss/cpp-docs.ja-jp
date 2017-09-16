---
title: "インライン アセンブラー (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C]
- inline assembler [C]
ms.assetid: 821acc77-60b1-434c-ba54-2ba930a25ab4
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: e7efb9e5168d16a50b22ff95c09d423327893f96
ms.contentlocale: ja-jp
ms.lasthandoff: 05/18/2017

---
# <a name="inline-assembler-c"></a>インライン アセンブラー (C)
**Microsoft 固有の仕様**  
  
 インライン アセンブラーでは、追加のアセンブリとリンク ステップを使用せずに、アセンブリ言語命令を C のソース プログラムに直接埋め込むことができます。 インライン アセンブラーは、コンパイラに組み込まれます。したがって、MASM (Microsoft Macro Assembler) などの別のアセンブラーは必要ではありません。  
  
 インライン アセンブラーは別のアセンブリとリンクの手順を必要としないので、別のアセンブラーより便利です。 インライン アセンブラー コードでは、スコープ内にある C 変数や関数名を使用できるので、プログラムの C コードと簡単に統合できます。 そして、アセンブリ コードは C のステートメントと混合できるため、C 単独では使いにくいタスクや不可能なタスクを行うことができます。  
  
 `__asm` キーワードは、インライン アセンブラーを呼び出し、C ステートメントが有効である任意の場所に使用できます。 これは、単独では使用できません。 アセンブリ命令、中かっこで囲まれた命令グループ、または少なくとも空の中かっこの後で指定する必要があります。 "`__asm` ブロック" という用語は、ここでは、中かっこに囲まれているかどうかを問わず、命令または命令のグループを示します。  
  
 次のコードは、中かっこで囲まれた単純な `__asm` ブロックです (コードは、カスタム関数プロローグ シーケンスです)。  
  
```  
__asm  
{  
   push ebp  
   mov  ebp, esp  
   sub  esp, __LOCAL_SIZE  
}  
```  
  
 または、各アセンブリ命令の前に `__asm` を置くことができます。  
  
```  
__asm push ebp  
__asm mov  ebp, esp  
__asm sub  esp, __LOCAL_SIZE  
```  
  
 `__asm` キーワードはステートメント区切り文字であるため、アセンブリ命令も同じ行に記述できます。  
  
```  
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE   
```  
  
 **Microsoft 固有の仕様はここまで**  
  
## <a name="see-also"></a>関連項目  
 [関数の属性](../c-language/function-attributes.md)