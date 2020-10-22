---
title: Naviguer dans le code C++ dans Visual Studio
description: Utilisez les différents outils dans Visual Studio pour naviguer dans votre codebase C++.
ms.date: 05/28/2019
ms.openlocfilehash: cc13326dee14e952c78e521344a6244249179cb8
ms.sourcegitcommit: 59b7c18703d1ffd66827db0e2eeece490d3d8789
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "90683492"
---
# <a name="navigate-c-code-in-visual-studio"></a>Naviguer dans le code C++ dans Visual Studio

Visual Studio fournit une suite d’outils qui vous permettent de naviguer dans votre codebase rapidement et efficacement.

## <a name="open-an-included-file"></a>Ouvrir un fichier inclus

Cliquez avec le bouton de droite sur une directive `#include`, puis sélectionnez **Atteindre le document**. Ou sélectionnez **F12** avec le curseur sur cette ligne pour ouvrir le fichier.

![C&#43;&#43; option de menu accéder au document](../ide/media/go-to-document.png "Atteindre le document")

## <a name="toggle-headercode-file"></a>Afficher ou masquer l’en-tête / le fichier de code

Vous pouvez basculer entre un fichier d’en-tête et son fichier source correspondant. Cliquez avec le bouton de droite n’importe où dans votre fichier, puis sélectionnez **Afficher ou masquer l'en-tête / le fichier de code**. Ou bien, vous pouvez également sélectionner **Ctrl+K**, **Ctrl+O**.

## <a name="go-to-definitiondeclaration"></a>Accéder à la définition/déclaration

Vous pouvez accéder à la définition d’un symbole de code en cliquant avec le bouton de droite dans l’éditeur et en sélectionnant **Atteindre la définition** ou en sélectionnant **F12**. Vous pouvez accéder à une déclaration de la même façon en cliquant avec le bouton de droite pour ouvrir le menu contextuel ou en sélectionnant **Ctrl+F12**.

![C&#43;&#43; accéder à la définition](../ide/media/go-to-def.png "Atteindre la définition")

## <a name="go-to"></a>Atteindre

**Atteindre** fait référence à un ensemble de fonctionnalités de navigation qui fournissent chacune un type de résultat spécifique basé sur des filtres que vous spécifiez.

Vous pouvez ouvrir **Atteindre** avec **Ctrl+,**. Cette action crée une zone de recherche au-dessus du document en cours de modification.

![C&#43;&#43; accéder à](../ide/media/go-to-cpp.png "Atteindre")

**Atteindre** inclut les filtres de recherche suivants :

- **Atteindre la ligne** (**CTRL + G**) : accède rapidement à une autre ligne dans le document actif.
- **Atteindre tout** (**CTRL +,**) ou (**Ctrl + T**) : les résultats de la recherche incluent tout ce qui suit.
- **Atteindre le fichier** (**CTRL 1, F**) : recherchez des fichiers dans votre solution.
- **Atteindre le type** (**CTRL 1, T**) : les résultats de la recherche sont les suivants :
  - Classes, structs et énumérations.
  - Interfaces et délégués (code managé uniquement).
- **Atteindre le membre** (**CTRL 1, M**) : les résultats de la recherche sont les suivants :
  - Variables globales et fonctions globales.
  - Variables membres de classe et fonctions membres.
  - Constantes.
  - Éléments d’énumération.
  - Propriétés et événements.
- **Atteindre le symbole** (**CTRL 1, S**) : les résultats de la recherche sont les suivants :
  - Résultats issus des recherches Atteindre les types et Atteindre les membres.
  - Toutes les autres constructions de langage C++, y compris les macros.

Quand vous appelez **Atteindre** avec **Ctrl +** pour la première fois, **Atteindre tout** est activé (aucun filtre n’est appliqué aux résultats de la recherche). Vous pouvez ensuite sélectionner le filtre que vous souhaitez en utilisant les boutons près de la zone de recherche. Vous pouvez appeler un filtre spécifique à l’aide de son raccourci clavier. Cette action ouvre la zone de recherche **Atteindre** avec ce filtre présélectionné. Tous les raccourcis clavier sont configurables.

Pour appliquer un filtre de texte, commencez votre requête de recherche par le caractère correspondant du filtre suivi d’un espace. (**Atteindre la ligne** peut éventuellement omettre l’espace.) Ces filtres de texte sont disponibles :

- Atteindre tout : (aucun filtre de texte)
- Atteindre un numéro de ligne spécifié : :
- Accéder au fichier : f
- Atteindre le type : t
- Atteindre le membre : m
- Atteindre le symbole : #

L’exemple suivant montre les résultats issus d’une opération *Atteindre les fichiers* utilisant le filtre « f » :

![Capture d’écran du menu atteindre les fichiers.](../ide/media/vs2017-go-to-results.png "Accéder au menu")

Pour afficher la liste des filtres de texte, tapez un caractère  ? suivi d’un espace. Vous pouvez également accéder aux commandes **Atteindre** avec le menu **Edition**. C’est une autre façon de mémoriser les principaux raccourcis clavier **Atteindre**.

![Capture d’écran du menu atteindre.](../ide/media/go-to-menu-cpp.png "Accéder au menu")

## <a name="find-or-find-in-files"></a>Rechercher ou Rechercher dans les fichiers

Vous pouvez exécuter une recherche de texte pour quoi que ce soit dans votre solution avec **Rechercher** ou (**Ctrl+F)** ou **Rechercher dans les fichiers** (**Ctrl+Maj+F**).

**Rechercher** peut être étendue à une sélection, au document actuel, à tous les documents ouverts, au projet actuel ou à l’ensemble de la solution. Vous pouvez utiliser des expressions régulières ainsi que du texte brut. En outre, la recherche met en évidence toutes les correspondances automatiquement dans l’IDE.

![Recherche de&#43;&#43; C](../ide/media/find-cpp.png "Rechercher")

La fonctionnalité **Rechercher dans les fichiers** est une version plus puissante de la fonctionnalité **Rechercher** qui affiche les résultats dans la fenêtre **Résultats de la recherche**. Vous pouvez, entre autres, effectuer une recherche dans des dépendances de code externes et filtrer par types de fichiers.

![Capture d’écran de la fenêtre Rechercher et remplacer montrant la page Rechercher dans les fichiers.](../ide/media/find-in-files-cpp.png "Rechercher dans les fichiers")

Vous pouvez organiser les résultats de **Rechercher dans les fichiers** dans deux fenêtres. Vous pouvez rassembler les résultats de plusieurs recherches. Sélectionnez un résultat pour accéder à l’emplacement concerné dans le fichier.

![Capture d’écran montrant un résultat de recherche Rechercher dans le fichier.](../ide/media/vs2017-find-in-files-results.png "Rechercher dans les fichiers")

Pour plus d’informations, consultez [Rechercher dans les fichiers](/visualstudio/ide/find-in-files) dans la documentation de Visual Studio.

## <a name="find-all-references"></a>Rechercher toutes les références

Pour rechercher toutes les utilisations d’un symbole dans votre codebase, placez le signe insertion dans ou juste après le symbole, puis cliquez avec le bouton de droite et sélectionnez **Rechercher toutes les références**. Vous pouvez filtrer, trier ou regrouper les résultats de différentes manières. Les résultats se remplissent de façon incrémentielle. Ils sont classés en tant que lectures ou écritures pour vous aider à voir ce que contient votre solution, par opposition aux en-têtes système ou aux autres bibliothèques.

![C&#43;&#43; Rechercher toutes les références](../ide/media/find-all-references-results-cpp.png "Rechercher toutes les références")

Vous regroupez les résultats en fonction des catégories suivantes :

- Projet, puis définition
- Définition uniquement
- Définition, puis projet
- Définition, puis chemin
- Définition, projet, puis chemin

#### <a name="filter-results"></a>Filtrer les résultats

Pour filtrer les résultats, placez le curseur sur une colonne, puis sélectionnez l’icône de filtre qui s’affiche. Vous pouvez filtrer les résultats de la première colonne pour masquer des éléments que vous ne souhaitez peut-être pas voir, tels que les références de chaîne et de commentaire.

![C&#43;&#43; Rechercher tous les filtres de références](../ide/media/find-all-references-filters-cpp.png "Rechercher tous les filtres de références")

- **Résultats confirmés**: références de code réelles au symbole recherché. Par exemple, la recherche d’une fonction membre appelée `Size` retourne toutes les références à `Size` qui correspondent à la portée de la classe définissant `Size`.

- **Résultats non confirmés**: ce filtre est désactivé par défaut, car il affiche les symboles dont le nom correspond, mais pas les références réelles au symbole que vous recherchez. Par exemple, si vous avez deux classes qui définissent chacune une fonction membre appelée `Size` et que vous exécutez une recherche de `Size` sur une référence à partir d’un objet de `Class1`, toutes les références à `Size` à partir de `Class2` apparaissent comme étant non confirmées.

- **Résultats non traités**: les opérations de **recherche de toutes les références** peuvent prendre du temps pour s’exécuter sur les codes base plus volumineux, de sorte que la liste des résultats affiche les résultats « non traités » ici. Les résultats non traités correspondent au nom du symbole faisant l’objet d’une recherche, mais qui n’ont pas encore été confirmés en tant que références de code réelles. Vous pouvez activer ce filtre pour obtenir des résultats plus rapidement. Soyez conscient que certains résultats peuvent ne pas correspondre à des références réelles.

#### <a name="sort-results"></a>Trier les résultats

Vous pouvez trier les résultats en fonction de n’importe quelle colonne en la sélectionnant. Vous pouvez passer de l’ordre croissant à l’ordre décroissant en sélectionnant la colonne à nouveau.

## <a name="navigation-bar"></a>Barre de navigation

Vous pouvez accéder à la définition d’un type dans un fichier ou à des membres de type, à l’aide de la **Barre de navigation** située au-dessus de la fenêtre de l’éditeur.

![Barre de navigation&#43;&#43; C](../ide/media/navbar-cpp.png "Barre de navigation")

## <a name="see-also"></a>Voir aussi

- [Lire et comprendre du code C++](read-and-understand-code-cpp.md)</br>
- [Modifier et refactoriser du code C++](read-and-understand-code-cpp.md)</br>
- [Collaborer avec Live Share pour C++](live-share-cpp.md)
