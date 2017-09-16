---
title: COleIPFrameWnd Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
dev_langs:
- C++
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
caps.latest.revision: 24
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
ms.translationtype: MT
ms.sourcegitcommit: 4e0027c345e4d414e28e8232f9e9ced2b73f0add
ms.openlocfilehash: 5828a7a2eb54ca13e28127361de1ed2958fa8e75
ms.contentlocale: ja-jp
ms.lasthandoff: 09/12/2017

---
# <a name="coleipframewnd-class"></a>COleIPFrameWnd Class
The base for your application's in-place editing window.  
  
## <a name="syntax"></a>Syntax  
  
```  
class COleIPFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|Constructs a `COleIPFrameWnd` object.|  
  
### <a name="public-methods"></a>Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Called by the framework when an item is activated for in-place editing.|  
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Called by the framework to reposition the in-place editing window.|  
  
## <a name="remarks"></a>Remarks  
 This class creates and positions control bars within the container application's document window. It also handles notifications generated by an embedded [COleResizeBar](../../mfc/reference/coleresizebar-class.md) object when the user resizes the in-place editing window.  
  
 For more information on using `COleIPFrameWnd`, see the article [Activation](../../mfc/activation-cpp.md).  
  
## <a name="inheritance-hierarchy"></a>Inheritance Hierarchy  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `COleIPFrameWnd`  
  
## <a name="requirements"></a>Requirements  
 **Header:** afxole.h  
  
##  <a name="coleipframewnd"></a>  COleIPFrameWnd::COleIPFrameWnd  
 Constructs a `COleIPFrameWnd` object and initializes its in-place state information, which is stored in a structure of type **OLEINPLACEFRAMEINFO**.  
  
```  
COleIPFrameWnd();
```  
  
### <a name="remarks"></a>Remarks  
 For more information, see [OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737) in the Windows SDK.  
  
##  <a name="oncreatecontrolbars"></a>  COleIPFrameWnd::OnCreateControlBars  
 The framework calls the `OnCreateControlBars` function when an item is activated for in-place editing.  
  
```  
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,  
    CWnd* pWndDoc);

 
virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,  
    CFrameWnd* pWndDoc);
```  
  
### <a name="parameters"></a>Parameters  
 *pWndFrame*  
 Pointer to the container application's frame window.  
  
 *pWndDoc*  
 Pointer to the container's document-level window. Can be **NULL** if the container is an SDI application.  
  
### <a name="return-value"></a>Return Value  
 Nonzero on success; otherwise, 0.  
  
### <a name="remarks"></a>Remarks  
 The default implementation does nothing. Override this function to perform any special processing required when control bars are created.  
  
##  <a name="repositionframe"></a>  COleIPFrameWnd::RepositionFrame  
 The framework calls the `RepositionFrame` member function to lay out control bars and reposition the in-place editing window so all of it is visible.  
  
```  
virtual void RepositionFrame(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>Parameters  
 `lpPosRect`  
 Pointer to a `RECT` structure or a `CRect` object containing the in-place frame window's current position coordinates, in pixels, relative to the client area.  
  
 `lpClipRect`  
 Pointer to a `RECT` structure or a `CRect` object containing the in-place frame window's current clipping-rectangle coordinates, in pixels, relative to the client area.  
  
### <a name="remarks"></a>Remarks  
 Layout of control bars in the container window differs from that performed by a non-OLE frame window. The non-OLE frame window calculates the positions of control bars and other objects from a given frame-window size, as in a call to [CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). The client area is what remains after space for control bars and other objects is subtracted. A `COleIPFrameWnd` window, on the other hand, positions toolbars in accordance with a given client area. In other words, `CFrameWnd::RecalcLayout` works "from the outside in," whereas `COleIPFrameWnd::RepositionFrame` works "from the inside out."  
  
## <a name="see-also"></a>See Also  
 [MFC Sample HIERSVR](../../visual-cpp-samples.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)
