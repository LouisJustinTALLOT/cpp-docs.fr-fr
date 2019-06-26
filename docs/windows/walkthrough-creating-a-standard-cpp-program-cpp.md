---
title: 'Procédure pas à pas : Création d’un programme C++ Standard (C++)'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: b3172dd6ed4c438bacedd6760da5ab65228396f3
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400905"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Procédure pas à pas : Création d’un programme C++ Standard (C++)

Vous pouvez utiliser Visual Studio pour créer des Standard C++ programmes. En suivant les étapes décrites dans cette procédure pas à pas, vous pouvez créer un projet, ajoutez un nouveau fichier au projet, modifiez le fichier pour ajouter du code C++, puis compiler et exécuter le programme à l’aide de Visual Studio.

Vous pouvez taper votre propre programme C++ ou utiliser un des exemples de programmes. L’exemple de programme dans cette procédure pas à pas est une application console. Cette application utilise le `set` conteneur dans la bibliothèque C++ Standard.

> [!NOTE]
> Si la conformité avec une version spécifique de la C++ norme du langage (par exemple, C ++ 14 ou C ++ 17) est requis, utilisez le `/std:C++14` ou `/std:c++17` option du compilateur. (Visual Studio 2017 et versions ultérieur.)

## <a name="prerequisites"></a>Prérequis

Pour compléter cette procédure pas à pas, vous devez comprendre les notions de base du langage C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>Pour créer un projet et ajoutez un fichier source

Les étapes suivantes varient légèrement selon la version de Visual Studio que vous utilisez. Vérifiez que vous avez sélectionné la bonne version dans le sélecteur de version situé en haut à gauche de la page.

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>Pour créer un C++ projet dans Visual Studio 2019

1. Dans le menu principal, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. En haut de la boîte de dialogue, définissez **Langage** sur **C++** , **Plateforme** sur **Windows** et **Type de projet** sur **Console**. 

1. À partir de la liste des types de projets, choisissez **Application console**, puis choisissez **Suivant**. Dans la page suivante, entrez un nom pour le projet et spécifier l’emplacement du projet si vous le souhaitez.

1. Choisissez le bouton **Créer** pour créer le projet.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>Pour créer un C++ projet dans Visual Studio 2017

1. Créer un projet en pointant sur **New** sur le **fichier** menu, puis en cliquant sur **projet**.

1. Dans le **Visual C++** volet des types de projets, cliquez sur **Windows Desktop**, puis cliquez sur **Application de Console Windows**.

1. Tapez un nom pour le projet. Par défaut, la solution qui contient le projet a le même nom que le projet, mais vous pouvez taper un nom différent. Vous pouvez également taper un autre emplacement pour le projet.

1. Cliquez sur **OK** pour créer le projet.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>Pour créer un C++ projet dans Visual Studio 2015

1. Créer un projet en pointant sur **New** sur le **fichier** menu, puis en cliquant sur **projet**.

1. Dans le **Visual C++** volet des types de projets, cliquez sur **Windows Desktop**, puis cliquez sur **Application de Console Windows**.

1. Dans le **nouveau projet** boîte de dialogue, développez **installé** > **modèles** > **Visual C++** , et puis sélectionnez **Win32**. Dans le volet central, sélectionnez **Application console Win32**.

1. Tapez un nom pour le projet. Par défaut, la solution qui contient le projet a le même nom que le projet, mais vous pouvez taper un nom différent. Vous pouvez également taper un autre emplacement pour le projet.

1. Cliquez sur **OK** pour créer le projet.

1. Terminer la **Assistant Application Win32**. 

1. Cliquez sur **suivant**, puis assurez-vous que **Application Console** est sélectionnée et décochez le **en-têtes précompilés** boîte. 

1. Cliquez sur **Terminer**.

::: moniker-end

## <a name="add-a-new-source-file"></a>Ajouter un nouveau fichier source

1. Si **l’Explorateur de solutions** n’apparaît pas, dans le **vue** menu, cliquez sur **l’Explorateur de solutions**.

1. Ajoutez un nouveau fichier source au projet, comme suit.

   1. Dans **l’Explorateur de solutions**, avec le bouton droit le **fichiers sources** dossier, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.

   1. Dans le **Code** nœud, cliquez sur **fichier C++ (.cpp)** , tapez un nom pour le fichier, puis cliquez sur **ajouter**.

   Le fichier .cpp apparaît dans le **fichiers sources** dossier **l’Explorateur de solutions**, et le fichier est ouvert dans l’éditeur Visual Studio.

1. Dans le fichier dans l’éditeur, tapez un programme C++ valid qui utilise la bibliothèque C++ Standard, ou copiez un des exemples de programmes et collez-le dans le fichier.

1. Enregistrez le fichier.

1. Dans le menu **Générer** , cliquez sur **Générer la solution**.

   Le **sortie** fenêtre affiche des informations sur la progression de la compilation, par exemple, l’emplacement du journal de génération et un message qui indique l’état de la build.

1. Dans le menu **Déboguer**, cliquez sur **Démarrer sans débogage**.

   Si vous avez utilisé l’exemple de programme, une fenêtre de commande s’affiche et indique si certains entiers ont été trouvés dans le jeu.

## <a name="next-steps"></a>Étapes suivantes

**Précédent :** [Applications console dans Visual C++](../windows/console-applications-in-visual-cpp.md)<br/>
**Suivant :** [Procédure pas à pas : compilation d’un programme C++ natif sur la ligne de commande](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
