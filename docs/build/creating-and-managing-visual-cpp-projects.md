---
title: Projets Visual Studio – C++
ms.date: 10/25/2019
helpviewer_keywords:
- ATL projects, creating
- Visual Studio C++ projects, creating
- projects [C++], creating
- Visual Studio C++ projects
- ATL projects
ms.assetid: 11003cd8-9046-4630-a189-a32bf3b88047
ms.openlocfilehash: d6bfefdaa3dfc67f861cf116718f89c0e9766e47
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624475"
---
# <a name="visual-studio-projects---c"></a>Projets Visual Studio – C++

Un *projet Visual Studio* est un projet basé sur le système de génération MSBuild. MSBuild est le système de génération natif pour Visual Studio. il s’agit généralement du meilleur système de génération à utiliser pour les programmes spécifiques à Windows. MSBuild est étroitement intégré à Visual Studio, mais vous pouvez aussi l’utiliser à partir de la ligne de commande. Pour les projets multiplateforme, ou les projets qui utilisent des bibliothèques Open source, nous vous recommandons d’utiliser des [projets cmake dans Visual Studio](cmake-projects-in-visual-studio.md) dans visual studio 2017 et versions ultérieures. Pour plus d’informations sur la mise à niveau de projets MSBuild à partir de versions antérieures de Visual Studio, consultez le [Guide de Portage et de mise C++ à niveau de Microsoft](../porting/visual-cpp-porting-and-upgrading-guide.md).

## <a name="create-a-project"></a>Créer un projet

::: moniker range="vs-2019"

Vous pouvez créer des projets C++ en choisissant **Fichier** > **Nouveau** > **Projet**, puis en définissant **Langage** sur C++. Dans la liste des résultats, vous voyez une liste de modèles de projet que vous pouvez filtrer en définissant le paramètre **Plateforme** ou **Type de projet** et ou tapant des mots clés dans la zone de recherche. 

   ![Modèles de projet Visual Studio 2019](../build/media/vs2019-choose-console-app.png "Boîte de dialogue Nouveau projet de Visual Studio 2019")

::: moniker-end

::: moniker range="vs-2017"

Vous pouvez créer des projets C++ en choisissant **Fichier** > **Nouveau** > **Projet**, puis en choisissant Visual C++ dans le volet gauche. Dans le volet central, vous voyez une liste de modèles de projet :

   ![Modèles de projet](../overview/media/vs2017-new-project.png "Boîte de dialogue Nouveau projet de Visual Studio 2017")

::: moniker-end

Pour plus d’informations sur tous les modèles de projet par défaut inclus dans Visual Studio, consultez [Modèles de projet C++ dans Visual Studio](reference/visual-cpp-project-types.md). Vous pouvez créer vos propres modèles de projet. Pour plus d’informations, consultez [Comment : créer des modèles de projet](/visualstudio/ide/how-to-create-project-templates).

Un projet que vous créez apparaît aussitôt dans la fenêtre [Explorateur de solutions](/visualstudio/ide/solutions-and-projects-in-visual-studio) :

   ![l'Explorateur de solutions](media/mathlibrary-solution-explorer-153.png)

Quand vous créez un projet, un fichier solution (.sln) est aussi créé. Vous pouvez ajouter des projets supplémentaires à la solution en cliquant dessus avec le bouton droit dans l’**Explorateur de solutions**. Le fichier solution permet de coordonner les dépendances de build quand vous avez plusieurs projets connexes, mais il n’a aucune autre utilité. Toutes les options du compilateur sont définies au niveau du projet.

## <a name="add-items"></a>Ajouter des éléments

Ajoutez des fichiers de code source, des icônes ou tout autre élément à votre projet en cliquant sur le projet avec le bouton droit dans l’**Explorateur de solutions** et en choisissant **Ajouter > Nouveau** ou **Ajouter > Existant**.

## <a name="add-third-party-libraries"></a>Ajouter des bibliothèques tierces

Pour ajouter des bibliothèques tierces, utilisez le gestionnaire de package [vcpkg](vcpkg.md). Exécutez l’étape d’intégration de Visual Studio pour définir les chemins de cette bibliothèque quand vous y faites référence dans un projet Visual Studio. 

## <a name="set-compiler-options-and-other-build-properties"></a>Définir les options du compilateur et autres propriétés de build

Pour configurer les paramètres de build d’un projet, cliquez avec le bouton droit sur le projet dans l’**Explorateur de solutions**, puis choisissez **Propriétés**. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](working-with-project-properties.md).

## <a name="compile-and-run"></a>Compiler et exécuter

Pour compiler et exécuter le nouveau projet, appuyez sur **F5** ou cliquez sur la *liste déroulante de débogage* qui présente la flèche verte dans la barre d’outils principale. C’est dans la *liste déroulante de configuration* que vous choisissez d’exécuter une build *Debug* ou *Release* (ou toute autre configuration personnalisée).

Un nouveau projet se compile sans erreur. Quand vous ajoutez votre propre code, vous pouvez parfois introduire une erreur ou déclencher un avertissement. Si une erreur empêche la génération d’aboutir, ce n’est pas le cas d’un avertissement. Toutes les erreurs et tous les avertissements s’affichent à la fois dans la Fenêtre Sortie et dans la Liste d’erreurs pendant la génération du projet. 

   ![Fenêtre Sortie et Liste d’erreurs](../overview/media/vs2017-output-error-list.png)

Dans la Liste d’erreurs, vous pouvez appuyer sur **F1** pour une erreur en surbrillance afin d’accéder à la rubrique correspondante dans la documentation.

## <a name="in-this-section"></a>Dans cette section

[Définir le compilateur C++ et les propriétés de build dans Visual Studio](working-with-project-properties.md)<br/>
Guide pratique pour utiliser Pages de propriétés et Feuilles de propriétés pour spécifier les paramètres de votre projet.

[Composants et bibliothèques de référence au moment de la création](adding-references-in-visual-cpp-projects.md)<br/>
Guide pratique pour inclure bibliothèques, DLL, composants COM et .NET dans un projet.
 
[Organiser des fichiers de sortie de projet](how-to-organize-project-output-files-for-builds.md)<br/>
Guide pratique pour personnaliser l’emplacement des fichiers exécutables créés dans le processus de build.

[Étapes de build personnalisée et événements de build](understanding-custom-build-steps-and-build-events.md)<br/>
Guide pratique pour ajouter une commande arbitraire au processus de build à des points spécifiés.

[Créer un projet à partir d’un code existant](how-to-create-a-cpp-project-from-existing-code.md)<br/>
Guide pratique pour créer un projet Visual Studio à partir d’une collection libre de fichiers sources.

## <a name="see-also"></a>Voir aussi

[Projets et systèmes de build](projects-and-build-systems-cpp.md)<br>
[Guide C++ de Portage et de mise à niveau Microsoft](../porting/visual-cpp-porting-and-upgrading-guide.md)
