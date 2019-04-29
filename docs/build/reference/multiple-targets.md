---
title: Cibles multiples
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, targets
- multiple targets in NMAKE
- targets, multiple in NMAKE
- NMAKE program, targets
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
ms.openlocfilehash: 43e5216d5e11e89aff9b6f0c69ff4e76a8cc9da8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320966"
---
# <a name="multiple-targets"></a>Cibles multiples

NMAKE évalue plusieurs cibles dans une seule dépendance comme si chacune était spécifiée dans un bloc de description distinct.

Par exemple, ceci...

```Output
bounce.exe leap.exe : jump.obj
   echo Building...
```

.. .est évalué comme ceci :

```Output
bounce.exe : jump.obj
   echo Building...
leap.exe : jump.obj
   echo Building...
```

## <a name="see-also"></a>Voir aussi

[Cibles](targets.md)
