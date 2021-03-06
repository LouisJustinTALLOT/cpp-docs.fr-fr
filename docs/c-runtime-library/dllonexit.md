---
description: 'En savoir plus sur : __dllonexit'
title: __dllonexit
ms.date: 11/04/2016
api_name:
- __dllonexit
api_location:
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __dllonexit
helpviewer_keywords:
- __dllonexit
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
ms.openlocfilehash: ef9dc444ecb1b36062a4dc9ea98ec9a15804f930
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151825"
---
# <a name="__dllonexit"></a>__dllonexit

Inscrit une routine à appeler au moment de la sortie.

## <a name="syntax"></a>Syntaxe

```
_onexit_t __dllonexit(   _onexit_t func,
   _PVFV **  pbegin,
   _PVFV **  pend
   )
```

#### <a name="parameters"></a>Paramètres

*func*<br/>
Pointeur vers une fonction à exécuter à la sortie.

*pbegin*<br/>
Pointeur vers une variable qui pointe vers le début d’une liste de fonctions à exécuter au moment du détachement.

*pend*<br/>
Pointeur vers une variable qui pointe vers la fin d’une liste de fonctions à exécuter au moment du détachement.

## <a name="return-value"></a>Valeur renvoyée

Si l’opération réussit, pointeur vers la fonction de l’utilisateur. Dans le cas contraire, pointeur **NULL**.

## <a name="remarks"></a>Notes

La fonction `__dllonexit` est analogue à la fonction [_onexit](../c-runtime-library/reference/onexit-onexit-m.md) sauf que les variables globales utilisées par cette fonction ne sont pas visibles pour cette routine. Au lieu de variables globales, cette fonction utilise les paramètres `pbegin` et `pend`.

Les fonctions `_onexit` et `atexit` dans une DLL liée à MSVCRT.LIB doivent conserver leur propre liste atexit/_onexit. Cette routine est le processus de travail appelé par de telles DLL.

Le type `_PVFV` est défini en tant que `typedef void (__cdecl *_PVFV)(void)`.

## <a name="requirements"></a>Spécifications

|Routine|Fichier obligatoire|
|-------------|-------------------|
|__dllonexit|onexit.c|

## <a name="see-also"></a>Voir aussi

[_onexit, _onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)
