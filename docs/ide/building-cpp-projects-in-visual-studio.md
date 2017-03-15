---
title: "G&#233;n&#233;ration de projets C++ dans Visual&#160;Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "générations (C++), à propos de la génération dans Visual Studio"
  - "projets (C++), générer"
  - "projets Visual C++, générer"
ms.assetid: 9e8bc1a2-bb17-4951-937a-c757ed88d2d1
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# G&#233;n&#233;ration de projets C++ dans Visual&#160;Studio
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Dans l'environnement de développement intégré \(IDE\) de Visual Studio, il existe plusieurs façons de générer une solution complète ou un seul projet dans cette solution.  Vous pouvez également modifier les paramètres de build et spécifier des étapes de génération personnalisées pour rendre plus efficace votre processus de développement.  
  
 Pour générer une solution ouverte dans [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] et sélectionnée dans l'**Explorateur de solutions**, vous pouvez effectuer les opérations suivantes au choix :  
  
-   Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
-   Dans l'**Explorateur de solutions**, ouvrez le menu contextuel de la solution, puis choisissez **Générer la solution**.  
  
-   Appuyez sur F7.  \(Raccourci clavier par défaut vers les paramètres de développement C\/C\+\+\)  
  
-   Dans la [Fenêtre Commande](../Topic/Command%20Window.md) \(dans la barre de menus, choisissez **Affichage**, **Autres fenêtres**, **Fenêtre Commande**\), entrez `Build.BuildSolution`.  
  
-   Dans la zone [Lancement rapide](../Topic/Quick%20Launch,%20Environment,%20Options%20Dialog%20Box.md), entrez `build build solution`.  
  
 Pour générer un projet qui est sélectionné dans l'**Explorateur de solutions**, vous pouvez effectuer l'une des opérations suivantes, au choix :  
  
-   Dans la barre de menus, choisissez **Générer**, **Générer \<Nom du projet\>**.  
  
-   Dans l'**Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **Générer**.  
  
-   Dans la fenêtre Commande \(dans la barre de menus, choisissez **Affichage**, **Autres fenêtres**, **Fenêtre Commande**\), entrez `Build.BuildOnlyProject`.  
  
-   Dans la zone de lancement rapide, entrez `build project only build only <nom du projet>`.  
  
 Quand vous générez une application Visual C\+\+ dans Visual Studio, vous pouvez modifier un grand nombre de paramètres de la build dans la boîte de dialogue Pages de propriétés du projet.  Pour obtenir des informations sur la façon de définir les propriétés du projet, consultez [Utilisation des propriétés de projet](../ide/working-with-project-properties.md).  
  
 Pour consulter un exemple illustrant l'utilisation de l'environnement IDE pour créer, générer et déboguer un projet C\+\+, reportez\-vous à [Procédure pas à pas : explorer l'environnement IDE de Visual Studio avec C\+\+](../Topic/Getting%20Started%20with%20C++%20in%20Visual%20Studio.md).  Pour consulter un exemple illustrant l'utilisation de l'environnement IDE pour générer un projet C\+\+\/CLR, voir [Procédure pas à pas : compilation d'un programme C\+\+ qui cible le CLR dans Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md).  Pour consulter un exemple illustrant l'utilisation de l'environnement IDE pour créer une application Windows Runtime, voir [Créer votre première application Windows Runtime en C\+\+](http://msdn.microsoft.com/library/windows/apps/hh974580.aspx).  
  
 Pour en savoir plus sur la manière de générer, modifier les paramètres de build et spécifier des étapes de génération personnalisées, reportez\-vous aux articles suivants.  
  
## Dans cette section  
 [Présentation des étapes de génération personnalisée et des événements de build](../ide/understanding-custom-build-steps-and-build-events.md)  
 Décrit comment personnaliser le processus de génération dans l'environnement de développement intégré.  
  
 [Macros pour les propriétés et les commandes de génération](../ide/common-macros-for-build-commands-and-properties.md)  
 Répertorie les macros que vous pouvez utiliser quand les chaînes sont acceptées.  
  
 [Génération de projets externes](../ide/building-external-projects.md)  
 Présente la génération de projets qui utilisent des fonctionnalités à l'extérieur de l'environnement de développement intégré.  
  
 [Fichiers projet](../ide/project-files.md)  
 Présente la structure XML d'un fichier .vcxproj.  
  
## Rubriques connexes  
 [VC\+\+ Directories, Projects, Options Dialog Box](http://msdn.microsoft.com/fr-fr/e027448b-c811-4c3d-8531-4325ad3f6e02)  
 Explique comment modifier le chemin de recherche des fichiers exécutables, des fichiers Include, des fichiers de bibliothèque et des fichiers de code source pendant une génération.  
  
 [Génération d'applications dans Visual Studio](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)  
 Fournit des informations sur la génération d'applications dans Visual Studio.  
  
 [Génération de programmes C\/C\+\+](../build/building-c-cpp-programs.md)  
 Fournit des liens vers des rubriques qui décrivent comment générer votre programme à partir de la ligne de commande ou de l'environnement de développement intégré de Visual Studio.  
  
 [Référence à la génération C\/C\+\+](../build/reference/c-cpp-building-reference.md)  
 Fournit des liens vers des présentations de la génération de programmes à l'aide des options C\+\+, du compilateur et de l'éditeur de liens, ainsi qu'avec des outils de génération supplémentaires.  
  
 [Mise à niveau de projets à partir de versions antérieures de Visual C\+\+](../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
 Fournit des liens vers des rubriques traitant des problèmes relatifs à la mise à niveau de Visual C\+\+ 6.0 et de projets ultérieurs vers Visual C\+\+ .NET.  
  
 [Porting and Upgrading Programs](http://msdn.microsoft.com/fr-fr/c36c44b3-5a9b-4bb4-9b7a-469aa770ed00)  
 Fournit des détails sur le déplacement d'applications et présente les makefiles.  
  
## Voir aussi  
 [Roadmap for Windows Store apps using C\+\+](http://msdn.microsoft.com/fr-fr/0b71e4a4-5d8a-4a20-b2ec-e40062675ec1)