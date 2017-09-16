---
title: Message Sending and Receiving | Microsoft Docs
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
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
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
ms.openlocfilehash: cd090ae51edcc14d4b820a52de04b9637991b745
ms.contentlocale: ja-jp
ms.lasthandoff: 09/12/2017

---
# <a name="message-sending-and-receiving"></a>Message Sending and Receiving
Consider the sending part of the process and how the framework responds.  
  
 Most messages result from user interaction with the program. Commands are generated by mouse clicks in menu items or toolbar buttons or by accelerator keystrokes. The user also generates Windows messages by, for example, moving or resizing a window. Other Windows messages are sent when events such as program startup or termination occur, as windows get or lose the focus, and so on. Control-notification messages are generated by mouse clicks or other user interactions with a control, such as a button or list-box control in a dialog box.  
  
 The **Run** member function of class `CWinApp` retrieves messages and dispatches them to the appropriate window. Most command messages are sent to the main frame window of the application. The `WindowProc` predefined by the class library gets the messages and routes them differently, depending on the category of message received.  
  
 Now consider the receiving part of the process.  
  
 The initial receiver of a message must be a window object. Windows messages are usually handled directly by that window object. Command messages, usually originating in the application's main frame window, get routed to the command-target chain described in [Command Routing](../mfc/command-routing.md).  
  
 Each object capable of receiving messages or commands has its own message map that pairs a message or command with the name of its handler.  
  
 When a command-target object receives a message or command, it searches its message map for a match. If it finds a handler for the message, it calls the handler. For more information about how message maps are searched, see [How the Framework Searches Message Maps](../mfc/how-the-framework-searches-message-maps.md). Refer again to the figure [Commands in the Framework](../mfc/user-interface-objects-and-command-ids.md).  
  
## <a name="see-also"></a>See Also  
 [How the Framework Calls a Handler](../mfc/how-the-framework-calls-a-handler.md)

