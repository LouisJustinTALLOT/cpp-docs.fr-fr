---
title: tolower, _tolower, towlower, _tolower_l, _towlower_l
ms.date: 11/04/2016
apiname:
- _tolower_l
- towlower
- tolower
- _tolower
- _towlower_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _totlower
- tolower
- _tolower
- towlower
helpviewer_keywords:
- tolower_l function
- _tolower_l function
- totlower function
- string conversion, to different characters
- lowercase, converting to
- tolower function
- string conversion, case
- towlower function
- _tolower function
- _totlower function
- towlower_l function
- case, converting
- characters, converting
- _towlower_l function
ms.assetid: 86e0fc02-94ae-4472-9631-bf8e96f67b92
ms.openlocfilehash: f7d017235eddb19b08353dceb332a2721e7434aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155513"
---
# <a name="tolower-tolower-towlower-tolowerl-towlowerl"></a>tolower, _tolower, towlower, _tolower_l, _towlower_l

Convertit un caractère en minuscule.

## <a name="syntax"></a>Syntaxe

```C
int tolower(
   int c
);
int _tolower(
   int c
);
int towlower(
   wint_t c
);
int _tolower_l(
   int c,
   _locale_t locale
);
int _towlower_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Caractère à convertir.

*locale*<br/>
Paramètres régionaux à utiliser pour une traduction spécifique aux paramètres régionaux.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines convertit une copie de *c* en minuscules si la conversion est possible et retourne le résultat. Il n’existe aucune valeur de retour réservée pour indiquer une erreur.

## <a name="remarks"></a>Notes

Chacune de ces routines convertit une lettre majuscule donnée en lettre minuscule si cela est possible et approprié. La conversion de casse **towlower** est spécifique aux paramètres régionaux. Seuls les caractères relevant des paramètres régionaux actifs changent de casse. Les fonctions sans le **_l** suffixe utiliser actuellement définis aux paramètres régionaux. Les versions de ces fonctions qui ont le **_l** suffixe prennent les paramètres régionaux en tant que paramètre et utiliser à la place actuellement définis aux paramètres régionaux. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Dans l’ordre pour **_tolower** donne les résultats attendus, [__isascii](isascii-isascii-iswascii.md) et [isupper](isupper-isupper-l-iswupper-iswupper-l.md) doivent retourner différente de zéro.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totlower**|**tolower**|**_mbctolower**|**towlower**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_l**|

> [!NOTE]
> **_tolower_l** et **_towlower_l** n’ont aucune dépendance vis-à-vis de paramètres régionaux et ne sont pas destinés à être appelée directement. Elles sont fournies pour une utilisation interne par **_totlower_l**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**tolower**|\<ctype.h>|
|**_tolower**|\<ctype.h>|
|**towlower**|\<ctype.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple dans [to, fonctions](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
[to, fonctions](../../c-runtime-library/to-functions.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
