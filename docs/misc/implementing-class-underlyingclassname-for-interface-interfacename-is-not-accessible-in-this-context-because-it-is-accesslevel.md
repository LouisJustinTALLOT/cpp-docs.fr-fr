---
title: "La classe d’impl&#233;mentation &#39;&lt;nom_classe_sous-jacente&gt;&#39; pour l’interface &#39;&lt;nom_interface&gt;&#39; n’est pas accessible dans ce contexte, car elle est &#39;&lt;niveau_acc&#232;s&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BC31109"
  - "vbc31109"
helpviewer_keywords: 
  - "BC31109"
ms.assetid: ab2a3bc3-b875-476f-b601-3e736ad2677e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La classe d’impl&#233;mentation &#39;&lt;nom_classe_sous-jacente&gt;&#39; pour l’interface &#39;&lt;nom_interface&gt;&#39; n’est pas accessible dans ce contexte, car elle est &#39;&lt;niveau_acc&#232;s&gt;&#39;
Une interface est déclarée avec la classe <xref:System.Runtime.InteropServices.CoClassAttribute> spécifiant une classe sous\-jacente, mais cette classe a un niveau d’accès qui empêche le code d’utilisation d’y accéder.  
  
 Le fait d’appliquer la classe <xref:System.Runtime.InteropServices.CoClassAttribute> à une interface a pour effet d’associer une classe sous\-jacente à l’interface. Cela permet au code de créer un objet directement à partir de l’interface en utilisant une clause `New`.  
  
 Si le code utilisant la clause `New` n’a pas accès à la classe sous\-jacente, par exemple si la classe est `Private`, le compilateur génère cette erreur.  
  
 **ID d’erreur :** BC31109  
  
### Pour corriger cette erreur  
  
1.  Si vous avez le contrôle de code source par rapport à la classe sous\-jacente, ajustez son niveau d’accès de sorte que le code d’utilisation puisse y accéder.  
  
2.  Si pour une raison quelconque, vous ne pouvez pas modifier le niveau d’accès de la classe sous\-jacente, supprimez la clause `New`. Vous ne pouvez pas créer un objet directement à partir de cette interface.  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.CoClassAttribute>   
 [New Operator](../Topic/New%20Operator%20\(Visual%20Basic\).md)   
 [Access Levels in Visual Basic](../Topic/Access%20Levels%20in%20Visual%20Basic.md)