---
title: _ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l
ms.date: 11/04/2016
apiname:
- _ismbclower
- _ismbclower_l
- _ismbcupper_l
- _ismbcupper
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 29a1e97f4583808931e5228a6905aed7c0a62702
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157272"
---
# <a name="ismbclower-ismbclowerl-ismbcupper-ismbcupperl"></a>_ismbclower, _ismbclower_l, _ismbcupper, _ismbcupper_l

Vérifie si un caractère multioctet est un caractère minuscule ou majuscule.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*c*<br/>
Caractère à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Chacune de ces routines retourne une valeur différente de zéro si le caractère satisfait à la condition de test ou 0 dans le cas contraire. Si *c*< = 255 et qu’il existe un correspondant **_ismbb** routine (par exemple, **_ismbcalnum** correspond à **_ismbbalnum**), le Il en résulte la valeur de retour correspondantes **_ismbb** routine.

## <a name="remarks"></a>Notes

Chacune de ces fonctions teste un caractère multioctet fourni pour un état donné.

Les versions de ces fonctions avec le **_l** suffixe sont identiques, sauf qu’ils utilisent les paramètres régionaux passé au lieu des paramètres régionaux actuels pour leur comportement dépendant des paramètres régionaux. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

|Routine|Condition de test|Exemple de page de codes 932|
|-------------|--------------------|---------------------------|
|**_ismbclower**|Caractère alphabétique minuscule|Retourne une valeur différente de zéro si et seulement si *c* est une représentation d’un octet d’une lettre en anglais minuscule ASCII : 0x61<=*c*<=0x7A.|
|**_ismbclower_l**|Caractère alphabétique minuscule|Retourne une valeur différente de zéro si et seulement si *c* est une représentation d’un octet d’une lettre en anglais minuscule ASCII : 0x61<=*c*<=0x7A.|
|**_ismbcupper**|Caractère alphabétique majuscule|Retourne une valeur différente de zéro si et seulement si *c* est une représentation d’un octet d’un caractère en anglais majuscule ASCII : 0 x 41 < =*c*< = 0x5A.|
|**_ismbcupper_l**|Caractère alphabétique majuscule|Retourne une valeur différente de zéro si et seulement si *c* est une représentation d’un octet d’un caractère en anglais majuscule ASCII : 0 x 41 < =*c*< = 0x5A.|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_ismbclower**|\<mbstring.h>|
|**_ismbclower_l**|\<mbstring.h>|
|**_ismbcupper**|\<mbstring.h>|
|**_ismbcupper_l**|\<mbstring.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[_ismbc, routines](../../c-runtime-library/ismbc-routines.md)<br/>
[Paramètres régionaux](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences de caractères multi-octets](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb, routines](../../c-runtime-library/ismbb-routines.md)<br/>
