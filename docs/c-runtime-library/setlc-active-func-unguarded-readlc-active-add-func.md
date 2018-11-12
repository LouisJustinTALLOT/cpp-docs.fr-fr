---
title: ___setlc_active_func, ___unguarded_readlc_active_add_func
ms.date: 11/04/2016
apiname:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
apilocation:
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- ___unguarded_readlc_active_add_func
- ___setlc_active_func
helpviewer_keywords:
- ___setlc_active_func
- ___unguarded_readlc_active_add_func
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
ms.openlocfilehash: 23095bb13108ec9fde2b168035009f440e9d96f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525776"
---
# <a name="setlcactivefunc-unguardedreadlcactiveaddfunc"></a>___setlc_active_func, ___unguarded_readlc_active_add_func

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

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|`___setlc_active_func`, `___unguarded_readlc_active_add_func`|none|

## <a name="see-also"></a>Voir aussi

[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)