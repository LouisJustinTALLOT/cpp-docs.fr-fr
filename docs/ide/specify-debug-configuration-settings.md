---
title: Nouveau projet à partir du code existant, paramètre Debug (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.debugsettings
dev_langs:
- C++
ms.assetid: 607339a8-9d33-458b-8095-dc73f374e29d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4139b5bf994a2034ad243fb3351c44847f3a85bf
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709635"
---
# <a name="specify-debug-configuration-settings-create-new-project-from-existing-code-files-wizard"></a>Spécifier les paramètres de configuration Debug, Assistant Créer un projet à partir de fichiers de code existants
Utilisez cette page de l’Assistant Créer un projet à partir de fichiers de code existants pour spécifier les paramètres de projet de la configuration Debug.  
  
## <a name="task-list"></a>Liste des tâches  
[Guide pratique pour créer un projet C++ à partir d’un code existant](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
- **Ligne de commande Build**

   Spécifie la ligne de commande qui génère le nouveau projet. Par exemple, entrez le nom du compilateur (ainsi que les commutateurs et les arguments) ou les scripts de génération à utiliser pour générer le nouveau projet. Cette option est activée quand l’option **Utiliser un système de génération externe** est sélectionnée dans la page **Spécifier les paramètres de projet** ; sinon, elle n’est pas disponible.  
  
- **Ligne de commande Rebuild**

   Spécifie la ligne de commande qui regénère le nouveau projet. Cette option est activée quand l’option **Utiliser un système de génération externe** est sélectionnée dans la page **Spécifier les paramètres de projet** ; sinon, elle n’est pas disponible.  
  
- **Ligne de commande Clean**

   Spécifie la ligne de commande qui permet de supprimer les fichiers de prise en charge générés par les outils de génération pour le nouveau projet. Cette option est activée quand l’option **Utiliser un système de génération externe** est sélectionnée dans la page **Spécifier les paramètres de projet** ; sinon, elle n’est pas disponible.  
  
- **Sortie (pour le débogage)**

   Spécifie le chemin du répertoire des fichiers de sortie pour la configuration Debug du nouveau projet. Cette option est activée quand l’option **Utiliser un système de génération externe** est sélectionnée dans la page **Spécifier les paramètres de projet** ; sinon, elle n’est pas disponible.  
  
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
