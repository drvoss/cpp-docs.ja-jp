---
title: Module::MethodReleaseNotifier クラス
ms.date: 09/17/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::Invoke
- module/Microsoft::WRL::Module::MethodReleaseNotifier::method_
- module/Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier
- module/Microsoft::WRL::Module::MethodReleaseNotifier::object_
helpviewer_keywords:
- Microsoft::WRL::Module::MethodReleaseNotifier class
- Microsoft::WRL::Module::MethodReleaseNotifier::Invoke method
- Microsoft::WRL::Module::MethodReleaseNotifier::method_ data member
- Microsoft::WRL::Module::MethodReleaseNotifier::MethodReleaseNotifier, constructor
- Microsoft::WRL::Module::MethodReleaseNotifier::object_ data member
ms.assetid: 5c2902be-964b-488f-9f1c-adf504995cbc
ms.openlocfilehash: c2b37073455f255eaea931e7aaedd1e34a14a104
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469343"
---
# <a name="modulemethodreleasenotifier-class"></a>Module::MethodReleaseNotifier クラス

現在のモジュールの最後のオブジェクトがリリースされたときに、イベント ハンドラーを呼び出します。 イベント ハンドラーは、オブジェクトとそのメソッドへのポインター メンバーによって指定されます。

## <a name="syntax"></a>構文

```cpp
template<typename T>
class MethodReleaseNotifier : public ReleaseNotifier;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
メンバー関数は、イベント ハンドラー オブジェクトの型。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

名前                                                                                                 | 説明
---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------
[Module::MethodReleaseNotifier::MethodReleaseNotifier](#methodreleasenotifier-methodreleasenotifier) | `Module::MethodReleaseNotifier` クラスの新しいインスタンスを初期化します。

### <a name="public-methods"></a>パブリック メソッド

名前                                                                   | 説明
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------
[Module::methodreleasenotifier:: 呼び出し](#methodreleasenotifier-invoke) | 現在関連付けられているイベント ハンドラーを呼び出す`Module::MethodReleaseNotifier`オブジェクト。

### <a name="protected-data-members"></a>プロテクト データ メンバー

名前                                                                    | 説明
----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------
[Module::MethodReleaseNotifier::method_](#methodreleasenotifier-method) | 現在のイベント ハンドラーへのポインターを保持`Module::MethodReleaseNotifier`オブジェクト。
[Module::MethodReleaseNotifier::object_](#methodreleasenotifier-object) | メンバー関数は、現在のイベント ハンドラー オブジェクトへのポインターを保持`Module::MethodReleaseNotifier`オブジェクト。

## <a name="inheritance-hierarchy"></a>継承階層

`ReleaseNotifier`

`MethodReleaseNotifier`

## <a name="requirements"></a>必要条件

**ヘッダー:** module.h

**名前空間:** Microsoft::WRL

## <a name="methodreleasenotifier-invoke"></a>Module::methodreleasenotifier:: 呼び出し

現在関連付けられているイベント ハンドラーを呼び出す`Module::MethodReleaseNotifier`オブジェクト。

```cpp
void Invoke();
```

## <a name="methodreleasenotifier-method"></a>Module::MethodReleaseNotifier::method_

現在のイベント ハンドラーへのポインターを保持`Module::MethodReleaseNotifier`オブジェクト。

```cpp
void (T::* method_)();
```

## <a name="methodreleasenotifier-methodreleasenotifier"></a>Module::MethodReleaseNotifier::MethodReleaseNotifier

`Module::MethodReleaseNotifier` クラスの新しいインスタンスを初期化します。

```cpp
MethodReleaseNotifier(
   _In_ T* object,
   _In_ void (T::* method)(),
   bool release) throw() :
            ReleaseNotifier(release), object_(object),
            method_(method);
```

### <a name="parameters"></a>パラメーター

*object*<br/>
メンバー関数は、イベント ハンドラー オブジェクト。

*method*<br/>
パラメーターのメンバー関数は、*オブジェクト*イベント ハンドラーは。

*release*<br/>
指定**true** 、基になる呼び出しを有効にする[モジュール:: ReleaseNotifier::Release()](../windows/module-releasenotifier-class.md#releasenotifier-release)メソッド。 それ以外の場合、指定**false**します。

## <a name="methodreleasenotifier-object"></a>Module::MethodReleaseNotifier::object_

メンバー関数は、現在のイベント ハンドラー オブジェクトへのポインターを保持`Module::MethodReleaseNotifier`オブジェクト。

```cpp
T* object_;
```
