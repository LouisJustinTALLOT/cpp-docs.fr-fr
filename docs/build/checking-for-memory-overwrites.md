---
description: 'En savoir plus sur : vérification des remplacements de mémoire'
title: Vérification des remplacements de mémoire
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: 53361a6aea3de54017be3c966f9500accd21ced1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163169"
---
# <a name="checking-for-memory-overwrites"></a>Vérification des remplacements de mémoire

Si vous recevez une violation d’accès sur un appel à une fonction de manipulation de segment de mémoire, il est possible que votre programme ait endommagé le tas. Voici un symptôme courant de cette situation :

```
Access Violation in _searchseg
```

La fonction [_heapchk](../c-runtime-library/reference/heapchk.md) est disponible à la fois dans les versions Debug et Release (Windows NT uniquement) pour vérifier l’intégrité du tas de la bibliothèque Runtime. Vous pouvez utiliser à `_heapchk` peu près de la même façon que la `AfxCheckMemory` fonction pour isoler un remplacement de segment de mémoire, par exemple :

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

Si cette fonction échoue, vous devez isoler à quel moment le segment de mémoire a été endommagé.

## <a name="see-also"></a>Voir aussi

[Résolution des problèmes de version Release](fixing-release-build-problems.md)
