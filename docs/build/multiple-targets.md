---
title: Cibles multiples
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, targets
- multiple targets in NMAKE
- targets, multiple in NMAKE
- NMAKE program, targets
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
ms.openlocfilehash: 28ac69a6e724b4e7c6fe838e0de3703cbdf0cfaa
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421427"
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

[Cibles](../build/targets.md)
