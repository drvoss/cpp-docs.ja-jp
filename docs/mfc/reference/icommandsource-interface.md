---
title: ICommandSource Interface | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandSource
- AFXWINFORMS/ICommandSource
- AFXWINFORMS/ICommandSource::AddCommandHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeHandler
- AFXWINFORMS/ICommandSource::AddCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::AddCommandUIHandler
- AFXWINFORMS/ICommandSource::PostCommand
- AFXWINFORMS/ICommandSource::RemoveCommandHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeHandler
- AFXWINFORMS/ICommandSource::RemoveCommandRangeUIHandler
- AFXWINFORMS/ICommandSource::RemoveCommandUIHandler
- AFXWINFORMS/ICommandSource::SendCommand
dev_langs:
- C++
helpviewer_keywords:
- ICommandSource interface [MFC]
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
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
ms.openlocfilehash: 0597617c7127e17ec4b8e97a00c8b22412489bdf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/12/2017

---
# <a name="icommandsource-interface"></a>ICommandSource Interface
Manages commands sent from a command source object to a user control.  
  
## <a name="syntax"></a>Syntax  
  
```  
interface class ICommandSource  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[ICommandSource::AddCommandHandler](#addcommandhandler)|Adds a command handler to a command source object.|  
|[ICommandSource::AddCommandRangeHandler](#addcommandrangehandler)|Adds a group of command handlers to a command source object.|  
|[ICommandSource::AddCommandRangeUIHandler](#addcommandrangeuihandler)|Adds a group of user interface command message handlers to a command source object.|  
|[ICommandSource::AddCommandUIHandler](#addcommandrangeuihandler)|Adds a user interface command message handler to a command source object.|  
|[ICommandSource::PostCommand](#postcommand)|Posts a message without waiting for it to be processed.|  
|[ICommandSource::RemoveCommandHandler](#removecommandhandler)|Removes a command handler from a command source object.|  
|[ICommandSource::RemoveCommandRangeHandler](#removecommandrangehandler)|Removes a group of command handlers from a command source object.|  
|[ICommandSource::RemoveCommandRangeUIHandler](#removecommandrangeuihandler)|Removes a group of user interface command message handlers from a command source object.|  
|[ICommandSource::RemoveCommandUIHandler](#removecommandrangeuihandler)|Removes a user interface command message handler from a command source object.|  
|[ICommandSource::SendCommand](#sendcommand)|Sends a message and waits for it to be processed before returning.|  
  
### <a name="remarks"></a>Remarks  
 When you host a user control in an MFC View, [CWinFormsView Class](../../mfc/reference/cwinformsview-class.md) routes commands and update command UI messages to the user control to allow it to handle MFC commands (for example, frame menu items and toolbar buttons). By implementing [ICommandTarget Interface](../../mfc/reference/icommandtarget-interface.md), you give the user control a reference to the `ICommandSource` object.  
  
 See [How to: Add Command Routing to the Windows Forms Control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) for an example of how to use `ICommandTarget`.  
  
 For more information on using Windows Forms, see [Using a Windows Form User Control in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
### <a name="requirements"></a>Requirements  
 **Header:** afxwinforms.h (defined in assembly atlmfc\lib\mfcmifc80.dll)  
  
## <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler
Adds a command handler to a command source object.
```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Parameters  
`cmdID`  
The command ID.  
`cmdHandler`  
A handle to the command handler method.

