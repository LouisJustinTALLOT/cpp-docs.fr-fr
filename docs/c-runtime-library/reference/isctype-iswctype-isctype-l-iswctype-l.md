---
title: _isctype, iswctype, _isctype_l, _iswctype_l
ms.date: 11/04/2016
api_name:
- _isctype_l
- iswctype
- _iswctype_l
- _isctype
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
- iswctype
- _isctype
- _isctype_l
- _iswctype
- isctype
- iswctype_l
- isctype_l
- _iswctype_l
helpviewer_keywords:
- isctype_l function
- iswctype_l function
- iswctype function
- _isctype function
- _isctype_l function
- _iswctype_l function
- isctype function
- _iswctype function
ms.assetid: cf7509b7-12fc-4d95-8140-ad2eb98173d3
ms.openlocfilehash: 9fefb852f8ebd34b932842ee4c12b53f79b29641
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954399"
---
# <a name="_isctype-iswctype-_isctype_l-_iswctype_l"></a>_isctype, iswctype, _isctype_l, _iswctype_l

Teste *c* pour la propriété CType spécifiée par l’argument *desc* . Pour chaque valeur valide de *desc*, il existe une routine de classification de caractères larges équivalente.

## <a name="syntax"></a>Syntaxe

```C
int _isctype(
   int c,
   _ctype_t desc
);
int _isctype_l(
   int c,
   _ctype_t desc,
   _locale_t locale
);
int iswctype(
   wint_t c,
   wctype_t desc
);
int _iswctype_l(
   wint_t c,
   wctype_t desc,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Entier à tester.

*desc*<br/>
Propriété à rechercher. Cette valeur est généralement récupérée à l’aide de ctype ou [wctype](wctype.md).

*locale*<br/>
Paramètres régionaux à utiliser pour les tests dépendant des paramètres régionaux.

## <a name="return-value"></a>Valeur de retour

**_isctype** et **iswctype** retournent une valeur différente de zéro si *c* a la propriété spécifiée par *desc* dans les paramètres régionaux actuels ou 0 dans le cas contraire. Les versions de ces fonctions avec le suffixe **_L** sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux actuels pour leur comportement dépendant des paramètres régionaux. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Le comportement de **_isctype** et **_isctype_l** n’est pas défini si *c* n’est pas EOF ni dans la plage 0 à 0xFF, inclus. Quand une bibliothèque CRT de débogage est utilisée et que *c* n’est pas l’une de ces valeurs, les fonctions déclenchent une assertion.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|N/A|**_isctype**|N/A|**_iswctype**|
|N/A|**_isctype_l**|N/A|**_iswctype_l**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_isctype**|\<ctype.h>|
|**iswctype**|\<ctype.h> ou \<wchar.h>|
|**_isctype_l**|\<ctype.h>|
|**_iswctype_l**|\<ctype.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
