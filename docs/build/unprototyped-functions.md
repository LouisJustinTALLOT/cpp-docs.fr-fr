---
title: Fonctions non prototypées | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df159942832479807b2dfe2679e709292ff3f44b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380470"
---
# <a name="unprototyped-functions"></a>Fonctions non prototypées
Pour les fonctions pas entièrement prototypées, l’appelant passe les valeurs entières en tant qu’entiers et les valeurs à virgule flottante double précision. Pour les valeurs à virgule flottante, le Registre entier et le Registre à virgule flottante contiendra la valeur float si l’appelé attend la valeur dans les registres d’entiers.  
  
```  
func1();  
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7  
   func1(2, 1.0, 7);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Convention d’appel](../build/calling-convention.md)