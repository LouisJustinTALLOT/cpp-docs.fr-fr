---
title: isdigit, iswdigit, _isdigit_l, _iswdigit_l
ms.date: 11/04/2016
apiname:
- _isdigit_l
- iswdigit
- _iswdigit_l
- isdigit
apilocation:
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _iswdigit_l
- _isdigit_l
- iswdigit
- isdigit
- _istdigit
- _istdigit_l
helpviewer_keywords:
- iswdigit function
- iswdigit_l function
- _iswdigit_l function
- _istdigit_l function
- _istdigit function
- istdigit function
- isdigit function
- isdigit_l function
- _ismbcdigit_l function
- _isdigit_l function
ms.assetid: 350b0093-843a-47b0-954e-c1776e8a3853
ms.openlocfilehash: 7e85028d43858543f8c9b9d4c5cf1b17664f8331
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331621"
---
# <a name="isdigit-iswdigit-isdigitl-iswdigitl"></a>isdigit, iswdigit, _isdigit_l, _iswdigit_l

Détermine si un entier représente un caractère numérique décimal.

## <a name="syntax"></a>Syntaxe

```C
int isdigit(
   int c
);
int iswdigit(
   wint_t c
);
int _isdigit_l(
   int c,
   _locale_t locale
);
int _iswdigit_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Entier à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines retourne différente de zéro si *c* est une représentation particulière d’un caractère numérique décimal. **IsDigit** retourne une valeur différente de zéro si *c* est un chiffre décimal (0 - 9). **iswdigit** retourne une valeur différente de zéro si *c* est un caractère large qui correspond à un caractère numérique décimal. Chacune de ces routines retourne 0 si *c* ne satisfait pas la condition de test.

Les versions de ces fonctions qui ont le **_l** suffixe utiliser les paramètres régionaux qui sont passé au lieu des paramètres régionaux actuels pour leur comportement dépendant des paramètres régionaux. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Le comportement de **isdigit** et **_isdigit_l** n’est pas défini si *c* n’est pas EOF ou dans la plage 0 à 0xFF, inclus. Quand une bibliothèque de débogage CRT est utilisée et *c* ne fait pas partie de ces valeurs, les fonctions déclenchent une assertion.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istdigit**|**isdigit**|[_ismbcdigit](ismbcalnum-functions.md)|**iswdigit**|
|**_istdigit_l**|**_isdigit_l**|[_ismbcdigit_l](ismbcalnum-functions.md)|**_iswdigit_l**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**isdigit**|\<ctype.h>|
|**iswdigit**|\<ctype.h> ou \<wchar.h>|
|**_isdigit_l**|\<ctype.h>|
|**_iswdigit_l**|\<ctype.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
