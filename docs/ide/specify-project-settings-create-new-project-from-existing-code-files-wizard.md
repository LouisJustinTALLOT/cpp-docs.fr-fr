---
title: Spécifier les paramètres du projet, Assistant Créer un projet à partir de fichiers de code existants | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.appsettings
dev_langs:
- C++
helpviewer_keywords:
- Create New Project From Existing Code Files Wizard, project settings
ms.assetid: 9b8860c9-d35f-4f18-9565-2934d3d7f569
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0f59b802b5a24c1b449f78cccee4744538a5a0e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338944"
---
# <a name="specify-project-settings-create-new-project-from-existing-code-files-wizard"></a>Spécifier les paramètres du projet, Assistant Créer un projet à partir de fichiers de code existants
Utilisez cette page de l’Assistant Créer un projet à partir de fichiers de code existants pour spécifier :  
  
-   L’environnement de génération du nouveau projet  
  
-   Les paramètres de génération correspondant à un type spécifique de nouveau projet à générer  
  
## <a name="task-list"></a>Liste des tâches  
 [Guide pratique pour créer un projet C++ à partir d’un code existant](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Utiliser Visual Studio**  
 Spécifie l’utilisation des outils de génération inclus dans Visual Studio pour générer le nouveau projet. Cette option est activée par défaut.  
  
 **Type de projet**  
 Spécifie le type de projet que l’Assistant va générer.  
  
 **Projet d’application Windows**  
 Indique que l’Assistant génère un projet pour une application Windows exécutable. Cette option est disponible dans la zone de liste déroulante **Type de projet**.  
  
 **Projet d’application console**  
 Indique que l’Assistant génère un projet pour une application console. Cette option est disponible dans la zone de liste déroulante **Type de projet**.  
  
 **Projet de bibliothèque de liens dynamiques (DLL)**  
 Indique que l’Assistant génère un projet pour une application de bibliothèque de liens dynamiques vide. Cette option est disponible dans la zone de liste déroulante **Type de projet**.  
  
 **Projet de bibliothèque statique (LIB)**  
 Indique que l’Assistant génère un projet pour une application de bibliothèque statique. Cette option est disponible dans la zone de liste déroulante **Type de projet**.  
  
 **Ajouter la prise en charge pour ATL**  
 Ajoute la prise en charge ATL au nouveau projet.  
  
 **Ajouter la prise en charge pour MFC**  
 Ajoute la prise en charge MFC au nouveau projet.  
  
 **Ajouter la prise en charge pour le Common Language Runtime**  
 Ajoute la prise en charge de la programmation CLR au nouveau projet.  
  
 **Common Language Runtime**  
 Spécifie que le nouveau projet doit être conforme aux fonctionnalités CLR.  
  
 **Common Language Runtime (ancienne syntaxe)**  
 Spécifie que le nouveau projet doit être compatible avec la syntaxe des extensions managées pour C++, qui est la syntaxe de programmation CLR précédant Visual C++ 2005.  
  
 **Utiliser un système de génération externe**  
 Spécifie l’utilisation d’outils de génération non inclus dans Visual Studio pour générer le nouveau projet. Quand cette option est sélectionnée, vous pouvez spécifier des lignes de commande de génération dans les pages **Spécifier les paramètres de configuration Debug** et **Spécifier les paramètres de configuration Release**.  
  
> [!NOTE]
>  Quand l’option **Utiliser un système de génération externe** est activée, l’IDE ne génère pas le nouveau projet et les options /D, /I, /Fi, /AI ou /FU ne sont pas nécessaires pour la compilation. Toutefois, ces options doivent être définies correctement pour qu’IntelliSense fonctionne correctement.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier les paramètres de configuration Debug, Assistant Créer un projet à partir de fichiers de code existants](../ide/specify-debug-configuration-settings.md)   
 [Spécifier les paramètres de configuration Release, Assistant Créer un projet à partir de fichiers de code existants](../ide/specify-release-configuration.md)