---
title: wctype
ms.date: 11/04/2016
api_name:
- wctype
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctype
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
ms.openlocfilehash: f77082bbcc5f3cd9d82fb40993c3ac678e7e7ba2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957798"
---
# <a name="wctype"></a>wctype

Détermine une règle de classification pour les codes à caractères larges.

## <a name="syntax"></a>Syntaxe

```C
wctype_t wctype(
   const char * property
);
```

### <a name="parameters"></a>Paramètres

*propriété*<br/>
Chaîne de propriété.

## <a name="return-value"></a>Valeur de retour

Si la catégorie **LC_CTYPE** des paramètres régionaux actuels ne définit pas une règle de classification dont le nom correspond à la *propriété*de chaîne de propriété, la fonction retourne la valeur zéro. Sinon, elle retourne une valeur différente de zéro qui peut être utilisée comme deuxième argument dans un appel ultérieur à [towctrans](towctrans.md).

## <a name="remarks"></a>Notes

La fonction détermine une règle de classification pour les codes à caractères larges. Les paires d’appels suivantes présentent le même comportement dans tous les paramètres régionaux (mais une implémentation peut définir des règles de classification supplémentaires même dans les paramètres régionaux « C ») :

|Fonction|Identique à|
|--------------|-------------|
|iswalnum(c)|iswctype(c, wctype( "alnum" ) )|
|iswalpha(c)|iswctype(c, wctype( "alpha" ) )|
|iswcntrl(c)|iswctype(c, wctype( "cntrl" ) )|
|iswdigit (c)|iswctype(c, wctype( "digit" ) )|
|iswgraph(c)|iswctype(c, wctype( "graph" ) )|
|iswlower (c)|iswctype(c, wctype( "lower" ) )|
|iswprint(c)|iswctype(c, wctype( "print" ) )|
|iswpunct(c)|iswctype(c, wctype( "punct" ) )|
|iswspace(c)|iswctype(c, wctype( "space" ) )|
|iswupper(c)|iswctype(c, wctype( "upper" ) )|
|iswxdigit(c)|iswctype(c, wctype( "xdigit" ) )|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**wctype**|\<wctype.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
