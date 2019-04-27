---
title: 'Procédure : créer un projet C++ à partir de code existant'
ms.date: 01/15/2019
helpviewer_keywords:
- C++, creating projects from existing code
- Create New Project From Existing Code Files Wizard, project settings
f1_keywords:
- vc.appwiz.importwiz.location
- vc.appwiz.importwiz.appsettings
- vc.appwiz.importwiz.debugsettings
- vc.appwiz.importwiz.releasesettings
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
ms.openlocfilehash: 1658e19595d8cfc7966ca881abfdd2aa8acf76ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62189026"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>Procédure : créer un projet C++ à partir de code existant

Dans Visual Studio, vous pouvez déplacer vos fichiers de code existants dans un projet C++ à l’aide de l’Assistant **Créer un projet à partir de fichiers de code existants**. Cet Assistant crée une solution de projet qui utilise le système MSBuild pour gérer les fichiers sources et la configuration de build. Il est optimisé pour les projets relativement simples qui n’ont pas de hiérarchies de dossiers complexes. L’Assistant n’est pas disponible dans les anciennes éditions Express de Visual Studio. 

Le déplacement de vos fichiers de code existants dans un projet C++ permet d’utiliser les fonctionnalités de gestion de projets MSBuild natives intégrées à l’IDE. Si vous préférez utiliser votre système de génération existant, comme des makefiles nmake, CMake ou des alternatives, vous pouvez utiliser l’option Ouvrir un dossier ou CMake à la place. Pour plus d’informations, consultez [Open Folder projects pour C++](open-folder-projects-cpp.md) ou [projets CMake dans Visual Studio](cmake-projects-in-visual-studio.md). Les deux options vous permettent d’utiliser les fonctionnalités de l’IDE comme [IntelliSense](/visualstudio/ide/using-intellisense) et [Propriétés du projet](working-with-project-properties.md).

### <a name="to-create-a-c-project-from-existing-code"></a>Pour créer un projet C++ à partir de code existant

1. Dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet à partir de code existant**.

1. Dans la première page de l’Assistant **Créer un projet à partir de fichiers de code existants**, sélectionnez **Visual C++** dans la liste **Quel type de projet souhaitez-vous créer ?**. Choisissez **Suivant** pour continuer.

1. Spécifiez l’emplacement de votre projet, le répertoire de vos fichiers sources et les types de fichiers importés par l’Assistant dans le nouveau projet. Choisissez **Suivant** pour continuer.

    | Paramètre | Description |
    | --- | --- |
    | **Emplacement du fichier projet** | Spécifie le chemin du répertoire du nouveau projet. Cet emplacement correspond à l’endroit où l’Assistant dépose tous les fichiers (et les sous-répertoires) du nouveau projet.<br/><br/>Sélectionnez **Parcourir** pour afficher la boîte de dialogue **Emplacement du fichier projet**. Accédez au dossier approprié et spécifiez le répertoire qui contient le nouveau projet. |
    | **Nom du projet** | Spécifie le nom du nouveau projet. Les fichiers projets, qui ont des extensions de fichier telles que .vcxproj, adoptent ce nom. Quant aux fichiers de code existants, ils conservent leur nom d’origine. |
    | **Ajouter les fichiers au projet à partir de ces dossiers** | Cochez cette option pour que l’Assistant copie les fichiers de code existants à partir de leur répertoire d’origine (qui est spécifié dans la zone de liste sous ce contrôle) dans le nouveau projet.<br/><br/>Cochez **Ajouter des sous-dossiers** pour spécifier de copier les fichiers de code à partir de tous les sous-répertoires dans le projet. Les répertoires sont listés dans la colonne **Dossier**.<br/>- Sélectionnez **Ajouter** pour afficher la boîte de dialogue **Ajouter les fichiers au projet à partir de ce dossier**, dans laquelle vous pouvez spécifier les répertoires dans lesquels l’Assistant recherche les fichiers de code existants.<br/>-Sélectionnez **Supprimer** pour supprimer le chemin du répertoire sélectionné dans la zone de liste.<br/><br/>Dans la zone **Types de fichiers à ajouter au projet**, spécifiez les types de fichiers que l’Assistant ajoute au nouveau projet en fonction des extensions de fichier données. Les extensions de fichier sont précédées du caractère générique astérisque et sont délimitées dans la liste d’extensions de fichier par un point-virgule. |
    | **Afficher tous les fichiers dans l’Explorateur de solutions** | Indique que tous les fichiers du nouveau projet doivent être visibles et affichés dans la fenêtre **Explorateur de solutions**. Cette option est activée par défaut. |

    ![Emplacement du projet](media/location.png)

