---
title: CRuntimeClass Structure | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
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
ms.openlocfilehash: e4f265a2d3a33819d78256ad8506cf8decd0cb8a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/12/2017

---
# <a name="cruntimeclass-structure"></a>CRuntimeClass Structure
Each class derived from `CObject` is associated with a `CRuntimeClass` structure that you can use to obtain information about an object or its base class at run time.  
  
## <a name="syntax"></a>Syntax  
  
```  
struct CRuntimeClass  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CRuntimeClass::CreateObject](#createobject)|Creates an object during run time.|  
|[CRuntimeClass::FromName](#fromname)|Creates an object during run time using the familiar class name.|  
|[CRuntimeClass::IsDerivedFrom](#isderivedfrom)|Determines if the class is derived from the specified class.|  
  
### <a name="public-data-members"></a>Public Data Members  
  
|Name|Description|  
|----------|-----------------|  
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|The name of the class.|  
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|The size of the object in bytes.|  
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|A pointer to the `CRuntimeClass` structure of the base class.|  
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|A pointer to the function that dynamically creates the object.|  
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|Returns the `CRuntimeClass` structure (only available when dynamically linked).|  
|[CRuntimeClass::m_wSchema](#m_wschema)|The schema number of the class.|  
  
## <a name="remarks"></a>Remarks  
 `CRuntimeClass` is a structure and therefore does not have a base class.  
  
 The ability to determine the class of an object at run time is useful when extra type checking of function arguments is needed, or when you must write special-purpose code based on the class of an object. Run-time class information is not supported directly by the C++ language.  
  
 `CRuntimeClass` provides information on the related C++ object, such as a pointer to the `CRuntimeClass` of the base class and the ASCII class name of the related class. This structure also implements various functions that can be used to dynamically create objects, specifying the type of object by using a familiar name, and determining if the related class is derived from a specific class.  
  
 For more information on using `CRuntimeClass`, see the article [Accessing Run-Time Class Information](../../mfc/accessing-run-time-class-information.md).  
  
## <a name="inheritance-hierarchy"></a>Inheritance Hierarchy  
 `CRuntimeClass`  
  
## <a name="requirements"></a>Requirements  
 **Header:** afx.h  
  
##  <a name="createobject"></a>  CRuntimeClass::CreateObject  
 Call this function to dynamically create the specified class during run time.  
  
```  
CObject* CreateObject();  
  
static CObject* PASCAL CreateObject(LPCSTR lpszClassName);  
  
static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```  
  
### <a name="parameters"></a>Parameters  
 `lpszClassName`  
 The familiar name of the class to be created.  
  
### <a name="return-value"></a>Return Value  
 A pointer to the newly created object, or **NULL** if the class name is not found or there is insufficient memory to create the object.  
  
### <a name="remarks"></a>Remarks  
 Classes derived from `CObject` can support dynamic creation, which is the ability to create an object of a specified class at run time. Document, view, and frame classes, for example, should support dynamic creation. For more information on dynamic creation and the `CreateObject` member, see [CObject Class](../../mfc/using-cobject.md) and [CObject Class: Specifying Levels of Functionality](../../mfc/specifying-levels-of-functionality.md).  
  
### <a name="example"></a>Example  
  See the example for [IsDerivedFrom](#isderivedfrom).  
  
##  <a name="fromname"></a>  CRuntimeClass::FromName  
 Call this function to retrieve the `CRuntimeClass` structure associated with the familiar name.  
  
```  
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);  
  
