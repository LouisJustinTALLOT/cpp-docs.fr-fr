---
description: 'En savoir plus sur : _ismbbalpha, _ismbbalpha_l'
title: _ismbbalpha, _ismbbalpha_l
ms.date: 4/2/2020
api_name:
- _ismbbalpha
- _ismbbalpha_l
- _o__ismbbalpha
- _o__ismbbalpha_l
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
- ismbbalpha
- ismbbalpha_l
- _ismbbalpha
- _ismbbalpha_l
helpviewer_keywords:
- ismbbalpha function
- ismbbalpha_l function
- _ismbbalpha function
- _ismbbalpha_l function
ms.assetid: 8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0
ms.openlocfilehash: 93ae26ff54af4cdee5f99e51c8f85d14ec51ae4e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335662"
---
# <a name="_ismbbalpha-_ismbbalpha_l"></a>_ismbbalpha, _ismbbalpha_l

Détermine si un caractère multioctet spécifié est alphanumérique.

## <a name="syntax"></a>Syntaxe

```C
int _ismbbalpha(
   unsigned int c
);
int _ismbbalpha_l(
   unsigned int c
);
```

### <a name="parameters"></a>Paramètres

*c*<br/>
Entier à tester.

*locale*<br/>
Paramètres régionaux à utiliser.

## <a name="return-value"></a>Valeur renvoyée

**_ismbbalpha** retourne une valeur différente de zéro si l’expression :

`isalpha(c) || _ismbbkalnum(c)`

est différent de zéro pour *c*, ou 0 si ce n’est pas le cas. **_ismbbalpha** utilise les paramètres régionaux actuels pour les paramètres de caractères dépendants des paramètres régionaux. **_ismbbalpha_l** est identique, à ceci près qu’elle utilise les paramètres régionaux passés.

## <a name="remarks"></a>Notes

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_ismbbalpha**|\<mbctype.h>|
|**_ismbbalpha_l**|\<mbctype.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Classification d’octets](../../c-runtime-library/byte-classification.md)<br/>
[Routines de _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
