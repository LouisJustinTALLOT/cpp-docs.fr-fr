---
description: 'En savoir plus sur : propriétés de l’éditeur de liens Clang (Android C++)'
title: Propriétés de l’éditeur de liens Clang (Android C++)
ms.date: 10/23/2017
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
f1_keywords:
- VC.Project.VCLinkerTool.Clang.OutputFile
- VC.Project.VCLinkerTool.Clang.Soname
- VC.Project.VCLinkerTool.Clang.ShowProgress
- VC.Project.VCLinkerTool.Clang.Version
- VC.Project.VCLinkerTool.Clang.VerboseOutput
- VC.Project.VCLinkerTool.Clang.IncrementalLink
- VC.Project.VCLinkerTool.Clang.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.Clang.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.Clang.UnresolvedReferences
- VC.Project.VCLinkerTool.Clang.OptimizeForMemory
- VC.Project.VCLinkerTool.Clang.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.Clang.ForceSymbolReferences
- VC.Project.VCLinkerTool.Clang.ForceFileOutput
- VC.Project.VCLinkerTool.Clang.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.Clang.GenerateMapFile
- VC.Project.VCLinkerTool.Clang.Relocation
- VC.Project.VCLinkerTool.Clang.FunctionBinding
- VC.Project.VCLinkerTool.Clang.NoExecStackRequired
- VC.Project.VCLinkerTool.Clang.WholeArchive
- VC.Project.VCLinkerTool.Clang.AdditionalOptionsPage
- VC.Project.VCLinkerTool.Clang.AdditionalDependencies
- VC.Project.VCLinkerTool.Clang.LibraryDependencies
ms.openlocfilehash: 65cbfb3d77dad3d78d8b343274d0fa65cf3ed457
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319272"
---
# <a name="clang-linker-properties-android-c"></a>Propriétés de l’éditeur de liens Clang (Android C++)

| Propriété | Description | Choices |
|--|--|--|
| Fichier de sortie | L’option substitue le nom et l’emplacement par défaut du programme créé par l’éditeur de liens. (-o) |
| Afficher la progression | Affiche les messages de progression de l’éditeur de liens. |
| Version | L’option -version indique à l’éditeur de liens de placer un numéro de version dans l’en-tête de l’exécutable. |
| Activer la sortie détaillée | L’option -verbose indique à l’éditeur de liens de générer la sortie des messages détaillés pour le débogage. |
| Activation des liens incrémentiels | L’option indique à l’éditeur de liens d’activer l’édition des liens incrémentielle. |
| Chemin de recherche de la bibliothèque partagée | Permet à l’utilisateur de remplir le chemin de recherche de la bibliothèque partagée. |
| Répertoires de bibliothèques supplémentaires | Permet à l’utilisateur de substituer le chemin de la bibliothèque d’environnement. (-L folder). |
| Signaler les références de symboles non résolus | Cette option s’il est activé signale des références de symboles non résolues. |
| Optimiser pour l’utilisation de la mémoire | Permet d’optimiser l’utilisation de la mémoire, en relisant les tables de symboles selon les besoins. |
| Bibliothèques par défaut spécifiques ignorées | Spécifie un ou plusieurs noms de bibliothèques par défaut à ignorer. |
| Références des symboles forcées | Force l’entrée du symbole dans le fichier de sortie en tant que symbole non défini. |
| Informations de symboles du débogueur | Informations de symboles du débogueur contenues dans le fichier de sortie. | **Inclure tout**<br /><br />**Omettre les symboles superflus pour le traitement du réadressage**<br /><br />**Omettre les informations de symboles du débogueur uniquement**<br /><br />**Omettre toutes les informations de symbole** |
| Empaqueter les informations de symboles du débogueur | Supprimez les informations relatives aux symboles du débogueur avant d’effectuer l’empaquetage.  Une copie du fichier binaire d’origine est utilisée pour le débogage. |
| Nom de fichier de mappage | L’option Map indique à l’éditeur de liens de créer un fichier de mappage avec le nom spécifié par l’utilisateur. |
| Marquer les variables ReadOnly après le réadressage | Cette option marque les variables en lecture seule après le réadressage. |
| Activer la liaison de fonction immédiate | Cette option marque l’objet pour une liaison de fonction immédiate. |
| Nécessiter une pile exécutable | Cette option marque la sortie en indiquant qu’elle ne nécessite pas de pile exécutable. |
| Archive complète | L’archive complète utilise l’ensemble du code des sources et des dépendances supplémentaires. |
| Options supplémentaires | Options supplémentaires. |
| Dépendances supplémentaires | Spécifie les éléments supplémentaires à ajouter à la ligne de commande de l’éditeur de liens. |
| Dépendances de bibliothèque | Cette option permet de spécifier des bibliothèques supplémentaires à ajouter à la ligne de commande de l’éditeur de liens. Les bibliothèques supplémentaires sont ajoutées à la fin de la ligne de commande de l’éditeur de liens démarrer avec *lib* et se terminent par *. a* ou *. so* .  (-lFILE) |
