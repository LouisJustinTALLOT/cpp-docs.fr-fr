---
title: srand
ms.date: 4/2/2020
api_name:
- srand
- _o_srand
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- srand
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
ms.openlocfilehash: a8d018d429b2a484f88b7c1e0679f1f799983910
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355483"
---
# <a name="srand"></a>srand

Définit la valeur de démarrage de la graine de pseudorandom nombre utilisé par la fonction **rand.**

## <a name="syntax"></a>Syntaxe

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>Paramètres

*seed*<br/>
Valeur initiale pour la génération de nombres pseudo-aléatoires

## <a name="remarks"></a>Notes

La fonction **srand** définit le point de départ pour générer une série d’intégrages pseudorandom dans le fil actuel. Pour réinitialiser le générateur pour créer la même séquence de résultats, appelez la fonction **srand** et utilisez à nouveau le même argument *de graine.* Toute autre valeur pour *les graines* définit le générateur à un point de départ différent dans la séquence de pseudorandom. **rand** récupère les nombres de pseudorandom qui sont générés. Appeler **rand** avant tout appel au **srand** génère la même séquence que **d’appeler srand** avec *des graines* passées comme 1.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [rand](rand.md).

## <a name="see-also"></a>Voir aussi

[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md)<br/>
[Rand](rand.md)<br/>
