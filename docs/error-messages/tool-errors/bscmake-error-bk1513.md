---
title: "Erreur BSCMAKE BK1513 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK1513"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1513"
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Erreur BSCMAKE BK1513
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

une mise à jour non incrémentielle nécessite tous les fichiers .SBR  
  
 BSCMAKE ne peut pas générer un nouveau fichier d'informations de consultation \(.bsc\), car un ou plusieurs fichiers .sbr sont tronqués.  Pour rechercher les noms des fichiers .sbr tronqués, lisez les avertissements [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) qui accompagnent cette erreur.  
  
 BSCMAKE peut mettre à jour un fichier .bsc avec un fichier .sbr tronqué, mais ne peut pas en générer un nouveau.  BSCMAKE peut générer un nouveau fichier .bsc dans les cas suivants :  
  
-   Fichier .bsc manquant.  
  
-   Nom de fichier incorrect spécifié pour un fichier .bsc.  
  
-   Fichier .bsc endommagé.  
  
 Pour résoudre ce problème, supprimez les fichiers .sbr tronqués et procédez à une régénération, ou nettoyez la solution et procédez à une régénération.  \(Dans l'IDE, choisissez **Générer**, **Nettoyer la solution**, puis choisissez **Générer**, **Régénérer la solution**.\)