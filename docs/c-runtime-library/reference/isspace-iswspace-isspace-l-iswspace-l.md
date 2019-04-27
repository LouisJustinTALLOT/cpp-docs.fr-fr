---
title: isspace, iswspace, _isspace_l, _iswspace_l
ms.date: 11/04/2016
apiname:
- iswspace
- _isspace_l
- _iswspace_l
- isspace
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
- iswspace
- _istspace
- isspace
helpviewer_keywords:
- iswspace function
- isspace function
- _iswspace_l function
- _isspace_l function
- iswspace_l function
- isspace_l function
- _istspace function
- istspace function
ms.assetid: b851e0c0-36bb-4dac-a1a3-533540939035
ms.openlocfilehash: bb3d18e5034be50d69531d2686b6c270ba55a1cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157381"
---
# <a name="isspace-iswspace-isspacel-iswspacel"></a>isspace, iswspace, _isspace_l, _iswspace_l

Détermine si un entier représente un espace.

## <a name="syntax"></a>Syntaxe

```C
int isspace(
   int c
);
int iswspace(
   wint_t c
);
int _isspace_l(
   int c,
   _locale_t locale
);
int _iswspace_l(
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

Chacune de ces routines retourne différente de zéro si *c* est une représentation particulière d’un caractère d’espacement. **isspace** retourne une valeur différente de zéro si *c* est un caractère d’espace blanc (0 x 09-0x0D ou 0 x 20). Le résultat de la condition de test pour le **isspace** fonction varie selon le **LC_CTYPE** catégorie des paramètres régionaux ; consultez [setlocale, _wsetlocale](setlocale-wsetlocale.md) pour plus d’informations. Les versions de ces fonctions qui n’ont pas la **_l** suffixe utilisent les paramètres régionaux actuels pour tout comportement dépendant des paramètres régionaux ; les versions qui ont le **_l** suffixe sont identiques, sauf qu’ils utilisent le paramètres régionaux qui sont passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

**iswspace** retourne une valeur différente de zéro si *c* est un caractère large qui correspond à un caractère d’espace blanc standard.

Le comportement de **isspace** et **_isspace_l** n’est pas défini si *c* n’est pas EOF ou dans la plage 0 à 0xFF, inclus. Quand une bibliothèque de débogage CRT est utilisée et *c* ne fait pas partie de ces valeurs, les fonctions déclenchent une assertion.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istspace**|**isspace**|[_ismbcspace](ismbcgraph-functions.md)|**iswspace**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**isspace**|\<ctype.h>|
|**iswspace**|\<ctype.h> ou \<wchar.h>|
|**_isspace_l**|\<ctype.h>|
|**_iswspace_l**|\<ctype.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
