---
title: Vérification des remplacements de mémoire | Documents Microsoft
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
ms.openlocfilehash: 258aa6ae01d48df6717135f7dc8b73fc3f9e697a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369849"
---
# <a name="checking-for-memory-overwrites"></a>Vérification des remplacements de mémoire
Si vous obtenez une violation d’accès sur un appel à une fonction de manipulation de segment de mémoire, il est possible que votre programme a endommagé le tas. Un problème courant de cette situation serait :  
  
```  
Access Violation in _searchseg  
```  
  
 Le [_heapchk](../../c-runtime-library/reference/heapchk.md) fonction est disponible dans les versions debug et les versions release (Windows NT uniquement) pour vérifier l’intégrité du tas de bibliothèque d’exécution. Vous pouvez utiliser `_heapchk` dans la même façon que le `AfxCheckMemory` fonction afin d’isoler le remplacement d’un segment de mémoire, par exemple :  
  
```  
if(_heapchk()!=_HEAPOK)  
   DebugBreak();  
```  
  
 Si cette fonction échoue, vous devez isoler à quel point le tas a été endommagé.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution de problèmes liés à la version Release](../../build/reference/fixing-release-build-problems.md)