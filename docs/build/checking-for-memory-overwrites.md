---
title: Vérification des remplacements de mémoire
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: 2c59cb96d640df6dcd96b9e0eafbcd325ed475f5
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342253"
---
# <a name="checking-for-memory-overwrites"></a>Vérification des remplacements de mémoire

Si vous recevez une violation d’accès sur un appel à une fonction de manipulation de segment de mémoire, il est possible que votre programme ait endommagé le tas. Voici un symptôme courant de cette situation :

```
Access Violation in _searchseg
```

La fonction [_heapchk](../c-runtime-library/reference/heapchk.md) est disponible à la fois dans les versions Debug et Release (Windows NT uniquement) pour vérifier l’intégrité du tas de la bibliothèque Runtime. Vous pouvez utiliser `_heapchk` à peu près de la même façon `AfxCheckMemory` que la fonction pour isoler un remplacement de segment de mémoire, par exemple :

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

Si cette fonction échoue, vous devez isoler à quel moment le segment de mémoire a été endommagé.

## <a name="see-also"></a>Voir aussi

[Résolution de problèmes liés à la version release](fixing-release-build-problems.md)
