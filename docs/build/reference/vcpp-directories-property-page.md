---
description: 'En savoir plus sur : page de propriétés des répertoires VC + + (Windows)'
title: Page de propriétés Répertoires VC++
ms.date: 07/17/2019
f1_keywords:
- VC.Project.VCDirectories.IncludePath
- VC.Project.VCDirectories.ReferencePath
- VC.Project.VCDirectories.SourcePath
- VC.Project.VCDirectories.LibraryWPath
- VC.Project.VCDirectories.ExecutablePath
- VC.Project.VCDirectories.LibraryPath
- VS.ToolsOptionsPages.Projects.VCDirectories
- VC.Project.VCDirectories.ExcludePath
helpviewer_keywords:
- VC++ Directories Property Page
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
ms.openlocfilehash: 6d5b30e635003aa4db35e3aef9e1a32f8fa3176c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247135"
---
# <a name="vc-directories-property-page-windows"></a>Répertoires VC++, page de propriétés (Windows)

Utilisez cette page de propriétés pour indiquer à Visual Studio les répertoires à utiliser durant la génération du projet sélectionné. Pour définir des répertoires pour plusieurs projets dans une solution, utilisez une feuille de propriétés personnalisée comme décrit dans [partager ou réutiliser les paramètres de projet C++ Visual Studio](../create-reusable-property-configurations.md).

Pour accéder à la version Linux de cette page, consultez [Répertoires VC++ (Linux C++)](../../linux/prop-pages/directories-linux.md).

Pour accéder à la page de propriétés **Répertoires VC++** :

1. Si la fenêtre **Explorateur de solutions** n’est pas visible, choisissez **Affichage** > **Explorateur de solutions** dans le menu principal.
1. Cliquez avec le bouton droit sur un nœud de projet (pas la solution de niveau supérieur), puis choisissez **Propriétés**.
1. Dans le volet gauche de la boîte de dialogue **Pages de propriétés**, sélectionnez **Propriétés de configuration** > **Répertoires VC++**.

Les propriétés des répertoires VC++ s’appliquent à un projet, et non au nœud de la solution de niveau supérieur. Si vous ne voyez pas **Répertoires VC++** sous **Propriétés de configuration**, sélectionnez un nœud de projet C++ dans la fenêtre **Explorateur de solutions** :

![Sélectionner le nœud du projet](../media/vcppdir.png "Sélectionnez le nœud du projet pour afficher les propriétés des répertoires VC + +")

Notez que la page de propriétés **Répertoires VC++** pour les projets multiplateformes se présente différemment. Pour obtenir des informations spécifiques aux projets Linux C++, consultez [Répertoires VC++ (Linux C++)](../../linux/prop-pages/directories-linux.md).

Si vous n’êtes pas familiarisé avec les *Propriétés de projet* dans Visual Studio, il peut s’avérer utile de lire d’abord la [définition du compilateur C++ et des propriétés de génération dans Visual Studio](../working-with-project-properties.md).

Les paramètres par défaut des propriétés **Répertoires VC++** varient selon le type de projet. Pour les projets de bureau, il s’agit notamment des emplacements des outils C++ pour un ensemble d’outils de plateforme spécifique et de l’emplacement du SDK Windows. Vous pouvez changer les paramètres **Ensemble d’outils de plateforme** et **Version du SDK Windows** dans la page **Propriétés de configuration** > **Général**.

Pour afficher les valeurs d’un des répertoires :

1. Sélectionnez l’une des propriétés dans la page **Répertoires VC++**. Par exemple, choisissez **Répertoires de bibliothèques**.
1. Choisissez le bouton avec une flèche vers le bas situé à la fin du champ de valeur de la propriété.
1. Dans le menu déroulant, choisissez **Modifier**.

![Modifier les répertoires de bibliothèque](../media/vcppdir_libdir_edit.png "Boîte de dialogue pour modifier les chemins de bibliothèque")

Une boîte de dialogue similaire à celle-ci s’affiche :

![Afficher les répertoires de bibliothèque](../media/vcppdir_libdir.png "Boîte de dialogue pour ajouter ou supprimer des chemins de bibliothèque")

Utilisez cette boîte de dialogue pour afficher les répertoires actifs. Toutefois, si vous souhaitez changer ou ajouter un répertoire, il est préférable d’utiliser le **Gestionnaire de propriétés** pour créer une feuille de propriétés ou modifier la feuille de propriétés d’utilisateur par défaut. Pour plus d’informations, consultez [partager ou réutiliser des paramètres de projet Visual Studio C++](../create-reusable-property-configurations.md).

