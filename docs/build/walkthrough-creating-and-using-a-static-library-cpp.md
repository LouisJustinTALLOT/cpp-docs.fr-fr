---
title: 'Procédure pas à pas : création et utilisation d’une bibliothèque statique (C++)'
description: Utilisez C++ pour créer une bibliothèque statique (. lib) dans Visual Studio.
ms.custom: get-started-article
ms.date: 04/25/2019
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.author: corob
ms.openlocfilehash: c81ccd970383c8571a7d0d1e77d4b8fe44900bcf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078182"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>Procédure pas à pas : création et utilisation d’une bibliothèque statique (C++)

Cette procédure pas à pas montre comment créer une bibliothèque statique (fichier .lib) à utiliser avec des applications C++. L’utilisation d’une bibliothèque statique est un excellent moyen de réutiliser le code. Plutôt que de réimplémenter les mêmes routines dans chaque application qui requiert la fonctionnalité, vous les écrivez une fois dans une bibliothèque statique, puis vous les référencez à partir des applications. Le code lié à partir d'une bibliothèque statique devient partie intégrante de votre application. Il n'est pas nécessaire d'installer un autre fichier pour utiliser le code.

Cette procédure pas à pas couvre les tâches suivantes :

- [Création d’un projet de bibliothèque statique](#CreateLibProject)

- [Ajout d’une classe à la bibliothèque statique](#AddClassToLib)

- [Création d’une application console C++ qui fait référence à la bibliothèque statique](#CreateAppToRefTheLib)

- [Utilisation des fonctionnalités de la bibliothèque statique dans l’application](#UseLibInApp)

- [Exécution de l’application](#RunApp)

## <a name="prerequisites"></a>Conditions préalables requises

Une connaissance des notions de base du langage C++.

##  <a name="creating-a-static-library-project"></a><a name="CreateLibProject"></a> Création d’un projet de bibliothèque statique

Les instructions relatives à la création du projet varient selon que vous utilisez Visual Studio 2019 ou une version antérieure. Vérifiez que vous disposez de la version appropriée dans l’angle supérieur gauche de cette page.

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>Pour créer un projet de bibliothèque statique dans Visual Studio 2019

1. Dans la barre de menus, choisissez **fichier** > **nouveau** **projet** > pour ouvrir la boîte de dialogue **créer un nouveau projet** .

1. En haut de la boîte de dialogue, définissez **Langage** sur **C++** , **Plateforme** sur **Windows** et **Type de projet** sur **Bibliothèque**.

1. Dans la liste filtrée des types de projets, choisissez **bibliothèque statique** , puis cliquez sur **suivant**. Dans la page suivante, entrez *MathFuncsLib* dans la zone **nom** pour spécifier un nom pour le projet, puis spécifiez l’emplacement du projet si vous le souhaitez.

1. Choisissez le bouton **Créer** pour créer le projet client.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>Pour créer un projet de bibliothèque statique dans Visual Studio 2017

1. Dans la barre de menus, choisissez **fichier** > **nouveau** **projet**>.

1. Dans le volet gauche de la boîte de dialogue **nouveau projet** , développez **installé** > **C++visuel**, puis sélectionnez **Bureau Windows**. Dans le volet central, sélectionnez **Assistant Windows Desktop**.

1. Spécifiez un nom pour le projet, par exemple *MathFuncsLib*, dans la zone **Nom** . Spécifiez un nom pour la solution, par exemple *StaticLibrary*, dans la zone **Nom de la solution** . Sélectionnez le bouton **OK** .

1. Sous **type d’application**, sélectionnez **bibliothèque statique (. lib)** .

1. Sous **options supplémentaires**, désactivez la case à cocher **en-tête précompilé** .

1. Choisissez **OK** pour créer le projet.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>Pour créer un projet de bibliothèque statique dans Visual Studio 2015

1. Dans la barre de menus, choisissez **fichier** > **nouveau** **projet**>.

1. Dans la boîte de dialogue **nouveau projet** , développez > **modèles** **installés** > **visuel C++** , puis sélectionnez **Win32**. Dans le volet central, sélectionnez **Application console Win32**.

1. Spécifiez un nom pour le projet, par exemple *MathFuncsLib*, dans la zone **Nom** . Spécifiez un nom pour la solution, par exemple *StaticLibrary*, dans la zone **Nom de la solution** . Sélectionnez le bouton **OK** .

1. Cliquez sur **Suivant**.

1. Sous **type d’application**, sélectionnez **bibliothèque statique**. Puis, décochez la case **en-tête précompilé** et choisissez **Terminer**.

::: moniker-end

##  <a name="adding-a-class-to-the-static-library"></a><a name="AddClassToLib"></a> Ajout d’une classe à la bibliothèque statique

### <a name="to-add-a-class-to-the-static-library"></a>Pour ajouter une classe à la bibliothèque statique

1. Pour créer un fichier d’en-tête pour une nouvelle classe, ouvrez le menu contextuel du projet **MathFuncsLib** dans **Explorateur de solutions**, puis choisissez **Ajouter** > **nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , dans le volet gauche, sous **Visual C++** , sélectionnez **Code**. Dans le volet central, sélectionnez **Fichier d’en-tête (.h)** . Spécifiez un nom pour le fichier d’en-tête, par exemple *MathFuncsLib.h*, puis sélectionnez le bouton **Ajouter** . Un fichier d’en-tête vierge s’affiche.

1. Ajoutez une classe nommée `MyMathFuncs` pour effectuer des opérations mathématiques courantes telles que l’addition, la soustraction, la multiplication et la Division. Le code doit ressembler à ce qui suit :

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]

1. Pour créer un fichier source pour la nouvelle classe, ouvrez le menu contextuel du projet **MathFuncsLib** dans **Explorateur de solutions**, puis choisissez **Ajouter** > **nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , dans le volet gauche, sous **Visual C++** , sélectionnez **Code**. Dans le volet central, sélectionnez **Fichier C++ (.cpp)** . Spécifiez un nom pour le fichier source, par exemple *MathFuncsLib.cpp*, puis sélectionnez le bouton **Ajouter** . Un fichier source vide s’affiche.

1. Utilisez ce fichier source pour implémenter les fonctionnalités pour **MyMathFuncs**. Le code doit ressembler à ce qui suit :

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]

1. Compilez la bibliothèque statique en sélectionnant **générer** > **générer la solution** dans la barre de menus. La compilation crée une bibliothèque statique qui peut être utilisée par d’autres programmes.

   > [!NOTE]
   > Lorsque vous générez un projet sur la ligne de commande Visual Studio, vous devez générer le programme en deux étapes. Tout d’abord, exécutez `cl /c /EHsc MathFuncsLib.cpp` pour compiler le code et créer un fichier objet nommé `MathFuncsLib.obj`. (La commande `cl` appelle le compilateur, Cl.exe, et l'option `/c` spécifie la compilation sans liaison.) Pour plus d’informations, consultez [/c (compiler sans liaison)](../build/reference/c-compile-without-linking.md).) Ensuite, exécutez `lib MathFuncsLib.obj` pour lier le code et créer la bibliothèque statique `MathFuncsLib.lib`. (La commande `lib` appelle le gestionnaire de bibliothèque Lib.exe. Pour plus d’informations, consultez [LIB Reference](../build/reference/lib-reference.md).)

##  <a name="creating-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a> Création d’une application console C++ qui fait référence à la bibliothèque statique

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>Pour créer une C++ application console qui fait référence à la bibliothèque statique dans Visual Studio 2019

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud supérieur de la solution et choisissez **Ajouter** > **nouveau projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet** .

1. En haut de la boîte de dialogue, définissez **Langage** sur **C++** , **Plateforme** sur **Windows** et **Type de projet** sur **Console**.

1. À partir de la liste des types de projets, choisissez **Application console**, puis choisissez **Suivant**. Dans la page suivante, entrez *MyExecRefsLib* dans la zone **nom** pour spécifier un nom pour le projet, puis spécifiez l’emplacement du projet si vous le souhaitez.

1. Choisissez le bouton **Créer** pour créer le projet client.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>Pour créer une C++ application console qui fait référence à la bibliothèque statique dans Visual Studio 2017

1. Dans la barre de menus, choisissez **fichier** > **nouveau** **projet**>.

1. Dans le volet gauche de la boîte de dialogue **nouveau projet** , développez **installé** > **C++visuel**, puis sélectionnez **Bureau Windows**. Dans le volet central, sélectionnez **Assistant Windows Desktop**.

1. Spécifiez un nom pour le projet, par exemple *MyExecRefsLib*, dans la zone **Nom** . Dans la liste déroulante, en regard de **Solution**, sélectionnez **Ajouter à la solution**. La commande ajoute le nouveau projet à la solution qui contient la bibliothèque statique. Sélectionnez le bouton **OK** .

1. Sous **type d’application**, sélectionnez **application console (. exe)** .

1. Sous **options supplémentaires**, désactivez la case à cocher **en-tête précompilé** .

1. Choisissez **OK** pour créer le projet.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>Pour créer une C++ application console qui fait référence à la bibliothèque statique dans Visual Studio 2015

1. Dans la barre de menus, choisissez **fichier** > **nouveau** **projet**>.

1. Dans la boîte de dialogue **nouveau projet** , développez > **modèles** **installés** > **visuel C++** , puis sélectionnez **Win32**. Dans le volet central, sélectionnez **Application console Win32**.

1. Spécifiez un nom pour le projet, par exemple *MyExecRefsLib*, dans la zone **Nom** . Dans la liste déroulante, en regard de **Solution**, sélectionnez **Ajouter à la solution**. La commande ajoute le nouveau projet à la solution qui contient la bibliothèque statique. Sélectionnez le bouton **OK** .

1. Cliquez sur **Suivant**.

1. Assurez-vous que l’option **application console** est sélectionnée. Cochez ensuite la case **projet vide** et choisissez **Terminer**.

::: moniker-end

##  <a name="using-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a> Utilisation des fonctionnalités de la bibliothèque statique dans l’application

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Pour utiliser les fonctionnalités de la bibliothèque statique dans l’application

1. Une fois que vous avez créé une application console, un programme vide est créé à votre intention. Le nom du fichier source est identique au nom que vous avez choisi précédemment. Dans l’exemple, il est nommé `MyExecRefsLib.cpp`.

1. Avant de pouvoir utiliser les routines mathématiques dans la bibliothèque statique, vous devez la référencer. Ouvrez le menu contextuel du projet **MyExecRefsLib** dans **Explorateur de solutions**, puis choisissez **Ajouter** une **référence**de > .

1. La boîte de dialogue **Ajouter une référence** répertorie les bibliothèques que vous pouvez référencer. L’onglet **projets** répertorie les projets dans la solution actuelle et toutes les bibliothèques auxquelles ils font référence. Sous l’onglet **Projets** , cochez la case **MathFuncsLib** , puis sélectionnez le bouton **OK** .

1. Pour référencer le fichier d’en-tête `MathFuncsLib.h`, vous devez modifier le chemin d’accès aux répertoires inclus. Dans la boîte de dialogue **Pages de propriétés** de **MyExecRefsLib**, développez le nœud **Propriétés de configuration** , développez **C/C++** , puis sélectionnez **Général**. En regard de **autres répertoires Include**, spécifiez le chemin d’accès du répertoire **MathFuncsLib** ou recherchez-le.

   Pour rechercher le chemin d’accès du répertoire, ouvrez la liste déroulante des valeurs de propriété, puis sélectionnez **Modifier**. Dans la boîte de dialogue **autres répertoires Include** , dans la zone de texte, sélectionnez une ligne vide, puis cliquez sur le bouton de sélection ( **...** ) à la fin de la ligne. Dans la boîte de dialogue **Sélectionner un répertoire** , sélectionnez le répertoire **MathFuncsLib** , puis choisissez le bouton **Sélectionner un dossier** pour enregistrer votre sélection et fermer la boîte de dialogue. Dans la boîte de dialogue **Autres répertoires Include** , choisissez le bouton **OK** puis, dans la boîte de dialogue **Pages de propriétés** , choisissez le bouton **OK** pour enregistrer les modifications apportées au projet.

1. Vous pouvez maintenant utiliser la classe `MyMathFuncs` dans cette application en incluant l’en-tête `#include "MathFuncsLib.h"` dans votre code. Remplacez le contenu de `MyExecRefsLib.cpp` par ce code :

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]

1. Générez le fichier exécutable en choisissant **générer** > **générer la solution** dans la barre de menus.

##  <a name="running-the-app"></a><a name="RunApp"></a> Exécution de l’application

### <a name="to-run-the-app"></a>Pour exécuter l’application

1. Assurez-vous que **MyExecRefsLib** est sélectionné comme projet par défaut en ouvrant le menu contextuel pour **MyExecRefsLib** dans l’ **Explorateur de solutions**, puis en choisissant **Définir comme projet de démarrage**.

1. Pour exécuter le projet, dans la barre de menus, choisissez **Déboguer** > **Démarrer sans débogage**. La sortie doit ressembler à ce qui suit :

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : création et utilisation d’une bibliothèque de liens dynamiques (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[Applications de bureau (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
