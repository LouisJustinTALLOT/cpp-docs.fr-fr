---
title: Projets Visual Studio - C++
ms.date: 12/12/2018
f1_keywords:
- vcprojects
- creatingmanagingVC
helpviewer_keywords:
- ATL projects, creating
- Visual C++ projects, creating
- projects [C++], creating
- Visual C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: b4772b9bd625a542a18039386fefe42840ab65b1
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038036"
---
# <a name="visual-studio-projects---c"></a>Projets Visual Studio - C++

Un *projet Visual Studio* est un projet basé sur le système de génération MSBuild. MSBuild est le système de génération natif pour Visual Studio et est généralement que le meilleur build système à utiliser pour les applications UWP, ainsi que des applications de bureau qui utilisent les bibliothèques MFC ou ATL, les composants COM et les autres programmes spécifiques à Windows. MSBuild est étroitement intégré à Visual Studio, mais vous pouvez également l’utiliser à partir de la ligne de commande. 

## <a name="create-a-project"></a>Créer un projet

Vous pouvez créer des projets C++ en choisissant **fichier &#124; New &#124; projet**, puis en cliquant sur Visual C++ dans le volet gauche. Dans le volet central, vous consultez une liste des modèles de projet : 

   ![Modèles de projet](../overview/media/vs2017-new-project.png "Boîte de dialogue Nouveau projet de Visual Studio 2017")

Pour plus d’informations sur tous les modèles de projet par défaut qui sont inclus dans Visual Studio, consultez [des modèles de projet C++ dans Visual Studio](reference/visual-cpp-project-types.md). Vous pouvez créer vos propres modèles de projet. Pour plus d'informations, voir [Procédure : Créer des modèles de projet](/visualstudio/ide/how-to-create-project-templates).

Après avoir créé un projet, il apparaît dans le [l’Explorateur de solutions](/visualstudio/ide/solutions-and-projects-in-visual-studio) fenêtre :

   ![Explorateur de solutions](media/mathlibrary-solution-explorer-153.png)

Lorsque vous créez un nouveau projet, un fichier solution (.sln) est également créé. Vous pouvez ajouter des projets supplémentaires à la solution en cliquant dessus dans **l’Explorateur de solutions**. Le fichier solution est utilisé pour coordonner les dépendances de génération lorsque vous avez plusieurs projets connexes, mais ne fait pas beaucoup de plus. Toutes les options du compilateur sont définies au niveau du projet.

## <a name="add-items"></a>Ajouter des éléments

Ajouter des fichiers de code source, des icônes ou d’autres éléments à votre projet en cliquant sur le projet dans **l’Explorateur de solutions** et en choisissant **Ajouter > nouveau** ou **Ajouter > existant**.

## <a name="add-third-party-libraries"></a>Ajouter des bibliothèques tierces

Pour ajouter des bibliothèques tierces, utilisez le [vcpkg](vcpkg.md) Gestionnaire de package. Exécutez l’étape d’intégration Visual Studio pour configurer les chemins d’accès à cette bibliothèque lorsque vous faites référence à partir de n’importe quel projet de Visual Studio. 

## <a name="set-compiler-options-and-other-build-properties"></a>Définir les options du compilateur et autres propriétés de build

Pour configurer les paramètres de build pour un projet, cliquez sur le projet dans **l’Explorateur de solutions** et choisissez **propriétés**. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](working-with-project-properties.md).

## <a name="compile-and-run"></a>Compiler et exécuter

Pour compiler et exécuter le nouveau projet, appuyez sur **F5** ou cliquez sur le *déboguer la liste déroulante* avec la flèche verte dans la barre d’outils principale. Le *liste déroulante configuration* vous permet de sélectionner s’il faut exécuter une *déboguer* ou *version* build (ou toute autre configuration personnalisée).

Un nouveau projet se compile sans erreur. Lorsque vous ajoutez votre propre code, vous pouvez parfois introduire une erreur ou déclencher un avertissement. Une erreur empêche la génération de fin ; un avertissement ne fait pas. Toutes les erreurs et avertissements seront affiche dans la fenêtre Sortie et dans la liste d’erreurs lorsque vous générez le projet. 

   ![Sortie fenêtre et liste d’erreurs](../overview/media/vs2017-output-error-list.png)

Dans la liste d’erreurs, vous pouvez appuyer sur **F1** sur une erreur en surbrillance pour accéder à sa rubrique de documentation.

## <a name="in-this-section"></a>Dans cette section

[Définir le compilateur C++ et générer des propriétés dans Visual Studio](working-with-project-properties.md)<br/>
Comment utiliser les Pages de propriétés et les feuilles de propriétés pour spécifier les paramètres de votre projet.

[Bibliothèques de référence et des composants au moment de la génération](adding-references-in-visual-cpp-projects.md)<br/>
Guide pratique pour inclure les composants COM et .NET et les bibliothèques, les DLL, dans un projet.
 
[Organiser les fichiers de sortie de projet](how-to-organize-project-output-files-for-builds.md)<br/>
Comment personnaliser l’emplacement des fichiers exécutables créé dans le processus de génération.

[Étapes de génération personnalisée et des événements de Build](understanding-custom-build-steps-and-build-events.md)<br/>
Comment ajouter n’importe quelle commande pour le processus de génération à points spécifiés.

[Créer un projet à partir d’un code existant](how-to-create-a-cpp-project-from-existing-code.md)<br/>
Comment créer un nouveau projet Visual Studio à partir d’une collection libre des fichiers sources.

## <a name="see-also"></a>Voir aussi

[Projets et des systèmes de génération](projects-and-build-systems-cpp.md)<br>
