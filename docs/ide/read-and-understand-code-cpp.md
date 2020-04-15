---
title: Lire et comprendre du code C++ dans Visual Studio
description: Utilisez l’éditeur de code C++ dans Visual Studio pour mettre en forme et comprendre votre code.
ms.date: 05/28/2019
ms.openlocfilehash: 9ed0a20fb73e4cc976392bc5e5f698f9658a0b48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377300"
---
# <a name="read-and-understand-c-code-in-visual-studio"></a>Lire et comprendre du code C++ dans Visual Studio

L’éditeur de code C++ et l’IDE Visual Studio vous aident de nombreuses façons quand vous développez. Certains sont propres à C++, alors que d'autres sont quasiment identiques pour tous les langages Visual Studio. Pour plus d’informations sur les fonctionnalités partagées, consultez [Écriture de code dans l’éditeur de code et de texte](/visualstudio/ide/writing-code-in-the-code-and-text-editor).  

## <a name="colorization"></a>Coloration

Visual Studio colore les éléments de la syntaxe pour différencier les types de symboles tels que les mots clés du langage, les noms de type, les noms de variable, les paramètres de fonction et les littéraux de chaîne.

![Colorisation de code](../ide/media/code-outline-colorization.png "Colorisation de CMD")

Le code non utilisé (par exemple, le code sous une ligne #if 0) a une couleur estompée.

![Code inactif](../ide/media/inactive-code-cpp.png "Code inactif CMD")

Vous pouvez personnaliser les couleurs en tapant « Polices » dans **Lancement rapide**, puis en choisissant **Polices et couleurs**. Dans la boîte de dialogue **Polices et couleurs**, faites défiler l’affichage jusqu’aux options C/C++, puis choisissez une police et/ou une couleur personnalisée(s).

## <a name="outlining"></a>mode Plan

Cliquez avec le bouton droit n’importe où dans un fichier de code source et choisissez **Mode Plan** pour réduire ou développer les blocs de code et/ou les régions personnalisées. Ceci vous permet de parcourir plus vite seulement le code qui vous intéresse. Pour plus d’informations, voir [Mode Plan](/visualstudio/ide/outlining).

![C&#43;&#43; Décrivant](../ide/media/vs2015_cpp_outlining.png "mode Plan")

Quand vous placez votre curseur devant une accolade, « { » ou « } », l’éditeur met en évidence l’accolade correspondante.

D’autres options de description sont situées sous **Edit** > **Outlining** dans le menu principal.

## <a name="line-numbers"></a>Numéros de ligne

Vous pouvez ajouter des numéros de ligne à votre projet en allant à **Tools** > **Options** > **Text Editor** > **All Languages** > **General** ou en recherchant "line num" avec Quick **Launch (Ctrl et Q)**. Les numéros de ligne peuvent être définis pour tous les langages ou pour seulement quelques langages, notamment C++.

## <a name="scroll-and-zoom"></a>Faire défiler et effectuer un zoom

Vous pouvez effectuer un zoom avant ou arrière dans l’éditeur en appuyant sur la touche **Ctrl** et en faisant tourner la roulette de la souris. Vous pouvez également effectuer un zoom à l’aide du paramètre de zoom dans le coin inférieur gauche.

![C&#43;&#43; Contrôle de zoom](../ide/media/zoom-control.png "Contrôle de zoom")

Le **mode Carte** pour la barre de défilement vous permet de faire défiler et parcourir un fichier de code rapidement, sans avoir à quitter votre emplacement actuel. Vous pouvez cliquer n’importe où sur la carte de code pour accéder directement à cet emplacement.

![Carte de code en C&#43;&#43;](../ide/media/vs2015-cpp-code-map.png "Carte du code")

Pour activer **le mode Carte**, tapez "carte" dans la boîte de recherche Quick **Launch** dans la barre d’outils principale et choisissez le mode carte **de défilement d’utilisation**. Pour plus d’informations, consultez [Comment : suivre votre code en personnalisant la barre de défilement](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

Quand le **mode Carte** est désactivé, la barre de défilement met toujours en évidence les modifications que vous avez apportées dans le fichier. Le vert indique les modifications enregistrées, le jaune les modifications non enregistrées.

## <a name="quick-info-and-parameter-info"></a>Info express et Informations sur les paramètres

Pointez n’importe quelle variable, fonction ou autre symbole pour obtenir des informations le concernant, y compris la déclaration et tout commentaire le précédant.

::: moniker range="vs-2019"

![Informations rapides en&#43;&#43;C](../ide/media/quick-info-vs2019.png "Info express")

L’info-bulle **Info express** contient un lien **Rechercher en ligne**. Rendez-vous sur **Tools** > **Options** > **Text Editor** > **CMD** > **Voir** pour spécifier le fournisseur de recherche.

Si votre code contient une erreur, vous pouvez pointer celle-ci afin qu’**Info express** affiche le message d’erreur correspondant. Vous trouverez également le message d’erreur dans la fenêtre Liste d’erreurs.

![Informations rapides sur l’erreur](../ide/media/quickinfo-on-error.png "Informations rapides sur l’erreur")

::: moniker-end

::: moniker range="<=vs-2017"

![Informations rapides en&#43;&#43;C](../ide/media/quick-info.png "Info express")

Si votre code contient une erreur, vous pouvez pointer celle-ci afin qu’**Info express** affiche le message d’erreur correspondant. Vous trouverez également le message d’erreur dans la fenêtre **Liste d’erreurs**.

![Informations rapides sur l’erreur](../ide/media/quickinfo-on-error.png "Informations rapides sur l’erreur")

::: moniker-end

Quand vous appelez une fonction, **Informations sur les paramètres** indique les types de paramètres et l’ordre dans lequel ils sont attendus.

![Informations sur les paramètres en C&#43;&#43;](../ide/media/parameter-info.png "Informations sur les paramètres")

## <a name="peek-definition"></a>Aperçu de la définition

Pointez une déclaration de variable ou de fonction, cliquez avec le bouton droit, puis choisissez **Aperçu de la définition** pour afficher sa définition inline sans quitter l’emplacement actuel. Pour plus d’informations, consultez [Aperçu de la définition (Alt+F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![Définition de C&#43;&#43; Peek](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

## <a name="f1-help"></a>Aide (F1)

Placez le curseur allumé ou juste après n’importe quel type, mot clé ou fonction et appuyez sur **F1** pour aller directement au sujet de référence pertinent sur docs.microsoft.com. **F1** travaille également sur les éléments de la liste d’erreurs, et dans de nombreuses boîtes de dialogue.

## <a name="class-view"></a>Affichage de classes

L’**Affichage de classes** affiche un ensemble d’arborescences pouvant faire l’objet d’une recherche, qui regroupent par projet tous les symboles de code et leurs hiérarchies parent/enfant et portée. Pour configurer ce que l’**Affichage de classes** affiche, accédez à **Paramètres de l’Affichage de classes** (cliquez sur l’icône en forme d’engrenage en haut de la fenêtre).

![Vue de classe en&#43;&#43;C](../ide/media/class-view.png "Affichage de classes")

## <a name="generate-graph-of-include-files"></a>Générer le graphique des fichiers Include

Cliquez avec le bouton droit sur un fichier de code dans votre projet et choisissez **Générer le graphique des fichiers Include** pour afficher un graphe montrant les fichiers qui sont inclus par d’autres fichiers.

![Graphique C&#43;&#43; des fichiers inclus](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="view-call-hierarchy"></a>Afficher la hiérarchie d'appels

Cliquez avec le bouton droit sur un appel de fonction pour afficher la liste récursive de toutes les fonctions qui sont appelées et de toutes les fonctions qui l’appellent. Chaque fonction de la liste peut être développée de la même façon. Pour plus d’informations, consultez [Hiérarchie d’appels](/visualstudio/ide/reference/call-hierarchy).

![C&#43;&#43; La Hiérarchie des appels](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="see-also"></a>Voir aussi

[Modifier et refactoriser du code (C++)](writing-and-refactoring-code-cpp.md)</br>
[Naviguer dans votre base de code C++ dans Visual Studio](navigate-code-cpp.md)</br>
[Collaborer avec Live Share pour C++](live-share-cpp.md)
