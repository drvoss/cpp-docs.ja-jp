---
title: Rubber-Banding and Trackers | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- trackers [MFC]
- CRectTracker class [MFC], implementing trackers
- OLE objects [MFC], selecting
- rubber banding [MFC]
- WM_LBUTTONDOWN [MFC]
ms.assetid: 0d0fa64c-6418-4baf-ab7f-2d16ca039230
caps.latest.revision: 10
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
ms.openlocfilehash: 3bf323ef1cd887b1f4dbc6129568249733000310
ms.contentlocale: ja-jp
ms.lasthandoff: 09/12/2017

---
# <a name="rubber-banding-and-trackers"></a>Rubber-Banding and Trackers
Another feature supplied with trackers is the "rubber-band" selection, which allows a user to select multiple OLE items by dragging a sizing rectangle around the items to be selected. When the user releases the left mouse button, items within the region selected by the user are selected and can be manipulated by the user. For instance, the user might drag the selection into another container application.  
  
 Implementing this feature requires some additional code in your application's `WM_LBUTTONDOWN` handler function.  
  
 The following code sample implements rubber-band selection and additional features.  
  
 [!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]  
  
 If you want to allow reversible orientation of the tracker during rubber-banding, you should call [CRectTracker::TrackRubberBand](../mfc/reference/crecttracker-class.md#trackrubberband) with the third parameter set to **TRUE**. Remember that allowing reversible orientation will sometimes cause [CRectTracker::m_rect](../mfc/reference/crecttracker-class.md#m_rect) to become inverted. This can be corrected by a call to [CRect::NormalizeRect](../atl-mfc-shared/reference/crect-class.md#normalizerect).  
  
 For more information, see [Container Client Items](../mfc/containers-client-items.md) and [Customizing Drag and Drop](../mfc/drag-and-drop-customizing.md).  
  
## <a name="see-also"></a>See Also  
 [Trackers: Implementing Trackers in Your OLE Application](../mfc/trackers-implementing-trackers-in-your-ole-application.md)   
 [CRectTracker Class](../mfc/reference/crecttracker-class.md)
