---
title: _ismbblead, _ismbblead_l
description: Décrit la bibliothèque Microsoft C Runtime (CRT) _ismbblead et les fonctions _ismbblead_l.
ms.date: 01/08/2020
api_name:
- _ismbblead_l
- _ismbblead
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
ms.openlocfilehash: 6a7bb992eeeb9c66a7cbdea0ed34cf797d374617
ms.sourcegitcommit: 7bd3567fc6a0e7124aab51cad63bbdb44a99a848
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75755036"
---
# <a name="_ismbblead-_ismbblead_l"></a>_ismbblead, _ismbblead_l

Teste un caractère pour déterminer s’il s’agit d’un octet de tête d’un caractère multioctet.

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

### <a name="parameters"></a>Parameters

\ *c*
Entier à tester.

*paramètres régionaux*\
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

Retourne une valeur différente de zéro si l’entier *c* est le premier octet d’un caractère multioctet.

## <a name="remarks"></a>Notes

Les caractères multioctets sont constitués d’un octet de tête suivi d’un octet de fin. Les octets de tête se distinguent en faisant partie d’une plage particulière pour un jeu de caractères donné. Par exemple, dans la page de codes 932 uniquement, les octets de tête sont compris entre 0x81-0x9F et 0xE0-0xFC.

**_ismbblead** utilise les paramètres régionaux actuels pour le comportement dépendant des paramètres régionaux. **_ismbblead_l** est identique, à ceci près qu’il utilise à la place les paramètres régionaux transmis. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

Lorsque les paramètres régionaux sont UTF-8, **_ismbblead** et **_ismbblead_l** retournent toujours 0 (false), que *c* soit un octet de tête ou non.

**_ismbblead** et **_ismbblead_l** sont spécifiques à Microsoft et ne font pas partie de la bibliothèque C standard. Nous vous déconseillons de les utiliser là où vous voulez un code portable. Pour la compatibilité C standard, utilisez **mbrlen** à la place.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlead**|Retourne toujours la valeur false|**_ismbblead**|Retourne toujours la valeur false|

## <a name="requirements"></a>Configuration requise pour

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_ismbblead**|\<mbctype.h> ou \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|
|**_ismbblead_l**|\<mbctype.h> ou \<mbstring.h>|\<ctype.h>,* \<limits.h>, \<stdlib.h>|

\* Pour les constantes manifestes des conditions de test.

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

\ de [classification d’octets](../../c-runtime-library/byte-classification.md)
[routines de _ismbb](../../c-runtime-library/ismbb-routines.md)\
[mbrlen](mbrlen.md)