1. Spécifiez les paramètres du projet à utiliser, par exemple l’environnement de génération du nouveau projet et les paramètres de génération correspondant à un type spécifique de nouveau projet à générer. Choisissez **Suivant** pour continuer.

    | Paramètre | Description |
    | --- | --- |
    | **Utiliser Visual Studio** | Spécifie l’utilisation des outils de génération inclus dans Visual Studio pour générer le nouveau projet. Cette option est activée par défaut.<br/><br/>Sélectionnez **Type de projet** pour spécifier le type de projet généré par l’Assistant. Choisissez **Projet d’application Windows**, **Projet d’application console**, **Projet DLL (Dynamically Linked Library)** ou **Projet LIB (Static Library)**.<br/><br/>Cochez **Ajouter la prise en charge pour ATL** pour ajouter la prise en charge ATL au nouveau projet.<br/><br/>Cochez **Ajouter la prise en charge pour MFC** pour ajouter la prise en charge MFC au nouveau projet.<br/><br/>Cochez **Ajouter la prise en charge pour le Common Language Runtime** pour ajouter la prise en charge de la programmation du CLR au projet. Choisissez **Prise en charge du Common Language Runtime** pour le type de conformité, par exemple **Common Language Runtime (ancienne syntaxe)** pour la conformité avec la syntaxe Extensions managées pour C++, la syntaxe de programmation du CLR antérieure à Visual C++ 2005. |
    | **Utiliser un système de génération externe** | Spécifie l’utilisation d’outils de génération qui ne sont pas inclus dans Visual Studio pour générer le nouveau projet. Quand cette option est sélectionnée, vous pouvez spécifier des lignes de commande de génération dans les pages **Spécifier les paramètres de configuration Debug** et **Spécifier les paramètres de configuration Release**. |

    ![Paramètres du projet](media/settings.png)

    > [!NOTE]
    > Quand l’option **Utiliser un système de génération externe** est cochée, l’IDE ne génère pas le projet. Les options /D, /I, /Fi, /AI et /FU ne sont donc pas nécessaires pour la compilation. Toutefois, ces options doivent être définies correctement pour qu’IntelliSense fonctionne correctement.

1. Spécifiez les paramètres de configuration Debug à utiliser. Choisissez **Suivant** pour continuer.

    | Paramètre | Description |
    | --- | --- |
    | **Ligne de commande Build** | Spécifie la ligne de commande qui génère le projet. Entrez le nom du compilateur (ainsi que tout commutateur ou argument) ou les scripts de génération à utiliser pour générer le projet. |
    | **Ligne de commande Rebuild** | Spécifie la ligne de commande qui regénère le nouveau projet. |
    | **Ligne de commande Clean** | Spécifie la ligne de commande qui permet de supprimer les fichiers de prise en charge générés par les outils de génération pour le projet. |
    | **Sortie (pour le débogage)** | Spécifie le chemin du répertoire des fichiers de sortie pour la configuration Debug du projet. |
    | **Définitions de préprocesseur (/D)** | Définit les symboles de préprocesseur du projet ; consultez [/D (Définitions de préprocesseur)](../build/reference/d-preprocessor-definitions.md). |
    | **Chemin de recherche Include (/I)** | Spécifie les chemins de répertoire consultés par le compilateur pour résoudre les références de fichier passées aux directives de préprocesseur dans le projet ; consultez [/I (Répertoires Include supplémentaires)](../build/reference/i-additional-include-directories.md). |
    | **Fichiers Include forcés (/FI)** | Spécifie les fichiers d’en-tête à traiter pendant la génération du projet ; consultez [/FI (Nom du fichier Include imposé)](../build/reference/fi-name-forced-include-file.md). |
    | **Chemins de recherche des assemblys .NET (/AI)** | Spécifie les chemins de répertoire consultés par le compilateur pour résoudre les références d’assembly .NET passées aux directives de préprocesseur dans le projet ; consultez [/AI (Spécifier les répertoires des métadonnées)](../build/reference/ai-specify-metadata-directories.md). |
    | **Utilisation forcée des assemblys .NET (/FU)** | Spécifie les assemblys .NET à traiter pendant la génération du projet ; consultez [/FU (Nom du fichier #using imposé)](../build/reference/fu-name-forced-hash-using-file.md). |

    ![Configuration du projet](media/config.png)

    > [!NOTE]
    > Les paramètres **Ligne de commande Build**, **Ligne de commande Rebuild**, **Ligne de commande Clean** et **Sortie (pour le débogage)** ne sont activés que si l’option **Utiliser un système de génération externe** est sélectionnée dans la page **Spécifier les paramètres du projet**.

1. Spécifiez les paramètres de configuration Release à utiliser, ces paramètres étant les mêmes que ceux de la configuration Debug. Choisissez **Terminer** pour générer le nouveau projet.

    > [!NOTE]
    > Ici, vous pouvez cocher **Identique à la configuration Debug** pour spécifier que l’Assistant génère des paramètres de projet de configuration Release identiques à ceux de la configuration Debug. Cette option est cochée par défaut. Toutes les autres options de cette page sont inactives, sauf si vous décochez cette case.
