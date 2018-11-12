---
title: 'Procédure pas à pas : création et utilisation d’une bibliothèque statique (C++)'
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.author: corob
ms.openlocfilehash: 506db5ea8e94887d9971b48c06ce8c0d6156dccb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429208"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>Procédure pas à pas : création et utilisation d’une bibliothèque statique (C++)

Cette procédure pas à pas montre comment créer une bibliothèque statique (fichier .lib) à utiliser avec des applications C++. L’utilisation d’une bibliothèque statique est un excellent moyen de réutiliser le code. Au lieu d’implémenter de nouveau les mêmes routines dans chaque application qui requiert les fonctionnalités, vous les écrivez une fois dans une bibliothèque statique et ensuite le référencer à partir des applications. Le code lié à partir d'une bibliothèque statique devient partie intégrante de votre application. Il n'est pas nécessaire d'installer un autre fichier pour utiliser le code.

Cette procédure pas à pas couvre les tâches suivantes :

- [Création d’un projet de bibliothèque statique](#CreateLibProject)

- [Ajout d’une classe à la bibliothèque statique](#AddClassToLib)

- [Création d’une application console C++ qui fait référence à la bibliothèque statique](#CreateAppToRefTheLib)

- [Utilisation des fonctionnalités de la bibliothèque statique dans l’application](#UseLibInApp)

- [Exécution de l’application](#RunApp)

## <a name="prerequisites"></a>Prérequis

Une connaissance des notions de base du langage C++.

##  <a name="CreateLibProject"></a> Création d’un projet de bibliothèque statique

### <a name="to-create-a-static-library-project"></a>Pour créer un projet de bibliothèque statique

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Dans le volet gauche de la **nouveau projet** boîte de dialogue, développez **installé** > **Visual C++**, puis sélectionnez **Windows Desktop**. Dans le volet central, sélectionnez **Windows Desktop Assistant**.

   > [!NOTE]
   > Pour les versions de Visual Studio antérieures à 2017, dans le **nouveau projet** boîte de dialogue, développez **installé** > **modèles**  >  **Visual C++**, puis sélectionnez **Win32**. Dans le volet central, sélectionnez **Application console Win32**.

1. Spécifiez un nom pour le projet, par exemple *MathFuncsLib*, dans la zone **Nom** . Spécifiez un nom pour la solution, par exemple *StaticLibrary*, dans la zone **Nom de la solution** . Sélectionnez le bouton **OK** .

    - Pour Visual Studio 2017,

        1. Sous **type d’Application**, sélectionnez **bibliothèque statique (.lib)**.

        1. Sous **des Options supplémentaires**, décochez la case la **en-tête précompilé** case à cocher.

        1. Choisissez **OK** pour créer le projet.

    - Pour les versions de Visual Studio antérieures à 2017,

        1. Cliquez sur **Suivant**.

        1. Sous **type d’Application**, sélectionnez **bibliothèque statique**. Décochez la **en-tête précompilé** et sélectionnez **Terminer**.

##  <a name="AddClassToLib"></a> Ajout d’une classe à la bibliothèque statique

### <a name="to-add-a-class-to-the-static-library"></a>Pour ajouter une classe à la bibliothèque statique

1. Pour créer un fichier d’en-tête pour une nouvelle classe, ouvrez le menu contextuel pour le **MathFuncsLib** projet **l’Explorateur de solutions**, puis choisissez **ajouter**  >   **Un nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , dans le volet gauche, sous **Visual C++**, sélectionnez **Code**. Dans le volet central, sélectionnez **Fichier d’en-tête (.h)**. Spécifiez un nom pour le fichier d’en-tête, par exemple *MathFuncsLib.h*, puis sélectionnez le bouton **Ajouter** . Un fichier d’en-tête vierge s’affiche.

1. Ajoutez une classe nommée `MyMathFuncs` pour effectuer des opérations mathématiques courantes telles que l’addition, soustraction, multiplication et division. Le code doit ressembler à :

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]

1. Pour créer un fichier source pour la nouvelle classe, ouvrez le menu contextuel pour le **MathFuncsLib** projet **l’Explorateur de solutions**, puis choisissez **ajouter**  >   **Un nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , dans le volet gauche, sous **Visual C++**, sélectionnez **Code**. Dans le volet central, sélectionnez **Fichier C++ (.cpp)**. Spécifiez un nom pour le fichier source, par exemple *MathFuncsLib.cpp*, puis sélectionnez le bouton **Ajouter** . Un fichier source vide s’affiche.

1. Utilisez ce fichier source pour implémenter les fonctionnalités pour **MyMathFuncs**. Le code doit ressembler à :

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]

1. Compilez la bibliothèque statique en sélectionnant **Build** > **générer la Solution** sur la barre de menus. La compilation crée une bibliothèque statique qui peut être utilisée par d’autres programmes.

   > [!NOTE]
   > Lorsque vous générez un projet sur la ligne de commande Visual Studio, vous devez générer le programme en deux étapes. Tout d’abord, exécutez `cl /c /EHsc MathFuncsLib.cpp` pour compiler le code et de créer un fichier objet nommé `MathFuncsLib.obj`. (La commande `cl` appelle le compilateur, Cl.exe, et l’option `/c` spécifie la compilation sans liaison. Pour plus d’informations, consultez [/c (compiler sans liaison)](../build/reference/c-compile-without-linking.md).) Ensuite, exécutez `lib MathFuncsLib.obj` pour lier le code et créer la bibliothèque statique `MathFuncsLib.lib`. (La commande `lib` appelle le gestionnaire de bibliothèque Lib.exe. Pour plus d’informations, consultez [LIB Reference](../build/reference/lib-reference.md).)

##  <a name="CreateAppToRefTheLib"></a> Création d’une application console C++ qui fait référence à la bibliothèque statique

### <a name="to-create-a-c-console-app-that-references-the-static-library"></a>Pour créer une application console C++ qui fait référence à la bibliothèque statique

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Dans le volet gauche de la **nouveau projet** boîte de dialogue, développez **installé** > **Visual C++**, puis sélectionnez **Windows Desktop**. Dans le volet central, sélectionnez **Windows Desktop Assistant**.

   > [!NOTE]
   > Pour les versions de Visual Studio antérieures à 2017, dans le **nouveau projet** boîte de dialogue, développez **installé** > **modèles**  >  **Visual C++**, puis sélectionnez **Win32**. Dans le volet central, sélectionnez **Application console Win32**.

1. Spécifiez un nom pour le projet, par exemple *MyExecRefsLib*, dans la zone **Nom** . Dans la liste déroulante, en regard de **Solution**, sélectionnez **Ajouter à la solution**. La commande ajoute le nouveau projet à la solution qui contient la bibliothèque statique. Sélectionnez le bouton **OK** .

    - Pour Visual Studio 2017,

        1. Sous **type d’Application**, sélectionnez **Application Console (.exe)**.

        1. Sous **des Options supplémentaires**, décochez la case la **en-tête précompilé** case à cocher.

        1. Choisissez **OK** pour créer le projet.

    - Pour les versions de Visual Studio antérieures à 2017,

        1. Cliquez sur **Suivant**.

        1. Assurez-vous que **application Console** est sélectionné. Vérifiez ensuite le **projet vide** et sélectionnez **Terminer**.

##  <a name="UseLibInApp"></a> Utilisation des fonctionnalités de la bibliothèque statique dans l’application

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Pour utiliser les fonctionnalités de la bibliothèque statique dans l’application

1. Une fois que vous avez créé une application console, un programme vide est créé à votre intention. Le nom du fichier source est identique au nom que vous avez choisi précédemment. Dans l’exemple, il est nommé `MyExecRefsLib.cpp`.

1. Avant de pouvoir utiliser les routines mathématiques dans la bibliothèque statique, vous devez la référencer. Ouvrez le menu contextuel pour le **MyExecRefsLib** projet **l’Explorateur de solutions**, puis choisissez **ajouter** > **référence**.

1. La boîte de dialogue **Ajouter une référence** répertorie les bibliothèques que vous pouvez référencer. Le **projets** onglet répertorie les projets de la solution actuelle et toutes les bibliothèques qu’ils référencent. Sous l’onglet **Projets** , cochez la case **MathFuncsLib** , puis sélectionnez le bouton **OK** .

1. Pour référencer le `MathFuncsLib.h` fichier d’en-tête, vous devez modifier le chemin d’accès des répertoires inclus. Dans la boîte de dialogue **Pages de propriétés** de **MyExecRefsLib**, développez le nœud **Propriétés de configuration** , développez **C/C++** , puis sélectionnez **Général**. Regard **autres répertoires Include**, spécifiez le chemin d’accès de la **MathFuncsLib** directory, ou accédez à ce dernier.

   Pour rechercher le chemin d’accès du répertoire, ouvrez la liste déroulante des valeurs de propriété, puis sélectionnez **Modifier**. Dans le **autres répertoires Include** boîte de dialogue, dans la zone de texte, sélectionnez une ligne vierge, puis choisissez le bouton de sélection (**...** ) à la fin de la ligne. Dans la boîte de dialogue **Sélectionner un répertoire** , sélectionnez le répertoire **MathFuncsLib** , puis choisissez le bouton **Sélectionner un dossier** pour enregistrer votre sélection et fermer la boîte de dialogue. Dans la boîte de dialogue **Autres répertoires Include** , choisissez le bouton **OK** puis, dans la boîte de dialogue **Pages de propriétés** , choisissez le bouton **OK** pour enregistrer les modifications apportées au projet.

1. Vous pouvez maintenant utiliser le `MyMathFuncs` classe dans cette application en incluant le `#include "MathFuncsLib.h"` en-tête dans votre code. Remplacez le contenu de `MyExecRefsLib.cpp` avec ce code :

   [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]

1. Générez le fichier exécutable en choisissant **Build** > **générer la Solution** sur la barre de menus.

##  <a name="RunApp"></a> Exécution de l’application

### <a name="to-run-the-app"></a>Pour exécuter l’application

1. Assurez-vous que **MyExecRefsLib** est sélectionné comme projet par défaut en ouvrant le menu contextuel pour **MyExecRefsLib** dans l’ **Explorateur de solutions**, puis en choisissant **Définir comme projet de démarrage**.

1. Pour exécuter le projet, dans la barre de menus, choisissez **Déboguer** > **Démarrer sans débogage**. La sortie doit ressembler à :

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : création et utilisation d’une bibliothèque de liens dynamiques (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[Applications de bureau (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
