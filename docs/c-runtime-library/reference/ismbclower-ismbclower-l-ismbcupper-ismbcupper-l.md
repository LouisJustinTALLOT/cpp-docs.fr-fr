---
title: _ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l
ms.date: 4/2/2020
api_name:
- _ismbclower
- _ismbclower_l
- _ismbcupper_l
- _ismbcupper
- _o__ismbclower
- _o__ismbclower_l
- _o__ismbcupper
- _o__ismbcupper_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbcupper
- _ismbclower
helpviewer_keywords:
- _ismbcupper function
- ismbclower function
- _ismbclower_l function
- ismbcupper_l function
- _ismbclower function
- ismbcupper function
- ismbclower_l function
- _ismbcupper_l function
ms.assetid: 17d89587-65bc-477c-ba8f-a84e63cf59e7
ms.openlocfilehash: 9a0991d974c33cff22044364f7a4351f160215a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342929"
---
# <a name="_ismbclower-_ismbclower_l-_ismbcupper-_ismbcupper_l"></a>_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l

Vérifie si un caractère multioctet est un caractère minuscule ou majuscule.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ismbclower(
   unsigned int c
);
int _ismbclower_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcupper(
   unsigned int c
);
int _ismbcupper_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*C*<br/>
Caractère à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines retourne une valeur différente de zéro si le caractère satisfait à la condition de test ou 0 dans le cas contraire. Si *c*<255 et qu’il y a une routine **_ismbb** correspondante (par exemple, **_ismbcalnum** correspond à **_ismbbalnum),** le résultat est la valeur de rendement de la routine **_ismbb** correspondante.

## <a name="remarks"></a>Notes

Chacune de ces fonctions teste un caractère multioctet fourni pour un état donné.

Les versions de ces fonctions avec le **suffixe _l** sont identiques, sauf qu’ils utilisent le lieu passé au lieu de la localisation actuelle pour leur comportement local-dépendant. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

|Routine|Condition de test|Exemple de page de codes 932|
|-------------|--------------------|---------------------------|
|**_ismbclower**|Caractère alphabétique minuscule|Retourne nonzero si et seulement si *c* est une représentation d’un seul-byte d’une lettre anglaise asCII lowercase: 0x61<*c*<'0x7A.|
|**_ismbclower_l**|Caractère alphabétique minuscule|Retourne nonzero si et seulement si *c* est une représentation d’un seul-byte d’une lettre anglaise asCII lowercase: 0x61<*c*<'0x7A.|
|**_ismbcupper**|Caractère alphabétique majuscule|Retourne nonzero si et seulement si *c* est une représentation unique-byte d’une lettre anglaise ASCII uppercase: 0x41<'*c*<'0x5A.|
|**_ismbcupper_l**|Caractère alphabétique majuscule|Retourne nonzero si et seulement si *c* est une représentation unique-byte d’une lettre anglaise ASCII uppercase: 0x41<'*c*<'0x5A.|

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_ismbclower**|\<mbstring.h>|
|**_ismbclower_l**|\<mbstring.h>|
|**_ismbcupper**|\<mbstring.h>|
|**_ismbcupper_l**|\<mbstring.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[_ismbc, routines](../../c-runtime-library/ismbc-routines.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
[routines _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
