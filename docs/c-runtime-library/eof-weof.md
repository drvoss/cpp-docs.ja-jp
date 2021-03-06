---
title: EOF、WEOF
ms.date: 11/04/2016
f1_keywords:
- EOF
helpviewer_keywords:
- EOF function
- WEOF function
- end of file
ms.assetid: a7150563-cdae-4cdf-9798-ad509990e505
ms.openlocfilehash: 9317fdad16121374b31e0862f3326f4150c71579
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667390"
---
# <a name="eof-weof"></a>EOF、WEOF

## <a name="syntax"></a>構文

```

#include <stdio.h>
```

## <a name="remarks"></a>コメント

EOF は、ファイルの終わり (場合によっては、エラー) が検出された場合に I/O ルーチンによって返されます。

WEOF は、ワイド型ストリームの終端を示すために、またはエラー状態を報告するために使用される **wint_t** 型の戻り値です。

## <a name="see-also"></a>参照

[putc、putwc](../c-runtime-library/reference/putc-putwc.md)<br/>
[ungetc、ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[fflush](../c-runtime-library/reference/fflush.md)<br/>
[fclose、_fcloseall](../c-runtime-library/reference/fclose-fcloseall.md)<br/>
[_ungetch、_ungetwch、_ungetch_nolock、_ungetwch_nolock](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)<br/>
[_putch、_putwch](../c-runtime-library/reference/putch-putwch.md)<br/>
[isascii、__isascii、iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)