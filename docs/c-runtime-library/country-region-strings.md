---
title: "国/地域別文字列 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.strings
dev_langs:
- C++
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
caps.latest.revision: 14
author: corob-msft
ms.author: corob
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
ms.sourcegitcommit: 22da7776e46171467a37d46c3de3227f060eaf77
ms.openlocfilehash: 272ce38cee55661a3f4a1eb751c8808b355b59be
ms.contentlocale: ja-jp
ms.lasthandoff: 08/11/2017

---
# <a name="countryregion-strings"></a>Country/Region Strings
国/地域識別文字列を言語識別文字列と組み合わせて、 `setlocale`、 `_wsetlocale`、 `_create_locale`、および `_wcreate_locale` の関数のロケール指定を作成できます。 さまざまなバージョンの Windows オペレーティング システムでサポートされている国/地域名の一覧については、「[National Language Support (NLS) API Reference (各国語サポート (NLS) API リファレンス)](https://www.microsoft.com/resources/msdn/goglobal/default.mspx)」をご覧ください。 一覧では、国/地域の文字列は **Locale - Language Country/Region** 列のいずれかの国の値、または **Country or Region name abbreviation** 列の省略形のいずれかとなります。 Windows オペレーティング システムのバージョンごとの言語サポートに関する詳細については、[MS-LCID]: Windows Language Code Identifier (LCID) Reference ([MS-LCID]: Windows 言語コード識別子 (LCID) リファレンス) の「[Appendix A: Product Behavior (付録 A: 製品の動作)](http://msdn.microsoft.com/goglobal/bb896001.aspx)」をご覧ください。  
  
 C ランタイム ライブラリの実装では、次の追加の国/地域識別文字列および省略形もサポートされています。  
  
|国/地域識別文字列|省略形|同等のロケール名|  
|----------------------------|------------------|----------------------------|  
|america|USA|en-US|  
|britain|GBR|en-GB|  
|china|CHN|zh-CN|  
|czech|CZE|cs-CZ|  
|england|GBR|en-GB|  
|great britain|GBR|en-GB|  
|holland|NLD|nl-NL|  
|hong-kong|HKG|zh-HK|  
|new-zealand|NZL|en-NZ|  
|nz|NZL|en-NZ|  
|pr china|CHN|zh-CN|  
|pr-china|CHN|zh-CN|  
|puerto-rico|PRI|es-PR|  
|slovak|SVK|sk-SK|  
|south africa|ZAF|af-ZA|  
|south korea|KOR|ko-KR|  
|south-africa|ZAF|af-ZA|  
|south-korea|KOR|ko-KR|  
|trinidad & tobago|TTO|en-TT|  
|uk|GBR|en-GB|  
|united-kingdom|GBR|en-GB|  
|united-states|USA|en-US|  
|us|USA|en-US|  
  
## <a name="see-also"></a>関連項目  
 [ロケール名、言語、および国/地域識別文字列](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [言語識別文字列](../c-runtime-library/language-strings.md)   
 [setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)