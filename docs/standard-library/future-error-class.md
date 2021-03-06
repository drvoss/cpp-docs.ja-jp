---
title: future_error クラス
ms.date: 11/04/2016
f1_keywords:
- future/std::future_error
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
ms.openlocfilehash: 2b3f754c0ceb7384d99c6a657de214d30aca24b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430474"
---
# <a name="futureerror-class"></a>future_error クラス

[future](../standard-library/future-class.md) オブジェクトを管理する型のメソッドによってスローされる例外オブジェクトを記述します。

## <a name="syntax"></a>構文

```cpp
class future_error : public logic_error {
public:
    future_error(error_code code);

const error_code& code() const throw();

const char *what() const throw();

};
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<将来 >

**名前空間:** std

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)<br/>
[logic_error クラス](../standard-library/logic-error-class.md)<br/>
[error_code クラス](../standard-library/error-code-class.md)<br/>
