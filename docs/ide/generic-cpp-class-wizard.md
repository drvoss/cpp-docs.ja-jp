---
title: "一般 C++ クラス ウィザード | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.class.generic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "一般 C++ クラス ウィザード [C++]"
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 一般 C++ クラス ウィザード
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一般 C\+\+ クラスをプロジェクトに追加します。  クラスは ATL または MFC からは継承しません。  
  
 **\[クラス名\]**  
 新しいクラスの名前を設定します。  
  
 **\[.h ファイル\]**  
 新しいクラスのヘッダー ファイル名を設定します。  既定では、\[クラス名\]に入力した名前に基づいた名前になります。  選択した場所にヘッダー ファイルを保存する、または既存のファイルにクラス宣言を追加するには、省略ボタン \(**\[...\]**\) をクリックします。  既存のファイルを選択した場合は、ウィザードの **\[完了\]** をクリックすると、ファイルの内容にクラス宣言を追加するかどうかをたずねるメッセージが表示されます。  宣言を追加する場合は **\[はい\]** をクリックし、ウィザードに戻って他のファイル名を指定する場合は **\[いいえ\]** をクリックします。  
  
 **\[.cpp ファイル\]**  
 新しいクラスの実装ファイル名を設定します。  既定では、\[クラス名\]に入力した名前に基づいた名前になります。  選択した場所に実装ファイルを保存する、または既存のファイルにクラス定義を追加するには、省略ボタン \(**\[...\]**\) をクリックします。  既存のファイルを選択した場合は、ウィザードの **\[完了\]** をクリックすると、ファイルの内容にクラス定義を追加するかどうかをたずねるメッセージが表示されます。  定義を追加する場合は **\[はい\]** をクリックし、ウィザードに戻って他のファイル名を指定する場合は **\[いいえ\]** をクリックします。  
  
 **\[基本クラス\]**  
 新しいクラスの基本クラスを設定します。  
  
 **\[アクセス\]**  
 新しいクラスの基本クラスのメンバーへのアクセス権を設定します。  アクセス修飾子とは、クラス メンバー関数に対してほかのクラスが持つアクセス権のレベルを指定するキーワードです。  アクセス権を指定する方法の詳細については、「[メンバー アクセス コントロール](../cpp/member-access-control-cpp.md)」を参照してください。  既定では、クラス アクセス レベルは、`public` です。  
  
-   `public`  
  
-   `protected`  
  
-   `private`  
  
-   **\[既定値\]** アクセス修飾子は生成されません。  
  
 **\[仮想デストラクター\]**  
 クラス デストラクターが仮想デストラクターかどうかを指定します。  仮想デストラクターを使用すると、派生クラスのインスタンスが削除されても正しいデストラクターを呼び出すことができます。  
  
 **\[インライン\]**  
 ヘッダーファイルに、クラス コンストラクターとクラス定義の両方をインライン関数として生成します。  
  
 **マネージ**  
 オンの場合、マネージ クラスとヘッダー ファイルを追加します。  オフの場合、ネイティブ クラスとヘッダー ファイルを追加します。  
  
## 参照  
 [一般 C\+\+ クラスの追加](../ide/adding-a-generic-cpp-class.md)