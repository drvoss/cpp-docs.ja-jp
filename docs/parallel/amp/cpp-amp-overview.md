---
title: "C++ AMP の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C++ Accelerated Massive Parallelism、要件"
  - "C++ Accelerated Massive Parallelism、アーキテクチャ"
  - "C++ AMP"
  - "C++ Accelerated Massive Parallelism, 概要"
  - "C++ Accelerated Massive Parallelism"
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
caps.latest.revision: 60
caps.handback.revision: 60
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ AMP の概要
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

C++ Accelerated Massive Parallelism (C++ AMP) は、独立したグラフィックス カードの GPU (graphics processing unit) などのデータ並列ハードウェアを活用して、C++ コードの実行を高速化します。 C++ AMP を使用することによって、並列化と異種ハードウェアを使用して実行を高速化できるように、多次元データ アルゴリズムをコーディングすることができます。 C++ AMP のプログラミング モデルには、多次元配列、インデックス作成、メモリ転送、タイル、数学関数ライブラリが含まれています。 C++ AMP の言語拡張機能を使用して、データを CPU から GPU へ、また GPU から CPU へどのように移動するかを制御でき、パフォーマンスを向上させることができます。  
  
## <a name="system-requirements"></a>システム要件  
  
- [!INCLUDE[win7](../../build/includes/win7_md.md)]、[!INCLUDE[win8](../../build/includes/win8_md.md)]、[!INCLUDE[winsvr08_r2](../../parallel/amp/includes/winsvr08_r2_md.md)]、または [!INCLUDE[winserver8](../../build/includes/winserver8_md.md)]  
  
-   DirectX 11 機能レベル 11.0 以降のハードウェア  
  
-   ソフトウェア エミュレーターでデバッグするには、[!INCLUDE[win8](../../build/includes/win8_md.md)] または [!INCLUDE[winserver8](../../build/includes/winserver8_md.md)] が必要です。 ハードウェアでデバッグするには、使用するグラフィックス カードのドライバーをインストールする必要があります。 詳細については、次を参照してください。 [GPU コードのデバッグ](../Topic/Debugging%20GPU%20Code.md)します。  
  
## <a name="introduction"></a>はじめに  
 次の 2 つの例は、C++ AMP の主要コンポーネントを示しています。 2 個の 1 次元配列の対応する要素を加算するとします。 追加するなど、 `{1, 2, 3, 4, 5}` と `{6, 7, 8, 9, 10}` を取得する `{7, 9, 11, 13, 15}`です。 C++ AMP を使用しない場合、数値を加算し、結果を表示するために、次のようなコードを記述します。  
  
```cpp  
  
#include <iostream>  
  
void StandardMethod() {  
  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5];  
  
    for (int idx = 0; idx < 5; idx++)  
    {  
        sumCPP[idx] = aCPP[idx] + bCPP[idx];  
    }  
  
    for (int idx = 0; idx < 5; idx++)  
    {  
        std::cout << sumCPP[idx] << "\n";  
    }  
}  
  
```  
  
 このコードの重要な部分は次のとおりです。  
  
-   データ: データは 3 個の配列で構成されています。 すべてランク (1) と長さ (5) が同じです。  
  
-   :イテレーション: 最初の `for` ループは配列の要素を反復処理するメカニズムを提供します。 合計を計算するために実行するコードは、最初の `for` ブロックに含まれています。  
  
-   インデックス: `idx` 変数は、配列の各要素にアクセスします。  
  
 C++ AMP を使用する場合は、代わりに次のようにコードを記述できます。  
  
