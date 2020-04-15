---
title: 'Procédure pas à pas : création d’un programme C++ standard (C++)'
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
ms.openlocfilehash: 105ac62131b45afdea2a445b5888a344f1e4d46c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370225"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Procédure pas à pas : création d’un programme C++ standard (C++)

Vous pouvez utiliser Visual Studio pour créer des programmes Standard C. En suivant les étapes de cette procédure pas à pas, vous pouvez créer un projet, ajouter un nouveau fichier au projet, modifier le fichier pour ajouter du code C, puis compiler et exécuter le programme en utilisant Visual Studio.

Vous pouvez taper votre propre programme de CMD ou utiliser l’un des programmes d’exemples. Le programme d’échantillon dans cette procédure pas à pas est une application de console. Cette application `set` utilise le conteneur de la Bibliothèque standard C.

> [!NOTE]
> Si la conformité à une version spécifique de la norme linguistique CMD (c.-à-d. C -14 ou C 17) est nécessaire, utilisez l’option `/std:c++14` ou `/std:c++17` le compilateur. (Visual Studio 2017 et plus tard.)

## <a name="prerequisites"></a>Prérequis

Pour compléter cette procédure pas à pas, vous devez comprendre les notions de base du langage C++.

### <a name="to-create-a-project-and-add-a-source-file"></a>Créer un projet et ajouter un fichier source

Les étapes suivantes varient légèrement selon la version de Visual Studio que vous utilisez. Pour voir la documentation de votre version préférée de Visual Studio, utilisez le contrôle du sélecteur **Version.** On le trouve en haut de la table des contenus sur cette page.

::: moniker range="vs-2019"

### <a name="to-create-a-c-project-in-visual-studio-2019"></a>Créer un projet de CMD dans Visual Studio 2019

1. Dans le menu principal, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. En haut de la boîte de dialogue, définissez **Langage** sur ** C++ **, **Plateforme** sur **Windows** et **Type de projet** sur **Console**.

1. À partir de la liste des types de projets, choisissez **Application console**, puis choisissez **Suivant**. Dans la page suivante, entrez un nom pour le projet et spécifiez l’emplacement du projet si désiré.

1. Choisissez le bouton **Créer** pour créer le projet.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-project-in-visual-studio-2017"></a>Créer un projet de CMD dans Visual Studio 2017

1. Créez un projet en pointant vers **New** on the **File** menu, puis en cliquant sur **Project**.

1. Dans le volet visual de type de projet **CMD,** cliquez sur **Windows Desktop,** puis cliquez sur **l’application console Windows**.

1. Tapez un nom pour le projet. Par défaut, la solution qui contient le projet porte le même nom que le projet, mais vous pouvez taper un nom différent. Vous pouvez également taper un emplacement différent pour le projet.

1. Cliquez sur **OK** pour créer le projet.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-project-in-visual-studio-2015"></a>Créer un projet de CMD dans Visual Studio 2015

1. Créez un projet en pointant vers **New** on the **File** menu, puis en cliquant sur **Project**.

1. Dans le volet visual de type de projet **CMD,** cliquez sur **Windows Desktop,** puis cliquez sur **l’application console Windows**.

1. Dans la boîte de dialogue **du nouveau projet,** étendre les**modèles** >  **installés** > **Visual CMD**, puis sélectionnez **Win32**. Dans le volet central, sélectionnez **Application console Win32**.

1. Tapez un nom pour le projet. Par défaut, la solution qui contient le projet porte le même nom que le projet, mais vous pouvez taper un nom différent. Vous pouvez également taper un emplacement différent pour le projet.

1. Cliquez sur **OK** pour créer le projet.

1. Complétez le **Win32 Application Wizard**.

1. Cliquez **sur Next**, puis assurez-vous que **l’application console** est sélectionnée et décochez la boîte **d’en-tête précompilée.**

1. Cliquez sur **Terminer**.

::: moniker-end

## <a name="add-a-new-source-file"></a>Ajouter un nouveau fichier source

1. Si **Solution Explorer** n’est pas affichée, sur le menu **View,** cliquez sur **Solution Explorer**.

1. Ajoutez un nouveau fichier source au projet, comme suit.

   1. Dans **Solution Explorer**, cliquez à droite sur le dossier Source **Files,** pointez-le vers **Ajouter,** puis cliquez sur **Nouvel Article**.

   1. Dans le nœud **de code,** cliquez sur **le fichier CMD (.cpp),** tapez un nom pour le fichier, puis cliquez sur **Ajouter**.

   Le fichier .cpp apparaît dans le dossier **Source Files** dans **Solution Explorer**, et le fichier est ouvert dans l’éditeur Visual Studio.

1. Dans le fichier de l’éditeur, tapez un programme CMD valide qui utilise la Bibliothèque standard de CMD, ou copiez l’un des programmes d’échantillons et collez-le dans le fichier.

1. Enregistrez le fichier .

1. Dans le menu **Générer**, cliquez sur **Générer la solution**.

   La fenêtre **de sortie** affiche des informations sur l’avancement de la compilation, par exemple, l’emplacement du journal de construction et un message indiquant l’état de la construction.

1. Dans le menu **Déboguer**, cliquez sur **Démarrer sans débogage**.

   Si vous avez utilisé le programme d’échantillons, une fenêtre de commande est affichée et indique si certains entiers se trouvent dans l’ensemble.

## <a name="next-steps"></a>Étapes suivantes

**Précédent :** [Applications de console dans Visual C](../windows/console-applications-in-visual-cpp.md)<br/>
**Suivant :** [Procédure pas à pas : Compilation d’un programme native CMD sur la ligne de commandement](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)

## <a name="see-also"></a>Voir aussi

[Référence linguistique de CMD](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque standard de CMD](../standard-library/cpp-standard-library-reference.md)
