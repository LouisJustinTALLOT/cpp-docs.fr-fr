---
title: Raccordements de défaillance | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4c69759034dbb7233970bd89616a062a369cc13
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721277"
---
# <a name="failure-hooks"></a>Raccordements de défaillance

Le raccordement de défaillance est activé dans la même manière que le [hook de notification](../../build/reference/notification-hooks.md). La routine de raccordement doit retourner une valeur appropriée afin que le traitement peut continuer (HINSTANCE ou FARPROC) ou 0 pour indiquer qu’une exception doit être levée.

La variable pointeur qui fait référence à la fonction définie par l’utilisateur est :

```
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

Le **DelayLoadInfo** structure contient toutes les données pertinentes nécessaires pour une notification exacte de l’erreur, y compris la valeur à partir de `GetLastError`.

Si la notification est **dliFailLoadLib**, la fonction de raccordement peut retourner :

- 0, si elle ne peut pas gérer l’échec.

- HMODULE, si le raccordement de défaillance résolu le problème et chargé lui-même la bibliothèque.

Si la notification est **dliFailGetProc**, la fonction de raccordement peut retourner :

- 0, si elle ne peut pas gérer l’échec.

- Une adresse valide proc (adresse de fonction d’importation), si le raccordement de défaillance a réussi à obtenir l’adresse elle-même.

## <a name="see-also"></a>Voir aussi

[Gestion et notification des erreurs](../../build/reference/error-handling-and-notification.md)