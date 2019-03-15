---
title: Partage ou resuse paramètres Visual Studio projet - C++
ms.date: 11/28/2018
helpviewer_keywords:
- project properties [C++], reusable
ms.openlocfilehash: 50e3795a4708a3c15ed25ee7ff6565470ef6989a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826086"
---
# <a name="share-or-resuse-visual-studio-project-settings"></a>Partage ou resuse paramètres du projet Visual Studio

Pour créer un groupe personnalisé de paramètres que vous pouvez partager avec d’autres utilisateurs ou les réutiliser dans plusieurs projets, utilisez **Gestionnaire de propriétés** pour créer un *feuille de propriétés* (fichier .props) pour stocker les paramètres pour chaque type de projet que vous souhaitez pouvoir réutiliser ou partager avec d’autres utilisateurs. À l’aide de la propriété feuilles sont beaucoup moins sujette aux erreurs que les autres façons de créer des paramètres « globaux ». 

> [!IMPORTANT]
> **Fichiers .user et pourquoi ils posent un problème**
>
> Les versions précédentes de Visual Studio utilisaient des feuilles de propriétés globales qui avaient une extension de nom de fichier .user et se trouvaient dans le dossier \<profil_utilisateur>\AppData\Local\Microsoft\MSBuild\v4.0\. Nous ne recommandons plus l'utilisation de ces fichiers, car ils définissent des propriétés pour les configurations de projet sur la base de chaque utilisateur et de chaque ordinateur. Ces paramètres « globaux » peuvent perturber les builds, surtout lorsque vous ciblez plusieurs plateformes sur votre ordinateur de build. Par exemple, si vous avez un projet MFC et un projet Windows Phone, les propriétés .user seraient non valides pour l'un d'eux. Les feuilles de propriétés réutilisables sont plus flexibles et plus fiables.
>
> Bien que les fichiers .user soient toujours installés par Visual Studio et participent à l'héritage des propriétés, ils sont vides par défaut. Une bonne pratique est de supprimer la référence correspondante dans le **Gestionnaire de propriétés** pour faire en sorte que les projets fonctionnent indépendamment des paramètres selon l’utilisateur et l’ordinateur. De cette façon, vous garantissez un comportement approprié dans un environnement de contrôle de code source (SCC).

Pour afficher le **Gestionnaire de propriétés**, dans la barre de menus, choisissez **Affichage**, **Autres fenêtres**, **Gestionnaire de propriétés**.

Si vous avez un ensemble de propriétés commun fréquemment utilisé à appliquer à plusieurs projets, vous pouvez utiliser le **Gestionnaire de propriétés** pour les capturer dans un fichier de *feuilles de propriétés* réutilisable qui, par convention, a une extension de nom de fichier .props. Vous pouvez appliquer la feuille (ou les feuilles) à de nouveaux projets afin de ne pas avoir à définir intégralement ses propriétés. Pour accéder au **Gestionnaire de propriétés**, dans la barre de menus, choisissez **Afficher**, **Gestionnaire de propriétés**.

![Menu contextuel du Gestionnaire de propriétés](media/sharingnew.png "SharingNew")

Sous chaque nœud de configuration, vous voyez des nœuds pour chaque feuille de propriétés qui s’applique à cette configuration. Le système ajoute des feuilles de propriétés qui définissent les valeurs selon les options que vous choisissez dans l’Assistant Application quand vous créez le projet. Cliquez avec le bouton droit sur n’importe quel nœud et choisissez Propriétés pour voir les propriétés qui s’appliquent à ce nœud. Toutes les feuilles de propriétés sont importées automatiquement dans la feuille de propriétés « master » du projet (ms.cpp.props) et sont évaluées par ordre d’apparition dans le Gestionnaire de propriétés. Vous pouvez les déplacer pour changer l’ordre d’évaluation. Les feuilles de propriétés qui sont évaluées par la suite remplacent les valeurs dans les feuilles précédemment évaluées. Consultez [l’héritage de propriété de projet](project-property-inheritance.md) pour plus d’informations sur l’ordre d’évaluation dans le fichier .vcxproj, les fichiers .props et .targets, variables d’environnement et la ligne de commande.

Si vous choisissez **Ajouter une nouvelle feuille de propriétés** et que vous sélectionnez, par exemple, la feuille de propriétés MyProps.props, une boîte de dialogue Page de propriétés apparaît. Remarquez qu'elle s'applique à la feuille de propriétés MyProps ; toutes les modifications que vous apportez sont écrites dans la feuille, et non dans le fichier projet (.vcxproj).

Les propriétés dans une feuille de propriétés sont remplacées si la même propriété est définie directement dans le fichier .vcxproj.

Vous pouvez importer une feuille de propriétés aussi souvent que nécessaire. Plusieurs projets d'une solution peuvent hériter des paramètres de la feuille de propriétés et un projet peut avoir plusieurs feuilles. Une feuille de propriétés peut hériter elle-même des paramètres d'une autre feuille de propriétés.

Vous pouvez également créer une feuille de propriétés pour plusieurs configurations. Pour cela, créez une feuille de propriétés pour chaque configuration, ouvrez le menu contextuel associé à l’une d’elles, choisissez **Ajouter une feuille de propriétés existante**, puis ajoutez les autres feuilles. Toutefois, si vous utilisez une feuille de propriétés commune, sachez que lorsque vous définissez une propriété, elle est définie pour toutes les configurations auxquelles la feuille s'applique et l'environnement IDE n'indique pas quels projets ou autres feuilles de propriétés héritent d'une feuille de propriétés donnée.

Dans les grandes solutions qui auront de nombreux projets, il peut être utile de créer une feuille de propriétés au niveau de la solution. Quand vous ajoutez un projet à la solution, utilisez le **Gestionnaire de propriétés** pour ajouter cette feuille de propriétés au projet. Si nécessaire au niveau du projet, vous pouvez ajouter une nouvelle feuille de propriétés pour définir des valeurs spécifiques au projet.

> [!IMPORTANT]
> Un fichier .props par défaut ne participe pas au contrôle de code source car il n'est pas créé en tant qu'élément de projet. Vous pouvez ajouter manuellement le fichier comme élément de solution si vous souhaitez l'inclure dans le contrôle de code source.

#### <a name="to-create-a-property-sheet"></a>Pour créer une feuille de propriétés

1. Dans la barre de menus, choisissez **Affichage**, **Gestionnaire de propriétés**. Le **Gestionnaire de propriétés** s’ouvre.

2. Pour définir la portée de la feuille de propriétés, sélectionnez l'élément auquel elle s'applique. Il peut s'agir d'une configuration particulière ou d'une autre feuille de propriétés. Ouvrez le menu contextuel de cet élément, puis choisissez **Ajouter une nouvelle feuille de propriétés de projet**. Spécifiez un nom et un emplacement.

3. Dans le **Gestionnaire de propriétés**, ouvrez la nouvelle feuille de propriétés et définissez les propriétés à inclure.
