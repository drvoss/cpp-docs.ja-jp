---
title: CStatusBarCtrl Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStatusBarCtrl
- AFXCMN/CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::Create
- AFXCMN/CStatusBarCtrl::CreateEx
- AFXCMN/CStatusBarCtrl::DrawItem
- AFXCMN/CStatusBarCtrl::GetBorders
- AFXCMN/CStatusBarCtrl::GetIcon
- AFXCMN/CStatusBarCtrl::GetParts
- AFXCMN/CStatusBarCtrl::GetRect
- AFXCMN/CStatusBarCtrl::GetText
- AFXCMN/CStatusBarCtrl::GetTextLength
- AFXCMN/CStatusBarCtrl::GetTipText
- AFXCMN/CStatusBarCtrl::IsSimple
- AFXCMN/CStatusBarCtrl::SetBkColor
- AFXCMN/CStatusBarCtrl::SetIcon
- AFXCMN/CStatusBarCtrl::SetMinHeight
- AFXCMN/CStatusBarCtrl::SetParts
- AFXCMN/CStatusBarCtrl::SetSimple
- AFXCMN/CStatusBarCtrl::SetText
- AFXCMN/CStatusBarCtrl::SetTipText
dev_langs:
- C++
helpviewer_keywords:
- CStatusBarCtrl [MFC], CStatusBarCtrl
- CStatusBarCtrl [MFC], Create
- CStatusBarCtrl [MFC], CreateEx
- CStatusBarCtrl [MFC], DrawItem
- CStatusBarCtrl [MFC], GetBorders
- CStatusBarCtrl [MFC], GetIcon
- CStatusBarCtrl [MFC], GetParts
- CStatusBarCtrl [MFC], GetRect
- CStatusBarCtrl [MFC], GetText
- CStatusBarCtrl [MFC], GetTextLength
- CStatusBarCtrl [MFC], GetTipText
- CStatusBarCtrl [MFC], IsSimple
- CStatusBarCtrl [MFC], SetBkColor
- CStatusBarCtrl [MFC], SetIcon
- CStatusBarCtrl [MFC], SetMinHeight
- CStatusBarCtrl [MFC], SetParts
- CStatusBarCtrl [MFC], SetSimple
- CStatusBarCtrl [MFC], SetText
- CStatusBarCtrl [MFC], SetTipText
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
caps.latest.revision: 20
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
ms.openlocfilehash: 4fc280d73aaef923e1045a20870d6659ecfa49d2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/12/2017

---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl Class
Provides the functionality of the Windows common status bar control.  
  
## <a name="syntax"></a>Syntax  
  
```  
class CStatusBarCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[CStatusBarCtrl::CStatusBarCtrl](#cstatusbarctrl)|Constructs a `CStatusBarCtrl` object.|  
  
### <a name="public-methods"></a>Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CStatusBarCtrl::Create](#create)|Creates a status bar control and attaches it to a `CStatusBarCtrl` object.|  
|[CStatusBarCtrl::CreateEx](#createex)|Creates a status bar control with the specified Windows extended styles and attaches it to a `CStatusBarCtrl` object.|  
|[CStatusBarCtrl::DrawItem](#drawitem)|Called when a visual aspect of an owner-draw status bar control changes.|  
|[CStatusBarCtrl::GetBorders](#getborders)|Retrieves the current widths of the horizontal and vertical borders of a status bar control.|  
|[CStatusBarCtrl::GetIcon](#geticon)|Retrieves the icon for a part (also known as a pane) in the current status bar control.|  
|[CStatusBarCtrl::GetParts](#getparts)|Retrieves a count of the parts in a status bar control.|  
|[CStatusBarCtrl::GetRect](#getrect)|Retrieves the bounding rectangle of a part in a status bar control.|  
|[CStatusBarCtrl::GetText](#gettext)|Retrieves the text from the given part of a status bar control.|  
|[CStatusBarCtrl::GetTextLength](#gettextlength)|Retrieve the length, in characters, of the text from the given part of a status bar control.|  
|[CStatusBarCtrl::GetTipText](#gettiptext)|Retrieves the tooltip text for a pane in a status bar.|  
|[CStatusBarCtrl::IsSimple](#issimple)|Checks a status window control to determine if it is in simple mode.|  
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|Sets the background color in a status bar.|  
|[CStatusBarCtrl::SetIcon](#seticon)|Sets the icon for a pane in a status bar.|  
|[CStatusBarCtrl::SetMinHeight](#setminheight)|Sets the minimum height of a status bar control's drawing area.|  
|[CStatusBarCtrl::SetParts](#setparts)|Sets the number of parts in a status bar control and the coordinate of the right edge of each part.|  
|[CStatusBarCtrl::SetSimple](#setsimple)|Specifies whether a status bar control displays simple text or displays all control parts set by a previous call to `SetParts`.|  
|[CStatusBarCtrl::SetText](#settext)|Sets the text in the given part of a status bar control.|  
|[CStatusBarCtrl::SetTipText](#settiptext)|Sets the tooltip text for a pane in a status bar.|  
  
## <a name="remarks"></a>Remarks  
 A "status bar control" is a horizontal window, usually displayed at the bottom of a parent window, in which an application can display various kinds of status information. The status bar control can be divided into parts to display more than one type of information.  
  
 This control (and therefore the `CStatusBarCtrl` class) is available only to programs running under Windows 95/98 and Windows NT version 3.51 and later.  
  
 For more information on using `CStatusBarCtrl`, see [Controls](../../mfc/controls-mfc.md) and [Using CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Inheritance Hierarchy  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CStatusBarCtrl`  
  
