---
description: 'En savoir plus sur : wctype'
title: wctype
ms.date: 1/14/2021
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctype
helpviewer_keywords:
- wctype function
- wide characters
ms.openlocfilehash: d0afd2bd163af967b11d0df58c84b62521ca6c2a
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98242927"
---
# `wctype`

Détermine une règle de classification pour les codes à caractères larges.

## <a name="syntax"></a>Syntaxe

```C
wctype_t wctype(
   const char * property
);
```

### <a name="parameters"></a>Paramètres

*`property`*\
Chaîne de propriété.

## <a name="return-value"></a>Valeur renvoyée

Si la **`LC_CTYPE`** catégorie des paramètres régionaux actuels ne définit pas une règle de classification dont le nom correspond à la chaîne de propriété *`property`* , la fonction retourne la valeur zéro. Sinon, elle retourne une valeur différente de zéro pouvant être utilisée comme deuxième argument pour un appel ultérieur à [`towctrans`](towctrans.md) .

## <a name="remarks"></a>Remarques

La fonction détermine une règle de classification pour les codes à caractères larges. Les paires d’appels suivantes présentent le même comportement dans tous les paramètres régionaux (mais une implémentation peut définir des règles de classification supplémentaires même dans les paramètres régionaux « C ») :

|Fonction|Identique à|
|--------------|-------------|
|`iswalnum(c)`|`iswctype(c, wctype( "alnum" ))`|
|`iswalpha(c)`|`iswctype(c, wctype( "alpha" ))`|
|`iswcntrl(c)`|`iswctype(c, wctype( "cntrl" ))`|
|`iswdigit(c)`|`iswctype(c, wctype( "digit" ))`|
|`iswgraph(c)`|`iswctype(c, wctype( "graph" ))`|
|`iswlower(c)`|`iswctype(c, wctype( "lower" ))`|
|`iswprint(c)`|`iswctype(c, wctype( "print" ))`|
|`iswpunct(c)`|`iswctype(c, wctype( "punct" ))`|
|`iswspace(c)`|`iswctype(c, wctype( "space" ))`|
|`iswupper(c)`|`iswctype(c, wctype( "upper" ))`|
|`iswxdigit(c)`|`iswctype(c, wctype( "xdigit" ))`|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|`wctype`|`<wctype.h>`|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)\
[`setlocale`, `_wsetlocale`](setlocale-wsetlocale.md)
