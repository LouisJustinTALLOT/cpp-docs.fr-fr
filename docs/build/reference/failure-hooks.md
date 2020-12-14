---
description: 'En savoir plus sur : raccordements de défaillance'
title: Raccordements de défaillance
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
ms.openlocfilehash: a0e74e3413fc81505941dd6f4545988a0d39436f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200726"
---
# <a name="failure-hooks"></a>Raccordements de défaillance

Le hook d’échec est activé de la même manière que le [raccordement de notification](notification-hooks.md). La routine de raccordement doit retourner une valeur appropriée afin que le traitement puisse continuer (HINSTANCE ou FARPROC) ou 0 pour indiquer qu’une exception doit être levée.

La variable pointeur qui fait référence à la fonction définie par l’utilisateur est la suivante :

```
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

La structure **DelayLoadInfo** contient toutes les données pertinentes nécessaires pour la création de rapports précis sur l’erreur, y compris la valeur de `GetLastError` .

Si la notification est **dliFailLoadLib**, la fonction de raccordement peut retourner :

- 0, s’il ne peut pas gérer l’échec.

- Un HMODULE, si le raccordement de défaillance a résolu le problème et a chargé la bibliothèque elle-même.

Si la notification est **dliFailGetProc**, la fonction de raccordement peut retourner :

- 0, s’il ne peut pas gérer l’échec.

- Adresse de procédure valide (adresse de la fonction d’importation) si le hook d’échec a réussi à obtenir l’adresse elle-même.

## <a name="see-also"></a>Voir aussi

[Gestion et notification des erreurs](error-handling-and-notification.md)
