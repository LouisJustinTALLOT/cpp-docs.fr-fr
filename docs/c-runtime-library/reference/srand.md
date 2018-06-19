---
title: srand | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- srand
apilocation:
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
apitype: DLLExport
f1_keywords:
- srand
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2b527561e312ce9c50dce106a243d7e49a1d303
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32406886"
---
# <a name="srand"></a>srand

Définit la valeur de départ de départ pour le Générateur de nombres pseudo-aléatoires utilisé par le **rand** (fonction).

## <a name="syntax"></a>Syntaxe

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>Paramètres

*valeur initiale* valeur initiale pour la génération de nombres pseudo-aléatoires

## <a name="remarks"></a>Notes

Le **srand** fonction définit le point de départ pour la génération d’une série d’entiers pseudo-aléatoire dans le thread actuel. Pour réinitialiser le générateur pour créer la même séquence de résultats, appelez le **srand** de fonction et utilisent le même *seed* argument à nouveau. Toute autre valeur pour *seed* définit le Générateur à un autre point de départ de la séquence pseudo-aléatoire. **RAND** récupère les nombres pseudo-aléatoires qui sont générés. Appel de **rand** avant tout appel à **srand** génère la même séquence que l’appel **srand** avec *seed* passé en tant que 1.

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
