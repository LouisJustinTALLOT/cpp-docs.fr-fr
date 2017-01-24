---
title: "&#39;Global&#39; doit &#234;tre suivi par&#160;&#39;.&#39; et par un identificateur | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36000"
  - "vbc36000"
helpviewer_keywords: 
  - "BC36000"
ms.assetid: 0007d7b4-54a2-4f09-904c-d5ad60a55f8e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Global&#39; doit &#234;tre suivi par&#160;&#39;.&#39; et par un identificateur
Le mot clé [Global \- delete](http://msdn.microsoft.com/fr-fr/18c8ba14-40f6-4978-8096-6a5852324635) apparaît dans un contexte autre que l’accès à un espace de noms.  
  
 `Global` a pour but d’autoriser votre code à accéder à un espace de noms racine à partir d’une structure d’espace de noms qui a bloqué cet espace de noms racine.  
  
 **ID d’erreur :** BC36000  
  
### Pour corriger cette erreur  
  
-   Si vous voulez accéder à un espace de noms racine, spécifiez\-le après le mot clé `Global` et un point \(`.`\).  
  
    ```  
    Dim keyInfo As Global.System.ConsoleKeyInfo  
    ```  
  
-   Si vous ne voulez pas accéder à un espace de noms racine, supprimez le mot clé `Global`.  
  
## Voir aussi  
 [Global \- delete](http://msdn.microsoft.com/fr-fr/18c8ba14-40f6-4978-8096-6a5852324635)