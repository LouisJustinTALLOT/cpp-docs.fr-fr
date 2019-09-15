---
title: _ismbbkprint, _ismbbkprint_l
ms.date: 11/04/2016
api_name:
- _ismbbkprint
- _ismbbkprint_l
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
- _ismbbkprint_l
- ismbbkprint
- _ismbbkprint
- ismbbkprint_l
helpviewer_keywords:
- _ismbbkprint function
- ismbbkprint_l function
- ismbbkprint function
- _ismbbkprint_l function
ms.assetid: 8d1d3258-1e34-4365-81ed-97c95de25475
ms.openlocfilehash: e2417718d7cb90e8032cfe9dad903d6610dc6ae7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954110"
---
# <a name="_ismbbkprint-_ismbbkprint_l"></a>_ismbbkprint, _ismbbkprint_l

Détermine si un caractère multioctet particulier est un symbole de ponctuation.

## <a name="syntax"></a>Syntaxe

```C
int _ismbbkprint(
   unsigned int c
);
int _ismbbkprint_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Entier à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur de retour

**_ismbbkprint** retourne une valeur différente de zéro si l’entier *c* est un texte non-ASCII ou un symbole de ponctuation non ASCII ou 0 dans le cas contraire. Par exemple, dans la page de codes 932 uniquement, **_ismbbkprint** teste la ponctuation katakana alphanumérique ou Katakana (plage : 0xA1 - 0xDF). **_ismbbkprint** utilise les paramètres régionaux actuels pour les paramètres de caractères dépendants des paramètres régionaux. **_ismbbkprint_l** est identique, à ceci près qu’il utilise les paramètres régionaux passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_ismbbkprint**|\<mbctype.h>|
|**_ismbbkprint_l**|\<mbctype.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classification d’octets](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb, routines](../../c-runtime-library/ismbb-routines.md)<br/>