static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```  
  
### <a name="parameters"></a>Parameters  
 `lpszClassName`  
 The familiar name of a class derived from `CObject`.  
  
### <a name="return-value"></a>Return Value  
 A pointer to a `CRuntimeClass` object, corresponding to the name as passed in `lpszClassName`. The function returns **NULL** if no matching class name was found.  
  
### <a name="example"></a>Example  
 [!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]  
  
##  <a name="isderivedfrom"></a>  CRuntimeClass::IsDerivedFrom  
 Call this function to determine if the calling class is derived from the class specified in the *pBaseClass* parameter.  
  
```  
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;

 
```  
  
### <a name="parameters"></a>Parameters  
 *pBaseClass*  
 The familiar name of a class derived from `CObject`.  
  
### <a name="return-value"></a>Return Value  
 **TRUE** if the class calling `IsDerivedFrom` is derived from the base class whose `CRuntimeClass` structure is given as a parameter; otherwise **FALSE**.  
  
### <a name="remarks"></a>Remarks  
 The relationship is determined by "walking" from the member's class up the chain of derived classes all the way to the top. This function only returns **FALSE** if no match is found for the base class.  
  
> [!NOTE]
>  To use the `CRuntimeClass` structure, you must include the `IMPLEMENT_DYNAMIC`, `IMPLEMENT_DYNCREATE`, or `IMPLEMENT_SERIAL` macro in the implementation of the class for which you want to retrieve run-time object information.  
  
 For more information on using `CRuntimeClass`, see the article [CObject Class: Accessing Run-Time Class Information](../../mfc/accessing-run-time-class-information.md).  
  
### <a name="example"></a>Example  
 [!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]  
  
##  <a name="m_lpszclassname"></a>  CRuntimeClass::m_lpszClassName  
 A null-terminated string containing the ASCII class name.  
  
### <a name="remarks"></a>Remarks  
 This name can be used to create an instance of the class using the `FromName` member function.  
  
### <a name="example"></a>Example  
  See the example for [IsDerivedFrom](#isderivedfrom).  
  
##  <a name="m_nobjectsize"></a>  CRuntimeClass::m_nObjectSize  
 The size of the object, in bytes.  
  
### <a name="remarks"></a>Remarks  
 If the object has data members that point to allocated memory, the size of that memory is not included.  
  
### <a name="example"></a>Example  
  See the example for [IsDerivedFrom](#isderivedfrom).  
  
##  <a name="m_pbaseclass"></a>  CRuntimeClass::m_pBaseClass  
 If your application statically links to MFC, this data member contains a pointer to the `CRuntimeClass` structure of the base class.  
  
### <a name="remarks"></a>Remarks  
 If your application dynamically links to the MFC library, see [m_pfnGetBaseClass](#m_pfngetbaseclass).  
  
### <a name="example"></a>Example  
  See the example for [IsDerivedFrom](#isderivedfrom).  
  
##  <a name="m_pfncreateobject"></a>  CRuntimeClass::m_pfnCreateObject  
 A function pointer to the default constructor that creates an object of your class.  
  
### <a name="remarks"></a>Remarks  
 This pointer is only valid if the class supports dynamic creation; otherwise, the function returns **NULL**.  
  
##  <a name="m_pfngetbaseclass"></a>  CRuntimeClass::m_pfnGetBaseClass  
 If your application uses the MFC library as a shared DLL, this data member points to a function that returns the `CRuntimeClass` structure of the base class.  
  
### <a name="remarks"></a>Remarks  
 If your application statically links to the MFC library, see [m_pBaseClass](#m_pbaseclass).  
  
### <a name="example"></a>Example  
  See the example for [IsDerivedFrom](#isderivedfrom).  
  
##  <a name="m_wschema"></a>  CRuntimeClass::m_wSchema  
 The schema number ( -1 for nonserializable classes).  
  
### <a name="remarks"></a>Remarks  
 For more information on schema numbers, see the [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro.  
  
### <a name="example"></a>Example  
  See the example for [IsDerivedFrom](#isderivedfrom).  
  
## <a name="see-also"></a>See Also  
 [Hierarchy Chart](../../mfc/hierarchy-chart.md)   
 [CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)   
 [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)   
 [RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)   
 [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)   
 [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)   
 [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)



