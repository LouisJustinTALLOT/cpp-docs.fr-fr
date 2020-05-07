---
title: Partager ou réutiliser des paramètres de projet Visual Studio-C++
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

Pour créer un groupe de paramètres personnalisé que vous pouvez partager avec d’autres personnes ou réutiliser dans plusieurs projets, utilisez **Gestionnaire de propriétés** pour créer une *feuille de propriétés* (fichier. props) afin de stocker les paramètres pour chaque type de projet que vous souhaitez pouvoir réutiliser ou partager avec d’autres utilisateurs. L’utilisation des feuilles de propriétés est beaucoup moins sujette aux erreurs que d’autres façons de créer des paramètres « globaux ».

> [!IMPORTANT]
> **Les fichiers .user et pourquoi ils sont problématiques**
>
> Les versions précédentes de Visual Studio utilisaient des feuilles de propriétés globales qui avaient une extension de nom de fichier .user et se trouvaient dans le dossier \<profil_utilisateur>\AppData\Local\Microsoft\MSBuild\v4.0\. Nous ne recommandons plus l'utilisation de ces fichiers, car ils définissent des propriétés pour les configurations de projet sur la base de chaque utilisateur et de chaque ordinateur. Ces paramètres « globaux » peuvent perturber les builds, surtout lorsque vous ciblez plusieurs plateformes sur votre ordinateur de build. Par exemple, si vous avez un projet MFC et un projet Windows Phone, les propriétés .user seraient non valides pour l'un d'eux. Les feuilles de propriétés réutilisables sont plus flexibles et plus fiables.
>
> Bien que les fichiers .user soient toujours installés par Visual Studio et participent à l'héritage des propriétés, ils sont vides par défaut. Une bonne pratique est de supprimer la référence correspondante dans le **Gestionnaire de propriétés** pour faire en sorte que les projets fonctionnent indépendamment des paramètres selon l’utilisateur et l’ordinateur. De cette façon, vous garantissez un comportement approprié dans un environnement de contrôle de code source (SCC).

Pour afficher **Gestionnaire de propriétés**, dans la barre de menus, choisissez **Afficher** > les**Gestionnaire de propriétés** ou **Afficher** > **les autres** > **Gestionnaire de propriétés**Windows, en fonction de vos paramètres.

Si vous avez un ensemble commun de propriétés fréquemment utilisées que vous souhaitez appliquer à plusieurs projets, vous pouvez utiliser **Gestionnaire de propriétés** pour les capturer dans un fichier de feuille de *Propriétés* réutilisable, qui par Convention a une extension de nom de fichier. props. Vous pouvez appliquer la feuille (ou les feuilles) à de nouveaux projets afin de ne pas avoir à définir intégralement ses propriétés.

![Menu contextuel de gestionnaire de propriétés](media/sharingnew.png "SharingNew")

Sous chaque nœud de configuration, vous voyez des nœuds pour chaque feuille de propriétés qui s’applique à cette configuration. Le système ajoute des feuilles de propriétés qui définissent les valeurs selon les options que vous choisissez dans l’Assistant Application quand vous créez le projet. Cliquez avec le bouton droit sur n’importe quel nœud et choisissez Propriétés pour voir les propriétés qui s’appliquent à ce nœud. Toutes les feuilles de propriétés sont importées automatiquement dans la feuille de propriétés « master » du projet (ms.cpp.props) et sont évaluées par ordre d’apparition dans le Gestionnaire de propriétés. Vous pouvez les déplacer pour changer l’ordre d’évaluation. Les feuilles de propriétés qui sont évaluées par la suite remplacent les valeurs dans les feuilles précédemment évaluées. Consultez [héritage des propriétés de projet](project-property-inheritance.md) pour plus d’informations sur l’ordre d’évaluation dans le fichier. vcxproj, les fichiers. props et. targets, les variables d’environnement et la ligne de commande.

Si vous choisissez **Ajouter une nouvelle feuille de propriétés de projet** , puis sélectionnez, par exemple, la feuille de propriétés MyProps. props, une boîte de dialogue page de propriétés s’affiche. Remarquez qu'elle s'applique à la feuille de propriétés MyProps ; toutes les modifications que vous apportez sont écrites dans la feuille, et non dans le fichier projet (.vcxproj).

Les propriétés dans une feuille de propriétés sont remplacées si la même propriété est définie directement dans le fichier .vcxproj.

Vous pouvez importer une feuille de propriétés aussi souvent que nécessaire. Plusieurs projets d'une solution peuvent hériter des paramètres de la feuille de propriétés et un projet peut avoir plusieurs feuilles. Une feuille de propriétés peut hériter elle-même des paramètres d'une autre feuille de propriétés.

Vous pouvez également créer une feuille de propriétés pour plusieurs configurations. Pour cela, créez une feuille de propriétés pour chaque configuration, ouvrez le menu contextuel associé à l’une d’elles, choisissez **Ajouter une feuille de propriétés existante**, puis ajoutez les autres feuilles. Toutefois, si vous utilisez une feuille de propriétés commune, sachez que lorsque vous définissez une propriété, elle est définie pour toutes les configurations auxquelles la feuille s’applique et l’IDE n’indique pas quels projets ou autres feuilles de propriétés héritent d’une feuille de propriétés donnée.

Dans les grandes solutions qui auront de nombreux projets, il peut être utile de créer une feuille de propriétés au niveau de la solution. Lorsque vous ajoutez un projet à la solution, utilisez **Gestionnaire de propriétés** pour ajouter cette feuille de propriétés au projet. Si nécessaire au niveau du projet, vous pouvez ajouter une nouvelle feuille de propriétés pour définir des valeurs spécifiques au projet.

> [!IMPORTANT]
> Un fichier. props par défaut ne participe pas au contrôle de code source, car il n’est pas créé en tant qu’élément de projet. Vous pouvez ajouter manuellement le fichier comme élément de solution si vous souhaitez l'inclure dans le contrôle de code source.

#### <a name="to-create-a-property-sheet"></a>Pour créer une feuille de propriétés

1. Dans la barre de menus, choisissez **Afficher** > **Gestionnaire de propriétés** ou **Afficher** > d'**autres** > **Gestionnaire de propriétés**Windows. Le **Gestionnaire de propriétés** s’ouvre.

2. Pour définir la portée de la feuille de propriétés, sélectionnez l'élément auquel elle s'applique. Il peut s'agir d'une configuration particulière ou d'une autre feuille de propriétés. Ouvrez le menu contextuel de cet élément, puis choisissez **Ajouter une nouvelle feuille de propriétés de projet**. Spécifiez un nom et un emplacement.

3. Dans **Gestionnaire de propriétés**, ouvrez la nouvelle feuille de propriétés, puis définissez les propriétés que vous souhaitez inclure.
