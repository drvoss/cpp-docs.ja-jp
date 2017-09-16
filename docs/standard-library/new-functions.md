---
title: '&lt;new&gt; functions | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
caps.latest.revision: 10
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 5d026c375025b169d5db8445cbb52c0c917b2d8d
ms.openlocfilehash: 0f796dc89314f9f6ac6da5c54f9afd16604fd1f6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="ltnewgt-functions"></a>&lt;new&gt; functions
|||  
|-|-|  
|[nothrow](#nothrow)|[set_new_handler](#set_new_handler)|  
  
##  <a name="nothrow"></a>  nothrow  
 Provides an object to be used as an argument for the `nothrow` versions of **new** and **delete**.  
  
```  
extern const std::nothrow_t nothrow;  
```  
  
### <a name="remarks"></a>Remarks  
 The object is used as a function argument to match the parameter type [std::nothrow_t](../standard-library/nothrow-t-structure.md).  
  
### <a name="example"></a>Example  
  See [operator new](../standard-library/new-operators.md#op_new) and [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr) for examples of how `std::nothrow_t` is used as a function parameter.  
  
##  <a name="set_new_handler"></a>  set_new_handler  
 Installs a user function that is to be called when `operator new` fails in its attempt to allocate memory.  
  
```  
new_handler set_new_handler(new_handler Pnew) throw();
```  
  
### <a name="parameters"></a>Parameters  
 `Pnew`  
 The new_handler to be installed.  
  
### <a name="return-value"></a>Return Value  
 0 on the first call and the previous `new_handler` on subsequent calls.  
  
### <a name="remarks"></a>Remarks  
 The function stores `Pnew` in a static [new handler](../standard-library/new-typedefs.md#new_handler) pointer that it maintains, then returns the value previously stored in the pointer. The new handler is used by [operator new](../standard-library/new-operators.md#op_new)( **size_t**).  
  
### <a name="example"></a>Example  
  
```cpp  
// new_set_new_handler.cpp  
// compile with: /EHsc  
#include<new>  
#include<iostream>  
  
using namespace std;  
void __cdecl newhandler( )  
{  
   cout << "The new_handler is called:" << endl;  
   throw bad_alloc( );  
   return;  
}  
  
int main( )   
{  
   set_new_handler (newhandler);  
   try  
   {  
      while ( 1 )   
      {  
         new int[5000000];  
         cout << "Allocating 5000000 ints." << endl;  
      }  
   }  
   catch ( exception e )  
   {  
      cout << e.what( ) << endl;  
   }  
}  
```  
  
```Output  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
The new_handler is called:  
bad allocation  
```  
  
## <a name="see-also"></a>See Also  
 [\<new>](../standard-library/new.md)

