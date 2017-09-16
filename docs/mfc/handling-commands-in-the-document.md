---
title: Handling Commands in the Document | Microsoft Docs
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
- message maps [MFC]], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 4e0027c345e4d414e28e8232f9e9ced2b73f0add
ms.openlocfilehash: 2e678a1f1e82ab405cd7d95c47c7771ebb7cb36d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/12/2017

---
# <a name="handling-commands-in-the-document"></a>Handling Commands in the Document
Your document class may also handle certain commands generated by menu items, toolbar buttons, or accelerator keys. By default, **CDocument** handles the Save and Save As commands on the File menu, using serialization. Other commands that affect the data may also be handled by member functions of your document. For example, in the Scribble program, class `CScribDoc` provides a handler for the Edit Clear All command, which deletes all of the data currently stored in the document. Documents can have message maps, but unlike views, documents cannot handle standard Windows messages — only **WM_COMMAND** messages, or "commands."  
  
## <a name="see-also"></a>See Also  
 [Using Documents](../mfc/using-documents.md)

