---
title: Définir vos C++ préférences de codage dans Visual Studio
ms.description: Customize C++ formatting, colors, layout, line numbers, menus and more in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: 90c9f39135b90a2c5015861a78dd8760b9a8aeed
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686886"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>Définir vos C++ préférences de codage dans Visual Studio

Vous pouvez rendre votre C++ expérience de codage plus pratique, plus productive et Pleasurable en personnalisant Visual Studio. Vous pouvez personnaliser les menus et les barres d’outils, organiser la disposition des fenêtres, définir des C++ thèmes de couleur, spécifier des règles de mise en forme, y compris plusieurs versions de ClangFormat, et créer des raccourcis clavier personnalisés. Vous pouvez synchroniser vos préférences sur plusieurs ordinateurs, et créer et stocker plusieurs ensembles de préférences et les partager avec des collègues. Vous pouvez installer des extensions à partir de la Visual Studio Marketplace qui fournissent un comportement personnalisé supplémentaire. La plupart de ces options sont documentées sous [personnaliser l’IDE de Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="arrange-window-layout"></a>Organiser la disposition des fenêtres

Dans la fenêtre Visual Studio, l’espace est divisé dans le menu principal, la barre d’outils, l’éditeur de code (ou la fenêtre de document) et les fenêtres outil (**Explorateur de solutions**, **liste d’erreurs**, etc.). Certaines fenêtres se chevauchent dans la même position. Par exemple, **Explorateur de solutions**, **affichage de classes**, **affichage des ressources**et **Explorateur du contrôle de code source** partagent tous la même position par défaut. Pour passer de l’un à l’autre, cliquez sur les onglets en bas du cadre. Pour que deux ou plusieurs de ces fenêtres soient visibles en même temps, il suffit de faire glisser l’une d’entre elles par sa barre de titre vers une nouvelle position. Vous pouvez l’ancrer à l’une des bordures de la fenêtre principale de Visual Studio, ou vous pouvez la rendre flottante. L’illustration suivante montre la fenêtre de **Team Explorer** en cours de glissement de sa position par défaut vers une nouvelle position ancrée sur le côté gauche de l’éditeur de code. La zone ombrée bleue indique l’emplacement où la fenêtre sera placée lorsque le bouton de la souris est relâché.

![Modification de la disposition des fenêtres](media/window-layout-move-team-explorer.png)

Dans la fenêtre de document, chaque fichier ouvert est contenu dans un cadre à onglets. Vous pouvez flotter ou verrouiller ces onglets comme des fenêtres outil. Pour plus d’informations, consultez [Personnalisation des dispositions de fenêtres dans Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Pour masquer toutes les fenêtres outil et agrandir la fenêtre de l’éditeur de code, appuyez sur **Alt** + **MAJ** + **entrée** pour activer/désactiver le *mode plein écran*.

## <a name="set-c-coding-styles-and-formatting"></a>Définir C++ les styles et la mise en forme du codage

Vous pouvez spécifier de nombreuses options de mise en forme du code, telles que la mise en retrait et les positions des accolades, en accédant à **Outils** > **options** > **éditeur de texte** > **C/C++**  > **mise en forme** (ou tapez **Appuyez sur CTRL + Q** et recherchez « mise en forme »). Vous pouvez également spécifier l’un des styles [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) (ou votre propre style ClangFormat personnalisé) :

![Options de ClangFormat](media/clang-format-ide.png)

Pour plus d’informations sur toutes les options de mise en forme, consultez [options, éditeur deC++texte, C/, mise en forme](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting).

## <a name="set-the-color-theme"></a>Définir le thème de couleur

Pour définir un arrière-plan clair ou sombre, tapez **CTRL + Q** et recherchez « thème de couleur ». Vous pouvez également y accéder via **outils** > **options** > **environnement** et choisir un **thème de couleur**:

![Thèmes de couleur](media/tools-options-color-theme.png)

L’illustration suivante montre le thème sombre :

![Thème foncé](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>Personnaliser la coloration du code

Dans Visual Studio 2019, vous pouvez choisir parmi trois modèles de *couleurs* prédéfinis qui spécifient comment les éléments de code sont colorés dans l’éditeur. Pour choisir un thème, accédez à **Outils** > **options** > **éditeur de texte**@no__t-**5 CC++/** @no__t-**8,** puis choisissez jeu de **couleurs**:

![C++Modèles de couleurs](media/color-schemes.png)

Dans le jeu de couleurs de **Visual Studio 2017** , la plupart des éléments de code sont simplement noirs. Dans le modèle de couleurs **amélioré** , les fonctions, les variables locales, les macros et les autres éléments sont colorés. Dans le **Enhanced (globales et Les membres)**  le schéma, les fonctions globales et les variables sont coloriées pour être contrastées avec les membres de classe. Le mode par défaut est **amélioré** et ressemble à ceci :

![Modèle de couleurs amélioré](media/color-scheme-enhanced.png)

Quel que soit le thème ou le modèle de couleurs actif, vous pouvez personnaliser la police et les couleurs des éléments de code individuels en accédant à **outils** > **options** > **environnement** > **polices et couleurs** (ou tapez  **Appuyez sur CTRL + Q** et recherchez « polices ». Faites défiler la liste des éléments d’affichage jusqu' C++ à ce que les options suivantes s’affichent :

![C++options de police et de couleur](media/tools-options-cpp-colors.png)

Les couleurs que vous définissez ici remplacent les valeurs définies pour les jeux de couleurs. Vous devez rétablir la couleur **par défaut** si vous l’avez modifiée, mais que vous souhaitez utiliser les couleurs par défaut pour le modèle de couleurs.

## <a name="customize-the-toolbars"></a>Personnaliser les barres d’outils

Les barres d’outils offrent un moyen pratique d’émettre des commandes avec un simple clic de souris, plutôt que d’utiliser les menus ou les raccourcis clavier. Visual Studio comprend un ensemble standard de barres d’outils. Pour le C++ développement standard, les barres d’outils les plus utiles sont probablement standard, éditeur de texte, générer, déboguer, contrôle de code source et éventuellement comparer des fichiers. Pour le développement Windows, l’éditeur de boîtes de dialogue et l’éditeur d’images sont utiles pour disposer les boîtes de dialogue et les icônes de modification.

Placez le curseur sur les icônes de la barre d’outils pour afficher la commande qu’il représente :

![Barre d’outils Info Express](media/toolbar-mouse-hover.png)

Vous pouvez ajouter ou supprimer des commandes ou créer une barre d’outils personnalisée en cliquant sur la flèche vers le bas. Pour déplacer la barre d’outils vers un nouvel emplacement, faites-la glisser sur la barre en pointillés à gauche :

![Personnaliser ou déplacer une barre d’outils](media/toolbar-move-edit.png).

Pour plus d'informations, voir [Procédure : Personnaliser les menus et les barres d’outils dans Visual Studio @ no__t-0.

## <a name="show-or-hide-line-numbers"></a>Afficher ou masquer les numéros de ligne

Pour spécifier si les numéros de ligne s’affichent à gauche des fenêtres de l’éditeur, recherchez et cochez ou décochez les **numéros de ligne**:

![Numéros de ligne](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>Créer des raccourcis clavier

Toutes les commandes dans Visual Studio peuvent être créées avec des raccourcis clavier à l’aide de différentes combinaisons de touches avec les touches Ctrl, Alt et Maj. Vous pouvez créer vos propres raccourcis en accédant à **outils** > **options** > **environnement** > **clavier** (ou appuyez sur **CTRL + Q** et recherchez « raccourcis »). Pour plus d’informations, consultez [identifier et personnaliser les raccourcis clavier dans Visual Studio](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).
