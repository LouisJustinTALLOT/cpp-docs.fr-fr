---
title: Page de propriétés Répertoires VC++
ms.date: 10/09/2018
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
ms.openlocfilehash: 3822a3c751ac06154e4b13a12f449e7f0ff2cc07
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825540"
---
# <a name="vc-directories-property-page-windows"></a>Répertoires VC++, page de propriétés (Windows)

Utilisez cette page de propriétés pour indiquer à Visual Studio les répertoires à utiliser durant la génération du projet sélectionné. Pour définir les répertoires pour plusieurs projets dans une solution, utilisez une feuille de propriétés personnalisées, comme décrit dans [les paramètres de projet de Visual Studio C++ partage ou resuse](../create-reusable-property-configurations.md).

Pour accéder à la version Linux de cette page, consultez [Répertoires VC++ (Linux C++)](../../linux/prop-pages/directories-linux.md).

Pour accéder à la page de propriétés **Répertoires VC++** :

1. Si la fenêtre **Explorateur de solutions** n’est pas visible, choisissez **Affichage** > **Explorateur de solutions** dans le menu principal.
1. Cliquez avec le bouton droit sur un nœud de projet (pas la solution de niveau supérieur), puis choisissez **Propriétés**.
1. Dans le volet gauche de la boîte de dialogue **Pages de propriétés**, sélectionnez **Propriétés de configuration** > **Répertoires VC++**.

Les propriétés des répertoires VC++ s’appliquent à un projet, et non au nœud de la solution de niveau supérieur. Si vous ne voyez pas **Répertoires VC++** sous **Propriétés de configuration**, sélectionnez un nœud de projet C++ dans la fenêtre **Explorateur de solutions** :

![Sélectionner le nœud de projet](../media/vcppdir.png "Sélectionner le nœud de projet pour voir les propriétés Répertoires VC++")

Notez que la page de propriétés **Répertoires VC++** pour les projets multiplateformes se présente différemment. Pour obtenir des informations spécifiques aux projets Linux C++, consultez [Répertoires VC++ (Linux C++)](../../linux/prop-pages/directories-linux.md).

