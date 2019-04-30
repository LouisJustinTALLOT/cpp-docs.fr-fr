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

Si vous obtenez une violation d’accès sur un appel à une fonction de manipulation de tas, il est possible que votre programme a altéré le tas. Un problème courant de cette situation serait :

```
Access Violation in _searchseg
```

Le [_heapchk](../c-runtime-library/reference/heapchk.md) fonction est disponible dans les versions debug et release génère (Windows NT uniquement) pour vérifier l’intégrité du tas de bibliothèque d’exécution. Vous pouvez utiliser `_heapchk` dans la même façon que le `AfxCheckMemory` (fonction) pour identifier un remplacement tas, par exemple :

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

Si cette fonction échoue, vous devez isoler à quel point le tas a été endommagé.

## <a name="see-also"></a>Voir aussi

[Résolution de problèmes liés à la version Release](fixing-release-build-problems.md)
