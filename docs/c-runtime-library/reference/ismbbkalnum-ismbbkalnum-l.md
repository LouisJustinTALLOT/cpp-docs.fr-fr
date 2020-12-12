---
description: 'En savoir plus sur : _ismbbkalnum, _ismbbkalnum_l'
title: _ismbbkalnum, _ismbbkalnum_l
ms.date: 4/2/2020
api_name:
- _ismbbkalnum
- _ismbbkalnum_l
- _o__ismbbkalnum
- _o__ismbbkalnum_l
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ismbbkalnum
- ismbbkalnum
- ismbbkalnum_l
- _ismbbkalnum_l
helpviewer_keywords:
- _ismbbkalnum_l function
- ismbbkalnum_l function
- _ismbbkalnum function
- ismbbkalnum function
ms.assetid: e1d70e7b-29d0-469c-9d93-442b99de22ac
ms.openlocfilehash: c9f18a80882b9f0bc703b0fbf5caace9746a486e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306311"
---
# <a name="_ismbbkalnum-_ismbbkalnum_l"></a>_ismbbkalnum, _ismbbkalnum_l

Détermine si un caractère multioctet particulier est un symbole de texte non ASCII.

## <a name="syntax"></a>Syntaxe

```C
int _ismbbkalnum(
   unsigned int c
);
int _ismbbkalnum_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Entier à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

**_ismbbkalnum** retourne une valeur différente de zéro si l’entier *c* est un symbole de texte non-ASCII autre que la ponctuation, ou 0 dans le cas contraire. **_ismbbkalnum** utilise les paramètres régionaux actifs pour les informations sur les caractères dépendants des paramètres régionaux. **_ismbbkalnum_l** est identique à **_ismbbkalnum** sauf qu’il prend les paramètres régionaux en tant que paramètre. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Notes

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_ismbbkalnum**|\<mbctype.h>|
|**_ismbbkalnum_l**|\<mbctype.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classification d’octets](../../c-runtime-library/byte-classification.md)<br/>
[Routines de _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