```cpp  
  
#include <amp.h>  
#include <iostream>  
using namespace concurrency;  
  
const int size = 5;  
  
void CppAmpMethod() {  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[size];  
  
    // Create C++ AMP objects.  
    array_view<const int, 1> a(size, aCPP);  
    array_view<const int, 1> b(size, bCPP);  
    array_view<int, 1> sum(size, sumCPP);  
    sum.discard_data();  
  
    parallel_for_each(   
        // Define the compute domain, which is the set of threads that are created.  
        sum.extent,   
        // Define the code to run on each thread on the accelerator.  
 [=](index<1> idx) restrict(amp)  
    {  
        sum[idx] = a[idx] + b[idx];  
    }  
    );  
  
    // Print the results. The expected output is "7, 9, 11, 13, 15".  
    for (int i = 0; i < size; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
 基本的な要素は同じですが、C++ AMP のコンストラクトが使用されています。  
  
-   データ: C++ 配列の作成に使用次の 3 つの C++ AMP [array_view](../../parallel/amp/reference/array-view-class.md) オブジェクトです。 4 個の値を指定して `array_view` オブジェクトを構築します。すなわち、各次元の `array_view` オブジェクトのデータ値、ランク、要素の型、および長さです。 ランクと型は型パラメーターとして渡されます。 データと長さは、コンストラクターのパラメーターとして渡されます。 この例では、コンストラクターに渡される C++ 配列は 1 次元です。 ランクと長さは `array_view` オブジェクト内のデータの四角形を構築するために使用され、データ値は配列の値を設定するために使用されます。 ランタイム ライブラリにも含まれる、 [array クラス](../../parallel/amp/reference/array-class.md), のようなインターフェイスがあり、 `array_view` クラスであり、この記事の後半で説明します。  
  
-   イテレーション: [parallel_for_each 関数 (C++ AMP)](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) データ要素を反復処理するためのメカニズムを提供または *計算ドメイン*します。 この例では、計算のドメインは `sum.extent` によって指定されます。 実行するコードが、ラムダ式に含まれているか、 *カーネル関数*します。 `restrict(amp)` は、C++ AMP で高速化できる C++ 言語のサブセットのみが使用されることを示します。  
  
-   インデックス: [index クラス](../../parallel/amp/reference/index-class.md) 変数 `idx`, 、ランクが 1 のランクと一致するので宣言された、 `array_view` オブジェクトです。 インデックスを使用することによって、`array_view` オブジェクトの個々の要素にアクセスできます。  
  
## <a name="shaping-and-indexing-data-index-and-extent"></a>データを構造化してインデックスを作成する: index と extent  
 カーネル コードを実行する前に、データ値を定義し、データの形式を宣言する必要があります。 すべてのデータは配列 (四角形) として定義され、任意のランク (次元数) を持つように配列を定義できます。 データは、任意の次元で任意のサイズにすることができます。  
  
### <a name="index-class"></a>index クラス  
  [Index クラス](../../parallel/amp/reference/index-class.md) の場所を指定、 `array` または `array_view` オブジェクト 1 つのオブジェクトの各次元の原点からのオフセットをカプセル化します。 配列内の位置にアクセスする場合、整数のインデックスのリストの代わりに、`index` オブジェクトを、インデックス作成演算子 `[]` に渡します。 使用して各次元の要素にアクセスすることができます、 [array::operator() 演算子](../Topic/array::operator\(\)%20Operator.md) または [array_view::operator() 演算子](../Topic/array_view::operator\(\)%20Operator.md)します。  
  
 次の例では、1 次元の `array_view` オブジェクト内の 3 番目の要素を指定する 1 次元インデックスを作成します。 このインデックスを使用して、`array_view` オブジェクトの 3 番目の要素を出力します。 出力は 3 になります。  
  
```cpp  
 
int aCPP[] = {1, 2, 3, 4, 5};  
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout <<a[idx] <<"\n";    
// Output: 3  
 
```  
  
 次の例では、2 次元の `array_view` オブジェクト内で、行 = 1、列 = 2 にある要素を指定する 2 次元インデックスを作成します。 `index` コンストラクターの最初のパラメーターは行コンポーネントで、2 番目のパラメーターは列コンポーネントです。 出力は、6 です。  
  
```cpp  
 
int aCPP[] = {1, 2, 3,  
    4, 5, 6};  
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] <<"\n";  
// Output: 6  
 
