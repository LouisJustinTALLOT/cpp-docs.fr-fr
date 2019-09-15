---
title: _ismbbblank, _ismbbblank_l
ms.date: 11/04/2016
api_name:
- _ismbbblank_l
- _ismbbblank
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
ms.assetid: d21b2e41-7206-41f5-85bb-9c9ab4f3e21b
ms.openlocfilehash: 21f4c88b00774159f8e6945973641e67718494e6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954243"
---
# <a name="_ismbbblank-_ismbbblank_l"></a>_ismbbblank, _ismbbblank_l

Détermine si un caractère multioctet spécifié est un caractère vide.

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _ismbbblank(
   unsigned int c
);
int _ismbbblank_l(
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

**_ismbbblank** retourne une valeur différente de zéro si *c* représente un caractère d’espace (0x20), un caractère de tabulation horizontale (0x09) ou un caractère spécifique aux paramètres régionaux qui est utilisé pour séparer les mots dans une ligne de texte pour laquelle **isspace** a la valeur true. Sinon, retourne 0. **_ismbbblank** utilise les paramètres régionaux actuels pour tout comportement dépendant des paramètres régionaux. **_ismbbblank_l** est identique, à ceci près qu’il utilise à la place les paramètres régionaux qui sont passés. Pour plus d’informations, consultez [Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_ismbbblank**|\<mbctype.h>|
|**_ismbbblank_l**|\<mbctype.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Classification d’octets](../../c-runtime-library/byte-classification.md)<br/>
[_ismbb, routines](../../c-runtime-library/ismbb-routines.md)<br/>
