---
title: _ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l
ms.date: 4/2/2020
api_name:
- _ismbckata
- _ismbchira_l
- _ismbchira
- _ismbckata_l
- _o__ismbchira
- _o__ismbchira_l
- _o__ismbckata
- _o__ismbckata_l
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
- ismbckata_l
- _ismbckata_l
- ismbckata
- ismbchira
- _ismbckata
- ismbchira_l
- _ismbchira_l
- _ismbchira
helpviewer_keywords:
- _ismbckata function
- _ismbchira function
- _ismbckata_l function
- Katakana
- ismbchira function
- _ismbchira_l function
- ismbchira_l function
- ismbdkata_l function
- Hiragana
- ismbckata function
ms.assetid: 2db388a2-be31-489b-81c8-f6bf3f0582d3
ms.openlocfilehash: d450702ae41f404606cda1bea613f3d99fadd06f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343217"
---
# <a name="_ismbchira-_ismbchira_l-_ismbckata-_ismbckata_l"></a>_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l

**Fonctions spécifiques à la page de codes 932**

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ismbchira(
   unsigned int c
);
int _ismbchira_l(
   unsigned int c,
   _locale_t locale
);
int _ismbckata(
   unsigned int c
);
int _ismbckata_l(
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

Chacune de ces routines retourne une valeur différente de zéro si le caractère satisfait à la condition de test ou 0 dans le cas contraire. Si *c* <255 et qu’il y a une routine **_ismbb** correspondante (par exemple, **_ismbcalnum** correspond à **_ismbbalnum),** le résultat est la valeur de rendement de la routine **_ismbb** correspondante.

## <a name="remarks"></a>Notes

Chacune de ces fonctions teste un caractère multioctet fourni pour un état donné.

Les versions de ces fonctions avec le **suffixe _l** sont identiques, sauf qu’ils utilisent le lieu passé au lieu de la localisation actuelle pour leur comportement local-dépendant. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

|Routine|Condition de test (page de codes 932 uniquement)|
|-------------|-------------------------------------------|
|**_ismbchira**|Double-byte Hiragana: 0x829F<*'c*<'0x82F1.|
|**_ismbchira_l**|Double-byte Hiragana: 0x829F<*'c*<'0x82F1.|
|**_ismbckata**|Katakana double-byte: 0x8340<'*c*<'0x8396.|
|**_ismbckata_l**|Katakana double-byte: 0x8340<'*c*<'0x8396.|

**Fin De la page de code 932 Spécifique**

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_ismbchira**|\<mbstring.h>|
|**_ismbchira_l**|\<mbstring.h>|
|**_ismbckata**|\<mbstring.h>|
|**_ismbckata_l**|\<mbstring.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classifications des caractères](../../c-runtime-library/character-classification.md)<br/>
[_ismbc, routines](../../c-runtime-library/ismbc-routines.md)<br/>
[is, isw, routines](../../c-runtime-library/is-isw-routines.md)<br/>
[Local](../../c-runtime-library/locale.md)<br/>
[Interprétation des séquences multioctets-caractères](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
