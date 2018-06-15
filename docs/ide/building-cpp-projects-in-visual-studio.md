---
title: Génération de projets C++ dans Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ projects, building
- projects [C++], building
- builds [C++], about building in Visual Studio
ms.assetid: 9e8bc1a2-bb17-4951-937a-c757ed88d2d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7008e7fe670471301968482fbd4c6c758f0ff5e
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33340500"
---
# <a name="building-c-projects-in-visual-studio"></a>Génération de projets C++ dans Visual Studio
Dans l'environnement de développement intégré (IDE) de Visual Studio, il existe plusieurs façons de générer une solution complète ou un seul projet dans cette solution. Vous pouvez également modifier les paramètres de build et spécifier des étapes de génération personnalisées pour rendre plus efficace votre processus de développement.  
  
 Pour générer une solution qui est ouverte dans Visual Studio et sélectionnée dans **l’Explorateur de solutions**, vous pouvez effectuer les opérations suivantes, au choix :  
  
-   Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
-   Dans **l’Explorateur de solutions**, ouvrez le menu contextuel de la solution, puis choisissez **Générer la solution**.  
  
-   Appuyez sur F7. (Raccourci clavier par défaut vers les paramètres de développement C/C++)  
  
-   Dans la [Fenêtre Commande](/visualstudio/ide/reference/command-window) (dans la barre de menus, choisissez **Affichage**, **Autres fenêtres**, **Fenêtre Commande**), entrez `Build.BuildSolution`.  
  
-   Dans la zone [Lancement rapide](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box), entrez `build build solution`.  
  
 Pour générer un projet qui est sélectionné dans **l’Explorateur de solutions**, vous pouvez effectuer les opérations suivantes, au choix :  
  
-   Dans la barre de menus, choisissez **Générer**, **Générer \<Nom du projet**.  
  
-   Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **Générer**.  
  
-   Dans la Fenêtre Commande (dans la barre de menus, choisissez **Affichage**, **Autres fenêtres**, **Fenêtre Commande**), entrez `Build.BuildOnlyProject`.  
  
-   Dans la zone Lancement rapide, entrez `build project only build only <project name>`.  
  
 Quand vous générez une application Visual C++ dans Visual Studio, vous pouvez modifier un grand nombre de paramètres de la build dans la boîte de dialogue Pages de propriétés du projet. Pour plus d’informations sur la définition des propriétés de projet, consultez [Utilisation des propriétés de projet](../ide/working-with-project-properties.md).  
  
 Pour un exemple d’utilisation de l’IDE afin de créer, générer et déboguer un projet C++, consultez [Procédure pas à pas : explorer l’IDE Visual Studio avec C++](/visualstudio/ide/getting-started-with-cpp-in-visual-studio). Pour un exemple d’utilisation de l’IDE afin de générer un projet C++/CLR, consultez [Procédure pas à pas : compilation d’un programme C++ qui cible le CLR dans Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md). Pour un exemple d’utilisation de l’IDE afin de créer une application Windows Runtime, consultez [Créer votre première application Windows Runtime en C++](http://msdn.microsoft.com/library/windows/apps/hh974580.aspx).  
  
 Pour en savoir plus sur la manière de générer, modifier les paramètres de build et spécifier des étapes de génération personnalisées, reportez-vous aux articles suivants.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Présentation des étapes de génération personnalisée et des événements de build](../ide/understanding-custom-build-steps-and-build-events.md)  
 Décrit comment personnaliser le processus de génération dans l'environnement de développement intégré.  
  
 [Macros courantes pour les propriétés et les commandes de génération](../ide/common-macros-for-build-commands-and-properties.md)  
 Répertorie les macros que vous pouvez utiliser quand les chaînes sont acceptées.  
  
 [Génération de projets externes](../ide/building-external-projects.md)  
 Présente la génération de projets qui utilisent des fonctionnalités à l'extérieur de l'environnement de développement intégré.  
  
 [Fichiers projet](../ide/project-files.md)  
 Présente la structure XML d'un fichier .vcxproj.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Répertoires VC++, Projets, Options (boîte de dialogue)](vcpp-directories-property-page.md)  
 (Projets MSBuild uniquement) Explique comment modifier le chemin de recherche des fichiers exécutables, des fichiers Include, des fichiers de bibliothèque et des fichiers de code source lors d’une génération.  
  
 [Compilation et génération](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 Fournit des informations sur la génération d'applications dans Visual Studio.  
  
 [Génération de programmes C/C++](../build/building-c-cpp-programs.md)  
 Fournit des liens vers des rubriques qui décrivent comment générer votre programme à partir de la ligne de commande ou de l'environnement de développement intégré de Visual Studio.  
  
 [Référence de la génération C/C++](../build/reference/c-cpp-building-reference.md)  
 Fournit des liens vers des présentations de la génération de programmes à l'aide des options C++, du compilateur et de l'éditeur de liens, ainsi qu'avec des outils de génération supplémentaires.  
  
 [Mise à niveau de projets à partir de versions antérieures de Visual C++](../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
 Fournit des liens vers des rubriques traitant des problèmes de mise à niveau de votre projet C++ vers des versions plus récentes de l’ensemble d’outils du compilateur.  
  
[Guide du portage et de la mise à niveau de Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)  
  Informations détaillées sur la mise à niveau d’applications C++ qui ont été créées dans des versions antérieures de Visual Studio et sur la migration des applications qui ont été créées avec des outils autres que Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications de plateforme Windows universelle (C++)](../windows/universal-windows-apps-cpp.md)