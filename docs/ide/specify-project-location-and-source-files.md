---
title: Nouveau projet à partir du code existant, fichiers sources (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.importwiz.location
dev_langs:
- C++
ms.assetid: 29ddffb9-5918-4d72-8c7a-a365f9de96dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3647ad3211043a5356649cb5f350ec07009f2279
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707835"
---
# <a name="specify-project-location-and-source-files-create-new-project-from-existing-code-files-wizard"></a>Spécifier l'emplacement du projet et les fichiers sources, Assistant Créer un projet à partir de fichiers de code existants
Utilisez cette page de l’Assistant Créer un projet à partir de fichiers de code existants pour spécifier :  
  
-   le chemin du répertoire du nouveau projet  
  
-   les répertoires dans lesquels rechercher les fichiers sources existants  
  
-   les types de fichiers que l’Assistant importera dans le nouveau projet  
  
## <a name="task-list"></a>Liste des tâches  
[Guide pratique pour créer un projet C++ à partir d’un code existant](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
- **Emplacement du fichier projet**

   Spécifie le chemin du répertoire du nouveau projet. Cet emplacement correspond à l’endroit où l’Assistant déposera tous les fichiers (et les sous-répertoires) du nouveau projet.  
  
- **Parcourir**

   Affiche la boîte de dialogue **Emplacement du fichier projet** dans laquelle vous spécifiez le répertoire qui contiendra le nouveau projet. Ce contrôle vous permet de naviguer vers le dossier de votre choix.  
  
- **Nom du projet**

   Spécifie le nom du nouveau projet. Les fichiers projet qui ont des extensions de fichier comme .vcxproj adopteront ce nom. Les fichiers de code existants garderont leur nom d’origine.  
  
- **Ajouter les fichiers au projet à partir de ces dossiers**

   Quand cette option est activée, l’Assistant copie les fichiers de code existants depuis leur répertoire d’origine (qui est spécifié dans la zone de liste sous ce contrôle) dans le nouveau projet.  
  
- **Ajouter les sous-dossiers**

   Spécifie de copier les fichiers de code à partir de tous les sous-répertoires du répertoire figurant dans la colonne **Dossier** dans le nouveau projet.  
  
- **Dossier**

   Indique le chemin du répertoire qui contient les fichiers de code existants à copier dans le nouveau projet. Cette colonne répertorie tous les répertoires dans lesquels l’Assistant recherchera les fichiers de code existants.  
  
- **Ajouter**

   Affiche la boîte de dialogue **Ajouter les fichiers au projet à partir de ce dossier**, dans laquelle vous pouvez spécifier les répertoires dans lesquels l’Assistant recherchera les fichiers de code existants.  
  
- **Supprimer**

   Supprime le chemin du répertoire qui est sélectionné dans la zone de liste à gauche de ce contrôle.  
  
- **Types de fichiers à ajouter au projet**

   Spécifie les types de fichiers que l’Assistant ajoutera au nouveau projet en fonction des extensions de fichier données. Les extensions de fichier sont précédées du caractère générique astérisque, et sont délimitées dans la liste d’extensions de fichier par un point-virgule.  
  
- **Afficher tous les fichiers dans l’Explorateur de solutions**

   Indique que tous les fichiers du nouveau projet doivent être visibles et affichés dans la fenêtre Explorateur de solutions. Cette option est activée par défaut.