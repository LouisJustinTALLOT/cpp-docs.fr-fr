---
title: Définir vos C++ préférences de codage dans Visual Studio
ms.description: Customize C++ formatting, colors, layout, line numbers, and menus in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: f1d222dc38720ea897cfbf2fb9fa0dd2727e7720
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816561"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>Définir vos C++ préférences de codage dans Visual Studio

Vous pouvez rendre votre C++ expérience de codage plus pratique, plus productive et Pleasurable en personnalisant Visual Studio. Vous pouvez :

- Personnaliser les menus et les barres d’outils.
- Réorganisez la disposition de fenêtre.
- Définir des thèmes de couleur.
- Spécifiez C++ les règles de mise en forme, y compris plusieurs styles de ClangFormat.
- Créer des raccourcis clavier personnalisés.

Vous pouvez synchroniser vos préférences sur plusieurs ordinateurs, et créer et stocker plusieurs ensembles de préférences et les partager avec des collègues. Vous pouvez installer des extensions à partir de la Visual Studio Marketplace, en vous donnant des options supplémentaires pour personnaliser le comportement. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="arrange-window-layout"></a>Organiser la disposition des fenêtres

Dans la fenêtre Visual Studio, l’espace est divisé dans le menu principal, la barre d’outils, l’éditeur de code (ou la fenêtre de document) et les fenêtres outil (telles que Explorateur de solutions et Liste d’erreurs). Certaines fenêtres se chevauchent dans la même position. Par exemple, Explorateur de solutions, Affichage de classes, Affichage des ressources et Explorateur du contrôle de code source partagent tous la même position par défaut. Vous pouvez basculer entre ces deux onglets en sélectionnant les onglets en bas du cadre. Pour que deux ou plusieurs de ces fenêtres soient visibles en même temps, il suffit de faire glisser l’une d’entre elles par sa barre de titre vers une nouvelle position. Vous pouvez l’ancrer à l’une des bordures de la fenêtre principale de Visual Studio, ou vous pouvez la rendre flottante.

La capture d’écran suivante montre la fenêtre de **Team Explorer** déplacée de sa position par défaut vers une nouvelle position ancrée sur le côté gauche de l’éditeur de code. La zone ombrée bleue indique l’emplacement où la fenêtre sera placée lorsque le bouton de la souris est relâché.

![Capture d’écran de la fenêtre de Team Explorer Visual Studio, avec modification de la disposition mise en surbrillance](media/window-layout-move-team-explorer.png)

