---
title: "Probl&#232;me possible d&#233;tect&#233; pendant la g&#233;n&#233;ration de l’assembly &#39;&lt;nom_assembly&gt;&#39;&#160;: &lt;erreur&gt; | Microsoft Docs"
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
  - "vbc40010"
  - "bc40010"
helpviewer_keywords: 
  - "BC40010"
ms.assetid: 3a4f4a4a-a5ad-4501-bf4c-0fbf25c50734
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Probl&#232;me possible d&#233;tect&#233; pendant la g&#233;n&#233;ration de l’assembly &#39;&lt;nom_assembly&gt;&#39;&#160;: &lt;erreur&gt;
L’outil ALink, appelé par le compilateur [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)], signale une erreur lors de la génération de l’assembly. Les causes possibles sont les suivantes :  
  
-   Un assembly signé fait référence à un assembly non signé. Dans ce cas, vous devez déterminer si l’assembly référencé répond à vos critères de sécurité.  
  
-   Une application 64 bits est créée sur une plateforme 32 bits. Dans ce cas, vous devez vous assurer que les versions 64 bits de tous les assemblys référencés sont installées sur la plateforme cible. Ceci est géré automatiquement pour les assemblys CLR, même si le message d’erreur est généré.  
  
 Ce message est un avertissement. Le compilateur continue de générer l’assembly. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **ID d’erreur :** BC40010  
  
### Pour corriger cette erreur  
  
1.  Examinez le message d’erreur et prenez les mesures nécessaires.  
  
2.  Recompilez le programme pour voir si l'erreur se produit à nouveau.  
  
3.  Si l'erreur se produit à nouveau, réinstallez le compilateur [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)].  
  
4.  Si l’erreur persiste après la réinstallation, rassemblez des informations sur le contexte dans lequel est survenue l’erreur, puis avertissez les services de support technique Microsoft.  
  
## Voir aussi  
 [PAVEOVER Support technique et accessibilité](http://msdn.microsoft.com/fr-fr/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)   
 [Common Language Runtime Overview](http://msdn.microsoft.com/fr-fr/0fd9aeae-af10-435f-86d4-e76619741e4a)