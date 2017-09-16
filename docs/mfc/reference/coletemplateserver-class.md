---
title: COleTemplateServer Class | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
dev_langs:
- C++
helpviewer_keywords:
- COleTemplateServer [MFC], COleTemplateServer
- COleTemplateServer [MFC], ConnectTemplate
- COleTemplateServer [MFC], Unregister
- COleTemplateServer [MFC], UpdateRegistry
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
caps.latest.revision: 23
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
ms.openlocfilehash: 7ea6cb24647abb96cf0d535a4b1c25055a68acb6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/12/2017

---
# <a name="coletemplateserver-class"></a>COleTemplateServer Class
Used for OLE visual editing servers, automation servers, and link containers (applications that support links to embeddings).  
  
## <a name="syntax"></a>Syntax  
  
```  
class COleTemplateServer : public COleObjectFactory  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|Constructs a `COleTemplateServer` object.|  
  
### <a name="public-methods"></a>Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|Connects a document template to the underlying `COleObjectFactory` object.|  
|[COleTemplateServer::Unregister](#unregister)|Unregisters the associated document template.|  
|[COleTemplateServer::UpdateRegistry](#updateregistry)|Registers the document type with the OLE system registry.|  
  
## <a name="remarks"></a>Remarks  
 This class is derived from the class [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); usually, you can use `COleTemplateServer` directly rather than deriving your own class. `COleTemplateServer` uses a [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) object to manage the server documents. Use `COleTemplateServer` when implementing a full server, that is, a server that can be run as a standalone application. Full servers are typically multiple document interface (MDI) applications, although single document interface (SDI) applications are supported. One `COleTemplateServer` object is needed for each type of server document an application supports; that is, if your server application supports both worksheets and charts, you must have two `COleTemplateServer` objects.  
  
 `COleTemplateServer` overrides the `OnCreateInstance` member function defined by `COleObjectFactory`. This member function is called by the framework to create a C++ object of the proper type.  
  
 For more information about servers, see the article [Servers: Implementing a Server](../../mfc/servers-implementing-a-server.md).  
  
## <a name="inheritance-hierarchy"></a>Inheritance Hierarchy  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)  
  
 `COleTemplateServer`  
  
## <a name="requirements"></a>Requirements  
 **Header:** afxdisp.h  
  
##  <a name="coletemplateserver"></a>  COleTemplateServer::COleTemplateServer  
 Constructs a `COleTemplateServer` object.  
  
```  
COleTemplateServer();
```  
  
### <a name="remarks"></a>Remarks  
 For a brief description of the use of the `COleTemplateServer` class, see the [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md) class overview.  
  
##  <a name="connecttemplate"></a>  COleTemplateServer::ConnectTemplate  
 Connects the document template pointed to by `pDocTemplate` to the underlying [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md) object.  
  
```  
void ConnectTemplate(
    REFCLSID clsid,  
    CDocTemplate* pDocTemplate,  
    BOOL bMultiInstance);
```  
  
### <a name="parameters"></a>Parameters  
 `clsid`  
 Reference to the OLE class ID that the template requests.  
  
 `pDocTemplate`  
 Pointer to the document template.  
  
 `bMultiInstance`  
 Indicates whether a single instance of the application can support multiple instantiations. If **TRUE**, multiple instances of the application are launched for each request to create an object.  
  
### <a name="remarks"></a>Remarks  
 For more information, see [CLSID Key](http://msdn.microsoft.com/library/windows/desktop/ms691424) in the Windows SDK.  
  
##  <a name="unregister"></a>  COleTemplateServer::Unregister  
 Unregisters the associated document template.  
  
```  
BOOL Unregister();
```  
  
### <a name="return-value"></a>Return Value  
 TRUE if successful; otherwise FALSE.  
  
### <a name="remarks"></a>Remarks  
 EnterRemarks  
  
##  <a name="updateregistry"></a>  COleTemplateServer::UpdateRegistry  
 Loads file-type information from the document-template string and places that information in the OLE system registry.  
  
```  
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,  
    LPCTSTR* rglpszRegister = NULL,  
    LPCTSTR* rglpszOverwrite = NULL,  
    BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>Parameters  
 `nAppType`  
 A value from the **OLE_APPTYPE** enumeration, which is defined in AFXDISP.H. It can have any one of the following values:  
  
- `OAT_INPLACE_SERVER` Server has full server user-interface.  
  
- `OAT_SERVER` Server supports only embedding.  
  
- `OAT_CONTAINER` Container supports links to embedded objects.  
  
- `OAT_DISPATCH_OBJECT` Object is `IDispatch`-capable.  
  
- **OAT_DOC_OBJECT_SERVER** Server supports both embedding and the Document Object component model.  
  
 `rglpszRegister`  
 A list of entries that is written into the registry only if no entries exist.  
  
 `rglpszOverwrite`  
 A list of entries that is written into the registry regardless of whether any preceding entries exist.  
  
 `bRegister`  
 Determines whether the class is to be registered. If `bRegister` is **TRUE**, the class is registered with the system registry. Otherwise, it unregisters the class.  
  
### <a name="remarks"></a>Remarks  
 The registration information is loaded by means of a call to [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). The substrings retrieved are those identified by the indexes **regFileTypeId**, **regFileTypeName**, and **fileNewName**, as described in the `GetDocString` reference pages.  
  
 If the **regFileTypeId** substring is empty or if the call to `GetDocString` fails for any other reason, this function fails and the file information is not entered in the registry.  
  
 The information in the arguments `rglpszRegister` and `rglpszOverwrite` is written to the registry through a call to [AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass). The default information, which is registered when the two arguments are **NULL**, is suitable for most applications. For information on the structure of the information in these arguments, see `AfxOleRegisterServerClass`.  
  
 For more information, see [Implementing the IDispatch Interface](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
## <a name="see-also"></a>See Also  
 [MFC Sample HIERSVR](../../visual-cpp-samples.md)   
 [COleObjectFactory Class](../../mfc/reference/coleobjectfactory-class.md)   
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [COleServerDoc Class](../../mfc/reference/coleserverdoc-class.md)   
 [COleServerItem Class](../../mfc/reference/coleserveritem-class.md)
