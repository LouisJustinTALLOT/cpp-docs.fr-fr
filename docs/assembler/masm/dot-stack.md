---
title: ".STACK | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ".STACK"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".STACK directive"
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .STACK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En cas de utilisation avec [.MODEL](../../assembler/masm/dot-model.md), définit un segment de pile \(avec la PILE de nom de segment\).  `size` facultatif spécifie le nombre d'octets pour la pile \(valeur par défaut 1.024\).  La directive d' `.STACK` ferme automatiquement l'instruction de pile.  
  
## Syntaxe  
  
```  
  
.STACK [[size]]  
```  
  
## Voir aussi  
 [Directives Reference](../../assembler/masm/directives-reference.md)