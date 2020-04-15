---
title: 'Procédure pas à pas : Créez et utilisez une bibliothèque statique (CMD)'
description: Utilisez C POUR créer une bibliothèque statique (.lib) dans Visual Studio.
ms.custom: get-started-article
ms.date: 04/13/2020
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
ms.openlocfilehash: 7148cc1de7c06ae57d61560311b342a1fc9dda1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335149"
---
# <a name="walkthrough-create-and-use-a-static-library"></a>Procédure pas à pas : Créez et utilisez une bibliothèque statique

Cette procédure pas à pas montre comment créer une bibliothèque statique (fichier .lib) à utiliser avec des applications C++. L’utilisation d’une bibliothèque statique est un excellent moyen de réutiliser le code. Plutôt que de réimplanter les mêmes routines dans chaque application qui nécessite la fonctionnalité, vous les écrivez une fois dans une bibliothèque statique, puis la référence à partir des applications. Le code lié à partir d’une bibliothèque statique fait partie de votre application , vous n’avez pas à installer un autre fichier pour utiliser le code.

Cette procédure pas à pas couvre les tâches suivantes :

- [Créer un projet de bibliothèque statique](#CreateLibProject)

- [Ajouter une classe à la bibliothèque statique](#AddClassToLib)

- [Créez une application console CMD qui fait référence à la bibliothèque statique](#CreateAppToRefTheLib)

- [Utilisez la fonctionnalité de la bibliothèque statique de l’application](#UseLibInApp)

- [Exécuter l’application](#RunApp)

## <a name="prerequisites"></a>Prérequis

Une connaissance des notions de base du langage C++.

## <a name="create-a-static-library-project"></a><a name="CreateLibProject"></a>Créer un projet de bibliothèque statique

Les instructions pour créer le projet varient selon votre version de Visual Studio. Pour voir la documentation de votre version préférée de Visual Studio, utilisez le contrôle du sélecteur **Version.** On le trouve en haut de la table des contenus sur cette page.

::: moniker range="vs-2019"

### <a name="to-create-a-static-library-project-in-visual-studio-2019"></a>Créer un projet de bibliothèque statique dans Visual Studio 2019

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. En haut de la boîte de dialogue, définissez **Langage** sur ** C++ **, **Plateforme** sur **Windows** et **Type de projet** sur **Bibliothèque**.

1. De la liste filtrée des types de projet, sélectionnez **Windows Desktop Wizard**, puis choisissez **Next**.

1. Dans la configuration de votre nouvelle page **de projet,** entrez *MathLibrary* dans la boîte de **nom du projet** pour spécifier un nom pour le projet. Entrez *StaticMath* dans la boîte **de nom Solution.** Choisissez le bouton **Créer** pour ouvrir le dialogue **du projet Windows Desktop.**

1. Dans le dialogue **Windows Desktop Project,** sous **type d’application**, sélectionnez **Bibliothèque statique (.lib)**.

1. En vertu **d’options supplémentaires**, décocher la case à cocher **en tête précompilée** si elle est cochée. Vérifiez la boîte **de projet vide.**

1. Choisissez **OK** pour créer le projet.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-static-library-project-in-visual-studio-2017"></a>Créer un projet de bibliothèque statique dans Visual Studio 2017

1. Sur la barre de menu, choisissez **File** > **New** > **Project**.

1. Dans la nouvelle boîte de dialogue **project,** sélectionnez Le**bureau Windows****Visual CMD** >  **installé.** >  Dans le volet central, sélectionnez **Assistant Windows Desktop**.

1. Spécifier un nom pour le projet, par exemple, *MathLibrary,* dans la boîte **à noms.** Spécifier un nom pour la solution, par exemple, *StaticMath,* dans la boîte **De nom de solution.** Choisissez le bouton **OK**.

1. Dans le dialogue **Windows Desktop Project,** sous **type d’application**, sélectionnez **Bibliothèque statique (.lib)**.

1. En vertu **d’options supplémentaires**, décochez la case à cocher **d’en-tête précompilée** si elle est cochée. Vérifiez la boîte **de projet vide.**

1. Choisissez **OK** pour créer le projet.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-static-library-project-in-visual-studio-2015"></a>Créer un projet de bibliothèque statique dans Visual Studio 2015

1. Sur la barre de menu, choisissez **File** > **New** > **Project**.

1. Dans la boîte de dialogue **du nouveau projet,** sélectionnez**Les modèles** >  **installés** > **Visual CMMD** > **Win32**. Dans le volet central, sélectionnez **Application console Win32**.

1. Spécifier un nom pour le projet, par exemple, *MathLibrary,* dans la boîte **à noms.** Spécifier un nom pour la solution, par exemple, *StaticMath,* dans la boîte **De nom de solution.** Choisissez le bouton **OK**.

1. Dans le **Win32 Application Wizard**, choisissez **Next**.

1. Dans la page **Paramètres d’application,** sous **type d’application**, sélectionnez **Bibliothèque Statique**. En vertu **d’options supplémentaires**, décocher la case à cocher **en tête précompilée.** Choisissez **Finition** pour créer le projet.

::: moniker-end

## <a name="add-a-class-to-the-static-library"></a><a name="AddClassToLib"></a>Ajouter une classe à la bibliothèque statique

### <a name="to-add-a-class-to-the-static-library"></a>Pour ajouter une classe à la bibliothèque statique

1. Pour créer un fichier d’en-tête pour une nouvelle classe, cliquez à droite pour ouvrir le menu raccourci pour le projet **MathLibrary** dans **Solution Explorer**, puis choisissez **Ajouter** > **un nouvel article**.

1. Dans la boîte de dialogue **Add New Item,** sélectionnez **Visual CMD** > **Code**. Dans le volet central, sélectionnez **Fichier d’en-tête (.h)**. Spécifier un nom pour le fichier d’en-tête, par exemple, *MathLibrary.h,* puis choisissez le bouton **Ajouter.** Un fichier d’en-tête presque vierge est affiché.

1. Ajoutez une déclaration pour `Arithmetic` une classe nommée pour effectuer des opérations mathématiques courantes telles que l’addition, la soustraction, la multiplication et la division. Le code doit ressembler à :

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

1. Pour créer un fichier source pour la nouvelle classe, ouvrez le menu raccourci pour le projet **MathLibrary** dans **Solution Explorer**, puis choisissez **Ajouter** > **un nouvel article**.

1. Dans la boîte de dialogue **Add New Item,** dans le volet central, sélectionnez **le fichier CMD (.cpp)**. Spécifier un nom pour le fichier source, par exemple, *MathLibrary.cpp,* puis choisissez le bouton **Ajouter.** Un fichier source vide s’affiche.

1. Utilisez ce fichier source pour implémenter la fonctionnalité pour la classe `Arithmetic`. Le code doit ressembler à :

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

1. Pour construire la bibliothèque statique, sélectionnez **Build** > **Build Solution** sur la barre de menu. La construction crée une bibliothèque statique, *MathLibrary.lib*, qui peut être utilisé par d’autres programmes.

   > [!NOTE]
   > Lorsque vous générez un projet sur la ligne de commande Visual Studio, vous devez générer le programme en deux étapes. Tout d’abord, exécuter `cl /c /EHsc MathLibrary.cpp` pour compiler le code et créer un fichier d’objets qui s’appelle *MathLibrary.obj*. (La `cl` commande invoque le compilateur, Cl.exe, et l’option `/c` spécifie compiler sans lien. Pour plus d’informations, voir [/c (Compile Sans lien)](../build/reference/c-compile-without-linking.md).) Deuxièmement, `lib MathLibrary.obj` exécutez pour lier le code et créer la bibliothèque statique *MathLibrary.lib*. (La commande `lib` appelle le gestionnaire de bibliothèque Lib.exe. Pour plus d’informations, consultez [LIB Reference](../build/reference/lib-reference.md).)

## <a name="create-a-c-console-app-that-references-the-static-library"></a><a name="CreateAppToRefTheLib"></a>Créez une application console CMD qui fait référence à la bibliothèque statique

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2019"></a>Pour créer une application console CMD qui fait référence à la bibliothèque statique de Visual Studio 2019

1. Dans **Solution Explorer**, cliquez à droite sur le nœud supérieur, Solution **'StaticMath'**, pour ouvrir le menu raccourci. Choisissez **Ajouter** > **un nouveau projet** pour ouvrir la boîte de dialogue Add a New **Project.**

1. En haut du dialogue, définissez le filtre **de type Projet** sur **console**.

1. À partir de la liste des types de projets, choisissez **Application console**, puis choisissez **Suivant**. Dans la page suivante, entrez *MathClient* dans la boîte **nom** pour spécifier un nom pour le projet.

1. Choisissez le bouton **Créer** pour créer le projet client.

1. Une fois que vous avez créé une application console, un programme vide est créé à votre intention. Le nom du fichier source est identique au nom que vous avez choisi précédemment. Dans l’exemple, il `MathClient.cpp`est nommé .

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2017"></a>Pour créer une application console CMD qui fait référence à la bibliothèque statique de Visual Studio 2017

1. Dans **Solution Explorer**, cliquez à droite sur le nœud supérieur, Solution **'StaticMath'**, pour ouvrir le menu raccourci. Choisissez **Ajouter** > **un nouveau projet** pour ouvrir la boîte de dialogue Add a New **Project.**

1. Dans la boîte de dialogue **Add New Project,** sélectionnez **Le** > **bureau Windows**Visual**CMD** > installé . Dans le volet central, sélectionnez **Assistant Windows Desktop**.

1. Spécifier un nom pour le projet, par exemple, *MathClient,* dans la boîte **à noms.** Choisissez le bouton **OK**.

1. Dans le dialogue **Windows Desktop Project,** sous **type d’application**, sélectionnez **Console Application (.exe)**.

1. En vertu **d’options supplémentaires**, décochez la case à cocher **d’en-tête précompilée** si elle est cochée.

1. Choisissez **OK** pour créer le projet.

1. Une fois que vous avez créé une application console, un programme vide est créé à votre intention. Le nom du fichier source est identique au nom que vous avez choisi précédemment. Dans l’exemple, il `MathClient.cpp`est nommé .

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-c-console-app-that-references-the-static-library-in-visual-studio-2015"></a>Pour créer une application console CMD qui fait référence à la bibliothèque statique de Visual Studio 2015

1. Dans **Solution Explorer**, cliquez à droite sur le nœud supérieur, Solution **'StaticMath'**, pour ouvrir le menu raccourci. Choisissez **Ajouter** > **un nouveau projet** pour ouvrir la boîte de dialogue Add a New **Project.**

1. Dans la boîte de dialogue **Add New Project,** sélectionnez **Le** > concept**de cmDmd d’installation** > **.** Dans le volet central, sélectionnez **Application console Win32**.

1. Spécifier un nom pour le projet, par exemple, *MathClient,* dans la boîte **à noms.** Choisissez le bouton **OK**.

1. Dans le dialogue **Win32 Application Wizard,** choisissez **Next**.

1. Sur la page **Paramètres d’application,** sous **type d’application,** assurez-vous que **l’application Console** est sélectionnée. En vertu **d’options supplémentaires,** décocher **l’en-tête précompilé,** puis vérifier la case à cocher **Projet vide.** Choisissez **Finition** pour créer le projet.

1. Pour ajouter un fichier source au projet vide, cliquez à droite pour ouvrir le menu raccourci pour le projet **MathClient** dans **Solution Explorer**, puis choisissez **Ajouter** > **un nouvel article**.

1. Dans la boîte de dialogue **Add New Item,** sélectionnez **Visual CMD** > **Code**. Dans le volet central, sélectionnez **Fichier C++ (.cpp)**. Spécifier un nom pour le fichier source, par exemple, *MathClient.cpp,* puis choisissez le bouton **Ajouter.** Un fichier source vide s’affiche.

::: moniker-end

## <a name="use-the-functionality-from-the-static-library-in-the-app"></a><a name="UseLibInApp"></a>Utilisez la fonctionnalité de la bibliothèque statique de l’application

### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Pour utiliser les fonctionnalités de la bibliothèque statique dans l’application

1. Avant de pouvoir utiliser les routines mathématiques dans la bibliothèque statique, vous devez la référencer. Ouvrez le menu raccourci pour le projet **MathClient** dans **Solution Explorer**, puis choisissez **Add** > **Reference**.

1. La boîte de dialogue **Ajouter une référence** répertorie les bibliothèques que vous pouvez référencer. **L’onglet Projets** répertorie les projets dans la solution actuelle et toutes les bibliothèques qu’ils renvoient. Ouvrez l’onglet **Projets,** sélectionnez la case à cocher **MathLibrary,** puis choisissez le bouton **OK.**

1. Pour référencer le fichier d’en-tête, `MathLibrary.h` vous devez modifier le chemin des répertoires inclus. Dans **Solution Explorer**, cliquez à droite sur **MathClient** pour ouvrir le menu raccourci. Choisissez **des propriétés** pour ouvrir la boîte de dialogue **MathClient Property Pages.**

1. Dans la boîte de dialogue **MathClient Property Pages,** définissez la **configuration** drop-down à **toutes les configurations**. Définissez la **plate-forme** drop-down à **toutes les plates-formes**.

1. Sélectionnez la page **Propriétés** > Configuration**C/CMD** > **General.** Dans la propriété **Additional Include Directories,** spécifiez le chemin de l’annuaire **MathLibrary,** ou naviguez pour elle.

   Pour parcourir le chemin du répertoire :

   1. Ouvrez la liste d’abandon de la valeur de la propriété **d’inclus d’annuaires supplémentaires,** puis choisissez **Edit**.

   1. Dans la boîte de dialogue **d’inclus supplémentaires,** cliquez double en haut de la boîte de texte. Ensuite, choisissez le bouton ellipsis (**...**) à la fin de la ligne.

   1. Dans la boîte de dialogue **Select Directory,** naviguez jusqu’à un niveau, puis sélectionnez le répertoire **MathLibrary.** Choisissez ensuite le bouton **Select Folder** pour enregistrer votre sélection.

   1. Dans la boîte de dialogue **d’annuaires inclus supplémentaire,** choisissez le bouton **OK.**

   1. Dans la boîte de dialogue **de Pages de propriété,** choisissez le bouton **OK** pour enregistrer vos modifications au projet.

1. Vous pouvez maintenant `Arithmetic` utiliser la classe `#include "MathLibrary.h"` de cette application en incluant l’en-tête de votre code. Remplacez le `MathClient.cpp` contenu de ce code :

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

1. Pour construire l’exécutable, choisissez **Build** > **Build Solution** sur la barre de menu.

## <a name="run-the-app"></a><a name="RunApp"></a>Exécuter l’application

### <a name="to-run-the-app"></a>Pour exécuter l’application

1. Assurez-vous que **MathClient** est sélectionné comme projet par défaut. Pour le sélectionner, cliquez à droite pour ouvrir le menu raccourci pour **MathClient** dans **Solution Explorer**, puis choisissez Set **comme StartUp Project**.

1. Pour exécuter le projet, sur la barre de menu, choisissez **Debug** > **Start Without Debugging**. La sortie doit ressembler à :

    ```Output
    a + b = 106.4
    a - b = -91.6
    a * b = 732.6
    a / b = 0.0747475
    ```

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : Création et utilisation d’une bibliothèque de liens dynamiques (CMD)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)<br/>
[Applications de bureau (Visual C++)](../windows/desktop-applications-visual-cpp.md)<br/>