```  
  
 次の例では、3 次元の `array_view` オブジェクト内で、奥行 = 0、行 = 1、列 = 3 にある要素を指定する 3 次元インデックスを作成します。 最初のパラメーターが奥行コンポーネント、2 番目のパラメーターが行コンポーネント、3 番目のパラメーターが列コンポーネントであることに注意してください。 出力は 8 です。  
  
```cpp  
 
int aCPP[] = {  
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,   
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};  
 
array_view<int, 3> a(2, 3, 4, aCPP);

// Specifies the element at 3, 1, 0.  
index<3> idx(0, 1, 3);

std::cout <<a[idx] <<"\n";  
 
// Output: 8  
 
```  
  
### <a name="extent-class"></a>extent クラス  
  [Extent クラス](../Topic/extent%20Class%20\(C++%20AMP\).md) の各次元のデータの長さを指定する、 `array` または `array_view` オブジェクトです。 範囲を作成し、範囲を使用して `array` または `array_view` オブジェクトを作成できます。 また、既存の `array` または `array_view` オブジェクトの範囲を取得することもできます。 次の例では、`array_view` オブジェクトの各次元の範囲の長さを出力します。  
  
```cpp  
 
int aCPP[] = {  
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,   
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};  
// There are 3 rows and 4 columns, and the depth is two.  
array_view<int, 3> a(2, 3, 4, aCPP);

std::cout <<"The number of columns is " <<a.extent[2] <<"\n";  
std::cout <<"The number of rows is " <<a.extent[1] <<"\n";  
std::cout <<"The depth is " <<a.extent[0]<<"\n";  
std::cout <<"Length in most significant dimension is " <<a.extent[0] <<"\n";  
 
```  
  
 次の例では、前の例のオブジェクトと同じ次元を持つ `array_view` オブジェクトを作成しますが、この例では、`extent` コンストラクターで明示的なパラメーターを使用する代わりに、`array_view` オブジェクトを使用します。  
  
```cpp  
 
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};  
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout <<"The number of columns is " <<a.extent[2] <<"\n";  
std::cout <<"The number of rows is " <<a.extent[1] <<"\n";  
std::cout <<"The depth is " <<a.extent[0] <<"\n";  
 
```  
  
## <a name="moving-data-to-the-accelerator-array-and-arrayview"></a>アクセラレータにデータを移動する: array と array_view  
 アクセラレータにデータを移動するために使用される 2 つのデータ コンテナーがランタイム ライブラリで定義されています。  [Array クラス](../../parallel/amp/reference/array-class.md) と [array_view クラス](../../parallel/amp/reference/array-view-class.md)します。 `array` クラスは、オブジェクトの構築時にデータの詳細コピーを作成するコンテナー クラスです。 `array_view` クラスは、カーネル関数がデータにアクセスするときにデータをコピーするラッパー クラスです。 ソース デバイスでデータが必要になったときは、データがコピーして戻されます。  
  
### <a name="array-class"></a>array クラス  
 `array` オブジェクトを構築するときに、データ セットへのポインターを含むコンストラクターを使用している場合、アクセラレータでデータの詳細コピーが作成されます。 カーネル関数は、アクセラレータ上のコピーを変更します。 カーネル関数の実行が終了すると、ソースのデータ構造にデータをコピーして戻す必要があります。 次の例では、ベクター内の各要素に 10 を乗算します。 カーネル関数が完了したら、[ベクター変換演算子]--brokenlink--(../Topic/array::operator%20std::vector%3Cvalue_type%3E%20Operator.md)is ベクター オブジェクトにデータをコピーするために使用します。  
  
```cpp  
 
std::vector<int> data(5);

for (int count = 0; count <5; count++)   
{  
    data[count] = count;  
}  
 
array<int, 1> a(5, data.begin(), data.end());

 
parallel_for_each(
    a.extent, 
 [=, &a](index<1> idx) restrict(amp)  
 {  
    a[idx] = a[idx]* 10;  
 });

 