Dans la fenêtre de document, chaque fichier ouvert est contenu dans un cadre à onglets. Vous pouvez flotter ou verrouiller ces onglets, tout comme les fenêtres outil. Pour plus d’informations, consultez [Personnalisation des dispositions de fenêtres dans Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Pour masquer toutes les fenêtres outil et agrandir la fenêtre de l’éditeur de code, appuyez sur **Alt** + **MAJ** + **entrée** pour activer/désactiver le *mode plein écran*.

## <a name="set-c-coding-styles-and-formatting"></a>Définir C++ les styles et la mise en forme du codage

Vous pouvez spécifier de nombreuses options de mise en forme du code, telles que la mise en retrait et les positions des accolades. Pour ce faire, accédez à **Outils** > **options** > **éditeur de texte**@no__t-**5 CC++/**  > **mise en forme** (ou tapez **CTRL + Q** et recherchez « mise en forme »). Vous pouvez également spécifier l’un des styles [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) (ou votre propre style ClangFormat personnalisé).

![Capture d’écran des options ClangFormat](media/clang-format-ide.png)

Pour plus d’informations sur toutes les options de mise en forme, consultez [options, éditeur deC++texte, C/, mise en forme](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting).

## <a name="set-the-color-theme"></a>Définir le thème de couleur

Pour définir un arrière-plan clair ou sombre, tapez **CTRL + Q** et recherchez « thème de couleur ». Vous pouvez également les trouver en accédant à **outils** > **options** > **environnement**, puis en choisissant thème de **couleur**.

![Capture d’écran des thèmes de couleur](media/tools-options-color-theme.png)

Par exemple, voici le thème sombre :

![Capture d’écran de Visual Studio avec le thème de couleur sombre](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>Personnaliser la coloration du code

Dans Visual Studio 2019, vous pouvez choisir parmi trois *modèles de couleurs*prédéfinis. Ils spécifient comment les éléments de code sont coloriés dans l’éditeur. Pour choisir un thème, accédez à **Outils** > **options** > **éditeur de texte**@no__t-**5 CC++/** @no__t-**8,** puis choisissez **jeu de couleurs**:

![Capture d' C++ écran des options de jeu de couleurs, avec mise en surbrillance améliorée](media/color-schemes.png)

Dans le modèle de couleurs appelé **Visual Studio 2017**, la plupart des éléments de code sont simplement noirs. Dans le modèle de couleurs **amélioré** , les fonctions, les variables locales, les macros et les autres éléments sont colorés. Dans le **Enhanced (globales et Les membres)**  le schéma, les fonctions globales et les variables sont coloriées pour être contrastées avec les membres de classe. Le mode par défaut est **amélioré**et ressemble à ceci :

![Capture d’écran du modèle de couleurs amélioré](media/color-scheme-enhanced.png)

Quel que soit le thème ou le modèle de couleurs actif, vous pouvez personnaliser la police et les couleurs des éléments de code individuels. Pour ce faire, accédez à **outils** > **options** > **environnement** > **polices et couleurs** (ou tapez **CTRL + Q** et recherchez « polices »). Faites défiler la liste des éléments affichés jusqu’à C++ ce que les options s’affichent.

![Capture d' C++ écran des options de police et de couleur](media/tools-options-cpp-colors.png)

Les couleurs que vous définissez ici remplacent les valeurs définies pour les jeux de couleurs. Si vous souhaitez revenir aux couleurs par défaut du modèle de couleurs, redéfinissez une couleur sur **par défaut**.

## <a name="customize-the-toolbars"></a>Personnaliser les barres d’outils

Les barres d’outils offrent un moyen pratique d’émettre des commandes d’un simple clic, plutôt que d’utiliser les menus ou les raccourcis clavier. Visual Studio comprend un ensemble standard de barres d’outils. Pour le C++ développement standard, les barres d’outils les plus utiles sont probablement standard, l’éditeur de texte, la génération, le débogage, le contrôle de code source et les fichiers de comparaison. Pour le développement Windows, l’éditeur de boîtes de dialogue et l’éditeur d’images sont utiles pour disposer les boîtes de dialogue et les icônes de modification.

Placez le curseur sur les icônes de la barre d’outils pour afficher la commande qu’il représente :

![Capture d’écran d’icônes de barre d’outils, avec des informations de commande disponibles au survol](media/toolbar-mouse-hover.png)

Vous pouvez ajouter ou supprimer des commandes, ou créer une barre d’outils personnalisée, en sélectionnant la flèche vers le bas. Pour déplacer la barre d’outils vers un nouvel emplacement, faites-la glisser sur la barre en pointillés à gauche.

![Capture d’écran de la barre d’outils avec une flèche vers le bas et une barre en pointillé en surbrillance](media/toolbar-move-edit.png).

Pour plus d'informations, voir [Procédure : Personnaliser les menus et les barres d’outils dans Visual Studio @ no__t-0.

## <a name="show-or-hide-line-numbers"></a>Afficher ou masquer les numéros de ligne

Vous pouvez spécifier si les numéros de ligne s’affichent à gauche des fenêtres de l’éditeur. Dans **options**, sous **C/C++** , sélectionnez **général**. Dans la section **paramètres** , sélectionnez ou effacez les **numéros de ligne**, en fonction de vos préférences.

![Capture d’écran des options générales, avec les numéros de ligne mis en surbrillance](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>Créer des raccourcis clavier

De nombreuses commandes dans Visual Studio ont des *raccourcis clavier*, des combinaisons de touches avec les touches Ctrl, Alt et Maj. Vous pouvez modifier ces raccourcis clavier ou en créer d’autres dans Visual Studio. Accédez à **outils** > **options** > **environnement** > **clavier** (ou **Appuyez sur CTRL + Q** et recherchez « raccourcis »). Pour plus d’informations, consultez [identifier et personnaliser les raccourcis clavier dans Visual Studio](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).
