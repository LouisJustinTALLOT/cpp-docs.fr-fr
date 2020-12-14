---
description: 'En savoir plus sur : _ismbbkpunct, _ismbbkpunct_l'
title: _ismbbkpunct, _ismbbkpunct_l
ms.date: 4/2/2020
api_name:
- _ismbbkpunct_l
- _ismbbkpunct
- _o__ismbbkpunct
- _o__ismbbkpunct_l
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
- ismbbkpunct_l
- _ismbbkpunct_l
- ismbbkpunct
- _ismbbkpunct
helpviewer_keywords:
- _ismbbkpunct_l function
- ismbbkpunct_l function
- ismbbkpunct function
- _ismbbkpunct function
ms.assetid: a04c59cd-5ca7-4296-bec0-2b0d7f04edd0
ms.openlocfilehash: da17df927b337e67df553baec8d56491db10a3d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229728"
---
# <a name="_ismbbkpunct-_ismbbkpunct_l"></a>_ismbbkpunct, _ismbbkpunct_l

Vérifie si un caractère multioctet est un caractère de ponctuation.

## <a name="syntax"></a>Syntaxe

```C
int _ismbbkpunct(
   unsigned int c
);
int _ismbbkpunct_l(
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

**_ismbbkpunct** retourne une valeur différente de zéro si l’entier *c* est un symbole de ponctuation non-ASCII, ou 0 dans le cas contraire. Par exemple, dans la page de codes 932 uniquement, **_ismbbkpunct** teste la présence d’une ponctuation katakana. **_ismbbkpunct** utilise les paramètres régionaux actuels pour les paramètres de caractères dépendants des paramètres régionaux. **_ismbbkpunct_l** est identique, à ceci près qu’il utilise les paramètres régionaux qui sont passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Notes

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_ismbbkpunct**|\<mbctype.h>|
|**_ismbbkpunct_l**|\<mbctype.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classification d’octets](../../c-runtime-library/byte-classification.md)<br/>
[Routines de _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
