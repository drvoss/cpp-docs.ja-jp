---
title: Platform::IDisposable インターフェイス
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
ms.openlocfilehash: f114959321c0ed3879a089b944a5ff1b19843118
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637438"
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable インターフェイス

アンマネージ リソースを解放するために使用されます。

## <a name="syntax"></a>構文

```cpp
public interface class IDisposable
```

## <a name="attributes"></a>属性

**GuidAttribute**("de0cbaea-8065-4a45-b196-c9d443f9bab3")

**VersionAttribute**(NTDDI_WIN8)

### <a name="members"></a>メンバー

IDisposable インターフェイスは IUnknown インターフェイスから継承します。 また IDisposable には次の種類のメンバーもあります。

**メソッド**

IDisposable インターフェイスには、次のメソッドがあります。

|メソッド|説明|
|------------|-----------------|
|Dispose|アンマネージ リソースを解放するために使用されます。|

### <a name="requirements"></a>必要条件

**クライアントがサポートされている最小:** Windows 8

**サポートされているサーバーの最小値:** Windows Server 2012

**名前空間:** Platform