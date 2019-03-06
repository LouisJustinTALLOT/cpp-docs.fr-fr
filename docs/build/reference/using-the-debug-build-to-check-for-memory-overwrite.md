---
title: Utilisation de la version debug pour vérifier les remplacements de mémoire
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
ms.openlocfilehash: 75f4d5aeddc617173aa33d96f8ff934fb8c1b320
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413834"
---
# <a name="using-the-debug-build-to-check-for-memory-overwrite"></a>Utilisation de la version debug pour vérifier les remplacements de mémoire

Pour utiliser la version debug pour vérifier les remplacements de mémoire, vous devez tout d’abord régénérer votre projet pour le débogage. Ensuite, accédez à tout au début de votre application `InitInstance` de fonction et ajoutez la ligne suivante :

```
afxMemDF |= checkAlwaysMemDF;
```

L’allocateur de mémoire debug place les octets de protection autour de toutes les allocations de mémoire. Toutefois, ces octets de garde ne servent à rien, sauf si vous vérifiez si elles ont été modifiés (ce qui indiquerait un remplacement de mémoire). Sinon, il fournit simplement une mémoire tampon qui peut, en fait, vous permettent de vous en sortir avec un remplacement de mémoire.

En activant le `checkAlwaysMemDF`, vous forcerez MFC pour effectuer un appel à la `AfxCheckMemory` fonction chaque fois qu’un appel à **nouveau** ou **supprimer** est effectuée. Si un remplacement de mémoire a été détecté, il génère un message TRACE qui ressemble à ce qui suit :

```
Damage Occurred! Block=0x5533
```

Si vous voyez un de ces messages, vous devez parcourir votre code pour déterminer où les dommages s’est produite. Pour identifier plus précisément où le remplacement de mémoire s’est produite, vous pouvez effectuer des appels explicites à `AfxCheckMemory` vous-même. Exemple :

```
ASSERT(AfxCheckMemory());
    DoABunchOfStuff();
    ASSERT(AfxCheckMemory());
```

Si la première instruction ASSERT réussit et que la seconde échoue, cela signifie que le remplacement de mémoire doit se sont produites dans la fonction entre les deux appels.

Selon la nature de votre application, vous pouvez constater que `afxMemDF` entraîne l’exécution trop lente même pour un test de votre programme. Le `afxMemDF` provoque la variable `AfxCheckMemory` à pour chaque appel à new et delete. Dans ce cas, vous devez distribuer vos propres appels à `AfxCheckMemory`(), comme indiqué ci-dessus et essayez d’isoler la mémoire remplacement de cette manière.

## <a name="see-also"></a>Voir aussi

[Résolution de problèmes liés à la version Release](../../build/reference/fixing-release-build-problems.md)