data = a;  
for (int i = 0; i <5; i++)   
{  
    std::cout <<data[i] <<"\n";  
}  
 
```  
  
### <a name="arrayview-class"></a>array_view クラス  
 `array_view` のメンバーは `array` クラスとほとんど同じですが、基になる動作は同じではありません。 `array_view` コンストラクターに渡されるデータは、`array` コンストラクターの場合とは異なり、GPU に複製されません。 代わりに、カーネル関数が実行されたときに、データはアクセラレータにコピーされます。 したがって、同じデータを使用する `array_view` オブジェクトを 2 つ作成する場合、両方の `array_view` オブジェクトは同じメモリ空間を参照します。 この場合、マルチスレッド アクセスを同期する必要があります。 `array_view` クラスを使用する主な利点は、必要な場合にのみデータが移動されることです。  
  
### <a name="comparison-of-array-and-arrayview"></a>array と array_view の比較  
 次の表は、`array` クラスと `array_view` クラスの類似点と相違点をまとめたものです。  
  
|説明|array クラス|array_view クラス|  
|-----------------|-----------------|-----------------------|  
|ランクが決定されるとき|コンパイル時。|コンパイル時。|  
|範囲が決定されるとき|実行時。|実行時。|  
|形式|長方形。|長方形。|  
|データ ストレージ|データ コンテナーである。|データ ラッパーである。|  
|コピー|定義時の明示的な詳細コピー。|カーネル関数を使用してアクセスされた場合の暗黙のコピー。|  
|データの取得|配列データを CPU スレッド上のオブジェクトにコピーして戻すことによる。|直接アクセスして、 `array_view` オブジェクトまたはを呼び出すこと、 [array_view::synchronize メソッド](../Topic/array_view::synchronize%20Method.md) に継続元のコンテナーにデータにアクセスします。|  
  
### <a name="shared-memory-with-array-and-arrayview"></a>共有メモリと配列および array_view  
 共有メモリは、CPU とアクセラレータの両方からアクセスできるメモリです。 共有メモリの使用は CPU とアクセラレータ間でのデータのコピーによるオーバーヘッドを排除するか、大幅に低下させます。 メモリは共有されますが、CPU とアクセラレータの両方から同時にアクセスすることはできず、同時にアクセスすると未定義の動作が発生します。  
  
 関連するアクセラレータがサポートする場合、`array` オブジェクトを使用して、共有メモリの使用のきめ細かな制御を指定できます。 アクセラレータが共有メモリをサポートするかどうかは、アクセラレータのによって決まります [supports_cpu_shared_memory](../Topic/accelerator::supports_cpu_shared_memory%20Data%20Member.md) を返すプロパティ `true` 共有メモリがサポートされている場合。 共有メモリがサポートされている場合、既定 [access_type 列挙型](../Topic/access_type%20Enumeration.md) によって決定は、メモリ、アクセラレータ上での割り当て、 `default_cpu_access_type` プロパティです。 既定では、`array` オブジェクトと `array_view` のオブジェクトはプライマリに関連する `access_type` と同じ `accelerator` を取得します。  
  
 設定して、 [array::cpu_access_type データ メンバー](../Topic/array::cpu_access_type%20Data%20Member.md) のプロパティ、 `array` を明示的にきめ細かく制御できますか共有メモリを使用する、計算のカーネル メモリ アクセス パターンに基づいて、ハードウェアのパフォーマンス特性にアプリを最適化できるようにします。 `array_view` は、関連付けられている `cpu_access_type` と同じ `array` を反映するか、または、array_view がデータ ソースを使用せずに構築される場合は、その `access_type` は、まずストレージを割り当てるようにする環境を反映します。 つまり、まずホスト (CPU) によってアクセスされた場合は、CPU データ ソースに対して作成されたかのように動作し、キャプチャによって関連付けられた `access_type` の `accelerator_view` を共有します。ただし、まず `accelerator_view` によってアクセスされた場合は、その `array` 上で作成された `accelerator_view` に対して作成されたかのように動作し、`array` の `access_type` を共有します。  
  
 次のコード例では、既定のアクセラレータが共有メモリをサポートし、異なる cpu_access_type 構成を持つ複数の配列を作成するかどうかを確認する方法を説明します。  
  
```cpp  
#include <amp.h>  
#include <iostream>  
  