Si vous n’êtes pas familiarisé avec *propriétés de projet* dans Visual Studio, il peut s’avérer utile de la première lecture [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

Les paramètres par défaut des propriétés **Répertoires VC++** varient selon le type de projet. Pour les projets de bureau, il s’agit notamment des emplacements des outils C++ pour un ensemble d’outils de plateforme spécifique et de l’emplacement du SDK Windows. Vous pouvez changer les paramètres **Ensemble d’outils de plateforme** et **Version du SDK Windows** dans la page **Propriétés de configuration** > **Général**.

Pour afficher les valeurs d’un des répertoires :

1. Sélectionnez l’une des propriétés dans la page **Répertoires VC++**. Par exemple, choisissez **Répertoires de bibliothèques**.
1. Choisissez le bouton avec une flèche vers le bas situé à la fin du champ de valeur de la propriété.
1. Dans le menu déroulant, choisissez **Modifier**.

![Modifier les répertoires de bibliothèques](../media/vcppdir_libdir_edit.png "Boîte de dialogue permettant de modifier des chemins de bibliothèques")

Une boîte de dialogue similaire à celle-ci s’affiche :

![Afficher les répertoires de bibliothèques](../media/vcppdir_libdir.png "Boîte de dialogue permettant d’ajouter ou de supprimer des chemins de bibliothèques")

Utilisez cette boîte de dialogue pour afficher les répertoires actifs. Toutefois, si vous souhaitez changer ou ajouter un répertoire, il est préférable d’utiliser le **Gestionnaire de propriétés** pour créer une feuille de propriétés ou modifier la feuille de propriétés d’utilisateur par défaut. Pour plus d’informations, consultez [les paramètres de projet de Visual Studio C++ partage ou resuse](../create-reusable-property-configurations.md).

Comme indiqué ci-dessus, la plupart des chemins hérités sont fournis sous forme de macros.  Pour examiner la valeur actuelle d’une macro, choisissez le bouton **Macros** dans le coin inférieur droit de la boîte de dialogue. Notez que de nombreuses macros dépendent du type de configuration. Deux macros identiques dans une build Debug et une build Release peuvent correspondre à un chemin différent.

Vous pouvez rechercher des correspondances partielles ou complètes dans la zone d’édition. L’illustration suivante montre toutes les macros contenant la chaîne « WindowsSDK », ainsi que le chemin actuel auquel correspond la macro :

![Voir les valeurs des macros](../media/vcppdir_libdir_macros.png "Boîte de dialogue permettant de modifier les macros")

Remarque : La liste est remplie en cours de frappe. N’appuyez pas sur **Entrée**.

Pour plus d’informations sur les macros et pourquoi vous devez utiliser à la place les chemins d’accès codés en dur chaque fois que possible, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

Pour obtenir la liste des macros couramment utilisées, consultez [macros courantes pour générer des propriétés et les commandes](common-macros-for-build-commands-and-properties.md).

Pour définir vos propres macros, deux options s’offrent à vous :

- Définissez des variables d’environnement dans une invite de commandes développeur. Toutes les variables d’environnement sont traitées comme propriétés/macros MSBuild.

- Définissez des macros utilisateur dans un fichier .props. Pour plus d’informations, consultez [Macros des pages de propriétés](../working-with-project-properties.md).

Pour plus d’informations, consultez ces billets de blog : [Répertoires VC ++](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx), [héritée et feuilles de propriétés](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx), et [Guide de mise à niveau de projet Visual Studio 2010 C++](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx).

## <a name="directory-types"></a>Types de répertoires

Vous pouvez également spécifier d'autres répertoires, comme suit.

**Répertoires d’exécutables**<br/>
Répertoires dans lesquels rechercher des fichiers exécutables. Correspond à la variable d’environnement **PATH**.

**Répertoires Include**<br/>
Répertoires dans lesquels rechercher des fichiers Include référencés dans le code source. Correspond à la variable d’environnement **INCLUDE**.

**Répertoires de référence**<br/>
Répertoires dans lesquels rechercher des fichiers d’assembly et de modules (métadonnées) référencés dans le code source par la directive [#using](../../preprocessor/hash-using-directive-cpp.md). Correspond à la variable d’environnement **LIBPATH**.

**Répertoires de bibliothèques**<br/>
Répertoires dans lesquels se trouvent des fichiers bibliothèques (.lib) ; cela inclut des bibliothèques Runtime. Correspond à la variable d’environnement **LIB**. Ce paramètre ne s’applique pas aux fichiers .obj. Pour lier à un fichier .obj, dans la page de propriétés **Propriétés de configuration** > **Éditeur de liens** > **Général**, sélectionnez **Répertoires de bibliothèques supplémentaires**, puis spécifiez le chemin relatif du fichier. Pour plus d’informations, consultez [Éditeur de liens, page de propriétés](linker-property-pages.md).

**Répertoires de la bibliothèque WinRT**<br/>
Répertoires dans lesquels rechercher des fichiers de la bibliothèque WinRT à utiliser dans les applications UWP (plateforme Windows universelle).

**Répertoires sources**<br/>
Répertoires dans lesquels rechercher des fichiers source à utiliser pour IntelliSense.

**Exclure des répertoires**<br/>
Avant chaque compilation, Visual Studio interroge l’horodatage sur tous les fichiers pour déterminer s’ils ont été modifiés depuis la compilation précédente. Si votre projet comporte des bibliothèques stables volumineuses, vous pouvez exclure ces répertoires de la vérification de l’horodatage pour tenter d’accélérer la génération.

## <a name="sharing-the-settings"></a>Partage des paramètres

Vous pouvez partager des paramètres de projet avec d'autres utilisateurs ou sur plusieurs ordinateurs. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).