### <a name="remarks"></a>Remarks
This method adds the command handler cmdHandler to the command source object and maps the handler to cmdID.
See [How to: Add Command Routing to the Windows Forms Control](https://msdn.microsoft.com/library/y33d8624.aspx) for an example of how to use AddCommandHandler.

## <a name="addcommandrangehandler"></a> ICommandSource::AddCommandRangeHandler

Adds a group of command handlers to a command source object.
```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```
### <a name="parameters"></a>Parameters  
`cmdIDMin`  
The beginning index of the command ID range.
`cmdIDMax`  
The ending index of the command ID range.
`cmdHandler`  
A handle to the message handler method to which the commands are mapped.
### <a name="remarks"></a>Remarks
This method maps a contiguous range of command IDs to a single message handler and adds it to the command source object. This is used for handling a group of related buttons with one method.

## <a name="addcommandrangeuihandler"></a> ICommandSource::AddCommandRangeUIHandler
Adds a group of user interface command message handlers to a command source object.
```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin, 
    unsigned int cmdIDMax, 
    CommandUIHandler^ cmdUIHandler);
```
### <a name="parameters"></a>Parameters  
`cmdIDMin`  
The beginning index of the command ID range.
`cmdIDMax`  
The ending index of the command ID range.
`cmdHandler`  
A handle to the message handler method to which the commands are mapped.

### <a name="remarks"></a>Remarks
This method maps a contiguous range of command IDs to a single user interface command message handler and adds it to the command source object. This is used for handling a group of related buttons with one method.

## <a name="addcommanduihandler"></a> ICommandSource::AddCommandUIHandler
Adds a user interface command message handler to a command source object.
```
void AddCommandUIHandler(
    unsigned int cmdID, 
    CommandUIHandler^ cmdUIHandler);
```
### <a name="parameters"></a>Parameters
`cmdID`  
The command ID.  
`cmdUIHandler`  
A handle to the user interface command message handler method.

### <a name="remarks"></a>Remarks
This method adds the user interface command message handler cmdHandler to the command source object and maps the handler to cmdID.

## <a name="postcommand"></a> ICommandSource::PostCommand
Posts a message without waiting for it to be processed.
```
void PostCommand(unsigned int command);
```
### <a name="parameters"></a>Parameters
`command`  
The command ID of the message to be posted.
### <a name="remarks"></a>Remarks
This method asynchronously posts the message mapped to the ID specified by command. It calls CWnd::PostMessage to place the message in the window's message queue and then returns without waiting for the corresponding window to process the message.


## <a name="removecommandhandler"></a> ICommandSource::RemoveCommandHandler
Removes a command handler from a command source object.
```
void RemoveCommandHandler(unsigned int cmdID);
```
### <a name="parameters"></a>Parameters
`cmdID`  
The command ID.
### <a name="remarks"></a>Remarks
This method removes the command handler mapped to cmdID from the command source object.


## <a name="removecommandrangecommandhandler"></a> ICommandSource::RemoveCommandRangeHandler 
Removes a group of command handlers from a command source object.
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```
### <a name="parameters"></a>Parameters
`cmdIDMin`  
The beginning index of the command ID range.
`cmdIDMax`  
The ending index of the command ID range.
### <a name="remarks"></a>Remarks
This method removes a group of message handlers, mapped to the command IDs specifed by cmdIDMin and cmdIDMax, from the command source object.

## <a name="removecommandrangeuihandler"></a> ICommandSource::RemoveCommandRangeUIHandler 
Removes a group of user interface command message handlers from a command source object.
```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```
### <a name="parameters"></a>Parameters
`cmdIDMin`  
The beginning index of the command ID range.
`cmdIDMax`  
The ending index of the command ID range.
### <a name="remarks"></a>Remarks
This method removes a group of user interface command message handlers, mapped to the command IDs specifed by cmdIDMin and cmdIDMax, from the command source object.

## <a name="removecommanduihandler"></a> ICommandSource::RemoveCommandUIHandler 
Removes a user interface command message handler from a command source object.
```
void RemoveCommandUIHandler(unsigned int cmdID);
```
### <a name="parameters"></a>Parameters
`cmdID`  
The command ID.
### <a name="remarks"></a>Remarks
This method removes the user interface command message handler mapped to cmdID from the command source object.

## <a name="sendcommand"></a> ICommandSource::SendCommand 
Sends a message and waits for it to be processed before returning.
```
void SendCommand(unsigned int command);
```
### <a name="parameters"></a>Parameters
`command`  
The command ID of the message to be sent.
### <a name="remarks"></a>Remarks
This method synchronously sends the message mapped to the ID specified by command. It calls CWnd::SendMessage to place the message in the window's message queue and waits until that window procedure has processed the message before returning.
## <a name="see-also"></a>See Also  
 [How to: Add Command Routing to the Windows Forms Control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [ICommandTarget Interface](../../mfc/reference/icommandtarget-interface.md)