Comme indiqué ci-dessus, la plupart des chemins hérités sont fournis sous forme de macros.  Pour examiner la valeur actuelle d’une macro, choisissez le bouton **Macros** dans le coin inférieur droit de la boîte de dialogue. Notez que de nombreuses macros dépendent du type de configuration. Deux macros identiques dans une build Debug et une build Release peuvent correspondre à un chemin différent.

Vous pouvez rechercher des correspondances partielles ou complètes dans la zone d’édition. L’illustration suivante montre toutes les macros contenant la chaîne « WindowsSDK », ainsi que le chemin actuel auquel correspond la macro :

![Voir les valeurs de macro](../media/vcppdir_libdir_macros.png "Boîte de dialogue pour modifier les macros")

Remarque : La liste est remplie à mesure que vous tapez. N’appuyez pas sur **Entrée**.

Pour plus d’informations sur les macros et la raison pour laquelle vous devez les utiliser au lieu de chemins d’accès codés en dur dans la mesure du possible, consultez [définir le compilateur C++ et les propriétés de génération dans Visual Studio](../working-with-project-properties.md).

Pour obtenir la liste des macros couramment utilisées, consultez [macros courantes pour les propriétés et les commandes de génération](common-macros-for-build-commands-and-properties.md).

Pour définir vos propres macros, deux options s’offrent à vous :

- Définissez des variables d’environnement dans une invite de commandes développeur. Toutes les variables d’environnement sont traitées comme propriétés/macros MSBuild.

- Définissez des macros utilisateur dans un fichier .props. Pour plus d’informations, consultez [Macros des pages de propriétés](../working-with-project-properties.md).

Pour plus d’informations, consultez [héritage des propriétés dans les projets Visual Studio](../project-property-inheritance.md)et les billets de blog suivants : [Répertoires VC + +](/archive/blogs/vsproject/vc-directories), [Guide de mise à niveau des projets C++ Visual Studio 2010](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/).

## <a name="directory-types"></a>Types de répertoires

Vous pouvez également spécifier d'autres répertoires, comme suit.

**Répertoires d’exécutables**<br/>
Répertoires dans lesquels rechercher des fichiers exécutables. Correspond à la variable d’environnement **PATH**.

**Répertoires Include**<br/>
Répertoires dans lesquels rechercher des fichiers Include référencés dans le code source. Correspond à la variable d’environnement **INCLUDE**.

**Répertoires de référence**<br/>
Répertoires dans lesquels rechercher des fichiers d’assembly et de modules (métadonnées) référencés dans le code source par la directive [#using](../../preprocessor/hash-using-directive-cpp.md). Correspond à la variable d’environnement **LIBPATH**.

**Répertoires de bibliothèques**<br/>
Répertoires dans lesquels se trouvent des fichiers bibliothèques (.lib) ; cela inclut des bibliothèques Runtime. Correspond à la variable d’environnement **LIB**. Ce paramètre ne s’applique pas aux fichiers. obj ; pour créer un lien vers un fichier. obj, sur la page **Propriétés de configuration**  >  général de l'**éditeur de liens**  >   , sélectionnez **dépendances de bibliothèque supplémentaires** , puis spécifiez le chemin d’accès relatif du fichier. Pour plus d’informations, consultez [Éditeur de liens, page de propriétés](linker-property-pages.md).

**Répertoires de la bibliothèque WinRT**<br/>
Répertoires dans lesquels rechercher des fichiers de la bibliothèque WinRT à utiliser dans les applications UWP (plateforme Windows universelle).

**Répertoires sources**<br/>
Répertoires dans lesquels rechercher des fichiers source à utiliser pour IntelliSense.

**Exclure des répertoires**<br/>
Avant chaque compilation, Visual Studio interroge l’horodatage sur tous les fichiers pour déterminer s’ils ont été modifiés depuis la compilation précédente. Si votre projet comporte des bibliothèques stables volumineuses, vous pouvez exclure ces répertoires de la vérification de l’horodatage pour tenter d’accélérer la génération.

## <a name="sharing-the-settings"></a>Partage des paramètres

Vous pouvez partager des paramètres de projet avec d'autres utilisateurs ou sur plusieurs ordinateurs. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).
