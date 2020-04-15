---
title: Partager ou réutiliser les paramètres du projet Visual Studio - C
ms.date: 07/17/2019
helpviewer_keywords:
- project properties [C++], reusable
ms.openlocfilehash: bcf54be0531c7150c1506eb6f5dda2b5bc95161f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328690"
---
# <a name="share-or-reuse-visual-studio-project-settings"></a>Partager ou réutiliser les paramètres de projet Visual Studio

Pour créer un groupe personnalisé de paramètres que vous pouvez partager avec d’autres ou réutiliser dans plusieurs projets, utilisez **Property Manager** pour créer une feuille *de propriété* (.fichiers accessoires) pour stocker les paramètres de chaque type de projet que vous souhaitez être en mesure de réutiliser ou de partager avec d’autres. L’utilisation de feuilles de propriété est beaucoup moins sujette aux erreurs que d’autres façons de créer des paramètres « globaux ».

> [!IMPORTANT]
> **Les fichiers .user et pourquoi ils sont problématiques**
>
> Les versions précédentes de Visual Studio utilisaient des feuilles de propriétés globales qui avaient une extension de nom de fichier .user et se trouvaient dans le dossier \<profil_utilisateur>\AppData\Local\Microsoft\MSBuild\v4.0\. Nous ne recommandons plus l'utilisation de ces fichiers, car ils définissent des propriétés pour les configurations de projet sur la base de chaque utilisateur et de chaque ordinateur. Ces paramètres « globaux » peuvent perturber les builds, surtout lorsque vous ciblez plusieurs plateformes sur votre ordinateur de build. Par exemple, si vous avez un projet MFC et un projet Windows Phone, les propriétés .user seraient non valides pour l'un d'eux. Les feuilles de propriétés réutilisables sont plus flexibles et plus fiables.
>
> Bien que les fichiers .user soient toujours installés par Visual Studio et participent à l'héritage des propriétés, ils sont vides par défaut. Une bonne pratique est de supprimer la référence correspondante dans le **Gestionnaire de propriétés** pour faire en sorte que les projets fonctionnent indépendamment des paramètres selon l’utilisateur et l’ordinateur. De cette façon, vous garantissez un comportement approprié dans un environnement de contrôle de code source (SCC).

Pour afficher **Property Manager**, sur la barre de menu, choisissez **View** > **Property Manager** ou **View** > **Other Windows** > **Property Manager**, selon vos paramètres.

Si vous avez un ensemble commun, fréquemment utilisé de propriétés que vous souhaitez appliquer à plusieurs projets, vous pouvez utiliser **gestionnaire de propriété** pour les capturer dans un fichier de feuille de *propriété* réutilisable, qui par convention a une extension de nom de fichier .props. Vous pouvez appliquer la feuille (ou les feuilles) à de nouveaux projets afin de ne pas avoir à définir intégralement ses propriétés.

![Menu contextuel de gestionnaire de propriétés](media/sharingnew.png "PartagerNew")

Sous chaque nœud de configuration, vous voyez des nœuds pour chaque feuille de propriétés qui s’applique à cette configuration. Le système ajoute des feuilles de propriétés qui définissent les valeurs selon les options que vous choisissez dans l’Assistant Application quand vous créez le projet. Cliquez avec le bouton droit sur n’importe quel nœud et choisissez Propriétés pour voir les propriétés qui s’appliquent à ce nœud. Toutes les feuilles de propriétés sont importées automatiquement dans la feuille de propriétés « master » du projet (ms.cpp.props) et sont évaluées par ordre d’apparition dans le Gestionnaire de propriétés. Vous pouvez les déplacer pour changer l’ordre d’évaluation. Les feuilles de propriétés qui sont évaluées par la suite remplacent les valeurs dans les feuilles précédemment évaluées. Voir [l’héritage de propriété du projet](project-property-inheritance.md) pour plus d’informations sur l’ordre d’évaluation dans le fichier .vcxproj, les fichiers .props et .targets, les variables de l’environnement et la ligne de commande.

Si vous choisissez **Ajouter la feuille de propriété du nouveau projet** et sélectionnez, par exemple, la feuille de propriété MyProps.props, une boîte de dialogue de page de propriété apparaît. Remarquez qu'elle s'applique à la feuille de propriétés MyProps ; toutes les modifications que vous apportez sont écrites dans la feuille, et non dans le fichier projet (.vcxproj).

Les propriétés dans une feuille de propriétés sont remplacées si la même propriété est définie directement dans le fichier .vcxproj.

Vous pouvez importer une feuille de propriétés aussi souvent que nécessaire. Plusieurs projets d'une solution peuvent hériter des paramètres de la feuille de propriétés et un projet peut avoir plusieurs feuilles. Une feuille de propriétés peut hériter elle-même des paramètres d'une autre feuille de propriétés.

Vous pouvez également créer une feuille de propriétés pour plusieurs configurations. Pour cela, créez une feuille de propriétés pour chaque configuration, ouvrez le menu contextuel associé à l’une d’elles, choisissez **Ajouter une feuille de propriétés existante**, puis ajoutez les autres feuilles. Toutefois, si vous utilisez une feuille de propriété commune, sachez que lorsque vous définissez une propriété, il est réglé pour toutes les configurations que la feuille s’applique à, et que l’IDE ne montre pas quels projets ou autres feuilles de propriété héritent d’une feuille de propriété donnée.

Dans les grandes solutions qui auront de nombreux projets, il peut être utile de créer une feuille de propriétés au niveau de la solution. Lorsque vous ajoutez un projet à la solution, utilisez **le gestionnaire immobilier** pour ajouter cette feuille de propriété au projet. Si nécessaire au niveau du projet, vous pouvez ajouter une nouvelle feuille de propriétés pour définir des valeurs spécifiques au projet.

> [!IMPORTANT]
> Un fichier .props par défaut ne participe pas au contrôle source car il n’est pas créé comme élément de projet. Vous pouvez ajouter manuellement le fichier comme élément de solution si vous souhaitez l'inclure dans le contrôle de code source.

#### <a name="to-create-a-property-sheet"></a>Pour créer une feuille de propriétés

1. Sur la barre de menu, choisissez **Voir** > **gestionnaire de propriété** ou **Afficher** > **d’autres Windows** > Property**Manager**. Le **Gestionnaire de propriétés** s’ouvre.

2. Pour définir la portée de la feuille de propriétés, sélectionnez l'élément auquel elle s'applique. Il peut s'agir d'une configuration particulière ou d'une autre feuille de propriétés. Ouvrez le menu contextuel de cet élément, puis choisissez **Ajouter une nouvelle feuille de propriétés de projet**. Spécifiez un nom et un emplacement.

3. Dans **Le gestionnaire de propriété,** ouvrez la nouvelle feuille de propriété et définissez ensuite les propriétés que vous voulez inclure.
