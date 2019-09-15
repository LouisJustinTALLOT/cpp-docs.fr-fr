---
title: wctrans
ms.date: 11/04/2016
api_name:
- wctrans
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctrans
helpviewer_keywords:
- character codes, wctrans
- characters, codes
- characters, converting
- wctrans function
ms.assetid: 215404bf-6d60-489c-9ae9-880e6b586162
ms.openlocfilehash: a75de3b699d0eb5ec6117d0f627e6a8ba34dbc62
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944884"
---
# <a name="wctrans"></a>wctrans

Détermine un mappage d’un ensemble de codes de caractères à un autre.

## <a name="syntax"></a>Syntaxe

```C
wctrans_t wctrans(
   const char *property
);
```

### <a name="parameters"></a>Paramètres

*propriété*<br/>
Chaîne qui spécifie une des transformations valides.

## <a name="return-value"></a>Valeur de retour

Si la catégorie **LC_CTYPE** des paramètres régionaux actifs ne définit pas un mappage dont le nom correspond à la *propriété*de chaîne de propriété, la fonction retourne la valeur zéro. Sinon, elle retourne une valeur différente de zéro qui peut être utilisée comme deuxième argument dans un appel ultérieur à [towctrans](towctrans.md).

## <a name="remarks"></a>Notes

Cette fonction détermine un mappage d’un ensemble de codes de caractères à un autre.

Les paires d’appels suivantes présentent le même comportement dans tous les paramètres régionaux, mais il est possible de définir des mappages supplémentaires même dans les paramètres régionaux « C » :

|Fonction|Identique à|
|--------------|-------------|
|ToLower (c)|towctrans(c, wctrans("towlower"))|
|towupper (c)|towctrans(c, wctrans("toupper"))|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**wctrans**|\<wctype.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

```C
// crt_wctrans.cpp
// compile with: /EHsc
// This example determines a mapping from one set of character
// codes to another.

#include <wchar.h>
#include <wctype.h>
#include <stdio.h>
#include <iostream>

int main()
{
    wint_t c = 'a';
    printf_s("%d\n",c);

    wctrans_t i = wctrans("toupper");
    printf_s("%d\n",i);

    wctrans_t ii = wctrans("towlower");
    printf_s("%d\n",ii);

    wchar_t wc = towctrans(c, i);
    printf_s("%d\n",wc);
}
```

```Output
97
1
0
65
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