## <a name="requirements"></a>Requirements  
 **Header:** afxcmn.h  
  
##  <a name="create"></a>  CStatusBarCtrl::Create  
 Creates a status bar control and attaches it to a `CStatusBarCtrl` object.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parameters  
 `dwStyle`  
 Specifies the status bar control's style. Apply any combination of status bar control styles listed in [Common Control Styles](http://msdn.microsoft.com/library/windows/desktop/bb775498) in the Windows SDK. This parameter must include the **WS_CHILD** style. It should also include the **WS_VISIBLE** style.  
  
 `rect`  
 Specifies the status bar control's size and position. It can be either a [CRect](../../atl-mfc-shared/reference/crect-class.md) object or a [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure.  
  
 `pParentWnd`  
 Specifies the status bar control's parent window, usually a `CDialog`. It must not be **NULL.**  
  
 `nID`  
 Specifies the status bar control's ID.  
  
### <a name="return-value"></a>Return Value  
 Nonzero if successful; otherwise zero.  
  
### <a name="remarks"></a>Remarks  
 You construct a `CStatusBarCtrl` in two steps. First, call the constructor, and then call **Create**, which creates the status bar control and attaches it to the `CStatusBarCtrl` object.  
  
 The default position of a status window is along the bottom of the parent window, but you can specify the `CCS_TOP` style to have it appear at the top of the parent window's client area. You can specify the **SBARS_SIZEGRIP** style to include a sizing grip at the right end of the status window. Combining the `CCS_TOP` and **SBARS_SIZEGRIP** styles is not recommended, because the resulting sizing grip is not functional even though the system draws it in the status window.  
  
 To create a status bar with extended window styles, call [CStatusBarCtrl::CreateEx](#createex) instead of **Create**.  
  
### <a name="example"></a>Example  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]  
  
##  <a name="createex"></a>  CStatusBarCtrl::CreateEx  
 Creates a control (a child window) and associates it with the `CStatusBarCtrl` object.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parameters  
 `dwExStyle`  
 Specifies the extended style of the control being created. For a list of extended Windows styles, see the `dwExStyle` parameter for [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) in the Windows SDK.  
  
 `dwStyle`  
 Specifies the status bar control's style. Apply any combination of status bar control styles listed in [Common Control Styles](http://msdn.microsoft.com/library/windows/desktop/bb775498) in the Windows SDK. This parameter must include the **WS_CHILD** style. It should also include the **WS_VISIBLE** style.  
  
 `rect`  
 A reference to a [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure describing the size and position of the window to be created, in client coordinates of `pParentWnd`.  
  
 `pParentWnd`  
 A pointer to the window that is the control's parent.  
  
 `nID`  
 The control's child-window ID.  
  
### <a name="return-value"></a>Return Value  
 Nonzero if successful; otherwise 0.  
  
### <a name="remarks"></a>Remarks  
 Use `CreateEx` instead of [Create](#create) to apply extended Windows styles, specified by the Windows extended style preface **WS_EX_**.  
  
##  <a name="cstatusbarctrl"></a>  CStatusBarCtrl::CStatusBarCtrl  
 Constructs a `CStatusBarCtrl` object.  
  
```  
CStatusBarCtrl();
```  
  
##  <a name="drawitem"></a>  CStatusBarCtrl::DrawItem  
 Called by the framework when a visual aspect of an owner-draw status bar control changes.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parameters  
 `lpDrawItemStruct`  
 A long pointer to a [DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802) structure that contains information about the type of drawing required.  
  
### <a name="remarks"></a>Remarks  
 The **itemAction** member of the `DRAWITEMSTRUCT` structure defines the drawing action that is to be performed.  
  
 By default, this member function does nothing. Override this member function to implement drawing for an owner-draw `CStatusBarCtrl` object.  
  
 The application should restore all graphics device interface (GDI) objects selected for the display context supplied in `lpDrawItemStruct` before this member function terminates.  
  
##  <a name="getborders"></a>  CStatusBarCtrl::GetBorders  
 Retrieves the status bar control's current widths of the horizontal and vertical borders and of the space between rectangles.  
  
```  
BOOL GetBorders(int* pBorders) const;  
  
BOOL GetBorders(
    int& nHorz,  
    int& nVert,  
    int& nSpacing) const;  
```  
  
### <a name="parameters"></a>Parameters  
 *pBorders*  
 Address of an integer array having three elements. The first element receives the width of the horizontal border, the second receives the width of the vertical border, and the third receives the width of the border between rectangles.  
  
 *nHorz*  
 Reference to an integer that receives the width of the horizontal border.  
  
 *nVert*  
 Reference to an integer that receives the width of the vertical border.  
  
 *nSpacing*  
 Reference to an integer that receives the width of the border between rectangles.  
  
### <a name="return-value"></a>Return Value  
 Nonzero if successful; otherwise zero.  
  
### <a name="remarks"></a>Remarks  
 These borders determine the spacing between the outside edge of the control and the rectangles within the control that contain text.  
  
### <a name="example"></a>Example  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]  
  
##  <a name="geticon"></a>  CStatusBarCtrl::GetIcon  
 Retrieves the icon for a part (also known as a pane) in the current status bar control.  
  
```  
HICON GetIcon(int iPart) const;  
```  
  
### <a name="parameters"></a>Parameters  
  
|Parameter|Description|  
|---------------|-----------------|  
|[in] `iPart`|The zero-based index of the part that contains the icon to be retrieved. If this parameter is -1, the status bar is assumed to be a simple mode status bar.|  
  
### <a name="return-value"></a>Return Value  
 The handle to the icon if the method successful; otherwise, `NULL`.  
  
### <a name="remarks"></a>Remarks  
 This method sends the [SB_GETICON](http://msdn.microsoft.com/library/windows/desktop/bb760744) message, which is described in the Windows SDK.  
  
 A status bar control consists of a row of text output panes, which are also known as parts. For more information about the status bar, see [Status Bar Implementation in MFC](../../mfc/status-bar-implementation-in-mfc.md) and [Setting the Mode of a CStatusBarCtrl Object](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).  
  
### <a name="example"></a>Example  
 The following code example defines a variable, `m_statusBar`, that is used to access the current status bar control. This variable is used in the next example.  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]  
  
### <a name="example"></a>Example  
 The following code example copies an icon to two panes of the current status bar control. In an earlier section of the code example we created a status bar control with three panes and then added an icon to the first pane. This example retrieves the icon from the first pane and then adds it to the second and third pane.  
  
 [!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]  
  
##  <a name="getparts"></a>  CStatusBarCtrl::GetParts  
 Retrieves a count of the parts in a status bar control.  
  
```  
int GetParts(
    int nParts,  
    int* pParts) const;  
```  
  
### <a name="parameters"></a>Parameters  
 `nParts`  
 Number of parts for which to retrieve coordinates. If this parameter is greater than the number of parts in the control, the message retrieves coordinates for existing parts only.  
  
 *pParts*  
 Address of an integer array having the same number of elements as the number of parts specified by `nParts`. Each element in the array receives the client coordinate of the right edge of the corresponding part. If an element is set to - 1, the position of the right edge for that part extends to the right edge of the status bar.  
  
### <a name="return-value"></a>Return Value  
 The number of parts in the control if successful, or zero otherwise.  
  
### <a name="remarks"></a>Remarks  
 This member function also retrieves the coordinate of the right edge of the given number of parts.  
  
### <a name="example"></a>Example  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]  
  
##  <a name="getrect"></a>  CStatusBarCtrl::GetRect  
 Retrieves the bounding rectangle of a part in a status bar control.  
  
```  
BOOL GetRect(
    int nPane,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parameters  
 `nPane`  
 Zero-based index of the part whose bounding rectangle is to be retrieved.  
  
 `lpRect`  
 Address of a [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure that receives the bounding rectangle.  
  
### <a name="return-value"></a>Return Value  
 Nonzero if successful; otherwise zero.  
  
### <a name="example"></a>Example  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]  
  
##  <a name="gettext"></a>  CStatusBarCtrl::GetText  
 Retrieves the text from the given part of a status bar control.  
  
```  
CString GetText(
    int nPane,  
    int* pType = NULL) const;  
  
int GetText(
    LPCTSTR lpszText,  
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>Parameters  
 `lpszText`  
 Address of the buffer that receives the text. This parameter is a null-terminated string.  
  
 `nPane`  
 Zero-based index of the part from which to retrieve text.  
  
 `pType`  
 Pointer to an integer that receives the type information. The type can be one of these values:  
  
- **0** The text is drawn with a border to appear lower than the plane of the status bar.  
  
- `SBT_NOBORDERS` The text is drawn without borders.  
  
- `SBT_POPOUT` The text is drawn with a border to appear higher than the plane of the status bar.  
  
- `SBT_OWNERDRAW` If the text has the `SBT_OWNERDRAW` drawing type, `pType` receives this message and returns the 32-bit value associated with the text instead of the length and operation type.  
  
### <a name="return-value"></a>Return Value  
 The length, in characters, of the text or a [CString](../../atl-mfc-shared/reference/cstringt-class.md) containing the current text.  
  
### <a name="example"></a>Example  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]  
  
##  <a name="gettextlength"></a>  CStatusBarCtrl::GetTextLength  
 Retrieves the length, in characters, of the text from the given part of a status bar control.  
  
```  
int GetTextLength(
    int nPane,  
    int* pType = NULL) const;  
```  
  
### <a name="parameters"></a>Parameters  
 `nPane`  
 Zero-based index of the part from which to retrieve text.  
  
 `pType`  
 Pointer to an integer that receives the type information. The type can be one of these values:  
  
- **0** The text is drawn with a border to appear lower than the plane of the status bar.  
  
- `SBT_NOBORDERS` The text is drawn without borders.  
  
- `SBT_OWNERDRAW` The text is drawn by the parent window.  
  
- `SBT_POPOUT` The text is drawn with a border to appear higher than the plane of the status bar.  
  
### <a name="return-value"></a>Return Value  
 The length, in characters, of the text.  
  
### <a name="example"></a>Example  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]  
  
##  <a name="gettiptext"></a>  CStatusBarCtrl::GetTipText  
 Retrieves the tooltip text for a pane in a status bar.  
  
```  
CString GetTipText(int nPane) const;  
```  
  
### <a name="parameters"></a>Parameters  
 `nPane`  
 The zero-based index of status bar pane to receive the tooltip text.  
  
### <a name="return-value"></a>Return Value  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) object containing the text to be used in the tooltip.  
  
### <a name="remarks"></a>Remarks  
 This member function implements the behavior of the Win32 message [SB_GETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760751), as described in the Windows SDK.  
  
### <a name="example"></a>Example  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]  
  
##  <a name="issimple"></a>  CStatusBarCtrl::IsSimple  
 Checks a status window control to determine if it is in simple mode.  
  
```  
BOOL IsSimple() const;  
```  
  
### <a name="return-value"></a>Return Value  
 Nonzero if the status window control is in simple mode; otherwise zero.  
  
### <a name="remarks"></a>Remarks  
 This member function implements the behavior of the Win32 message [SB_ISSIMPLE](http://msdn.microsoft.com/library/windows/desktop/bb760753), as described in the Windows SDK.  
  
##  <a name="setbkcolor"></a>  CStatusBarCtrl::SetBkColor  
 Sets the background color in a status bar.  
  
```  
COLORREF SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>Parameters  
 `cr`  
 **COLORREF** value that specifies the new background color. Specify the `CLR_DEFAULT` value to cause the status bar to use its default background color.  
  
### <a name="return-value"></a>Return Value  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) value that represents the previous default background color.  
  
### <a name="remarks"></a>Remarks  
 This member function implements the behavior of the Win32 message [SB_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760754), as described in the Windows SDK.  
  
### <a name="example"></a>Example  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]  
  
##  <a name="seticon"></a>  CStatusBarCtrl::SetIcon  
 Sets the icon for a pane in a status bar.  
  
```  
BOOL SetIcon(
    int nPane,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Parameters  
 `nPane`  
 The zero-based index of the pane that will receive the icon. If this parameter is -1, the status bar is assumed to be a simple status bar.  
  
 `hIcon`  
 Handle to the icon to be set. If this value is **NULL**, the icon is removed from the part.  
  
### <a name="return-value"></a>Return Value  
 Nonzero if successful; otherwise zero.  
  
### <a name="remarks"></a>Remarks  
 This member function implements the behavior of the Win32 message [SB_SETICON](http://msdn.microsoft.com/library/windows/desktop/bb760755), as described in the Windows SDK.  
  
### <a name="example"></a>Example  
  See the example for [CStatusBarCtrl::SetBkColor](#setbkcolor).  
  
##  <a name="setminheight"></a>  CStatusBarCtrl::SetMinHeight  
 Sets the minimum height of a status bar control's drawing area.  
  
```  
void SetMinHeight(int nMin);
```  
  
### <a name="parameters"></a>Parameters  
 `nMin`  
 Minimum height, in pixels, of the control.  
  
### <a name="remarks"></a>Remarks  
 The minimum height is the sum of `nMin` and twice the width, in pixels, of the vertical border of the status bar control.  
  
### <a name="example"></a>Example  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]  
  
##  <a name="setparts"></a>  CStatusBarCtrl::SetParts  
 Sets the number of parts in a status bar control and the coordinate of the right edge of each part.  
  
```  
BOOL SetParts(
    int nParts,  
    int* pWidths);
```  
  
### <a name="parameters"></a>Parameters  
 `nParts`  
 Number of parts to set. The number of parts cannot be greater than 255.  
  
 *pWidths*  
 Address of an integer array having the same number of elements as parts specified by `nParts`. Each element in the array specifies the position, in client coordinates, of the right edge of the corresponding part. If an element is - 1, the position of the right edge for that part extends to the right edge of the control.  
  
### <a name="return-value"></a>Return Value  
 Nonzero if successful; otherwise zero.  
  
### <a name="example"></a>Example  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]  
  
##  <a name="setsimple"></a>  CStatusBarCtrl::SetSimple  
 Specifies whether a status bar control displays simple text or displays all control parts set by a previous call to [SetParts](#setparts).  
  
```  
BOOL SetSimple(BOOL bSimple = TRUE);
```  
  
### <a name="parameters"></a>Parameters  
 [in] `bSimple`  
 Display-type flag. If this parameter is `TRUE`, the control displays simple text; if it is `FALSE`, it displays multiple parts.  
  
### <a name="return-value"></a>Return Value  
 Always returns 0.  
  
### <a name="remarks"></a>Remarks  
 If your application changes the status bar control from non-simple to simple, or vice versa, the system immediately redraws the control.  
  
##  <a name="settext"></a>  CStatusBarCtrl::SetText  
 Sets the text in the given part of a status bar control.  
  
```  
BOOL SetText(
    LPCTSTR lpszText,  
    int nPane,  
    int nType);
```  
  
### <a name="parameters"></a>Parameters  
 `lpszText`  
 Address of a null-terminated string specifying the text to set. If `nType` is `SBT_OWNERDRAW`, `lpszText` represents 32 bits of data.  
  
 `nPane`  
 Zero-based index of the part to set. If this value is 255, the status bar control is assumed to be a simple control having only one part.  
  
 `nType`  
 Type of drawing operation. See [SB_SETTEXT message](http://msdn.microsoft.com/library/bb760758\(vs.85\).aspx) for a list of possible values.  
  
### <a name="return-value"></a>Return Value  
 Nonzero if successful; otherwise zero.  
  
### <a name="remarks"></a>Remarks  
 The message invalidates the portion of the control that has changed, causing it to display the new text when the control next receives the `WM_PAINT` message.  
  
### <a name="example"></a>Example  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]  
  
##  <a name="settiptext"></a>  CStatusBarCtrl::SetTipText  
 Sets the tooltip text for a pane in a status bar.  
  
```  
void SetTipText(
    int nPane,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>Parameters  
 `nPane`  
 The zero-based index of status bar pane to receive the tooltip text.  
  
 *pszTipText*  
 A pointer to a string containing the tooltip text.  
  
### <a name="remarks"></a>Remarks  
 This member function implements the behavior of the Win32 message [SB_SETTIPTEXT](http://msdn.microsoft.com/library/windows/desktop/bb760759), as described in the Windows SDK.  
  
### <a name="example"></a>Example  
 [!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]  
  
## <a name="see-also"></a>See Also  
 [CWnd Class](../../mfc/reference/cwnd-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl Class](../../mfc/reference/ctoolbarctrl-class.md)
