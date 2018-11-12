---
title: Pages de propriétés (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.NotAProp.Edit
helpviewer_keywords:
- project-file macro
- project properties [C++], default values
- user-defined values
- project properties [C++], setting
- macros, project-file
- property pages, project settings
- Visual C++ projects, properties
- build macro
- user-defined macros
ms.assetid: 13ffe3ea-1bc3-4bee-be5e-053a8a99cce4
ms.openlocfilehash: 4058f6574dcaa6d383295b63bfd27c5c1a0056aa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526448"
---
# <a name="property-pages-visual-c"></a>Pages de propriétés (Visual C++)

Les pages de propriétés vous permettent de spécifier les paramètres des projets Visual Studio. Pour ouvrir la boîte de dialogue **Pages de propriétés** d’un projet Visual Studio, dans le menu **Projet**, choisissez **Propriétés**.

Vous pouvez spécifier les paramètres du projet pour qu'ils s'appliquent à toutes les configurations de build. Vous pouvez aussi spécifier différentes propriétés de projet pour chaque configuration de build. Par exemple, vous pouvez spécifier certains paramètres pour la configuration Release et d’autres paramètres pour la configuration Debug.

La boîte de dialogue **Pages de propriétés** n’affiche pas nécessairement toutes les pages disponibles. Les pages affichées varient en fonction des types de fichiers contenus dans le projet.

Pour plus d’informations, consultez [Utilisation des propriétés de projet](../ide/working-with-project-properties.md).

Pour les projets non-Windows, consultez [Informations de référence sur les pages de propriétés dans un projet Linux](../linux/prop-pages-linux.md)<!-- or [C++ Cross Platform Property Page Reference](../linux/prop-pages-linux.md)-->.

## <a name="default-properties-vs-modified-properties"></a>Propriétés par défaut et propriétés modifiées

Quand vous créez un projet à partir de la boîte de dialogue **Nouveau projet**, Visual Studio utilise le modèle de projet spécifié pour initialiser les propriétés du projet. Par conséquent, les valeurs des propriétés du modèle peuvent être considérées comme des valeurs par défaut pour ce type de projet. Dans d'autres types de projets, les propriétés peuvent avoir des valeurs par défaut différentes.

Une valeur de propriété de projet apparaît en gras si elle est modifiée. Une propriété de projet peut être modifiée pour les raisons suivantes :

- L'Assistant Application modifie la propriété, car il exige une valeur de propriété différente de celle spécifiée dans le modèle de projet.

- Vous pouvez spécifier une valeur de propriété différente dans la boîte de dialogue **Nouveau projet**.

- Vous pouvez spécifier une valeur de propriété différente dans une page de propriétés du projet.

> [!TIP]
> Pour voir le jeu de valeurs de propriétés final que MSBuild utilise pour générer votre projet, examinez le fichier de sortie du préprocesseur, que vous pouvez créer en utilisant cette ligne de commande : **MSBuild /preprocess:** *nom_fichier_sortie_préprocesseur*<sub>opt</sub> *nom_fichier_projet*<sub>opt</sub>

## <a name="resetting-properties"></a>Réinitialisation des propriétés

Quand vous consultez la boîte de dialogue **Pages de propriétés** d’un projet et que le nœud du projet est sélectionné dans **l’Explorateur de solutions**, pour un grand nombre de propriétés, vous pouvez sélectionner **Hériter des paramètres par défaut du parent ou du projet**, ou modifier la valeur d’une autre façon.

Quand vous consultez la boîte de dialogue **Pages de propriétés** d’un projet et qu’un fichier est sélectionné dans **l’Explorateur de solutions**, pour un grand nombre de propriétés, vous pouvez sélectionner **Hériter des paramètres par défaut du parent ou du projet**, ou modifier la valeur d’une autre façon. Cependant, si le projet contient de nombreux fichiers dont certaines propriétés ont des valeurs différentes des valeurs par défaut du projet, la génération de ce dernier prend plus de temps.

> [!TIP]
> Pour actualiser la boîte de dialogue **Pages de propriétés** de sorte qu’elle affiche les sélections les plus récentes, choisissez **Appliquer**.

La plupart des valeurs par défaut du projet sont les valeurs par défaut du système (plateforme). Certains paramètres par défaut du projet dérivent des feuilles de style qui sont appliquées au moment où vous mettez à jour les propriétés dans la section **Paramètres par défaut du projet** de la page de propriétés de configuration **Général** du projet. Pour plus d'informations, consultez [Général, page de propriétés (Projet)](../ide/general-property-page-project.md).

## <a name="specifying-user-defined-values"></a>Spécification de valeurs définies par l'utilisateur

Vous devez définir la valeur de certaines propriétés. Une valeur définie par l'utilisateur peut contenir un ou plusieurs caractères alphanumériques ou des noms de macros de fichiers projet. Si certaines de ces propriétés ne peuvent prendre qu'une seule valeur définie par l'utilisateur, d'autres peuvent en accepter plusieurs prenant la forme d'une liste délimitée par des points-virgules.

Pour définir une propriété avec une valeur définie par l'utilisateur ou une liste si la propriété peut accepter plusieurs valeurs définies par l'utilisateur, dans la colonne située à droite du nom de la propriété, procédez de l'une des façons suivantes :

- Tapez la valeur ou la liste de valeurs.

- Choisissez la flèche déroulante. Si **Modifier** est disponible, choisissez-le, puis tapez la valeur ou la liste de valeurs dans la zone de texte. Une autre façon de spécifier une liste est de taper chaque valeur sur une ligne distincte dans la zone de texte. Dans la page de propriétés, les valeurs s'affichent sous forme de liste délimitée par des points-virgules.

   Pour insérer une macro de fichier projet comme valeur, choisissez **Macros**, puis double-cliquez sur le nom de la macro.

- Choisissez la flèche déroulante. Si **Parcourir** est disponible, choisissez-le, puis sélectionnez une ou plusieurs valeurs.

Pour une propriété multivaleur, l’option **Hériter des paramètres par défaut du parent ou du projet** est disponible quand vous choisissez la flèche déroulante de la colonne à droite du nom de la propriété, puis choisissez **Modifier**. Cette option est activée par défaut.

Notez qu'une page de propriétés présente uniquement les paramètres correspondant au niveau actuel d'une propriété à valeurs multiples qui hérite d'un autre niveau. Par exemple, si un fichier est sélectionné dans **l’Explorateur de solutions** et que vous sélectionnez la propriété **Définitions de préprocesseur** C/C++, les définitions au niveau du fichier sont affichées, mais pas les définitions héritées au niveau du projet. Pour afficher à la fois les valeurs du niveau actuel et les valeurs héritées, choisissez la flèche déroulante de la colonne à droite du nom de la propriété, puis **Modifier**. Si vous utilisez le [modèle de projet Visual C++](https://docs.microsoft.com/dotnet/api/microsoft.visualstudio.vcprojectengine), ce comportement s’applique aussi aux objets des fichiers et projets. Ainsi, quand vous formulez une requête pour récupérer les valeurs d'une propriété au niveau du fichier, vous n'obtenez pas les valeurs de cette même propriété au niveau du projet. Vous devez obtenir explicitement les valeurs de la propriété au niveau du projet. De même, certaines valeurs héritées d'une propriété peuvent provenir d'une feuille de style qui n'est pas accessible par programmation.

## <a name="in-this-section"></a>Dans cette section

[Avancé, Outil Manifeste, Propriétés de configuration, boîte de dialogue Pages de propriétés de \<NomProjet>](../ide/advanced-manifest-tool.md)

[Ligne de commande, pages de propriétés](../ide/command-line-property-pages.md)

[Étape de génération personnalisée, page de propriétés : général](../ide/custom-build-step-property-page-general.md)

[Ajout de références](../ide/adding-references-in-visual-cpp-projects.md)

[Général, page de propriétés (Fichier)](../ide/general-property-page-file.md)

[Général, page de propriétés (Projet)](../ide/general-property-page-project.md)

[Général, Outil Manifeste, Propriétés de configuration, boîte de dialogue Pages de propriétés de \<NomProjet>](../ide/general-manifest-tool-configuration-properties.md)

[HLSL, page de propriétés](../ide/hlsl-property-pages.md)

[HLSL, page de propriétés : Avancé](../ide/hlsl-property-pages-advanced.md)

[HLSL, page de propriétés : Général](../ide/hlsl-property-pages-general.md)

[HLSL, page de propriétés : fichiers de sortie](../ide/hlsl-property-pages-output-files.md)

[Entrée et sortie, Outil Manifeste, Propriétés de configuration, boîte de dialogue Pages de propriétés de \<NomProjet>](../ide/input-and-output-manifest-tool.md)

[COM isolé, Outil Manifeste, Propriétés de configuration, boîte de dialogue Pages de propriétés de \<NomProjet>](../ide/isolated-com-manifest-tool.md)

[Éditeur de liens, page de propriétés](../ide/linker-property-pages.md)

[Ressources managées, page de propriétés](../ide/managed-resources-property-page.md)

[Outil Manifeste, page de propriétés](../ide/manifest-tool-property-pages.md)

[MIDL, page de propriétés](../ide/midl-property-pages.md)

[MIDL, page de propriétés : Avancé](../ide/midl-property-pages-advanced.md)

[MIDL, page de propriétés : Général](../ide/midl-property-pages-general.md)

[MIDL, page de propriétés : Sortie](../ide/midl-property-pages-output.md)

[NMake, page de propriétés](../ide/nmake-property-page.md)

[Ressources, page de propriétés](../ide/resources-property-pages.md)

[Répertoires VC++, page de propriétés](../ide/vcpp-directories-property-page.md)

[Références web, page de propriétés](../ide/web-references-property-page.md)

[XML Data Generator Tool, page de propriétés](../ide/xml-data-generator-tool-property-page.md)

[Outil Générateur de documents XML, page de propriétés](../ide/xml-document-generator-tool-property-pages.md)

## <a name="see-also"></a>Voir aussi

[Guide pratique pour créer et supprimer les dépendances d’un projet](/visualstudio/ide/how-to-create-and-remove-project-dependencies)<br>
[Guide pratique pour créer et modifier des configurations](/visualstudio/ide/how-to-create-and-edit-configurations)
