---
title: 'Procédure pas à pas : Créer et utiliser votre propre bibliothèque de liens dynamiques (C++)'
description: Utilisez C++ pour créer une bibliothèque de liens dynamiques (DLL) Windows dans Visual Studio.
ms.custom: conceptual
ms.date: 04/22/2019
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: 53cde029973c14bfc5aae521946ebeadbed738ca
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611983"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Procédure pas à pas : Créer et utiliser votre propre bibliothèque de liens dynamiques (C++)

Cette procédure pas à pas montre comment utiliser l’IDE Visual Studio pour créer votre propre bibliothèque de liens dynamiques (DLL) écrite en C++, puis l’utiliser à partir d’une autre application C++. Les DLL (également appelés bibliothèques partagées dans les systèmes d’exploitation UNIX) sont un des types de composants Windows les plus utiles. Vous pouvez les utiliser pour partager du code et des ressources ainsi que pour réduire la taille de vos applications et faciliter leur maintenance et leur extension. Dans le cadre de cette procédure pas à pas, vous créez tout d’abord une DLL qui implémente certaines fonctions mathématiques, puis une application console qui utilise les fonctions de la DLL. Tout au long du processus, vous êtes initié à certaines des techniques de programmation et des conventions utilisées dans les DLL Windows.

Cette procédure pas à pas couvre les tâches suivantes :

- Créer un projet DLL dans Visual Studio.

- Ajouter des fonctions et des variables exportées à la DLL.

- Créez un projet d’application console dans Visual Studio.

- Utilisez les fonctions et variables importées à partir de la DLL dans l’application console.

- Téléchargez l’application terminée.

Comme une bibliothèque liée statiquement, une DLL _exporte_ des variables, des fonctions et des ressources par nom et votre application _importe_ ces noms pour utiliser ces variables, fonctions et ressources. Contrairement à une bibliothèque liée statiquement, Windows connecte les importations dans votre application aux exportations dans une DLL au moment du chargement ou au moment de l’exécution, au lieu de les connecter au moment de la liaison. Windows requiert des informations supplémentaires qui ne font pas partie du modèle de compilation standard C++ pour établir ces connexions. Le compilateur MSVC implémente certaines extensions spécifiques dans C++ pour fournir ces informations supplémentaires. Nous allons expliquer ces extensions au fur et à mesure.

Cette procédure pas à pas crée deux solutions Visual Studio ; une qui crée la DLL et une qui crée l’application cliente. La DLL utilise la convention d’appel C et peut donc être appelée à partir d’applications créées à l’aide d’autres langues, à condition que la plateforme et les conventions d’appel et de liaison correspondent. L’application cliente utilise _liaison implicite_, où Windows lie l’application à la DLL au moment du chargement. Cette liaison permet à l’application d’appeler les fonctions fournies par la DLL, telles que les fonctions dans une bibliothèque liée statiquement.

