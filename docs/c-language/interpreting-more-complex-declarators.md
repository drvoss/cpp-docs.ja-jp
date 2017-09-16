---
title: "より複雑な宣言子の解釈 | Microsoft Docs"
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
- complex declarators
- interpreting complex declarators
ms.assetid: dd5b7019-c86d-4645-a5cc-21f834de6f4a
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
ms.openlocfilehash: c5bd11f2056bae9588a28c443d2b5c3d287c672d
ms.contentlocale: ja-jp
ms.lasthandoff: 05/18/2017

---
# <a name="interpreting-more-complex-declarators"></a>より複雑な宣言子の解釈
宣言子をかっこで囲んで、"複雑な宣言子" の特定の解釈を指定できます。 複雑な宣言子は、複数の配列、ポインター、または関数の修飾子で修飾される識別子です。 1 つの ID には、配列、ポインター、関数修飾子のさまざまな組み合わせを適用できます。 通常、`typedef` を使用して、宣言を簡素化できます。 「[typedef 宣言](../c-language/typedef-declarations.md)」を参照してください。  
  
 複雑な宣言の解釈で、角かっこおよびかっこ (つまり、識別子の右側の修飾子) はアスタリスク (つまり、識別子の左側の修飾子) より優先されます。 角かっことかっこは同じ優先順位を持ち、左から右に関連付けられます。 宣言子が完全に解釈された後、型指定子は最後のステップとして適用されます。 かっこを使用し、既定の関連付けの順序をオーバーライドして、特定の解釈を強制できます。 ただし、識別子名はかっこで囲む必要があります。 これは、誤ってパラメーター リストとして解釈される場合があります。  
  
 複雑な宣言子を解釈する最も簡単な方法は、次の 4 つの手順でそれらを "内側から外側に向かって" 読み取ることです。  
  
1.  識別子から開始し、角かっこまたはかっこ (存在する場合) を直接右方向へ検索します。  
  
2.  これらの角かっこまたはかっこを解釈し、左にあるアスタリスクを探します。  
  
3.  どの段階においても、右かっこが発生したら、戻って、かっこ内のすべてに対して規則 1 および 2 を適用します。  
  
4.  型指定子を適用します。  
  
    ```  
    char *( *(*var)() )[10];  
     ^   ^  ^ ^ ^   ^    ^  
     7   6  4 2 1   3    5  
    ```  
  
 この例では、手順に順番に番号が振られ、次のように解釈できます。  
  
1.  識別子 `var` を次として宣言します  
  
2.  次へのポインター  
  
3.  次を返す関数  
  
4.  次へのポインター  
  
5.  次の 10 要素の配列  
  
6.  次へのポインター  
  
7.  `char` 値。  
  
## <a name="examples"></a>例  
 次の例は、その他の複雑な宣言を示し、かっこが宣言の意味にどのように影響を与える可能性があるかを示します。  
  
```  
int *var[5]; /* Array of pointers to int values */  
```  
  
 配列修飾子はポインター修飾子よりも高い優先順位を持つため、`var` は配列として宣言されています。 ポインター修飾子は配列要素の型に適用されます。したがって、配列要素は `int` 値へのポインターです。  
  
```  
int (*var)[5]; /* Pointer to array of int values */  
```  
  
 `var` のこの定義では、かっこによって、配列修飾子よりも高い優先順位がポインター修飾子に与えられ、`var` は 5 つの `int` 値の配列へのポインターとして宣言されます。  
  
```  
long *var( long, long ); /* Function returning pointer to long */  
```  
  
 関数の修飾子はポインターの修飾子よりも優先順位が高いため、`var` のこの宣言は **long** 値へのポインターを返す関数として `var` を宣言します。 関数は、引数として 2 つの **long** 値を受け入れるように宣言されます。  
  
```  
long (*var)( long, long ); /* Pointer to function returning long */  
```  
  
 この例は、前の例に似ています。 かっこによって関数の修飾子よりも高い優先順位がポインターの修飾子に与えられ、`var` は **long** 値を返す関数へのポインターとして宣言されます。 もう一度、関数は 2 個の **long** 引数を受け取ります。  
  
```  
struct both       /* Array of pointers to functions */  
{                 /*   returning structures         */  
    int a;  
    char b;  
} ( *var[5] )( struct both, struct both );  
```  
  
 配列の要素は、関数にすることはできませんが、この宣言は、関数へのポインターの配列を宣言する方法を示します。 この例では、`var` は、2 つのメンバーを持つ構造体を返す関数へのポインターを 5 つ含む配列として宣言されます。 関数の引数は、同じ構造体型 `both` を持つ 2 つの構造体として宣言されます。 `*var[5]` を囲むかっこが必要であることに注意してください。 これらがない場合、宣言は次に示すように、関数の配列を宣言しようとする無効な記述になります。  
  
```  
/* ILLEGAL */  
struct both *var[5](struct both, struct both);  
```  
  
 次のステートメントは、ポインターの配列を宣言します。  
  
```  
unsigned int *(* const *name[5][10] ) ( void );  
```  
  
 `name` 配列には、多次元配列で編成された 50 個の要素があります。 要素は、定数のポインターへのポインターです。 この定数ポインターは、符号なしの型へのポインターを返す、パラメーターを持たない関数をポイントします。  
  
 次の例は、3 つの **double** 値の配列へのポインターを返す関数です。  
  
```  
double ( *var( double (*)[3] ) )[3];  
```  
  
 この宣言では、配列を返す関数が無効であるため、関数は配列へのポインターを返します。 ここで、`var` は、3 つの **double** 値の配列へのポインターを返す関数として宣言されます。 関数 `var` は 1 つの引数を取ります。 戻り値などの引数は、3 つの **double** 値から成る配列へのポインターです。 引数の型は、複雑な *abstract-declarator* で指定されます。 引数型のアスタリスクを囲むかっこが必要です。かっこがないと、引数の型は **double** 値への 3 つのポインターの配列となります。 抽象宣言子の詳細と例については、「[抽象宣言子](../c-language/c-abstract-declarators.md)」を参照してください。  
  
```  
union sign         /* Array of arrays of pointers */  
{                  /* to pointers to unions       */  
     int x;  
     unsigned y;  
} **var[5][5];  
```  
  
 上の例に示すように、ポインターは別のポインターを指すことができ、配列は要素として配列を含めることができます。 ここで、`var` は 5 つの要素の配列です。 各要素は、2 つのメンバーを持つ共用体へのポインターへのポインターから成る 5 つの要素を持つ配列です。  
  
```  
union sign *(*var[5])[5]; /* Array of pointers to arrays  
                             of pointers to unions        */  
```  
  
 この例は、かっこの配置によって宣言の意味がどのように変わるかを示しています。 この例では、`var` は、ポインターの要素を 5 つ含む配列です。それらのポインターはそれぞれ、要素として共有体へのポインターを 5 つ含む配列を指します。 `typedef` を使用して複雑な宣言を回避する方法の例については、「[typedef 宣言](../c-language/typedef-declarations.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [宣言と型](../c-language/declarations-and-types.md)