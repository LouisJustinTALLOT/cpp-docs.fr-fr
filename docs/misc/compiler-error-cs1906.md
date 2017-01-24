---
title: "Erreur du compilateur CS1906 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1906"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1906"
ms.assetid: 1a6abf5c-f673-4256-93ac-313dce50acc0
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1906
Option 'option' non valide ; la visibilité de la ressource doit être 'public' ou 'private'  
  
 Cette erreur indique une option de ligne de commande [\/resource \(incorporer un fichier de ressources au fichier de sortie\)](../Topic/-resource%20\(C%23%20Compiler%20Options\).md) ou [\/linkresource \(créer un lien vers une ressource .NET Framework\)](../Topic/-linkresource%20\(C%23%20Compiler%20Options\).md) non valide. Vérifiez la syntaxe de l’option de ligne de commande **\/resource** ou **\/linkresource** et assurez\-vous que le modificateur d’accessibilité utilisé est soit **public**, soit `private`.