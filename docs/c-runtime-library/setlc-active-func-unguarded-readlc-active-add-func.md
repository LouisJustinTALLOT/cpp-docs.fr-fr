---
description: 'En savoir plus sur : ___setlc_active_func, ___unguarded_readlc_active_add_func'
title: ___setlc_active_func, ___unguarded_readlc_active_add_func
ms.date: 11/04/2016
api_name:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
api_location:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___unguarded_readlc_active_add_func
- ___setlc_active_func
helpviewer_keywords:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
ms.openlocfilehash: 85273b52102e9cca2e42ba4401da60b1d292560c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277084"
---
# <a name="___setlc_active_func-___unguarded_readlc_active_add_func"></a>___setlc_active_func, ___unguarded_readlc_active_add_func

OBSOLÈTE. Le CRT exporte ces fonctions internes uniquement pour préserver la compatibilité binaire.

## <a name="syntax"></a>Syntaxe

```cpp
int ___setlc_active_func(void);
int * ___unguarded_readlc_active_add_func(void);
```

## <a name="return-value"></a>Valeur de retour

La valeur retournée n'est pas significative.

## <a name="remarks"></a>Notes

Bien que les fonctions CRT internes `___setlc_active_func` et `___unguarded_readlc_active_add_func` soient obsolètes et plus utilisées, elles sont exportées par la bibliothèque CRT pour préserver la compatibilité binaire. Le rôle initial de `___setlc_active_func` était de retourner le nombre d'appels actifs à la fonction `setlocale`. Le rôle initial de `___unguarded_readlc_active_add_func` était de retourner le nombre de fonctions qui référençaient les paramètres locaux sans les verrouiller.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|`___setlc_active_func`, `___unguarded_readlc_active_add_func`|aucun|

## <a name="see-also"></a>Voir aussi

[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)
