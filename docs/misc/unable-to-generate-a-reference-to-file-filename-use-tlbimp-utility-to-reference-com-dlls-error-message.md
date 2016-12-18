---
title: "Impossible de g&#233;n&#233;rer une r&#233;f&#233;rence au fichier &#39;&lt;nom_fichier&gt;&#39; (utilisez l’utilitaire TLBIMP pour faire r&#233;f&#233;rence aux DLL COM)&#160;: &lt;message d’erreur&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30142"
  - "bc30142"
helpviewer_keywords: 
  - "BC30142"
ms.assetid: ee0f2c77-3714-4ec2-bddf-d098ab77722f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de g&#233;n&#233;rer une r&#233;f&#233;rence au fichier &#39;&lt;nom_fichier&gt;&#39; (utilisez l’utilitaire TLBIMP pour faire r&#233;f&#233;rence aux DLL COM)&#160;: &lt;message d’erreur&gt;
Le compilateur [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] appelle Assembly Linker \(Al.exe, également appelé Alink\) pour générer un assembly avec un manifeste. L’éditeur de liens a signalé une erreur lors de la recherche ou de la validation d’un fichier DLL COM\+.  
  
 **ID d’erreur :** BC30142  
  
### Pour corriger cette erreur  
  
1.  Examinez le message d’erreur entre guillemets et consultez la rubrique [Erreurs et avertissements de l’outil Al.exe](http://msdn.microsoft.com/fr-fr/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) pour obtenir davantage d’explications et de conseils.  
  
2.  Si la référence souhaitée porte sur une DLL COM au lieu d’une DLL COM\+, utilisez l’outil [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) pour générer la référence.  
  
3.  Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.  
  
## Voir aussi  
 [Al.exe \(Assembly Linker\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)   
 [Erreurs et avertissements de l’outil Al.exe](http://msdn.microsoft.com/fr-fr/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)   
 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)   
 [PAVEOVER Support technique et accessibilité](http://msdn.microsoft.com/fr-fr/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)