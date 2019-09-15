---
title: srand
ms.date: 01/02/2018
api_name:
- srand
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
ms.openlocfilehash: 03e2b87a37d1b520b6e2b32c2f756fea625eb9a2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957998"
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

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

Consultez l’exemple relatif à [rand](rand.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
