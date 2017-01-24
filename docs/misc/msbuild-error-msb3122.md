---
title: "MSBuild Error MSB3122 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsApplicationNotFullTrust"
helpviewer_keywords: 
  - "MSB3122"
ms.assetid: 523e4160-f165-437a-9f19-fb2ec77d46f5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3122
**MSB3122 : L'utilisation d'associations de fichiers requiert une confiance totale.**  
  
 Dans le cadre de la publication d'une application qui configure des associations de fichiers, l'application doit être de confiance totale.  
  
### Pour corriger cette erreur  
  
-   Activez les paramètres de sécurité ClickOnce et définissez la confiance totale pour l'application.  Pour plus d'informations, consultez [How to: Enable ClickOnce Security Settings](../Topic/How%20to:%20Enable%20ClickOnce%20Security%20Settings.md).  
  
## Voir aussi  
 [Page Publier, Concepteur de projets](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [ClickOnce Application Manifest](../Topic/ClickOnce%20Application%20Manifest.md)   
 [Sécurité d'accès du code pour les applications ClickOnce](../Topic/Code%20Access%20Security%20for%20ClickOnce%20Applications.md)