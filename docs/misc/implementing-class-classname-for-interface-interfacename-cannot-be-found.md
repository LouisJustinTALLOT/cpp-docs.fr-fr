---
title: "La classe d’impl&#233;mentation &#39;&lt;nom_classe&gt;&#39; pour l’interface &#39;&lt;nom_interface&gt;&#39; est introuvable | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31094"
  - "bc31094"
helpviewer_keywords: 
  - "BC31094"
ms.assetid: 262cb67e-2930-4a4a-a63e-bb2e201b3b93
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La classe d’impl&#233;mentation &#39;&lt;nom_classe&gt;&#39; pour l’interface &#39;&lt;nom_interface&gt;&#39; est introuvable
Une classe d’implémentation de l’assembly d’interopérabilité n’est pas disponible.  
  
 **ID d’erreur :** BC31094  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que la bibliothèque de types pour l’objet COM est valide.  
  
2.  Utilisez l’importateur de bibliothèques de types \(Tlbimp.exe\) pour créer manuellement un assembly d’interopérabilité, puis ajoutez à ce dernier une référence à partir de votre projet.  
  
## Voir aussi  
 [Implements Statement](../Topic/Implements%20Statement.md)   
 [COM Interop](../Topic/COM%20Interop%20\(Visual%20Basic\).md)   
 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)