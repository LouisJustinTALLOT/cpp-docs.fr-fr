---
description: 'En savoir plus sur : srand'
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: bea91841b549fae09faa4345767fc22cf4d6208e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292168"
---
# <a name="srand"></a>srand

Définit la valeur initiale de départ pour le générateur de nombres pseudo-aléatoires utilisé par la fonction **Rand** .

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

La fonction **srand** définit le point de départ pour générer une série d’entiers Pseudo-aléatoires dans le thread actuel. Pour réinitialiser le générateur afin de créer la même séquence de résultats, appelez la fonction **srand** et réutilisez le même argument *Seed* . Toute autre valeur pour *Seed* définit le générateur à un point de départ différent dans la séquence Pseudo-aléatoire. **Rand** récupère les nombres pseudo-aléatoires qui sont générés. L’appel de **Rand** avant tout appel à **srand** génère la même séquence que l’appel de **srand** avec une *valeur de départ* passée comme 1.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [rand](rand.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
