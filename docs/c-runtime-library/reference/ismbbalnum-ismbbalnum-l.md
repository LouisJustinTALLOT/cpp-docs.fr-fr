---
description: 'En savoir plus sur : _ismbbalnum, _ismbbalnum_l'
title: _ismbbalnum, _ismbbalnum_l
ms.date: 4/2/2020
api_name:
- _ismbbalnum
- _ismbbalnum_l
- _o__ismbbalnum
- _o__ismbbalnum_l
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
- _ismbbalnum
- ismbbalnum
- _ismbbalnum_l
- ismbbalnum_l
helpviewer_keywords:
- _ismbbalnum_l function
- ismbbalnum function
- ismbbalnum_l function
- _ismbbalnum function
ms.assetid: 8025de50-a871-49fd-9ae6-f437b47aa987
ms.openlocfilehash: e4caf523d788cba4466d3d21beb6470d80b9aefd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306330"
---
# <a name="_ismbbalnum-_ismbbalnum_l"></a>_ismbbalnum, _ismbbalnum_l

Détermine si un caractère multioctet spécifié est alphabétique ou numérique.

## <a name="syntax"></a>Syntaxe

```C
int _ismbbalnum(
   unsigned int c
);
int _ismbbalnum_l(
   unsigned int c
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Entier à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

**_ismbbalnum** retourne une valeur différente de zéro si l’expression :

`isalnum(c) || _ismbbkalnum(c)`

est différent de zéro pour *c*, ou 0 si ce n’est pas le cas.

La version de cette fonction avec le suffixe **_L** est identique, sauf qu’elle utilise les paramètres régionaux passés au lieu des paramètres régionaux actuels pour son comportement dépendant des paramètres régionaux.

## <a name="remarks"></a>Notes

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_ismbbalnum**|\<mbctype.h>|
|**_ismbbalnum_l**|\<mbctype.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Classification d’octets](../../c-runtime-library/byte-classification.md)<br/>
[Routines de _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
