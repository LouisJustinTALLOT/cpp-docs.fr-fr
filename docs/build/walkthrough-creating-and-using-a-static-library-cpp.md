---
title: 'Procédure pas à pas : Créer et utiliser une bibliothèque statique (C++)'
description: Utilisez C++ pour créer une bibliothèque statique (. lib) dans Visual Studio.
ms.custom: get-started-article
ms.date: 04/13/2020
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.openlocfilehash: 6cb379baafc506570b1bdc1b286b35c40f8cd0d8
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924381"
---
# <a name="walkthrough-create-and-use-a-static-library"></a>Procédure pas à pas : création et utilisation d’une bibliothèque statique

Cette procédure pas à pas montre comment créer une bibliothèque statique (fichier .lib) à utiliser avec des applications C++. L’utilisation d’une bibliothèque statique est un excellent moyen de réutiliser le code. Plutôt que de réimplémenter les mêmes routines dans chaque application qui requiert la fonctionnalité, vous les écrivez une fois dans une bibliothèque statique, puis vous les référencez à partir des applications. Le code lié à partir d’une bibliothèque statique devient partie intégrante de votre application : vous n’êtes pas obligé d’installer un autre fichier pour utiliser le code.

Cette procédure pas à pas couvre les tâches suivantes :

- [Créer un projet de bibliothèque statique](#CreateLibProject)

- [Ajouter une classe à la bibliothèque statique](#AddClassToLib)

- [Créer une application console C++ qui fait référence à la bibliothèque statique](#CreateAppToRefTheLib)

- [Utiliser la fonctionnalité de la bibliothèque statique dans l’application](#UseLibInApp)

- [Exécuter l’application](#RunApp)

## <a name="prerequisites"></a>Conditions préalables requises

Une connaissance des notions de base du langage C++.

## <a name="create-a-static-library-project"></a><a name="CreateLibProject"></a> Créer un projet de bibliothèque statique

Les instructions relatives à la création du projet varient en fonction de votre version de Visual Studio. Pour consulter la documentation de votre version par défaut de Visual Studio, utilisez le contrôle sélecteur de **version** . Elle se trouve en haut de la table des matières sur cette page.

::: moniker range="msvc-160"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>Pour créer un projet de bibliothèque statique dans Visual Studio 2019

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. En haut de la boîte de dialogue, définissez **Langage** sur **C++**, **Plateforme** sur **Windows** et **Type de projet** sur **Bibliothèque**.

1. Dans la liste filtrée des types de projets, sélectionnez **Assistant du bureau Windows**, puis choisissez **suivant**.

1. Dans la page **configurer votre nouveau projet** , entrez *MathLibrary* dans la zone **nom du projet** pour spécifier un nom pour le projet. Entrez *StaticMath* dans la zone nom de la **solution** . Cliquez sur le bouton **créer** pour ouvrir la boîte de dialogue **projet de bureau Windows** .

1. Dans la boîte de dialogue **projet de bureau Windows** , sous **type d’application**, sélectionnez **bibliothèque statique (. lib)**.

1. Sous **options supplémentaires**, décochez la case **en-tête précompilé** si elle est activée. Activez la case à cocher **projet vide** .

1. Choisissez **OK** pour créer le projet.

::: moniker-end

::: moniker range="msvc-150"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>Pour créer un projet de bibliothèque statique dans Visual Studio 2017

1. Dans la barre de menus, choisissez **fichier** > **nouveau** > **projet**.

1. Dans la boîte de dialogue **nouveau projet** , sélectionnez **installé**  >  **Visual C++**  >  **Bureau Windows**. Dans le volet central, sélectionnez **Assistant Windows Desktop**.

1. Spécifiez un nom pour le projet (par exemple, *MathLibrary*) dans la zone **nom** . Spécifiez un nom pour la solution (par exemple, *StaticMath*) dans la zone nom de la **solution** . Choisissez le bouton **OK**.

1. Dans la boîte de dialogue **projet de bureau Windows** , sous **type d’application**, sélectionnez **bibliothèque statique (. lib)**.

1. Sous **options supplémentaires**, décochez la case **en-tête précompilé** si elle est activée. Activez la case à cocher **projet vide** .

1. Choisissez **OK** pour créer le projet.

::: moniker-end

::: moniker range="msvc-140"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>Pour créer un projet de bibliothèque statique dans Visual Studio 2015

1. Dans la barre de menus, choisissez **fichier** > **nouveau** > **projet**.

1. Dans la boîte de dialogue **nouveau projet** , sélectionnez modèles **installés**  >  **Templates**  >  **Visual C++**  >  **Win32**. Dans le volet central, sélectionnez **Application console Win32**.

1. Spécifiez un nom pour le projet (par exemple, *MathLibrary*) dans la zone **nom** . Spécifiez un nom pour la solution (par exemple, *StaticMath*) dans la zone nom de la **solution** . Choisissez le bouton **OK**.

1. Dans l **'Assistant application Win32**, choisissez **suivant**.

1. Dans la page Paramètres de l' **application** , sous **type d’application**, sélectionnez **bibliothèque statique**. Sous **options supplémentaires**, décochez la case **en-tête précompilé** . Choisissez **Terminer** pour créer le projet.

::: moniker-end

## <a name="add-a-class-to-the-static-library"></a><a name="AddClassToLib"></a> Ajouter une classe à la bibliothèque statique

### <a name="to-add-a-class-to-the-static-library"></a>Pour ajouter une classe à la bibliothèque statique

1. Pour créer un fichier d’en-tête pour une nouvelle classe, cliquez avec le bouton droit pour ouvrir le menu contextuel du projet **MathLibrary** dans **Explorateur de solutions**, puis choisissez **Ajouter**  >  **un nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Visual C++**  >  **code**. Dans le volet central, sélectionnez **Fichier d’en-tête (.h)**. Spécifiez un nom pour le fichier d’en-tête (par exemple, *MathLibrary. h*), puis cliquez sur le bouton **Ajouter** . Un fichier d’en-tête presque vide s’affiche.

1. Ajoutez une déclaration pour une classe nommée `Arithmetic` pour effectuer des opérations mathématiques courantes telles que l’addition, la soustraction, la multiplication et la Division. Le code doit ressembler à ce qui suit :

    ```cpp
    // MathLibrary.h
    #pragma once

    namespace MathLibrary
    {
        class Arithmetic
        {
        public:
            // Returns a + b
            static double Add(double a, double b);

            // Returns a - b
            static double Subtract(double a, double b);

            // Returns a * b
            static double Multiply(double a, double b);

            // Returns a / b
            static double Divide(double a, double b);
        };
    }
    ```

1. Pour créer un fichier source pour la nouvelle classe, ouvrez le menu contextuel du projet **MathLibrary** dans **Explorateur de solutions**, puis choisissez **Ajouter**  >  **un nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , dans le volet central, sélectionnez **fichier C++ (. cpp)**. Spécifiez un nom pour le fichier source (par exemple, *MathLibrary. cpp*), puis cliquez sur le bouton **Ajouter** . Un fichier source vide s’affiche.

1. Utilisez ce fichier source pour implémenter les fonctionnalités de la classe `Arithmetic` . Le code doit ressembler à ce qui suit :

    ```cpp
    // MathLibrary.cpp
    // compile with: cl /c /EHsc MathLibrary.cpp
    // post-build command: lib MathLibrary.obj

    #include "MathLibrary.h"

    namespace MathLibrary
    {
        double Arithmetic::Add(double a, double b)
        {
            return a + b;
        }

        double Arithmetic::Subtract(double a, double b)
        {
            return a - b;
        }

        double Arithmetic::Multiply(double a, double b)
        {
            return a * b;
        }

        double Arithmetic::Divide(double a, double b)
        {
            return a / b;
        }
    }
    ```

1. Pour générer la bibliothèque statique, sélectionnez **générer**  >  **générer la solution** dans la barre de menus. La build crée une bibliothèque statique, *MathLibrary. lib*, qui peut être utilisée par d’autres programmes.

   > [!NOTE]
   > Lorsque vous générez un projet sur la ligne de commande Visual Studio, vous devez générer le programme en deux étapes. Commencez par exécuter `cl /c /EHsc MathLibrary.cpp` pour compiler le code et créer un fichier objet nommé *MathLibrary. obj*. (La `cl` commande appelle le compilateur, Cl.exe, et l' `/c` option spécifie la compilation sans liaison. Pour plus d’informations, consultez [/c (compiler sans liaison)](../build/reference/c-compile-without-linking.md).) Ensuite, exécutez `lib MathLibrary.obj` pour lier le code et créer la bibliothèque statique *MathLibrary. lib*. (La commande `lib` appelle le gestionnaire de bibliothèque Lib.exe. Pour plus d’informations, consultez [LIB Reference](../build/reference/lib-reference.md).)

## <a name="create-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a> Créer une application console C++ qui fait référence à la bibliothèque statique

::: moniker range="msvc-160"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>Pour créer une application console C++ qui fait référence à la bibliothèque statique dans Visual Studio 2019

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud supérieur, **solution « StaticMath »**, pour ouvrir le menu contextuel. Choisissez **Ajouter**  >  un **nouveau projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet** .

1. En haut de la boîte de dialogue, définissez le filtre de **type de projet** sur **console**.

1. À partir de la liste des types de projets, choisissez **Application console**, puis choisissez **Suivant**. Dans la page suivante, entrez *MathClient* dans la zone **nom** pour spécifier un nom pour le projet.

1. Choisissez le bouton **Créer** pour créer le projet client.

1. Une fois que vous avez créé une application console, un programme vide est créé à votre intention. Le nom du fichier source est identique au nom que vous avez choisi précédemment. Dans l’exemple, il s’agit du nom `MathClient.cpp` .

::: moniker-end

::: moniker range="msvc-150"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>Pour créer une application console C++ qui fait référence à la bibliothèque statique dans Visual Studio 2017

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud supérieur, **solution « StaticMath »**, pour ouvrir le menu contextuel. Choisissez **Ajouter**  >  un **nouveau projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet** .

1. Dans la boîte de dialogue **Ajouter un nouveau projet** , sélectionnez **installé**  >  **Visual C++**  >  **Bureau Windows**. Dans le volet central, sélectionnez **Assistant Windows Desktop**.

1. Spécifiez un nom pour le projet (par exemple, *MathClient*) dans la zone **nom** . Choisissez le bouton **OK**.

1. Dans la boîte de dialogue **projet de bureau Windows** , sous **type d’application**, sélectionnez **application console (. exe)**.

1. Sous **options supplémentaires**, décochez la case **en-tête précompilé** si elle est activée.

1. Choisissez **OK** pour créer le projet.

1. Une fois que vous avez créé une application console, un programme vide est créé à votre intention. Le nom du fichier source est identique au nom que vous avez choisi précédemment. Dans l’exemple, il s’agit du nom `MathClient.cpp` .

::: moniker-end

::: moniker range="msvc-140"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>Pour créer une application console C++ qui fait référence à la bibliothèque statique dans Visual Studio 2015

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud supérieur, **solution « StaticMath »**, pour ouvrir le menu contextuel. Choisissez **Ajouter**  >  un **nouveau projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet** .

1. Dans la boîte de dialogue **Ajouter un nouveau projet** , sélectionnez **installé**  >  **Visual C++**  >  **Win32**. Dans le volet central, sélectionnez **Application console Win32**.

1. Spécifiez un nom pour le projet (par exemple, *MathClient*) dans la zone **nom** . Choisissez le bouton **OK**.

1. Dans la boîte de dialogue de l' **Assistant application Win32** , choisissez **suivant**.

1. Dans la page Paramètres de l' **application** , sous **type d’application**, assurez-vous que l’option **application console** est sélectionnée. Sous **options supplémentaires**, décochez la case **en-tête précompilé**, puis cochez la case **projet vide** . Choisissez **Terminer** pour créer le projet.

1. Pour ajouter un fichier source au projet vide, cliquez avec le bouton droit pour ouvrir le menu contextuel du projet **MathClient** dans **Explorateur de solutions**, puis choisissez **Ajouter** > **un nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Visual C++**  >  **code**. Dans le volet central, sélectionnez **Fichier C++ (.cpp)**. Spécifiez un nom pour le fichier source (par exemple, *MathClient. cpp*), puis cliquez sur le bouton **Ajouter** . Un fichier source vide s’affiche.

::: moniker-end

## <a name="use-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a> Utiliser la fonctionnalité de la bibliothèque statique dans l’application

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Pour utiliser les fonctionnalités de la bibliothèque statique dans l’application

1. Avant de pouvoir utiliser les routines mathématiques dans la bibliothèque statique, vous devez la référencer. Ouvrez le menu contextuel du projet **MathClient** dans **Explorateur de solutions**, puis choisissez **Ajouter** une  >  **référence**.

1. La boîte de dialogue **Ajouter une référence** répertorie les bibliothèques que vous pouvez référencer. L’onglet **projets** répertorie les projets dans la solution actuelle et toutes les bibliothèques auxquelles ils font référence. Ouvrez l’onglet **projets** , activez la case à cocher **MathLibrary** , puis choisissez le bouton **OK** .

1. Pour référencer le `MathLibrary.h` fichier d’en-tête, vous devez modifier le chemin d’accès aux répertoires inclus. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **MathClient** pour ouvrir le menu contextuel. Sélectionnez **Propriétés** pour ouvrir la boîte de dialogue **pages de propriétés de MathClient** .

1. Dans la boîte de dialogue **pages de propriétés de MathClient** , définissez la liste déroulante **configuration** sur **toutes les configurations**. Définissez la liste déroulante **plateforme** sur **toutes les plateformes**.

1. Sélectionnez la page de propriétés général des **Propriétés de configuration**  >  **C/C++**  >  **General** . Dans la propriété **autres répertoires Include** , spécifiez le chemin d’accès du répertoire **MathLibrary** ou recherchez-le.

   Pour rechercher le chemin d’accès au répertoire :

   1. Ouvrez la liste déroulante de la valeur de propriété **autres répertoires Include** , puis choisissez **modifier**.

   1. Dans la boîte de dialogue **autres répertoires Include** , double-cliquez en haut de la zone de texte. Cliquez ensuite sur le bouton de sélection (**...**) à la fin de la ligne.

   1. Dans la boîte de dialogue **Sélectionner un répertoire** , accédez à un niveau, puis sélectionnez le répertoire **MathLibrary** . Cliquez ensuite sur le bouton **Sélectionner un dossier** pour enregistrer votre sélection.

   1. Dans la boîte de dialogue **autres répertoires Include** , choisissez le bouton **OK** .

   1. Dans la boîte de dialogue **pages de propriétés** , choisissez le bouton **OK** pour enregistrer les modifications apportées au projet.

1. Vous pouvez maintenant utiliser la `Arithmetic` classe dans cette application en incluant l' `#include "MathLibrary.h"` en-tête dans votre code. Remplacez le contenu de `MathClient.cpp` par le code suivant :

    ```cpp
    // MathClient.cpp
    // compile with: cl /EHsc MathClient.cpp /link MathLibrary.lib

    #include <iostream>
    #include "MathLibrary.h"

    int main()
    {
        double a = 7.4;
        int b = 99;

        std::cout << "a + b = " <<
            MathLibrary::Arithmetic::Add(a, b) << std::endl;
        std::cout << "a - b = " <<
            MathLibrary::Arithmetic::Subtract(a, b) << std::endl;
        std::cout << "a * b = " <<
            MathLibrary::Arithmetic::Multiply(a, b) << std::endl;
        std::cout << "a / b = " <<
            MathLibrary::Arithmetic::Divide(a, b) << std::endl;

        return 0;
    }
    ```

1. Pour générer le fichier exécutable, choisissez **générer**  >  **générer la solution** dans la barre de menus.

## <a name="run-the-app"></a><a name="RunApp"></a> Exécuter l’application

### <a name="to-run-the-app"></a>Pour exécuter l’application

1. Assurez-vous que **MathClient** est sélectionné comme projet par défaut. Pour le sélectionner, cliquez avec le bouton droit pour ouvrir le menu contextuel de **MathClient** dans **Explorateur de solutions**, puis choisissez **définir comme projet de démarrage**.

1. Pour exécuter le projet, dans la barre de menus, choisissez **Déboguer**  >  **exécuter sans débogage**. La sortie doit ressembler à ce qui suit :

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : création et utilisation d’une bibliothèque de liens dynamiques (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[Applications de bureau (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
