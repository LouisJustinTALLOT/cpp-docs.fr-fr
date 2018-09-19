---
title: Configuration Release du nouveau projet à partir de code existant | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.releasesettings
dev_langs:
- C++
ms.assetid: 3e2fc73c-bdbd-4790-b2bd-d31731f0cece
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c4e7d5fb707c455aa7b7fb9f0e14dff95ee5633f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703356"
---
# <a name="specify-release-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>Spécifier les paramètres de configuration Release, Assistant Créer un projet à partir de fichiers de code existants
Utilisez cette page de l’Assistant Créer un projet à partir de fichiers de code existants pour spécifier les paramètres de projet de la configuration Release.  
  
## <a name="task-list"></a>Liste des tâches  
 [Guide pratique pour créer un projet C++ à partir d’un code existant](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
- **Identique à la configuration Debug**

   Spécifie que l’Assistant génère des paramètres de projet de configuration Release identiques à ceux de la configuration Debug. Cette option est cochée par défaut. Toutes les autres options de cette page sont inactives, sauf si vous décochez cette case.  
  
- **Ligne de commande Build**

   Spécifie la ligne de commande qui génère le nouveau projet. Entrez le nom du compilateur ainsi que les commutateurs ou les arguments à utiliser pour générer le nouveau projet. Cette option est activée quand l’option **Utiliser un système de génération externe** est sélectionnée dans la page **Spécifier les paramètres de projet**.  
  
- **Ligne de commande Rebuild**

   Spécifie la ligne de commande qui regénère le nouveau projet. Cette option est activée quand l’option **Utiliser un système de génération externe** est sélectionnée dans la page **Spécifier les paramètres de projet**.  
  
- **Ligne de commande Clean**

   Spécifie la ligne de commande qui supprime les fichiers de support générés par les outils de génération pour le nouveau projet. Cette option est activée quand l’option **Utiliser un système de génération externe** est sélectionnée dans la page **Spécifier les paramètres de projet**.  
  
- **Sortie (pour le débogage)**

   Spécifie le chemin du répertoire des fichiers de sortie pour la configuration Debug du nouveau projet. Cette option est activée quand l’option **Utiliser un système de génération externe** est sélectionnée dans la page **Spécifier les paramètres de projet**.  
  
- **Définitions de préprocesseur (/D)**

   Définit les symboles de préprocesseur pour le nouveau projet. Pour plus d'informations, consultez [/D (Preprocessor Definitions)](../build/reference/d-preprocessor-definitions.md).  
  
- **Chemin de recherche Include (/I)**

   Spécifie les chemins à ajouter à la liste de répertoires consultée par le compilateur pour résoudre les références de fichier passées aux directives de préprocesseur dans le nouveau projet. Pour plus d’informations, consultez l’article [/I (Autres répertoires Include)](../build/reference/i-additional-include-directories.md).  
  
- **Fichiers Include forcés (/FI)**

   Spécifie les fichiers d’en-tête à traiter pendant la génération du nouveau projet. Pour plus d’informations, consultez l’article [/FI (Nom du fichier Include imposé)](../build/reference/fi-name-forced-include-file.md).  
  
- **Chemins de recherche des assemblys .NET (/AI)**

   Spécifie les chemins de répertoire consultés par le compilateur pour résoudre les références d’assembly .NET passées aux directives de préprocesseur dans le nouveau projet. Pour plus d’informations, consultez l’article [/AI (Spécifier les répertoires des métadonnées)](../build/reference/ai-specify-metadata-directories.md).  
  
- **Utilisation forcée des assemblys .NET (/FU)**

   Spécifie les assemblys .NET à traiter pendant la génération du nouveau projet. Pour plus d’informations, consultez l’article [/FU (Nom du fichier #using imposé)](../build/reference/fu-name-forced-hash-using-file.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier les paramètres du projet, Assistant Créer un projet à partir de fichiers de code existants](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)