using namespace Concurrency;  
  
int main()  
{  
  accelerator acc = accelerator(accelerator::default_accelerator);  
  
  // Early out if the default accelerator doesn’t support shared memory.  
  if (!acc.supports_cpu_shared_memory)  
  {  
    std::cout << "The default accelerator does not support shared memory" << std::endl;  
    return 1;  
  }  
  
  // Override the default CPU access type.  
  acc.default_cpu_access_type = access_type_read_write  
  
  // Create an accelerator_view from the default accelerator. The  
  // accelerator_view inherits its default_cpu_access_type from acc.  
  accelerator_view acc_v = acc.default_view;  
  
  // Create an extent object to size the arrays.  
  extent<1> ex(10);  
  
  // Input array that can be written on the CPU.  
  array<int, 1> arr_w(ex, acc_v, access_type_write);  
  
  // Output array that can be read on the CPU.  
  array<int, 1> arr_r(ex, acc_v, access_type_read);  
  
  // Read-write array that can be both written to and read from on the CPU.  
  array<int, 1> arr_rw(ex, acc_v, access_type_read_write);  
}  
  
```  
  
## <a name="executing-code-over-data-parallelforeach"></a>データに対してコードを実行する: parallel_for_each  
  [Parallel_for_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 関数定義内のデータに対してアクセラレータで実行するコード、 `array` または `array_view` オブジェクトです。 このトピックの概要で示した次のコードを考えてます。  
  
```cpp  
  
#include <amp.h>  
#include <iostream>  
using namespace concurrency;  
  
