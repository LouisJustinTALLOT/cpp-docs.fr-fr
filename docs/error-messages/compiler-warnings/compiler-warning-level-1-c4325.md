---
title: Compilateur avertissement (niveau 1) C4325 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4325
dev_langs:
- C++
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 936433987f823ae7d5d22cfd075f188dd5d4b1e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277642"
---
# <a name="compiler-warning-level-1-c4325"></a>Avertissement du compilateur (niveau 1) C4325
**attributs pour la section '**   
 ***section* ' ignoré**  
  
 Vous ne pouvez pas modifier les attributs d’une section standard. Par exemple :  
  
```  
#pragma section(".sdata", long)  
```  
  
 Ceci remplacerait le `.sdata` section standard qui utilise le **court** type de données avec le **long** type de données.  
  
 Sections standards dont vous ne pouvez pas modifier les attributs incluent,  
  
-   .Data  
  
-   .sdata  
  
-   .BSS  
  
-   .sbss  
  
-   .Text  
  
-   .const  
  
-   .sconst  
  
-   .rdata  
  
-   .srdata  
  
 Des sections supplémentaires peuvent être ajoutées plus tard.  
  
## <a name="see-also"></a>Voir aussi  
 [section](../../preprocessor/section.md)