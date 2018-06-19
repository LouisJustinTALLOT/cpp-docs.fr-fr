---
title: toupper, _toupper, towupper, _toupper_l, _towupper_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _toupper_l
- towupper
- toupper
- _towupper_l
- _toupper
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
apitype: DLLExport
f1_keywords:
- towupper
- _toupper
- _totupper
- toupper
dev_langs:
- C++
helpviewer_keywords:
- _toupper function
- towupper function
- uppercase, converting strings to
- totupper function
- string conversion, to different characters
- towupper_l function
- toupper_l function
- string conversion, case
- _toupper_l function
- _towupper_l function
- _totupper function
- case, converting
- characters, converting
- toupper function
ms.assetid: cdef1b0f-b19c-4d11-b7d2-cf6334c9b6cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73157691cc1635d038339d9fe707aa535e1df93f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32413458"
---
# <a name="toupper-toupper-towupper-toupperl-towupperl"></a>toupper, _toupper, towupper, _toupper_l, _towupper_l

Convertit le caractère en majuscule.

## <a name="syntax"></a>Syntaxe

```C
int toupper(
   int c
);
int _toupper(
   int c
);
int towupper(
   wint_t c
);
int _toupper_l(
   int c ,
   _locale_t locale
);
int _towupper_l(
   wint_t c ,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Caractère à convertir.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines convertit une copie de *c*, si possible et retourne le résultat.

Si *c* est un caractère large pour lequel **iswlower** est différente de zéro et il existe un caractère large correspondant pour lequel [iswupper](isupper-isupper-l-iswupper-iswupper-l.md) est différent de zéro, **towupper** retourne le caractère large correspondant ; dans le cas contraire, **towupper** retourne *c* inchangée.

Il n’existe aucune valeur de retour réservée pour indiquer une erreur.

Dans l’ordre pour **toupper** afin de donner les résultats attendus, [__isascii](isascii-isascii-iswascii.md) et [islower](islower-iswlower-islower-l-iswlower-l.md) doit retourner différente de zéro.

## <a name="remarks"></a>Notes

Chacune de ces routines convertit une lettre minuscule donnée en lettre majuscule si cela est possible et approprié. La conversion de casse **towupper** est spécifique aux paramètres régionaux. Seuls les caractères relevant des paramètres régionaux actifs changent de casse. Les fonctions sans le **_l** suffixe utiliser actuellement défini aux paramètres régionaux. Les versions de ces fonctions avec le **_l** suffixe prend les paramètres régionaux en tant que paramètre et l’utiliser à la place la paramètres régionaux. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Dans l’ordre pour **toupper** afin de donner les résultats attendus, [__isascii](isascii-isascii-iswascii.md) et [isupper](isupper-isupper-l-iswupper-iswupper-l.md) doit retourner différente de zéro.

[Routines de conversion de données](../../c-runtime-library/data-conversion.md)

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totupper**|**toupper**|**_mbctoupper**|**towupper**|
|**_totupper_l**|**_toupper_l**|**_mbctoupper_l**|**_towupper_l**|

> [!NOTE]
> **_toupper_l** et **_towupper_l** n’ont aucune dépendance des paramètres régionaux et ne sont pas destinés à être appelée directement. Elles sont fournies à un usage interne par **_totupper_l**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**toupper**|\<ctype.h>|
|**_toupper**|\<ctype.h>|
|**towupper**|\<ctype.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple dans [to, fonctions](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Voir aussi

[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
[to, fonctions](../../c-runtime-library/to-functions.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