void AddArrays() {  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5] = {0, 0, 0, 0, 0};  
  
    array_view<int, 1> a(5, aCPP);  
    array_view<int, 1> b(5, bCPP);  
    array_view<int, 1> sum(5, sumCPP);  
  
    parallel_for_each(  
        sum.extent,   
 [=](index<1> idx) restrict(amp)  
        {  
            sum[idx] = a[idx] + b[idx];  
        }  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
 `parallel_for_each` メソッドは、計算ドメインとラムダ式の 2 個の引数を使用します。  
  
  *計算ドメイン* は、 `extent` オブジェクトまたは `tiled_extent` の並列実行を作成するスレッドのセットを定義するオブジェクト。 計算ドメインの各要素について、1 つのスレッドが生成されます。 この場合、`extent` オブジェクトは 1 次元で、5 個の要素があります。 したがって、5 個のスレッドが開始されます。  
  
  *ラムダ式* 各スレッドで実行するコードを定義します。 Capture 句 `[=]`, 、ラムダ式の本体が、ここでは、値によってキャプチャされたすべての変数をアクセスすることを示す `a`, 、`b`, 、および `sum`です。 この例では、パラメーター リストは `index`という名前の 1 次元の `idx` 変数を作成します。 `idx[0]` の値は、最初のスレッドでは 0、それ以降の各スレッドでは 1 ずつ増加します。 `restrict(amp)` は、C++ AMP で高速化できる C++ 言語のサブセットのみが使用されることを示します。  Restrict 修飾子を持つ関数に関する制限事項については、「 [だけに制限する (C++ AMP)](../../cpp/restrict-cpp-amp.md)します。 詳細については、表示、 [ラムダ式の構文](../../cpp/lambda-expression-syntax.md)します。  
  
 ラムダ式では、実行するコードを含めることも、別のカーネル関数を呼び出すこともできます。 カーネル関数には `restrict(amp)` 修飾子を含める必要があります。 次の例は前の例と同じですが、別のカーネル関数を呼び出します。  
  
```cpp  
  
#include <amp.h>  
#include <iostream>  
using namespace concurrency;  
  
void AddElements(index<1> idx, array_view<int, 1> sum, array_view<int, 1> a, array_view<int, 1> b) restrict(amp)  
{  
    sum[idx] = a[idx] + b[idx];  
}  
  
void AddArraysWithFunction() {  
  
    int aCPP[] = {1, 2, 3, 4, 5};  
    int bCPP[] = {6, 7, 8, 9, 10};  
    int sumCPP[5] = {0, 0, 0, 0, 0};  
  
    array_view<int, 1> a(5, aCPP);  
    array_view<int, 1> b(5, bCPP);  
    array_view<int, 1> sum(5, sumCPP);  
  
    parallel_for_each(  
        sum.extent,   
 [=](index<1> idx) restrict(amp)  
        {  
            AddElements(idx, sum, a, b);  
        }  
    );  
  
    for (int i = 0; i < 5; i++) {  
        std::cout << sum[i] << "\n";  
    }  
}  
  
```  
  
## <a name="accelerating-code-tiles-and-barriers"></a>コードの加速化: タイルとバリア  
 タイルを使用することによって、さらに高速化を実現できます。 タイルのスレッドを等しい四角形のサブセットに分割するか、 *タイル*します。 データ セットと、コーディングしているアルゴリズムに基づいて、適切なタイトルのサイズを決定します。 アクセスがある各スレッドの *グローバル* 全体を基準としてのデータ要素の位置 `array` または `array_view` へのアクセスと、 *ローカル* タイルを基準としています。 ローカル インデックス値を使用すると、インデックス値をグローバルからローカルに変換するコードを記述する必要がないため、コードは簡略化されます。 タイルを使用して、呼び出して、 [extent::tile メソッド](../Topic/extent::tile%20Method.md) 、計算ドメインで、 `parallel_for_each` メソッド、および使用する、 [tiled_index](../../parallel/amp/reference/tiled-index-class.md) ラムダ式内のオブジェクト。  
  
 一般的なアプリケーションでは、タイルの要素はなんらかの方法で関連付けられており、コードではタイル全体で値にアクセスして追跡する必要があります。 使用して、 [tile_static キーワード](../Topic/tile_static%20Keyword.md) キーワードおよび [tile_barrier::wait メソッド](../Topic/tile_barrier::wait%20Method.md) これを実現します。 `tile_static` キーワードを持つ変数のスコープはタイル全体であり、各タイルについて、この変数のインスタンスが作成されます。 タイル スレッドの変数に対するアクセスの同期を処理する必要があります。  [Tile_barrier::wait メソッド](../Topic/tile_barrier::wait%20Method.md) 、タイル内のすべてのスレッドの呼び出しに達するまで、現在のスレッドの実行を停止 `tile_barrier::wait`します。 したがって、`tile_static` 変数を使用することによって、タイル全体で値を累積できます。 次に、すべての値にアクセスする必要がある計算を終了できます。  
  
 次の図は、タイルに配置されたサンプリング データの 2 次元配列を表します。  
  
 ![並べて表示されたエクステントのインデックス値](../../parallel/amp/media/camptiledgridexample.png "CampTiledGridExample")  
  
 次のコード例では、前の図のサンプリング データを使用します。 このコードは、タイル内の各値を、タイル内の値の平均に置き換えます。  
  
```cpp  
 
// Sample data:  
int sampledata[] = {  
    2, 2, 9, 7, 1, 4,  
    4, 4, 8, 8, 3, 4,  
    1, 5, 1, 2, 5, 2,  
    6, 8, 3, 2, 7, 2};  
 
// The tiles:  
// 2 2    9 7    1 4  
// 4 4    8 8    3 4  
//  
// 1 5    1 2    5 2  
// 6 8    3 2    7 2  
 
// Averages:  
int averagedata[] = {   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
    0, 0, 0, 0, 0, 0,   
};  
 
array_view<int, 2> sample(4, 6, sampledata);

array_view<int, 2> average(4, 6, averagedata);

 
parallel_for_each(*// Create threads for sample.extent and divide the extent into 2 x 2 tiles.  
    sample.extent.tile<2,2>(), 
 [=](tiled_index<2,2> idx) restrict(amp)  
 { *// Create a 2 x 2 array to hold the values in this tile.  
    tile_static int nums[2][2]; *// Copy the values for the tile into the 2 x 2 array.  
    nums[idx.local[1]][idx.local[0]] = sample[idx.global]; *// When all the threads have executed and the 2 x 2 array is complete, find the average.  
    idx.barrier.wait();
int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1]; *// Copy the average into the array_view.  
    average[idx.global] = sum / 4;  
 });

 
for (int i = 0; i <4; i++) {  
    for (int j = 0; j <6; j++) {  
    std::cout <<average(i,j) <<" ";  
 }  
    std::cout <<"\n";  
}  
 
// Output:  
// 3 3 8 8 3 3  
// 3 3 8 8 3 3  
// 5 5 2 2 4 4  
// 5 5 2 2 4 4  
 
```  
  
## <a name="math-libraries"></a>数値演算ライブラリ  
 C++ AMP には 2 つの数値演算ライブラリが含まれます。 倍精度ライブラリ、 [concurrency::precise_math 名前空間](../Topic/Concurrency::precise_math%20Namespace.md) 関数の倍精度サポートを提供します。 また、ハードウェアでの倍精度サポートは必要ですが、単精度関数もサポートします。 準拠、 [C99 仕様 (ISO/IEC 9899)](http://go.microsoft.com/fwlink/LinkId=225887)します。 アクセラレータは倍精度を完全にサポートしている必要があります。 値を確認するにはあるかどうかを指定できます、 [accelerator::supports_double_precision データ メンバー](../Topic/accelerator::supports_double_precision%20Data%20Member.md)します。 高速数値演算ライブラリで、 [concurrency::fast_math 名前空間](../../parallel/amp/reference/concurrency-fast-math-namespace.md), 、数値演算関数の別のセットが含まれています。 これらの関数は、`float` のオペランドのみをサポートするため、実行速度は速くなりますが、精度は倍精度数値演算ライブラリほど高くありません。 関数は \<amp_math.h> ヘッダー ファイルに含まれており、すべて `restrict(amp)` で宣言されます。 内の関数、\< cmath> ヘッダー ファイルは、両方にインポート、 `fast_math` と `precise_math` 名前空間。  `restrict` キーワードを使用して区別するために、\< cmath> バージョンおよび C++ AMP のバージョン。 次のコードは、計算のドメインにある各値の高速メソッドを使用して、10 を底とする対数を計算します。  
  
```cpp  
  
#include <amp.h>  
#include <amp_math.h>  
#include <iostream>  
using namespace concurrency;  
  
void MathExample() {  
  
    double numbers[] = { 1.0, 10.0, 60.0, 100.0, 600.0, 1000.0 };  
    array_view<double, 1> logs(6, numbers);  
  
    parallel_for_each(  
        logs.extent,  
 [=] (index<1> idx) restrict(amp) {  
            logs[idx] = concurrency::fast_math::log10(logs[idx]);  
        }  
    );  
  
    for (int i = 0; i < 6; i++) {  
        std::cout << logs[i] << "\n";  
    }  
}  
  
```  
  
## <a name="graphics-library"></a>グラフィックス ライブラリ  
 C++ AMP には、アクセラレータ機能を使用するグラフィックスのプログラミング用に設計されたグラフィックス ライブラリが含まれます。 このライブラリは、ネイティブ グラフィックス機能をサポートするデバイスでのみ使用されます。 メソッドは、 [concurrency::graphics 名前空間](../../parallel/amp/reference/concurrency-graphics-namespace.md) \< amp_graphics.h > ヘッダー ファイルに含まれるとします。 グラフィックス ライブラリの主要コンポーネントは次のとおりです。  
  
- [texture クラス](../Topic/texture%20Class.md): texture クラスを使用してメモリまたはファイルからテクスチャを作成することができます。 テクスチャは、データを格納するという点で配列に似ており、代入とコピーの構築の点では標準テンプレート ライブラリ (STL) のコンテナーに似ています。 詳細については、次を参照してください。 [STL コンテナー](../../standard-library/stl-containers.md)します。 `texture` クラスのテンプレート パラメーターは、要素型とランクです。 ランクには 1、2、または 3 を指定できます。 要素型には、後で説明する short ベクター型のいずれかを指定できます。  
  
- [writeonly_texture_view クラス](../Topic/writeonly_texture_view%20Class.md): すべてのテクスチャへの書き込み専用のアクセスを提供します。  
  
- [Short ベクター ライブラリ](http://msdn.microsoft.com/ja-jp/4c4f5bed-c396-493b-a238-c347563f645f): 2、3、および 4 に基づく、長さの short ベクター型のセットを定義 `int`, 、`uint`, 、`float`, 、`double`, 、[norm](../../parallel/amp/reference/norm-class.md), 、または [unorm](../../parallel/amp/reference/unorm-class.md)します。  
  
## <a name="includewin8appnamelongtokenwin8appnamelongmdmd-apps"></a>[!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] アプリ  
 他の C++ ライブラリと同様に、[!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] アプリで C++ AMP を使用できます。 C++、C#、Visual Basic、または JavaScript を使用して作成されたアプリに C++ AMP コードを含める方法については、次の記事を参照してください。  
  
- [Windows ストア アプリで C++ AMP の使用](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)  
  
- [チュートリアル: C++ および JavaScript による呼び出しでの基本的な Windows ランタイム コンポーネントの作成](http://go.microsoft.com/fwlink/p/LinkId=249077)  
  
- [Bing マップ トリップ オプティマイザーでは、JavaScript および C++ での Windows ストア アプリ](http://go.microsoft.com/fwlink/p/LinkId=249078)  
  
- [Windows ランタイムを使用して c# から C++ AMP を使用する方法](http://go.microsoft.com/fwlink/p/LinkId=249080)  
  
- [C# から C++ AMP を使用する方法](http://go.microsoft.com/fwlink/p/LinkId=249081)  
  
- [マネージ コードからネイティブ関数を呼び出す](../../dotnet/calling-native-functions-from-managed-code.md)  
  
## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP と同時実行ビジュアライザー  
 同時実行ビジュアライザーには、C++ AMP コードのパフォーマンスを分析するためのサポートが含まれます。 これらの機能については、次の記事を参照してください。  
  
- [GPU アクティビティ グラフ](../Topic/GPU%20Activity%20Graph.md)  
  
- [GPU アクティビティ (ページング)](../Topic/GPU%20Activity%20\(Paging\).md)  
  
- [GPU アクティビティ (このプロセス)](../Topic/GPU%20Activity%20\(This%20Process\).md)  
  
- [GPU アクティビティ (他のプロセス)](../Topic/GPU%20Activity%20\(Other%20Processes\).md)  
  
- [チャネル (スレッド ビュー)](../Topic/Channels%20\(Threads%20View\).md)  
  
- [同時実行ビジュアライザーで C++ AMP コードの分析](http://go.microsoft.com/fwlink/LinkID=253987&clcid=0x409)  
  
## <a name="performance-recommendations"></a>パフォーマンスに関する推奨事項  
 符号なし整数の剰余と除算のパフォーマンスは、符号付き整数の剰余と除算のパフォーマンスよりも優れています。 できる限り、符号なし整数を使用することをお勧めします。  
  
## <a name="see-also"></a>「  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [ラムダ式の構文](../../cpp/lambda-expression-syntax.md)   
 [リファレンス (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)   
 [ネイティブ コードのブログでの並列プログラミング](http://go.microsoft.com/fwlink/p/LinkId=238472)