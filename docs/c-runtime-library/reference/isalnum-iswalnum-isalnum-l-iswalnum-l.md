---
title: isalnum, iswalnum, _isalnum_l, _iswalnum_l
ms.date: 11/04/2016
apiname:
- _iswalnum_l
- _isalnum_l
- iswalnum
- isalnum
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
- _istalnum_l
- _iswalnum_l
- iswalnum
- _isalnum_l
- isalnum
- _istalnum
helpviewer_keywords:
- _istalnum function
- _ismbcalnum_l function
- iswalnum function
- isalnum function
- istalnum function
- _isalnum_l function
- _istalnum_l function
- _iswalnum_l function
ms.assetid: 0dc51306-ade8-4944-af27-e4176fc89093
ms.openlocfilehash: 3aa9adada9ad904221b91e41ac2d843b174677ae
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57209884"
---
# <a name="isalnum-iswalnum-isalnuml-iswalnuml"></a>isalnum, iswalnum, _isalnum_l, _iswalnum_l

Détermine si un entier représente un caractère alphanumérique.

## <a name="syntax"></a>Syntaxe

```C
int isalnum( int c );
int iswalnum( wint_t c );
int _isalnum_l( int c,  _locale_t locale );
int _iswalnum_l( wint_t c, _locale_t locale );
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Entier à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines retourne différente de zéro si *c* est une représentation particulière d’un caractère alphanumérique. **isalnum** retourne une valeur différente de zéro si **isalpha** ou **isdigit** est différente de zéro pour *c*, autrement dit, si *c* se trouve dans le plages A - Z, a - z ou 0 - 9. **iswalnum** retourne une valeur différente de zéro si **iswalpha** ou **iswdigit** est différente de zéro pour *c*. Chacune de ces routines retourne 0 si *c* ne satisfait pas la condition de test.

Les versions de ces fonctions qui ont le **_l** suffixe utiliser les paramètres régionaux qui sont passés au lieu des paramètres régionaux actuels. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Le comportement de **isalnum** et **_isalnum_l** n’est pas défini si *c* n’est pas EOF ou dans la plage 0 à 0xFF, inclus. Quand une bibliothèque de débogage CRT est utilisée et *c* ne fait pas partie de ces valeurs, les fonctions déclenchent une assertion.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istalnum**|**isalnum**|[_ismbcalnum](ismbcalnum-functions.md)|**iswalnum**|
|**_istalnum_l**|**_isalnum_l**|**_ismbcalnum_l**|**_iswalnum_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**isalnum**|\<ctype.h>|
|**iswalnum**|\<ctype.h> ou \<wchar.h>|
|**_isalnum_l**|\<ctype.h>|
|**_iswalnum_l**|\<ctype.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
