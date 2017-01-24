---
title: "Une r&#233;f&#233;rence &#224; l’assembly &#39;&lt;nom_assembly&gt;&#39; contenant l’interface impl&#233;ment&#233;e &#39;&lt;nom_interface&gt;&#39; est requise | Microsoft Docs"
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
  - "vbc30009"
  - "bc30009"
helpviewer_keywords: 
  - "BC30009"
ms.assetid: b2dfb89d-7fde-4a8e-ba7f-fe1e59eabaca
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une r&#233;f&#233;rence &#224; l’assembly &#39;&lt;nom_assembly&gt;&#39; contenant l’interface impl&#233;ment&#233;e &#39;&lt;nom_interface&gt;&#39; est requise
Une référence à l’assembly '\<nom\_assembly\>' contenant l’interface implémentée '\<nom\_interface\>' est requise. Ajoutez\-en une à votre projet.  
  
 L’interface est définie dans une bibliothèque de liens dynamiques \(DLL\) ou un assembly qui n’est pas directement référencé dans votre projet. Le compilateur [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] nécessite une référence pour éviter toute ambiguïté au cas où l’interface serait définie dans plusieurs DLL ou assemblys.  
  
 **ID d’erreur :** BC30009  
  
### Pour corriger cette erreur  
  
-   Incluez le nom de la DLL ou de l’assembly non référencé dans vos références de projet.  
  
## Voir aussi  
 [NIB : Référencement d’espaces de noms et de composants](http://msdn.microsoft.com/fr-fr/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Dépannage de références rompues](../Topic/Troubleshooting%20Broken%20References.md)