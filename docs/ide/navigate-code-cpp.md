---
title: Naviguer dans le code C++ dans Visual Studio
description: Utilisez les différents outils dans Visual Studio pour naviguer dans votre base de code C++.
ms.date: 05/28/2019
ms.openlocfilehash: 5f01307cc82fb1e61ba6fd0c922ea376279fba8b
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66742035"
---
# <a name="navigate-c-code-in-visual-studio"></a>Naviguer dans le code C++ dans Visual Studio

Visual Studio fournit une suite d’outils qui vous permettent de naviguer dans votre base de code rapidement et efficacement.

## <a name="open-an-included-file"></a>Ouvrir un fichier inclus

Pour ouvrir un fichier, cliquez avec le bouton droit sur une directive `#include` et choisissez **Accéder au document**, ou appuyez sur **F12** après avoir placé le curseur dans la ligne du fichier concerné.

![Option de menu Accéder au document, C&#43;&#43;](../ide/media/go-to-document.png "Accéder au document")

## <a name="toggle-headercode-file"></a>Afficher ou masquer l’en-tête / le fichier de code

Vous pouvez basculer entre un fichier d’en-tête et son fichier source correspondant en cliquant avec le bouton droit n’importe où dans votre fichier et en choisissant **Afficher ou masquer l’en-tête / le fichier de code** ou bien en appuyant sur **Ctrl+K, Ctrl+O**.

## <a name="go-to-definitiondeclaration"></a>Accéder à la définition/déclaration

Vous pouvez accéder à la définition d’un symbole de code en cliquant avec le bouton droit dans l’éditeur et en choisissant **Accéder à la définition**, ou bien en appuyant sur **F12**. Vous pouvez accéder à une déclaration de la même façon dans le menu contextuel, ou en appuyant sur **Ctrl+F12**.

![Accéder à la définition, C&#43;&#43;](../ide/media/go-to-def.png "Accéder à la définition")

## <a name="go-to"></a>Atteindre

**Atteindre** fait référence à un ensemble de fonctionnalités de navigation qui fournissent chacune un type de résultat spécifique basé sur des filtres que vous spécifiez. 

Vous pouvez ouvrir **Atteindre** avec **Ctrl+,** . Cette action crée une zone de recherche au-dessus du document en cours de modification.

![Atteindre, C&#43;&#43;](../ide/media/go-to-cpp.png "Atteindre")

**Atteindre** inclut les filtres de recherche suivants :

- **Atteindre la ligne (Ctrl+G)**  : passer rapidement à une autre ligne dans votre document actuel
- **Atteindre tout (Ctrl+,)** ou **(Ctrl+T)**  : les résultats de la recherche incluent tout ce qui suit
- **Accéder au fichier (Ctrl 1, F)**  : rechercher des fichiers dans votre solution
- **Atteindre le type (Ctrl 1, T)**  : les résultats de la recherche incluent :
  - Classes, structs, énumérations
  - Interfaces et délégués (code managé uniquement)
- **Atteindre le membre (Ctrl 1, M)**  : les résultats de la recherche incluent :
  - Variables globales et fonctions globales
  - Fonctions membres et variables membres de classe
  - Constantes
  - Éléments d’énumération
  - Propriétés et événements
- **Atteindre le symbole (Ctrl 1, S)**  : les résultats de la recherche incluent :
  - Résultats issus des recherches Atteindre le type et Atteindre le membre
  - Toutes les autres constructions de langage C++, y compris les macros

Quand vous appelez **Atteindre** avec **Ctrl +** pour la première fois, **Atteindre tout** est activé (aucun filtre n’est appliqué aux résultats de la recherche). Vous pouvez ensuite sélectionner le filtre souhaité en utilisant les boutons situés près de la zone de recherche. Vous pouvez appeler un filtre spécifique à l’aide de son raccourci clavier. Cette action ouvre la zone de recherche **Atteindre** avec ce filtre présélectionné. Tous les raccourcis clavier sont configurables.

Pour appliquer un filtre de texte, démarrez votre requête de recherche avec le caractère correspondant du filtre suivi d’un espace. (**Atteindre la ligne** peut éventuellement omettre l’espace.) Voici les filtres de texte disponibles :

- Atteindre tout : (aucun filtre de texte)
- Atteindre un numéro de ligne spécifié : :
- Accéder au fichier : f
- Atteindre le type : t
- Atteindre le membre : m
- Atteindre le symbole : #

L’exemple suivant montre les résultats issus d’une opération *Accéder aux fichiers* utilisant le filtre « f » :

![Zone de recherche, C&#43;&#43;](../ide/media/vs2017-go-to-results.png "Zone de recherche")

Pour afficher la liste des filtres de texte, tapez un caractère  ? suivi d’un espace. Vous pouvez également accéder aux commandes **Atteindre** avec le menu **Edition**. C’est une autre façon de mémoriser les principaux raccourcis clavier Atteindre.

![Menu Atteindre, C&#43;&#43;](../ide/media/go-to-menu-cpp.png "Menu Atteindre")

## <a name="find--find-in-files"></a>Rechercher/Rechercher dans les fichiers

Vous pouvez exécuter une recherche de texte pour quoi que ce soit dans votre solution avec **Rechercher (Ctrl+F)** ou **Rechercher dans les fichiers (Ctrl+Maj+F)** .

La fonctionnalité Rechercher peut être limitée à une sélection, au document actuel, à tous les documents ouverts, au projet actuel ou à l’ensemble de la solution. Vous pouvez utiliser des expressions régulières ainsi que du texte brut. En outre, la recherche met en évidence toutes les correspondances automatiquement dans l’IDE.

![Rechercher, C&#43;&#43;](../ide/media/find-cpp.png "Rechercher")

La fonctionnalité **Rechercher dans les fichiers** est une version plus puissante de la fonctionnalité **Rechercher** qui affiche les résultats dans la fenêtre **Résultats de la recherche**. Vous pouvez, entre autres, effectuer une recherche dans des dépendances de code externes et filtrer par types de fichiers. 

![Rechercher dans les fichiers, C&#43;&#43;](../ide/media/find-in-files-cpp.png "Rechercher dans les fichiers")

Vous pouvez organiser les résultats de **Rechercher dans les fichiers** dans deux fenêtres. Vous pouvez rassembler les résultats de plusieurs recherches. Cliquez sur un résultat pour accéder à l’emplacement concerné dans le fichier.

![Rechercher dans les fichiers, C&#43;&#43](../ide/media/vs2017-find-in-files-results.png "Rechercher dans les fichiers")

Pour plus d’informations, consultez [Rechercher dans les fichiers](/visualstudio/ide/find-in-files) dans la documentation de Visual Studio.

## <a name="find-all-references"></a>Rechercher toutes les références

Pour rechercher toutes les utilisations d’un symbole dans votre base de code, placez le signe insertion dans ou juste après le symbole, puis cliquez avec le bouton droit et choisissez **Rechercher toutes les références**. Vous pouvez filtrer, trier ou regrouper les résultats de différentes manières. Les résultats se remplissent de façon incrémentielle. Ils sont classés en tant que lectures ou écritures pour vous aider à voir ce que contient votre solution, par opposition aux en-têtes système ou autres bibliothèques.

![Rechercher toutes les références, C&#43;&#43;](../ide/media/find-all-references-results-cpp.png "Rechercher toutes les références")

Vous regroupez les résultats en fonction des catégories suivantes :

- Projet, puis définition
- Définition uniquement
- Définition, puis projet
- Définition, puis chemin
- Définition, projet, puis chemin

 #### <a name="filter-results"></a>Filtrer les résultats

Pour filtrer les résultats, placez le curseur sur une colonne, puis cliquez sur l’icône de filtre qui s’affiche. Vous pouvez filtrer les résultats de la première colonne pour masquer des éléments que vous ne souhaitez peut-être pas voir, tels que les références de chaîne et de commentaire.

![Filtres pour Rechercher toutes les références, C&#43;&#43;](../ide/media/find-all-references-filters-cpp.png "Filtres pour Rechercher toutes les références")

- **Résultats confirmés** : références de code réelles au symbole faisant l’objet d’une recherche. Par exemple, la recherche d’une fonction membre appelée `Size` retourne toutes les références à `Size` qui correspondent à la portée de la classe définissant `Size`.

- **Résultats non confirmés** : ce filtre est désactivé par défaut, car il affiche les symboles dont le nom correspond, mais qui ne sont pas des références réelles au symbole que vous recherchez. Par exemple, si vous avez deux classes qui définissent chacune une fonction membre appelée `Size` et que vous exécutez une recherche de `Size` sur une référence à partir d’un objet de `Class1`, toutes les références à `Size` à partir de `Class2` apparaissent comme étant non confirmées.

- **Résultats non traités** : Les opérations **Rechercher toutes les références** peuvent prendre un certain temps sur les codes base plus grands ; ainsi, la liste des résultats affiche les résultats « non traités » ici. Les résultats non traités correspondent au nom du symbole faisant l’objet d’une recherche, mais n’ont pas encore été confirmés en tant que références de code réelles. Vous pouvez activer ce filtre pour obtenir des résultats plus rapidement. Soyez conscient que certains résultats peuvent ne pas correspondre à des références réelles.

 #### <a name="sort-results"></a>Trier les résultats

Vous pouvez trier les résultats en fonction de n’importe quelle colonne en cliquant sur celle-ci. Vous pouvez passer de l’ordre croissant à l’ordre décroissant, et vice versa, en recliquant sur la colonne.

## <a name="navigation-bar"></a>Barre de navigation

Vous pouvez accéder à la définition d’un type dans un fichier, ou à des membres de type, à l’aide de la **Barre de Navigation** située au-dessus de la fenêtre de l’éditeur.

![Barre de navigation, C&#43;&#43;](../ide/media/navbar-cpp.png "Barre de navigation")

## <a name="see-also"></a>Voir aussi

[Lire et comprendre du code C++](read-and-understand-code-cpp.md)</br>
[Modifier et refactoriser du code C++](read-and-understand-code-cpp.md)</br>
[Collaborer avec Live Share pour C++](live-share-cpp.md)