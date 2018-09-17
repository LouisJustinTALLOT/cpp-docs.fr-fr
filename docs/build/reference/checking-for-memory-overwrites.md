---
title: Vérification des remplacements de mémoire | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 246f625e899016080662f27a5901962c1c62f1a8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718640"
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