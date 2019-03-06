---
title: Vérification des remplacements de mémoire
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: b37bd68519aea1194b601e89fefd0f14d428630a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422193"
---
# <a name="checking-for-memory-overwrites"></a>Vérification des remplacements de mémoire

Si vous obtenez une violation d’accès sur un appel à une fonction de manipulation de tas, il est possible que votre programme a altéré le tas. Un problème courant de cette situation serait :

```
Access Violation in _searchseg
```

Le [_heapchk](../../c-runtime-library/reference/heapchk.md) fonction est disponible dans les versions debug et release génère (Windows NT uniquement) pour vérifier l’intégrité du tas de bibliothèque d’exécution. Vous pouvez utiliser `_heapchk` dans la même façon que le `AfxCheckMemory` (fonction) pour identifier un remplacement tas, par exemple :

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

Si cette fonction échoue, vous devez isoler à quel point le tas a été endommagé.

## <a name="see-also"></a>Voir aussi

[Résolution de problèmes liés à la version Release](../../build/reference/fixing-release-build-problems.md)
