---
title: Utilisation de la version debug pour vérifier les remplacements de mémoire
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
ms.openlocfilehash: 42e3a7f1f1c34ba5a263adfca7496c24e162ab5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314284"
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>Utilisation de la version debug pour vérifier les remplacements de mémoire

Pour utiliser la version Debug pour vérifier le remplacement de mémoire, vous devez d’abord régénérer votre projet pour le débogage. Ensuite, accédez au début de la `InitInstance` fonction de votre application et ajoutez la ligne suivante :

```
afxMemDF |= checkAlwaysMemDF;
```

L’allocateur de mémoire de débogage place des octets de protection autour de toutes les allocations de mémoire. Toutefois, ces octets de protection ne sont pas utiles, à moins que vous ne vérifiiez s’ils ont été modifiés (ce qui indiquerait un remplacement de mémoire). Dans le cas contraire, il fournit simplement une mémoire tampon qui peut, en fait, vous permettre de vous débarrasser d’un remplacement de mémoire.

En activant `checkAlwaysMemDF`le, vous forcerez les MFC à appeler `AfxCheckMemory` la fonction chaque fois qu’un appel à **New** ou **Delete** est effectué. Si un remplacement de mémoire a été détecté, il génère un message de TRACE qui ressemble à ce qui suit :

```
Damage Occurred! Block=0x5533
```

Si vous voyez l’un de ces messages, vous devez parcourir votre code pour déterminer où les dommages se sont produits. Pour isoler plus précisément l’emplacement où le remplacement de mémoire s’est produit, vous pouvez `AfxCheckMemory` effectuer des appels explicites à vous-même. Par exemple :

```
ASSERT(AfxCheckMemory());
    DoABunchOfStuff();
    ASSERT(AfxCheckMemory());
```

Si la première assertion réussit et que la deuxième échoue, cela signifie que le remplacement de mémoire doit avoir eu lieu dans la fonction entre les deux appels.

Selon la nature de votre application, vous pouvez constater que `afxMemDF` votre programme s’exécute trop lentement pour un test même. La `afxMemDF` variable entraîne `AfxCheckMemory` l’appel de pour chaque appel à New et DELETE. Dans ce cas, vous devez répartir vos propres appels `AfxCheckMemory`à () comme indiqué ci-dessus et essayer d’isoler le remplacement de la mémoire de cette façon.

## <a name="see-also"></a>Voir aussi

[Résolution de problèmes liés à la version release](fixing-release-build-problems.md)
