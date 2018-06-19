---
title: Avertissement (niveau 1) du compilateur C4103 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4103
dev_langs:
- C++
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f072db4a260d2c83d1dd4b373630cd6e585efc2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284730"
---
# <a name="compiler-warning-level-1-c4103"></a>Avertissement (niveau 1) du compilateur C4103
'NomFichier' : alignement modifié après l’en-tête, peut être due à l’absence de #pragma Pack (pop) système  
  
 La compression affecte la disposition des classes, et en règle générale, si la modification de la compression sur les fichiers d’en-tête, il peut y avoir des problèmes.  
  
 Utilisez #pragma [pack](../../preprocessor/pack.md)(pop) avant de quitter le fichier d’en-tête pour résoudre cet avertissement.  
  
 L’exemple suivant génère l’erreur C4103 :  
  
```  
// C4103.h  
#pragma pack(push, 4)  
  
// defintions and declarations  
  
// uncomment the following line to resolve  
// #pragma pack(pop)  
```  
  
 Puis,  
  
```  
// C4103.cpp  
// compile with: /LD /W1  
#include "c4103.h"   // C4103  
```