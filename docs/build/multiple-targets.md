---
title: Plusieurs cibles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- makefiles, targets
- multiple targets in NMAKE
- targets, multiple in NMAKE
- NMAKE program, targets
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66849bdbe28ac2bd965714de56f962df98ced133
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703662"
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

[Targets (Cibles MSBuild)](../build/targets.md)