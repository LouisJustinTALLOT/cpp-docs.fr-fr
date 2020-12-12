---
description: 'En savoir plus sur : procédure pas à pas : création d’un programme C++ standard (C++)'
title: 'Procédure pas à pas : création d’un programme C++ standard (C++)'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 64310c72a7c58402dfe8c58ce2dab8eb2cbd231e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283184"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Procédure pas à pas : création d’un programme C++ standard (C++)

Vous pouvez utiliser Visual Studio pour créer des programmes C++ standard. En suivant les étapes de cette procédure pas à pas, vous pouvez créer un projet, ajouter un nouveau fichier au projet, modifier le fichier pour ajouter du code C++, puis compiler et exécuter le programme à l’aide de Visual Studio.

Vous pouvez taper votre propre programme C++ ou utiliser l’un des exemples de programmes. L’exemple de programme de cette procédure pas à pas est une application console. Cette application utilise le `set` conteneur dans la bibliothèque C++ standard.

> [!NOTE]
> Si la compatibilité avec une version spécifique de la norme du langage C++ (par exemple, C++ 14 ou C++ 17) est requise, utilisez l' `/std:c++14` `/std:c++17` option du compilateur ou. (Visual Studio 2017 et versions ultérieures.)

## <a name="prerequisites"></a>Prérequis

Pour compléter cette procédure pas à pas, vous devez comprendre les notions de base du langage C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>Pour créer un projet et ajouter un fichier source

Les étapes suivantes varient légèrement selon la version de Visual Studio que vous utilisez. Pour consulter la documentation de votre version par défaut de Visual Studio, utilisez le contrôle sélecteur de **version** . Elle se trouve en haut de la table des matières sur cette page.

::: moniker range="msvc-160"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>Pour créer un projet C++ dans Visual Studio 2019

1. Dans le menu principal, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. En haut de la boîte de dialogue, définissez **Langage** sur **C++**, **Plateforme** sur **Windows** et **Type de projet** sur **Console**.

1. À partir de la liste des types de projets, choisissez **Application console**, puis choisissez **Suivant**. Dans la page suivante, entrez un nom pour le projet, puis spécifiez l’emplacement du projet si vous le souhaitez.

1. Choisissez le bouton **Créer** pour créer le projet.

::: moniker-end

::: moniker range="msvc-150"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>Pour créer un projet C++ dans Visual Studio 2017

1. Créez un projet en pointant sur **nouveau** dans le menu **fichier** , puis en cliquant sur **projet**.

1. Dans le volet types de projets **Visual C++** , cliquez sur **Bureau Windows**, puis sur **application console Windows**.

1. Tapez un nom pour le projet. Par défaut, la solution qui contient le projet porte le même nom que le projet, mais vous pouvez taper un nom différent. Vous pouvez également taper un autre emplacement pour le projet.

1. Cliquez sur **OK** pour créer le projet.

::: moniker-end

::: moniker range="msvc-140"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>Pour créer un projet C++ dans Visual Studio 2015

1. Créez un projet en pointant sur **nouveau** dans le menu **fichier** , puis en cliquant sur **projet**.

1. Dans le volet types de projets **Visual C++** , cliquez sur **Bureau Windows**, puis sur **application console Windows**.

1. Dans la boîte de dialogue **nouveau projet** , développez modèles **installés**  >    >  **Visual C++**, puis sélectionnez **Win32**. Dans le volet central, sélectionnez **Application console Win32**.

1. Tapez un nom pour le projet. Par défaut, la solution qui contient le projet porte le même nom que le projet, mais vous pouvez taper un nom différent. Vous pouvez également taper un autre emplacement pour le projet.

1. Cliquez sur **OK** pour créer le projet.

1. Terminez l **'Assistant application Win32**.

1. Cliquez sur **suivant**, puis assurez-vous que l’option **application console** est sélectionnée et décochez la case **en-têtes précompilés** .

1. Cliquez sur **Terminer**.

::: moniker-end

## <a name="add-a-new-source-file"></a>Ajouter un nouveau fichier source

1. Si **Explorateur de solutions** n’est pas affiché, dans le menu **affichage** , cliquez sur **Explorateur de solutions**.

1. Ajoutez un nouveau fichier source au projet, comme suit.

   1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le dossier **fichiers sources** , pointez sur **Ajouter**, puis cliquez sur **nouvel élément**.

   1. Dans le nœud **code** , cliquez sur **fichier C++ (. cpp)**, tapez un nom pour le fichier, puis cliquez sur **Ajouter**.

   Le fichier. cpp apparaît dans le dossier **fichiers sources** de **Explorateur de solutions**, et le fichier s’ouvre dans l’éditeur Visual Studio.

1. Dans le fichier de l’éditeur, tapez un programme C++ valide qui utilise la bibliothèque C++ standard, ou copiez l’un des exemples de programmes et collez-le dans le fichier.

1. Enregistrez le fichier .

1. Dans le menu **Générer**, cliquez sur **Générer la solution**.

   La fenêtre **sortie** affiche des informations sur la progression de la compilation, par exemple l’emplacement du journal de génération et un message qui indique l’état de la Build.

1. Dans le menu **Déboguer**, cliquez sur **Démarrer sans débogage**.

   Si vous avez utilisé l’exemple de programme, une fenêtre de commande s’affiche et indique si certains entiers sont détectés dans le jeu.

## <a name="next-steps"></a>Étapes suivantes

**Précédent :** [Applications console dans Visual C++](./overview-of-windows-programming-in-cpp.md)<br/>
**Étape suivante :** [procédure pas à pas : compilation d’un programme C++ natif sur la ligne de commande](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
