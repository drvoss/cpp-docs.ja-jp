---
title: (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.in
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
ms.openlocfilehash: bf23b1c776eccc284e5329b62bd45b0bd678823f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449700"
---
# <a name="in-c"></a>in (C++)

呼び出し元のプロシージャから呼び出されたプロシージャに渡されるパラメーターがあることを示します。

## <a name="syntax"></a>構文

```cpp
[in]
```

## <a name="remarks"></a>Remarks

**で**C++ 属性と同じ機能を持つ、[で](/windows/desktop/Midl/in)MIDL 属性。

## <a name="example"></a>例

参照してください[バインド可能な](bindable.md)を使用する方法の例については**で**します。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|インターフェイスのパラメーター、インターフェイス メソッド|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|**retval**|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[パラメーター属性](parameter-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[ID](id.md)<br/>
[out](out-cpp.md)