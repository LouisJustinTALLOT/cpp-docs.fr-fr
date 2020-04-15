---
title: _ismbblead, _ismbblead_l
description: Décrit les fonctions Microsoft C Runtime Library (CRT) _ismbblead et _ismbblead_l.
ms.date: 4/2/2020
api_name:
- _ismbblead_l
- _ismbblead
- _o__ismbblead
- _o__ismbblead_l
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
- ismbblead_l
- istlead
- _ismbblead
- _ismbblead_l
- ismbblead
- _istlead
helpviewer_keywords:
- _ismbblead_l function
- ismbblead function
- _ismbblead function
- istlead function
- ismbblead_l function
- _istlead function
ms.assetid: 2abc6f75-ed5c-472e-bfd0-e905a1835ccf
ms.openlocfilehash: ee3085d49a27f2f3c97c6578463cf3a0598b73c7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343578"
---
# <a name="_ismbblead-_ismbblead_l"></a>_ismbblead, _ismbblead_l

Teste un personnage pour déterminer s’il s’agit d’un byte de plomb d’un caractère multioctet.

## <a name="syntax"></a>Syntaxe

```C
int _ismbblead(
   unsigned int c
);
int _ismbblead_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*C*\
Entier à tester.

*locale*\
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur retournée

Retourne une valeur non zéro si l’integer *c* est le premier byte d’un caractère multioctet.

## <a name="remarks"></a>Notes

Les caractères multioctets sont constitués d’un octet de tête suivi d’un octet de fin. Les octets de tête se distinguent en faisant partie d’une plage particulière pour un jeu de caractères donné. Par exemple, dans la page de code 932 seulement, les octets de plomb vont de 0x81 - 0x9F et 0xE0 - 0xFC.

**_ismbblead** utilise le lieu actuel pour un comportement local-dépendant. **_ismbblead_l** est identique, sauf qu’il utilise le lieu passé à la place. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Lorsque le lieu est UTF-8, **_ismbblead** et **_ismbblead_l** toujours retourner 0 (faux), si *c* est un byte de plomb ou non.

**_ismbblead** et **_ismbblead_l** sont spécifiques à Microsoft, ne faisant pas partie de la bibliothèque Standard C. Nous ne vous recommandons pas de les utiliser là où vous voulez du code portable. Pour la compatibilité Standard C, utilisez **plutôt le mbrlen.**

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Cartographies de routine de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead**|Retourne toujours la valeur false|**_ismbblead**|Retourne toujours la valeur false|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_ismbblead**|\<mbctype.h> ou \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbblead_l**|\<mbctype.h> ou \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|

\* Pour les constantes manifestes des conditions de test.

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classification Byte](../../c-runtime-library/byte-classification.md)\
[_ismbb routines](../../c-runtime-library/ismbb-routines.md)\
[mbrlen](mbrlen.md)
