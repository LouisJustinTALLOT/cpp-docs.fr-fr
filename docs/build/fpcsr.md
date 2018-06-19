---
title: MxFpCsrCsr | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9defb41a026b32acb4375185f14c903788b91a23
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367444"
---
# <a name="fpcsr"></a>FpCsr
L’état du Registre inclut également le x87 mot de commande FPU. La convention d’appel définit ce Registre comme non volatil.  
  
 Le x87 Registre du mot de contrôle FPU est défini pour les valeurs standard suivantes au début de l’exécution du programme :  
  
```  
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)  
FPCSR[7]: Reserved - 0  
FPCSR[8:9]: Precision Control - 10B (double precision)  
FPCSR[10:11]: Rounding  control - 0 (round to nearest)  
FPCSR[12]: Infinity control - 0 (not used)  
```  
  
 Un appelant qui modifie l’un des champs dans FPCSR doit restaurer avant de retourner à son appelant. En outre, un appelant qui a modifié l’un de ces champs doive restaurer leurs valeurs standard avant d’appeler un appelant, sauf si le contrat de l’appelé attend les valeurs modifiées.  
  
 Il existe deux exceptions aux règles relatives à la volatilité-non des indicateurs de contrôle :  
  
1.  Dans les fonctions où documentée de la fonction donnée vise à modifier le MxFpCsrCsr non volatils indicateurs.  
  
2.  Lorsqu’il est prouvée corriger que les résultats de la violation de ces règles dans un programme qui se comporte ou a la même en tant que programme où ces règles ne sont pas violées, par exemple, via l’analyse de la totalité du programme.  
  
## <a name="see-also"></a>Voir aussi  
 [Convention d’appel](../build/calling-convention.md)