Cette procédure pas à pas n’aborde pas quelques situations courantes. Elle ne montre pas comment d’autres langages de programmation utilisent les DLL C++. Elle ne montre pas comment créer une DLL de ressource uniquement. Elle ne montre pas non plus comment utiliser une liaison explicite pour charger des DLL pendant l’exécution plutôt qu’au moment du chargement. Rassurez-vous, vous pouvez utiliser Visual C++ pour effectuer toutes ces tâches. Pour obtenir des liens vers d’autres informations sur les DLL, consultez [Créer des DLL C/C++ DLL dans Visual Studio](dlls-in-visual-cpp.md). Pour plus d’informations sur les liaisons implicites et explicites, consultez [Détermination de la méthode de liaison à utiliser](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Pour plus d’informations sur la création de DLL C++ à utiliser avec des langages de programmation qui ont recours à des conventions de liaison en langage C, consultez [Exportation de fonctions C++ à utiliser dans des exécutables en langage C](exporting-cpp-functions-for-use-in-c-language-executables.md). Pour plus d’informations sur la création de DLL à utiliser avec les langages .NET, consultez [Appel de fonctions DLL à partir d’applications Visual Basic](calling-dll-functions-from-visual-basic-applications.md).

## <a name="prerequisites"></a>Prérequis

- Un ordinateur qui exécute Microsoft Windows 7 ou versions ultérieures. Nous recommandons Windows 10 pour une expérience de développement optimale.

- Une copie de Visual Studio. Pour plus d’informations sur le téléchargement et l’installation de Visual Studio, consultez [Installer Visual Studio](/visualstudio/install/install-visual-studio). Lorsque vous exécutez le programme d’installation, assurez-vous que la charge de travail **développement Desktop en C++** est activée. Ne vous inquiétez pas si vous n’avez pas installé cette charge de travail en même temps que Visual Studio. Vous pouvez réexécuter le programme d’installation et l’installer maintenant.

   ![Développement Desktop en C++](media/desktop-development-with-cpp.png "Développement Desktop en C++")

- Une compréhension des principes fondamentaux de l’utilisation de l’IDE Visual Studio. Si vous avez déjà utilisé des applications de bureau Windows, vous n’aurez probablement aucun mal à suivre. Pour une introduction, consultez [Visite guidée des fonctionnalités de l’IDE Visual Studio](/visualstudio/ide/visual-studio-ide).

- Une compréhension de suffisamment de notions de base du langage C++ pour pouvoir suivre. Ne vous inquiétez pas, nous ne faisons rien de bien compliqué.

## <a name="create-the-dll-project"></a>Créer le projet DLL

Dans cet ensemble de tâches, vous créez un projet pour votre DLL, ajoutez du code et générez-le. Pour commencer, démarrez l’IDE Visual Studio et connectez-vous si nécessaire. Les instructions varient légèrement selon la version de Visual Studio que vous utilisez. Assurez-vous que vous avez sélectionné la version correcte dans le contrôle en haut à gauche de cette page.

::: moniker range="=vs-2019"

### <a name="to-create-a-dll-project-in-visual-studio-2019"></a>Pour créer un projet DLL dans Visual Studio 2019

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

   ![Créer un projet DLL](media/create-new-dll-project-2019.png "Créer le projet MathLibrary")

1. En haut de la boîte de dialogue, définissez **Langage** sur **C++**, **Plateforme** sur **Windows** et **Type de projet** sur **Bibliothèque**. 

1. Dans la liste filtrée des types de projets, choisissez **Bibliothèque de liens dynamiques (DLL)**, puis choisissez **Suivant**. Dans la page suivante, entrez `MathLibrary` dans la zone de texte **nom** pour donner un nom au projet et indiquer son emplacement si vous le souhaitez.

1. Choisissez le bouton **Créer** pour créer le projet.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-dll-project-in-visual-studio-2017"></a>Pour créer un projet DLL dans Visual Studio 2017

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.

1. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **Installé** et **Visual C++** si nécessaire, puis choisissez **Windows Desktop**. Dans le volet central, sélectionnez **Assistant Windows Desktop**. Entrez `MathLibrary` dans la zone de texte **Nom** pour donner un nom au projet.

   ![Nommer le projet MathLibrary](media/mathlibrary-new-project-name-153.png "Nommer le projet MathLibrary")

1. Choisissez le bouton **OK** pour ignorer la boîte de dialogue **Nouveau projet** et démarrez l’Assistant **Windows Desktop**.

1. Dans l’Assistant **projet Windows Desktop**, sous **Type d’application**, sélectionnez **Bibliothèque de liens dynamiques (.dll)**.

   ![Créer une DLL dans l’Assistant de projet Windows Desktop](media/mathlibrary-desktop-project-wizard-dll.png "Créer une DLL dans l’Assistant de projet Windows Desktop")

1. Choisissez le bouton **OK** pour créer le projet.

> [!NOTE]
> Des étapes supplémentaires sont nécessaires pour résoudre un problème dans Visual Studio 2017 version 15.3. Suivez ces instructions pour voir si vous devez effectuer cette modification.
>
>1. Dans l’**Explorateur de solutions**, si vous ne l’avez pas encore fait, sélectionnez le projet **MathLibrary** sous **Solution « MathLibrary »**.
>
>1. Dans la barre de menus, choisissez **Projet** > **Propriétés**.
>
>1. Dans le volet gauche de la boîte de dialogue **Pages de propriétés**, sélectionnez **Préprocesseur** sous **Propriétés de configuration** > **C/C++**. Vérifiez le contenu de la propriété **Définitions de préprocesseur**.<br/><br/>![Vérifier la propriété des définitions de préprocesseur](media/mathlibrary-153bug-preprocessor-definitions-check.png "Vérifier la propriété des définitions de préprocesseur")<br/><br/>Si vous voyez **MATHLIBRARY&#95;EXPORTS** dans la liste **Définitions de préprocesseur**, vous n’avez pas besoin de modifier quoi que ce soit. Si vous voyez **MathLibrary&#95;EXPORTS** au lieu de cela, continuez à suivre ces étapes.
>
>1. En haut de la boîte de dialogue **Pages de propriétés**, définissez la liste déroulante **Configuration** sur **Toutes les configurations**.
>
>1. Dans le volet des propriétés, sélectionnez le contrôle de la liste déroulante en regard de la zone d’édition pour **Définitions de préprocesseur**, puis choisissez **Modifier**.<br/><br/>![Modifiez la propriété Définitions de préprocesseur](media/mathlibrary-153bug-preprocessor-definitions-property.png "Modifiez la propriété Définitions de préprocesseur")
>
>1. Dans le volet supérieur de la boîte de dialogue **Définitions de préprocesseur**, ajoutez un nouveau symbole, `MATHLIBRARY_EXPORTS`.<br/><br/>![Ajoutez le symbole MATHLIBRARY_EXPORTS](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "Ajoutez le symbole MATHLIBRARY_EXPORTS")
>
>1. Choisissez **OK** pour faire ignorer la boîte de dialogue **Définitions de préprocesseur**, puis choisissez **OK** pour enregistrer vos modifications apportées aux propriétés du projet.

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>Pour créer un projet DLL dans des versions antérieures de Visual Studio

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **Installé** > **Modèles** et sélectionnez **Visual C++** , puis, dans le volet central, sélectionnez **Application Console Win32**. Entrez `MathLibrary` dans la zone d’édition **Nom** pour donner un nom au projet.

   ![Nommer le projet MathLibrary](media/mathlibrary-project-name.png "Nommer le projet MathLibrary")

1. Choisissez le bouton **OK** pour ignorer la boîte de dialogue **Nouveau projet** et démarrez l’**Assistant Application Win32**.

   ![Présentation de l’Assistant Application Win32](media/mathlibrary-project-wizard-1.png "Présentation de l’Assistant Application Win32")

1. Choisissez le bouton **Suivant**. À la page **Paramètres d'application**, sous **Type d’application**, sélectionnez **DLL**.

   ![Créez des DLL dans l’Assistant Application Win32](media/mathlibrary-project-wizard-2.png "Créez des DLL dans l’Assistant Application Win32")

1. Choisissez le bouton **Terminer** pour créer le projet.

Lorsque l’Assistant a terminé la solution, vous pouvez voir les fichiers projet et source générés dans la fenêtre de **l’Explorateur de solutions** dans Visual Studio.

![Solution générée dans Visual Studio](media/mathlibrary-solution-explorer-153.png "Solution générée dans Visual Studio")

Pour l’instant, cette DLL ne fait pas grand-chose. Ensuite, vous créez un fichier d’en-tête pour déclarer les fonctions exportées par votre DLL, puis vous ajoutez les définitions de fonction à la DLL pour la rendre plus utile.

::: moniker-end

### <a name="to-add-a-header-file-to-the-dll"></a>Pour ajouter un fichier d’en-tête à la DLL

1. Pour créer un fichier d'en-tête pour vos fonctions, dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.

1. Dans le volet gauche de la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Visual C++**. Dans le volet central, sélectionnez **Fichier d’en-tête (.h)**. Spécifiez `MathLibrary.h` comme nom pour le fichier d’en-tête.

   ![Ajouter un en-tête dans la boîte de dialogue Ajouter un nouvel élément](media/mathlibrary-add-new-item-header-file.png "Ajouter un fichier d’en-tête dans la boîte de dialogue Ajouter un nouvel élément")

1. Choisissez le bouton **Ajouter** pour générer un fichier d’en-tête vide, qui s’affiche dans une nouvelle fenêtre d’éditeur.

   ![Fichier MathLibrary.h vide dans l’éditeur](media/edit-empty-mathlibrary-header.png "Fichier MathLibrary.h vide dans l’éditeur")

1. Remplacez le contenu du fichier d’en-tête par ce code :

   ```cpp
   // MathLibrary.h - Contains declarations of math functions
   #pragma once

   #ifdef MATHLIBRARY_EXPORTS
   #define MATHLIBRARY_API __declspec(dllexport)
   #else
   #define MATHLIBRARY_API __declspec(dllimport)
   #endif

   // The Fibonacci recurrence relation describes a sequence F
   // where F(n) is { n = 0, a
   //               { n = 1, b
   //               { n > 1, F(n-2) + F(n-1)
   // for some initial integral values a and b.
   // If the sequence is initialized F(0) = 1, F(1) = 1,
   // then this relation produces the well-known Fibonacci
   // sequence: 1, 1, 2, 3, 5, 8, 13, 21, 34, ...

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   extern "C" MATHLIBRARY_API void fibonacci_init(
       const unsigned long long a, const unsigned long long b);

   // Produce the next value in the sequence.
   // Returns true on success and updates current value and index;
   // false on overflow, leaves current value and index unchanged.
   extern "C" MATHLIBRARY_API bool fibonacci_next();

   // Get the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned long long fibonacci_current();

   // Get the position of the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned fibonacci_index();
   ```

Ce fichier d’en-tête déclare certaines fonctions pour produire une séquence Fibonacci généralisée avec deux valeurs initiales. Un appel à `fibonacci_init(1, 1)` génère la séquence familière de nombres Fibonacci.

Notez les instructions du préprocesseur en haut du fichier. Par défaut, le modèle Nouveau projet pour une DLL ajoute **\<em>PROJECTNAME\</em>&#95;EXPORTS** aux macros de préprocesseur définis pour le projet de DLL. Dans cet exemple, Visual Studio définit **MATHLIBRARY&#95;EXPORTS** lorsque votre projet de DLL MathLibrary est créé. 

::: moniker range="=vs-2017"

(L’Assistant dans Visual Studio 2017 version 15.3 ne force pas la saisie de cette définition de symbole en majuscules. Si vous nommez votre projet « MathLibrary », le symbole défini est MathLibrary&#95;EXPORTS au lieu de MATHLIBRARY&#95;EXPORTS. C’est pourquoi il existe les étapes supplémentaires ci-dessus pour ajouter ce symbole.)

::: moniker-end

Lorsque le macro **MATHLIBRARY&#95;EXPORTS** est défini, le macro **MATHLIBRARY&#95;API** définit le modificateur `__declspec(dllexport)` sur les déclarations de fonctions. Ce modificateur indique au compilateur et à l’éditeur de liens d’exporter une fonction ou une variable à partir de la DLL afin qu’elle puisse être utilisée par d’autres applications. Lorsque **MATHLIBRARY&#95;EXPORTS** n’est pas défini, par exemple, lorsque le fichier d’en-tête est inclus dans une application cliente, **MATHLIBRARY&#95;API** applique le modificateur `__declspec(dllimport)` aux déclarations. Ce modificateur optimise l'importation de la fonction dans une application. Pour plus d’informations, consultez [dllexport, dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>Pour ajouter une implémentation à la DLL

::: moniker range="vs-2019"

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Fichiers sources** et ajoutez un nouveau fichier .cpp appelé `MathLibrary.cpp` de la même façon que vous avez ajouté un nouveau fichier d’en-tête à l’étape précédente.

::: moniker-end

1. Dans la fenêtre de l’éditeur, sélectionnez l’onglet **MathLibrary.cpp** s’il est déjà ouvert. S’il ne l’est pas, dans **l’Explorateur de solutions**, ouvrez **MathLibrary.cpp** dans le dossier **Fichiers sources** du projet **MathLibrary**.

1. Dans l’éditeur, remplacez le contenu du fichier de code MathLibrary.cpp par le code suivant :

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h" // use pch.h in Visual Studio 2019
   #include <utility>
   #include <limits.h>
   #include "MathLibrary.h"

   // DLL internal state variables:
   static unsigned long long previous_;  // Previous value, if any
   static unsigned long long current_;   // Current sequence value
   static unsigned index_;               // Current seq. position

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   void fibonacci_init(
       const unsigned long long a,
       const unsigned long long b)
   {
       index_ = 0;
       current_ = a;
       previous_ = b; // see special case when initialized
   }

   // Produce the next value in the sequence.
   // Returns true on success, false on overflow.
   bool fibonacci_next()
   {
       // check to see if we'd overflow result or position
       if ((ULLONG_MAX - previous_ < current_) ||
           (UINT_MAX == index_))
       {
           return false;
       }

       // Special case when index == 0, just return b value
       if (index_ > 0)
       {
           // otherwise, calculate next sequence value
           previous_ += current_;
       }
       std::swap(current_, previous_);
       ++index_;
       return true;
   }

   // Get the current value in the sequence.
   unsigned long long fibonacci_current()
   {
       return current_;
   }

   // Get the current index position in the sequence.
   unsigned fibonacci_index()
   {
       return index_;
   }
   ```

Pour vérifier que tout fonctionne à ce stade, compilez la bibliothèque de liens dynamiques. Pour ce faire, choisissez **Créer** > **Créer des solution** dans la barre de menus. Le résultat doit ressembler à ce qui suit :

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Félicitations, vous avez créé une DLL à l’aide de Visual C++ ! Ensuite, vous allez créer une application cliente qui utilise les fonctions exportées par la DLL.

## <a name="create-a-client-app-that-uses-the-dll"></a>Créer une application cliente qui utilise la DLL

Lorsque vous créez une DLL, vous devez penser à la façon dont votre DLL peut être utilisée. Pour compiler du code qui appelle les fonctions exportées par une DLL, les déclarations doivent être incluses dans le code source du client. Au moment de la liaison, lorsque ces appels aux fonctions DLL sont résolus, l’éditeur de liens doit comporter une *bibliothèque d’importation*, un fichier de bibliothèque spécial qui, au lieu du code réel, contient des informations indiquant à Windows comment rechercher les fonctions. Et en cours d’exécution, la DLL doit être à la disposition du client à un emplacement que le système d’exploitation peut trouver.

Pour utiliser une DLL (la vôtre ou une DLL d’un tiers), votre projet d’application cliente doit rechercher les en-têtes qui déclarent les exportations de la DLL, les bibliothèques d’importation pour l’éditeur de liens et la DLL proprement dite. Une méthode peut consister à copier tous ces fichiers dans votre projet client. Pour les DLL de tiers qui sont peu susceptibles de changer pendant le développement de votre client, cette méthode peut être la meilleure façon de les utiliser. Toutefois, lorsque vous créez également la DLL, il est préférable d’éviter la duplication. Si vous effectuez une copie des fichiers DLL qui sont en cours de développement, vous pouvez par inadvertance modifier un fichier d’en-tête dans une copie, mais pas dans l’autre, ou utiliser une bibliothèque obsolète. Pour éviter ce problème, nous vous recommandons de définir le chemin include dans votre projet de client pour inclure les fichiers d’en-tête DLL à partir du projet DLL. Définissez également le chemin de la bibliothèque dans votre projet client pour inclure les bibliothèques d’importation DLL à partir du projet DLL. Et pour finir, copiez la DLL créée à partir du projet DLL dans votre répertoire de sortie de build. Cette étape permet à votre application cliente d’utiliser le code DLL que vous créez.

::: moniker range="vs-2019"

### <a name="to-create-a-client-app-in-visual-studio-2019"></a>Pour créer une application cliente dans Visual Studio 2019

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. En haut de la boîte de dialogue, définissez **Langage** sur **C++**, **Plateforme** sur **Windows** et **Type de projet** sur **Console**. 

1. À partir de la liste des types de projets, choisissez **Application console**, puis choisissez **Suivant**. Dans la page suivante, entrez `MathClient` dans la zone de texte **nom** pour donner un nom au projet et indiquer son emplacement si vous le souhaitez.

   ![Nommer le projet client](media/mathclient-project-name-2019.png "Nommer le projet client")

1. Choisissez le bouton **Créer** pour créer le projet client.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-client-app-in-visual-studio-2017"></a>Pour créer une application cliente dans Visual Studio 2017

1. Pour créer une application C++ qui utilise la DLL que vous avez créée, dans la barre de menus, choisissez **Fichier**, > **Nouveau** > **Projet**.

1. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, sélectionnez **Windows Desktop** sous **Installé** > **Visual C++**. Dans le volet central, sélectionnez **Assistant Windows Desktop**. Indiquez le nom du projet, `MathClient` dans la zone d’édition **Nom**.

   ![Nommer le projet client](media/mathclient-new-project-name-153.png "Nommer le projet client")

1. Choisissez **OK** pour démarrer l’Assistant  **projet Windows Desktop**. Dans l’Assistant, choisissez **OK** pour créer le projet d’application cliente.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>Pour créer une application cliente dans des versions antérieures de Visual Studio 2017

1. Pour créer une application C++ qui utilise la DLL que vous avez créée, dans la barre de menus, choisissez **Fichier**, > **Nouveau** > **Projet**.

1. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, sélectionnez **Win32** sous **Installé** > **Modèles** > **Visual C++**. Dans le volet central, sélectionnez **Application console Win32**. Indiquez le nom du projet, `MathClient` dans la zone d’édition **Nom**.

   ![Nommer le projet client](media/mathclient-project-name.png "Nommer le projet client")

1. Choisissez le bouton **OK** pour ignorer la boîte de dialogue **Nouveau projet** et démarrez l’**Assistant Application Win32**. Dans la page **Vue d'ensemble** de la boîte de dialogue **Assistant Application Win32** , choisissez le bouton **Suivant** .

1. Dans la page **Paramètres de l'application** sous **Type d'application**, sélectionnez **Application console** si elle n’est pas encore sélectionnée.

1. Choisissez le bouton **Terminer** pour créer le projet.

::: moniker-end

Lorsque l’Assistant a terminé, un projet d’application console minimal est créé pour vous. Le nom du fichier source principal est identique au nom du projet que vous avez saisi précédemment. Dans cet exemple, il est nommé **MathClient.cpp**. Vous pouvez le créer, mais il n’utilise pas encore votre DLL.

Ensuite, pour appeler les fonctions MathLibrary dans votre code source, votre projet doit inclure le fichier MathLibrary.h. Vous pouvez copier ce fichier d’en-tête dans votre projet d’application cliente, puis l’ajouter au projet comme élément existant. Cette méthode peut être un bon choix pour des bibliothèques tierces. Toutefois, si vous travaillez sur le code de votre DLL en même temps que votre client, ceci peut entraîner dans un fichier en-tête des modifications qui ne seront pas visibles dans l’autre. Pour éviter ce problème, vous pouvez modifier le chemin **Autres répertoires Include** dans votre projet pour inclure le chemin d’accès à l’en-tête d’origine.

### <a name="to-add-the-dll-header-to-your-include-path"></a>Pour ajouter l’en-tête de la DLL à votre chemin Include

1. Cliquez avec le bouton droit sur le nœud **MathClient** dans **l’Explorateur de solutions** pour ouvrir la boîte de dialogue **Pages de propriétés**.

1. Dans la zone de liste déroulante **Configuration**, sélectionnez **Toutes les configurations** si ce n’est pas encore fait.

1. Dans le volet gauche, sélectionnez **Général** sous **Propriétés de configuration** > **C/C++**.

1. Dans le volet des propriétés, sélectionnez le contrôle de la liste déroulante en regard de la zone d’édition pour **Autres répertoires Include**, puis choisissez **Modifier**.

   ![Modifier la propriété Autres répertoires Include](media/mathclient-additional-include-directories-property.png "Modifier la propriété Autres répertoires Include")

1. Double-cliquez dans le volet supérieur de la boîte de dialogue **Autres répertoires Include** pour activer un contrôle d’édition.

1. Dans le contrôle d’édition, spécifiez le chemin de l’emplacement du fichier d'en-tête **MathLibrary.h**. Dans ce cas, vous pouvez utiliser un chemin relatif du dossier qui contient vos fichiers .cpp dans le projet client au dossier qui contient le fichier .h file dans le projet DLL. Si votre projet client est dans une solution distincte dans le même dossier que la solution DLL, le chemin relatif doit ressembler à ceci :

   `..\..\MathLibrary\MathLibrary`

   Si vos projets DLL et client se trouvent dans la même solution, ou que les solutions sont dans des dossiers différents, vous devez ajuster le chemin relatif en conséquence.

   ![Ajouter l’emplacement de l’en-tête à la propriété Autres répertoires Include](media/mathclient-additional-include-directories.png "Ajouter l’emplacement de l’en-tête à la propriété Autres répertoires Include")

1. Une fois que vous avez saisi le chemin du fichier d'en-tête dans la boîte de dialogue **Autres répertoires Include** , choisissez le bouton **OK** pour revenir à la boîte de dialogue **Pages de propriétés** , puis choisissez le bouton **OK** pour enregistrer vos modifications.

Vous pouvez désormais inclure le fichier **MathLibrary.h** et utiliser les fonctions qu’il déclare dans votre application cliente. Remplacez le contenu de **MathClient.cpp** à l’aide de ce code :

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
// #include "pch.h" Uncomment for Visual Studio 2017 and earlier
#include <iostream>
#include "MathLibrary.h"

int main()
{
    // Initialize a Fibonacci relation sequence.
    fibonacci_init(1, 1);
    // Write out the sequence values until overflow.
    do {
        std::cout << fibonacci_index() << ": "
            << fibonacci_current() << std::endl;
    } while (fibonacci_next());
    // Report count of values written before overflow.
    std::cout << fibonacci_index() + 1 <<
        " Fibonacci sequence values fit in an " <<
        "unsigned 64-bit integer." << std::endl;
}
```

Ce code peut être compilé, mais pas lié, car l’éditeur de liens ne peut pas encore trouver la bibliothèque d’importation requise pour créer l’application. L’éditeur de liens doit rechercher le fichier MathLibrary.lib pour une liaison réussie. Ajouter le fichier MathLibrary.lib à la build en définissant la propriété **Dépendances supplémentaires**. Là encore, vous pouvez copier le fichier de bibliothèque dans votre projet d’application cliente, mais si la bibliothèque et l’application cliente sont en cours de développement, ceci peut entraîner dans une copie des modifications qui ne sont pas visibles dans l’autre. Pour éviter ce problème, vous pouvez modifier le chemin **Répertoires de bibliothèques supplémentaires** dans votre projet pour inclure le chemin de la bibliothèque d’origine lors de la liaison.

### <a name="to-add-the-dll-import-library-to-your-project"></a>Pour ajouter la bibliothèque d’importation DLL à votre projet

1. Cliquez avec le bouton droit sur le nœud **MathClient** dans **l’Explorateur de solutions** pour ouvrir la boîte de dialogue **Pages de propriétés**.

1. Dans la zone de liste déroulante **Configuration**, sélectionnez **Toutes les configurations** si ce n’est pas encore fait. Ce paramètre garantit que le chemin est défini pour les versions de débogage et de mise en production.

1. Dans le volet gauche, sélectionnez **Entrée** sous **Propriétés de configuration** > **Éditeur de liaison**. Dans le volet des propriétés, sélectionnez le contrôle de la liste déroulante en regard de la zone d’édition pour les **Dépendances supplémentaires**, puis choisissez **Modifier**.

   ![Modifier la propriété Dépendances supplémentaires](media/mathclient-additional-dependencies-property.png "Modifier la propriété Dépendances supplémentaires")

1. Dans la boîte de dialogue **Dépendances supplémentaires**, ajoutez `MathLibrary.lib` à la liste dans le contrôle d'édition supérieur.

   ![Ajoutez la dépendance de bibliothèque](media/mathclient-additional-dependencies.png "Ajoutez la dépendance de bibliothèque")

1. Choisissez **OK** pour revenir à la boîte de dialogue **Pages de propriétés**.

1. Dans le volet gauche, sélectionnez **Général** sous **Propriétés de configuration** > **Éditeur de liens**. Dans le volet des propriétés, sélectionnez le contrôle de la liste déroulante en regard de la zone d’édition pour **Répertoires de bibliothèques supplémentaires**, puis choisissez **Modifier**.

   ![Modifier la propriété Répertoires de bibliothèques supplémentaires](media/mathclient-additional-library-directories-property.png "Modifier la propriété Répertoires de bibliothèques supplémentaires")

1. Double-cliquez dans le volet supérieur de la boîte de dialogue **Répertoires de bibliothèques supplémentaires** pour activer un contrôle d’édition. Dans le contrôle d’édition, spécifiez le chemin de l’emplacement du fichier **MathLibrary.lib**. Entrez cette valeur pour utiliser une macro qui fonctionne pour les versions de débogage et de mise en production :

   `..\..\MathLibrary\$(IntDir)`

   ![Ajouter le répertoire de la bibliothèque](media/mathclient-additional-library-directories.png "Ajouter le répertoire de la bibliothèque")

1. Une fois que vous avez saisi le chemin du fichier de bibliothèque dans la boîte de dialogue **Répertoires de bibliothèques supplémentaires**, choisissez le bouton **OK** pour revenir à la boîte de dialogue **Pages de propriétés**.

Votre application cliente peut maintenant compiler et lier correctement, mais elle n’a toujours pas tout ce dont elle a besoin pour s’exécuter. Lorsque le système d’exploitation charge votre application, il recherche la DLL MathLibrary. S’il ne la trouve pas dans certains répertoires du système, dans le chemin de l’environnement ou dans le répertoire de l’application locale, le chargement échoue. Une façon d’éviter ce problème consiste à copier la DLL dans le répertoire qui contient votre exécutable client dans le cadre du processus de création. Pour copier la DLL, vous pouvez ajouter un **événement post-build** à votre projet, pour ajouter une commande qui copie la DLL dans votre répertoire de sortie de build. La commande spécifiée ici copie la DLL uniquement si elle est manquante ou si elle a changé et utilise des macros pour copier vers les emplacements corrects de débogage ou de mise en production ou à partir de ces derniers pour votre configuration.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>Pour copier la DLL dans un événement post-build

1. Cliquez avec le bouton droit sur le nœud **MathClient** dans **l’Explorateur de solutions** pour ouvrir la boîte de dialogue **Pages de propriétés**.

1. Dans la zone de liste déroulante Configuration, sélectionnez **Toutes les configurations** si ce n’est pas encore fait.

1. Dans le volet gauche, sélectionnez **Événement post-build** sous **Propriétés de configuration** > **Événements de build**.

1. Dans le volet des propriétés, sélectionnez le contrôle d’édition dans le champ **Ligne de commande**, puis entrez la commande suivante :

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![Ajouter la commande post-build](media/mathclient-post-build-command-line.png "Ajouter la commande post-build")

1. Choisissez le bouton **OK** pour enregistrer les changements que vous avez apportés aux propriétés du projet.

Maintenant, votre application cliente a tout ce dont il a besoin pour générer et exécuter. Compilez l’application en sélectionnant **Build**,  > **Générer la solution** dans la barre de menus. La fenêtre **Sortie** dans Visual Studio doit afficher quelque chose comme :

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>pch.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Félicitations, vous avez créé une application qui appelle des fonctions dans votre DLL. Exécutez maintenant votre application pour voir ce qu’elle fait. Dans la barre de menus, choisissez **Déboguer** > **Démarrer sans débogage**. Visual Studio ouvre une fenêtre de commande dans laquelle le programme doit exécuter. La dernière partie de la sortie doit avoir cette forme :

![Démarrer l’application cliente sans débogage](media/mathclient-run-without-debugging.png "Démarrer l’application cliente sans débogage")

Appuyez sur une touche pour masquer la fenêtre de commande.

Maintenant que vous avez créé une DLL et une application cliente, vous pouvez faire des essais. Essayez de définir des points d’arrêt dans le code de l’application cliente et exécutez l’application dans le débogueur. Regardez ce qui se passe lorsque vous parcourez un appel de bibliothèque. Ajoutez d’autres fonctions à la bibliothèque, ou écrivez une autre application cliente qui utilise votre DLL.

Lorsque vous déployez votre application, vous devez également déployer les DLL qu’elle utilise. La manière la plus simple de mettre les DLL que vous générez ou celles de tiers que vous incluez à la disposition de votre application consiste à les placer dans le même répertoire que votre application. C’est ce que l’on appelle aussi le *déploiement app-local*. Pour plus d’informations sur le déploiement, consultez [Deployment in Visual C++](../windows/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Voir aussi

[Appel de fonctions de la DLL à partir d’applications Visual Basic](calling-dll-functions-from-visual-basic-applications.md)
