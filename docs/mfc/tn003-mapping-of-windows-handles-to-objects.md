---
title: 'TN003: Mapping of Windows Handles to Objects | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mapping
dev_langs:
- C++
helpviewer_keywords:
- TN003
- handle maps
- Windows handles to objects [MFC]
- mappings [MFC]], Windows handles to objects
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
caps.latest.revision: 15
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
ms.translationtype: HT
ms.sourcegitcommit: 4e0027c345e4d414e28e8232f9e9ced2b73f0add
ms.openlocfilehash: b1ae730c803bd8c8e4e3f5c5a700ccfb52fb738e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/12/2017

---
# <a name="tn003-mapping-of-windows-handles-to-objects"></a>TN003: Mapping of Windows Handles to Objects
This note describes the MFC routines that support mapping Windows object handles to C++ objects.  
  
## <a name="the-problem"></a>The Problem  
 Windows objects are typically represented by various [HANDLE](http://msdn.microsoft.com/library/windows/desktop/aa383751) objects The MFC classes wrap Windows object handles with C++ objects. The handle wrapping functions of the MFC class library let you find the C++ object that is wrapping the Windows object that has a particular handle. However, sometimes an object does not have a C++ wrapper object and at these times the system creates a temporary object to act as the C++ wrapper.  
  
 The Windows objects that use handle maps are as follows:  
  
-   HWND ([CWnd](../mfc/reference/cwnd-class.md) and `CWnd`-derived classes)  
  
-   HDC ([CDC](../mfc/reference/cdc-class.md) and `CDC`-derived classes)  
  
-   HMENU ([CMenu](../mfc/reference/cmenu-class.md))  
  
-   HPEN ([CGdiObject](../mfc/reference/cgdiobject-class.md))  
  
-   HBRUSH (`CGdiObject`)  
  
-   HFONT (`CGdiObject`)  
  
-   HBITMAP (`CGdiObject`)  
  
-   HPALETTE (`CGdiObject`)  
  
-   HRGN (`CGdiObject`)  
  
-   HIMAGELIST ([CImageList](../mfc/reference/cimagelist-class.md))  
  
-   SOCKET ([CSocket](../mfc/reference/csocket-class.md))  
  
 Given a handle to any one of these objects, you can find the MFC object that wraps the handle by calling the static method `FromHandle`. For example, given an HWND called `hWnd`, the following line will return a pointer to the `CWnd` that wraps `hWnd`:  
  
```  
CWnd::FromHandle(hWnd)  
```  
  
 If `hWnd` does not have a specific wrapper object, a temporary `CWnd` is created to wrap `hWnd`. This makes it possible to obtain a valid C++ object from any handle.  
  
 After you have a wrapper object, you can retrieve its handle from a public member variable of the wrapper class. In the case of a `CWnd`, `m_hWnd` contains the HWND for that object.  
  
## <a name="attaching-handles-to-mfc-objects"></a>Attaching Handles to MFC Objects  
 Given a newly created handle-wrapper object and a handle to a Windows object, you can associate the two by calling the `Attach` function as in this example:  
  
```  
CWnd myWnd;  
myWnd.Attach(hWnd);
```  
  
 This makes an entry in the permanent map associating `myWnd` and `hWnd`. Calling `CWnd::FromHandle(hWnd)` will now return a pointer to `myWnd`. When `myWnd` is deleted, the destructor will automatically destroy `hWnd` by calling the Windows [DestroyWindow](http://msdn.microsoft.com/library/windows/desktop/ms632682) function. If this is not desired, `hWnd` must be detached from `myWnd` before `myWnd` is destroyed (normally when leaving the scope at which `myWnd` was defined). The `Detach` method does this.  
  
```  
myWnd.Detach();
```  
  
## <a name="more-about-temporary-objects"></a>More About Temporary Objects  
 Temporary objects are created whenever `FromHandle` is given a handle that does not already have a wrapper object. These temporary objects are detached from their handle and deleted by the `DeleteTempMap` functions. By default [CWinThread::OnIdle](../mfc/reference/cwinthread-class.md#onidle) automatically calls `DeleteTempMap` for each class that supports temporary handle maps. This means that you cannot assume a pointer to a temporary object will be valid past the point of exit from the function where the pointer was obtained.  
  
## <a name="wrapper-objects-and-multiple-threads"></a>Wrapper Objects and Multiple Threads  
 Both temporary and permanent objects are maintained on a per-thread basis. That is, one thread cannot access another thread's C++ wrapper objects, regardless of whether it is temporary or permanent.  
  
 To pass these objects from one thread to another, always send them as their native `HANDLE` type. Passing a C++ wrapper object from one thread to another will often cause unexpected results.  
  
## <a name="see-also"></a>See Also  
 [Technical Notes by Number](../mfc/technical-notes-by-number.md)   
 [Technical Notes by Category](../mfc/technical-notes-by-category.md)

