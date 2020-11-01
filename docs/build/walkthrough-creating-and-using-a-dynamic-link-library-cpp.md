---
title: 'Procédure pas à pas : création et utilisation de votre propre bibliothèque de liens dynamiques (C++)'
description: Utilisez C++ pour créer une bibliothèque de liens dynamiques (DLL) Windows dans Visual Studio.
ms.custom: conceptual
ms.date: 08/22/2019
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: 0018df31e19a3f1a68a1c4a0bde37d6fa2678406
ms.sourcegitcommit: 868838273eda35eb72c78dccf4121940dcc04706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2020
ms.locfileid: "92924481"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Procédure pas à pas : création et utilisation de votre propre bibliothèque de liens dynamiques (C++)

Cette procédure pas à pas montre comment utiliser l’IDE de Visual Studio pour créer votre propre bibliothèque de liens dynamiques (DLL) écrite en Microsoft C++ (MSVC). Il montre ensuite comment utiliser la DLL à partir d’une autre application C++. Les dll (également appelées *bibliothèques partagées* dans les systèmes d’exploitation basés sur UNIX) sont l’un des types de composants Windows les plus utiles. Vous pouvez les utiliser pour partager du code et des ressources, et pour réduire la taille de vos applications. Les dll peuvent même faciliter le service et l’extension de vos applications.

Dans cette procédure pas à pas, vous allez créer une DLL qui implémente certaines fonctions mathématiques. Vous allez ensuite créer une application console qui utilise les fonctions de la DLL. Vous obtiendrez également une présentation de certaines des techniques de programmation et des conventions utilisées dans les dll Windows.

Cette procédure pas à pas couvre les tâches suivantes :

- Créer un projet DLL dans Visual Studio.

- Ajouter des fonctions et des variables exportées à la DLL.

- Créez un projet d’application console dans Visual Studio.

- Utilisez les fonctions et variables importées à partir de la DLL dans l’application console.

- Exécutez l’application terminée.

À l’instar d’une bibliothèque liée de manière statique, une DLL _exporte_ des variables, des fonctions et des ressources par nom. Une application cliente _importe_ les noms pour utiliser ces variables, fonctions et ressources. Contrairement à une bibliothèque liée statiquement, Windows connecte les importations dans votre application aux exportations dans une DLL au moment du chargement ou au moment de l’exécution, au lieu de les connecter au moment de la liaison. Windows requiert des informations supplémentaires qui ne font pas partie du modèle de compilation standard C++ pour établir ces connexions. Le compilateur MSVC implémente certaines extensions spécifiques dans C++ pour fournir ces informations supplémentaires. Nous allons expliquer ces extensions au fur et à mesure.

Cette procédure pas à pas crée deux solutions Visual Studio ; une qui crée la DLL et une qui crée l’application cliente. La DLL utilise la Convention d’appel C. Il peut être appelé à partir d’applications écrites dans d’autres langages de programmation, à condition que la plateforme, les conventions d’appel et les conventions de liaison correspondent. L’application cliente utilise _liaison implicite_ , où Windows lie l’application à la DLL au moment du chargement. Cette liaison permet à l’application d’appeler les fonctions fournies par la DLL, telles que les fonctions dans une bibliothèque liée statiquement.

Cette procédure pas à pas n’aborde pas quelques situations courantes. Le code n’affiche pas l’utilisation des dll C++ par d’autres langages de programmation. Il n’indique pas comment [créer une dll de ressource uniquement](creating-a-resource-only-dll.md), ou comment utiliser la [liaison explicite](linking-an-executable-to-a-dll.md#linking-explicitly) pour charger des dll au moment de l’exécution plutôt qu’au moment du chargement. Rest garantis, vous pouvez utiliser MSVC et Visual Studio pour effectuer toutes ces opérations.

Pour obtenir des liens vers d’autres informations sur les DLL, consultez [Créer des DLL C/C++ DLL dans Visual Studio](dlls-in-visual-cpp.md). Pour plus d’informations sur la liaison implicite et la liaison explicite, consultez [déterminer la méthode de liaison à utiliser](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Pour plus d’informations sur la création de dll C++ à utiliser avec les langages de programmation qui utilisent des conventions de liaison de langage C, consultez [exportation de fonctions c++ à utiliser dans des exécutables en langage c](exporting-cpp-functions-for-use-in-c-language-executables.md). Pour plus d’informations sur la création de DLL à utiliser avec les langages .NET, consultez [Appel de fonctions DLL à partir d’applications Visual Basic](calling-dll-functions-from-visual-basic-applications.md).

## <a name="prerequisites"></a>Prérequis

- Un ordinateur qui exécute Microsoft Windows 7 ou versions ultérieures. Nous recommandons Windows 10 pour une expérience de développement optimale.

::: moniker range=">=msvc-150"

- Une copie de Visual Studio. Pour plus d’informations sur le téléchargement et l’installation de Visual Studio, consultez [Installer Visual Studio](/visualstudio/install/install-visual-studio). Lorsque vous exécutez le programme d’installation, assurez-vous que la charge de travail **développement Desktop en C++** est activée. Ne vous inquiétez pas si vous n’avez pas installé cette charge de travail en même temps que Visual Studio. Vous pouvez réexécuter le programme d’installation et l’installer maintenant.

   ![Développement Desktop en C++](media/desktop-development-with-cpp.png "Développement Desktop en C++")

::: moniker-end

::: moniker range="msvc-140"

- Une copie de Visual Studio. Pour plus d’informations sur le téléchargement et l’installation de Visual Studio 2015, consultez [installer Visual studio 2015](/visualstudio/install/install-visual-studio-2015?view=vs-2015&preserve-view=true). Utilisez une installation **personnalisée** pour installer le compilateur et les outils C++, car ils ne sont pas installés par défaut.

::: moniker-end

- Une compréhension des principes fondamentaux de l’utilisation de l’IDE Visual Studio. Si vous avez déjà utilisé des applications de bureau Windows, vous n’aurez probablement aucun mal à suivre. Pour une introduction, consultez [Visite guidée des fonctionnalités de l’IDE Visual Studio](/visualstudio/ide/visual-studio-ide).

- Une compréhension de suffisamment de notions de base du langage C++ pour pouvoir suivre. Ne vous inquiétez pas, nous ne faisons rien de bien compliqué.

::: moniker range="msvc-150"

> [!NOTE]
> Cette procédure pas à pas suppose que vous utilisez Visual Studio 2017 version 15,9 ou ultérieure. Certaines versions antérieures de Visual Studio 2017 comportaient des erreurs dans les modèles de code ou utilisaient des boîtes de dialogue d’interface utilisateur différentes. Pour éviter les problèmes, utilisez la Visual Studio Installer pour mettre à jour Visual Studio 2017 vers la version 15,9 ou ultérieure.

::: moniker-end

## <a name="create-the-dll-project"></a>Créer le projet DLL

Dans cet ensemble de tâches, vous créez un projet pour votre DLL, ajoutez du code et générez-le. Pour commencer, démarrez l’IDE Visual Studio et connectez-vous si nécessaire. Les instructions varient légèrement en fonction de la version de Visual Studio que vous utilisez. Assurez-vous que vous avez sélectionné la version correcte dans le contrôle en haut à gauche de cette page.

::: moniker range=">=msvc-160"

### <a name="to-create-a-dll-project-in-visual-studio-2019"></a>Pour créer un projet DLL dans Visual Studio 2019

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet** .

   ![Créer un projet de DLL](media/create-new-dll-project-2019.png "Créer le projet MathLibrary")

1. En haut de la boîte de dialogue, définissez **Langage** sur **C++** , **Plateforme** sur **Windows** et **Type de projet** sur **Bibliothèque** .

1. Dans la liste filtrée des types de projets, sélectionnez **bibliothèque de liens dynamiques (dll)** , puis cliquez sur **suivant** .

1. Dans la page **configurer votre nouveau projet** , entrez *MathLibrary* dans la zone **nom du projet** pour spécifier un nom pour le projet. Laissez les valeurs d' **emplacement** et de **nom de solution** par défaut. Définissez la **solution** pour **créer une nouvelle solution** . Désactivez la case à cocher **Placer la solution et le projet dans le même répertoire** si elle est activée.

1. Choisissez le bouton **Créer** pour créer le projet.

Lorsque la solution est créée, vous pouvez voir les fichiers projet et source générés dans la fenêtre **Explorateur de solutions** dans Visual Studio.

![Capture d’écran de la fenêtre de Explorateur de solutions Visual Studio 2019 avec la bibliothèque mathématique mise en surbrillance.](media/mathlibrary-solution-explorer-162.png "Solution générée dans Visual Studio")

::: moniker-end

::: moniker range="msvc-150"

### <a name="to-create-a-dll-project-in-visual-studio-2017"></a>Pour créer un projet DLL dans Visual Studio 2017

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Nouveau projet** .

1. Dans le volet gauche de la boîte de dialogue **nouveau projet** , sélectionnez **installé**  >  **Visual C++**  >  **Bureau Windows** . Dans le volet central, sélectionnez **bibliothèque de liens dynamiques (dll)** . Entrez *MathLibrary* dans la zone **nom** pour spécifier un nom pour le projet. Laissez les valeurs d' **emplacement** et de **nom de solution** par défaut. Définissez la **solution** pour **créer une nouvelle solution** . Cochez la case **créer le répertoire pour la solution** si elle est décochée.

   ![Capture d’écran de la boîte de dialogue Nouveau projet de Visual Studio 2017 avec la bibliothèque mathématique dans la zone de texte nom.](media/mathlibrary-new-project-name-159.png "Nommer le projet MathLibrary")

1. Choisissez le bouton **OK** pour créer le projet.

Lorsque la solution est créée, vous pouvez voir les fichiers projet et source générés dans la fenêtre **Explorateur de solutions** dans Visual Studio.

![Capture d’écran de la fenêtre de Explorateur de solutions Visual Studio 2017 avec la bibliothèque mathématique mise en surbrillance.](media/mathlibrary-solution-explorer-159.png "Solution générée dans Visual Studio")

::: moniker-end

::: moniker range="msvc-140"

### <a name="to-create-a-dll-project-in-visual-studio-2015-and-older-versions"></a>Pour créer un projet DLL dans Visual Studio 2015 et versions antérieures

1. Dans la barre de menus, choisissez **fichier** > **nouveau** > **projet** .

1. Dans le volet gauche de la boîte de dialogue **Nouveau projet** , développez **Installé** > **Modèles** et sélectionnez **Visual C++** , puis, dans le volet central, sélectionnez **Application Console Win32** . Entrez *MathLibrary* dans la zone d’édition **nom** pour spécifier un nom pour le projet. Laissez les valeurs d' **emplacement** et de **nom de solution** par défaut. Définissez la **solution** pour **créer une nouvelle solution** . Cochez la case **créer le répertoire pour la solution** si elle est décochée.

   ![Capture d’écran de la boîte de dialogue Nouveau projet de Visual Studio 2015 avec la bibliothèque mathématique dans la zone de texte nom.](media/mathlibrary-project-name.png "Nommer le projet MathLibrary")

1. Choisissez le bouton **OK** pour ignorer la boîte de dialogue **Nouveau projet** et démarrez l’ **Assistant Application Win32** .

   ![Vue d’ensemble de l’Assistant application Win32](media/mathlibrary-project-wizard-1.png "Vue d’ensemble de l’Assistant application Win32")

1. Choisissez le bouton **Suivant** . À la page **Paramètres d'application** , sous **Type d’application** , sélectionnez **DLL** .

   ![Créer une DLL dans l’Assistant application Win32](media/mathlibrary-project-wizard-2.png "Créer une DLL dans l’Assistant application Win32")

1. Choisissez le bouton **Terminer** pour créer le projet.

Lorsque l’Assistant a terminé la solution, vous pouvez voir les fichiers projet et source générés dans la fenêtre de **l’Explorateur de solutions** dans Visual Studio.

![Capture d’écran de la fenêtre de Explorateur de solutions Visual Studio 2015 avec la bibliothèque mathématique mise en surbrillance.](media/mathlibrary-solution-explorer-153.png "Solution générée dans Visual Studio")

::: moniker-end

Pour l’instant, cette DLL ne fait pas grand-chose. Ensuite, vous allez créer un fichier d’en-tête pour déclarer les fonctions que votre DLL exporte, puis ajouter les définitions de fonction à la DLL pour la rendre plus utile.

### <a name="to-add-a-header-file-to-the-dll"></a>Pour ajouter un fichier d’en-tête à la DLL

1. Pour créer un fichier d’en-tête pour vos fonctions, dans la barre de menus, choisissez **projet**  >  **Ajouter un nouvel élément** .

1. Dans le volet gauche de la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Visual C++** . Dans le volet central, sélectionnez **Fichier d’en-tête (.h)** . Spécifiez *MathLibrary. h* comme nom pour le fichier d’en-tête.

   ![Ajouter un en-tête dans la boîte de dialogue Ajouter un nouvel élément](media/mathlibrary-add-new-item-header-file.png "Ajouter un fichier d’en-tête dans la boîte de dialogue Ajouter un nouvel élément")

1. Choisissez le bouton **Ajouter** pour générer un fichier d’en-tête vide, qui s’affiche dans une nouvelle fenêtre d’éditeur.

   ![Fichier MathLibrary. h vide dans l’éditeur](media/edit-empty-mathlibrary-header.png "Fichier MathLibrary. h vide dans l’éditeur")

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

Notez les instructions du préprocesseur en haut du fichier. Le nouveau modèle de projet pour un projet DLL ajoute **_ProjectName_ &#95;exporte** aux macros de préprocesseur définies. Dans cet exemple, Visual Studio définit **MATHLIBRARY&#95;EXPORTS** lorsque votre projet de DLL MathLibrary est créé.

Lorsque le macro **MATHLIBRARY&#95;EXPORTS** est défini, le macro **MATHLIBRARY&#95;API** définit le modificateur `__declspec(dllexport)` sur les déclarations de fonctions. Ce modificateur indique au compilateur et à l’éditeur de liens d’exporter une fonction ou une variable à partir de la DLL pour une utilisation par d’autres applications. Lorsque **MATHLIBRARY&#95;EXPORTS** n’est pas défini, par exemple, lorsque le fichier d’en-tête est inclus dans une application cliente, **MATHLIBRARY&#95;API** applique le modificateur `__declspec(dllimport)` aux déclarations. Ce modificateur optimise l'importation de la fonction dans une application. Pour plus d’informations, consultez [dllexport, dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>Pour ajouter une implémentation à la DLL

::: moniker range=">=msvc-160"

1. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le nœud **fichiers sources** et choisissez **Ajouter**  >  **un nouvel élément** . Créez un nouveau fichier. cpp appelé *MathLibrary. cpp* , de la même façon que vous avez ajouté un nouveau fichier d’en-tête à l’étape précédente.

1. Dans la fenêtre de l’éditeur, sélectionnez l’onglet **MathLibrary.cpp** s’il est déjà ouvert. Si ce n’est pas le cas, dans **Explorateur de solutions** , double-cliquez sur **MathLibrary. cpp** dans le dossier **fichiers sources** du projet **MathLibrary** pour l’ouvrir.

1. Dans l’éditeur, remplacez le contenu du fichier de code MathLibrary.cpp par le code suivant :

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "pch.h" // use stdafx.h in Visual Studio 2017 and earlier
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

::: moniker-end

::: moniker range="<=msvc-150"

1. Dans la fenêtre de l’éditeur, sélectionnez l’onglet **MathLibrary.cpp** s’il est déjà ouvert. Si ce n’est pas le cas, dans **Explorateur de solutions** , double-cliquez sur **MathLibrary. cpp** dans le dossier **fichiers sources** du projet **MathLibrary** pour l’ouvrir.

1. Dans l’éditeur, remplacez le contenu du fichier de code MathLibrary.cpp par le code suivant :

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h" // use pch.h in Visual Studio 2019 and later
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

::: moniker-end

Pour vérifier que tout fonctionne à ce stade, compilez la bibliothèque de liens dynamiques. Pour compiler, choisissez **générer**  >  **générer la solution** dans la barre de menus. La DLL et la sortie de compilateur associée sont placées dans un dossier appelé *Debug* juste sous le dossier de la solution. Si vous créez une version Release, la sortie est placée dans un dossier appelé *Release* . Le résultat suivant doit ressembler à ce qui suit :

::: moniker range=">=msvc-160"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>pch.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="msvc-150"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="msvc-140"

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

::: moniker-end

Félicitations, vous avez créé une DLL à l’aide de Visual Studio ! Ensuite, vous allez créer une application cliente qui utilise les fonctions exportées par la DLL.

## <a name="create-a-client-app-that-uses-the-dll"></a>Créer une application cliente qui utilise la DLL

Lorsque vous créez une DLL, réfléchissez à la façon dont les applications clientes peuvent l’utiliser. Pour appeler les fonctions ou accéder aux données exportées par une DLL, les déclarations du code source client doivent être disponibles au moment de la compilation. Au moment de la liaison, l’éditeur de liens exige des informations pour résoudre les appels de fonction ou les accès aux données. Une DLL fournit ces informations dans une *bibliothèque d’importation* , un fichier qui contient des informations sur la façon de rechercher les fonctions et les données, au lieu du code réel. Et en cours d’exécution, la DLL doit être à la disposition du client à un emplacement que le système d’exploitation peut trouver.

Qu’il s’agisse de votre propre ou d’un tiers, votre projet d’application cliente a besoin de plusieurs informations pour utiliser une DLL. Il doit rechercher les en-têtes qui déclarent les exportations de DLL, les bibliothèques d’importation pour l’éditeur de liens et la DLL elle-même. Une solution consiste à copier tous ces fichiers dans votre projet client. Pour les DLL de tiers qui sont peu susceptibles de changer pendant le développement de votre client, cette méthode peut être la meilleure façon de les utiliser. Toutefois, lorsque vous créez également la DLL, il est préférable d’éviter la duplication. Si vous effectuez une copie locale des fichiers DLL en cours de développement, vous risquez de modifier accidentellement un fichier d’en-tête dans une copie, mais pas dans l’autre, ou d’utiliser une bibliothèque obsolète.

Pour éviter tout code non synchronisé, nous vous recommandons de définir le chemin d’accès Include dans votre projet client de façon à inclure les fichiers d’en-tête DLL directement à partir de votre projet DLL. Définissez également le chemin de la bibliothèque dans votre projet client pour inclure les bibliothèques d’importation DLL à partir du projet DLL. Enfin, copiez la DLL générée à partir du projet DLL dans le répertoire de sortie de la génération du client. Cette étape permet à votre application cliente d’utiliser le code DLL que vous créez.

::: moniker range=">=msvc-160"

### <a name="to-create-a-client-app-in-visual-studio"></a>Pour créer une application cliente dans Visual Studio

1. Dans la barre de menus, choisissez **fichier** > **nouveau** > **projet** pour ouvrir la boîte de dialogue **créer un nouveau projet** .

1. En haut de la boîte de dialogue, définissez **Langage** sur **C++** , **Plateforme** sur **Windows** et **Type de projet** sur **Console** .

1. À partir de la liste des types de projets, choisissez **Application console** , puis choisissez **Suivant** .

1. Dans la page **configurer votre nouveau projet** , entrez *MathClient* dans la zone **nom du projet** pour spécifier un nom pour le projet. Laissez les valeurs d' **emplacement** et de **nom de solution** par défaut. Définissez la **solution** pour **créer une nouvelle solution** . Désactivez la case à cocher **Placer la solution et le projet dans le même répertoire** si elle est activée.

   ![Capture d’écran de la boîte de dialogue créer un nouveau projet avec l’option application de la console mise en surbrillance.](media/mathclient-project-name-2019.png "Nommer le projet client")

1. Choisissez le bouton **Créer** pour créer le projet client.

Un projet d’application console minimal est créé pour vous. Le nom du fichier source principal est identique au nom du projet que vous avez saisi précédemment. Dans cet exemple, il est nommé **MathClient.cpp** . Vous pouvez le créer, mais il n’utilise pas encore votre DLL.

::: moniker-end

::: moniker range="msvc-150"

### <a name="to-create-a-client-app-in-visual-studio-2017"></a>Pour créer une application cliente dans Visual Studio 2017

1. Pour créer une application C++ qui utilise la DLL que vous avez créée, dans la barre de menus, choisissez **Fichier,** > **Nouveau** > **Projet** .

1. Dans le volet gauche de la boîte de dialogue **Nouveau projet** , sélectionnez **Windows Desktop** sous **Installé** > **Visual C++** . Dans le volet central, sélectionnez **application console Windows** . Spécifiez le nom du projet, *MathClient* , dans la zone d’édition **nom** .  Laissez les valeurs d' **emplacement** et de **nom de solution** par défaut. Définissez la **solution** pour **créer une nouvelle solution** . Cochez la case **créer le répertoire pour la solution** si elle est décochée.

   ![Capture d’écran de la boîte de dialogue Nouveau projet avec installé > Visual C plus > Windows Desktop sélectionné, application console Windows mise en surbrillance et client mathématique typé dans la zone de texte nom.](media/mathclient-new-project-name-159.png "Nommer le projet client")

1. Choisissez **OK** pour créer le projet d’application cliente.

Un projet d’application console minimal est créé pour vous. Le nom du fichier source principal est identique au nom du projet que vous avez saisi précédemment. Dans cet exemple, il est nommé **MathClient.cpp** . Vous pouvez le créer, mais il n’utilise pas encore votre DLL.

::: moniker-end

::: moniker range="msvc-140"

### <a name="to-create-a-client-app-in-visual-studio-2015"></a>Pour créer une application cliente dans Visual Studio 2015

1. Pour créer une application C++ qui utilise la DLL que vous avez créée, dans la barre de menus, choisissez **Fichier,** > **Nouveau** > **Projet** .

1. Dans le volet gauche de la boîte de dialogue **Nouveau projet** , sélectionnez **Win32** sous **Installé** > **Modèles** > **Visual C++** . Dans le volet central, sélectionnez **Application console Win32** . Spécifiez le nom du projet, *MathClient* , dans la zone d’édition **nom** . Laissez les valeurs d' **emplacement** et de **nom de solution** par défaut. Définissez la **solution** pour **créer une nouvelle solution** . Cochez la case **créer le répertoire pour la solution** si elle est décochée.

   ![Capture d’écran de la boîte de dialogue Nouveau projet avec les modèles de > installés > Visual C plus > l’application console Win32 sélectionnée, Visual C plus, et le client mathématique tapé dans la zone de texte nom.](media/mathclient-project-name.png "Nommer le projet client")

1. Choisissez le bouton **OK** pour ignorer la boîte de dialogue **Nouveau projet** et démarrez l’ **Assistant Application Win32** . Dans la page **Vue d'ensemble** de la boîte de dialogue **Assistant Application Win32** , choisissez le bouton **Suivant** .

1. Dans la page **Paramètres de l'application** sous **Type d'application** , sélectionnez **Application console** si elle n’est pas encore sélectionnée.

1. Choisissez le bouton **Terminer** pour créer le projet.

Lorsque l’Assistant a terminé, un projet d’application console minimal est créé pour vous. Le nom du fichier source principal est identique au nom du projet que vous avez saisi précédemment. Dans cet exemple, il est nommé **MathClient.cpp** . Vous pouvez le créer, mais il n’utilise pas encore votre DLL.

::: moniker-end

Ensuite, pour appeler les fonctions MathLibrary dans votre code source, votre projet doit inclure le fichier *MathLibrary. h* . Vous pouvez copier ce fichier d’en-tête dans votre projet d’application cliente, puis l’ajouter au projet comme élément existant. Cette méthode peut être un bon choix pour des bibliothèques tierces. Toutefois, si vous travaillez sur le code de votre DLL et de votre client en même temps, les fichiers d’en-tête peuvent ne pas être synchronisés. Pour éviter ce problème, définissez le chemin d’accès aux **autres répertoires Include** dans votre projet de façon à inclure le chemin d’accès à l’en-tête d’origine.

### <a name="to-add-the-dll-header-to-your-include-path"></a>Pour ajouter l’en-tête de la DLL à votre chemin Include

1. Cliquez avec le bouton droit sur le nœud **MathClient** dans **l’Explorateur de solutions** pour ouvrir la boîte de dialogue **Pages de propriétés** .

1. Dans la zone de liste déroulante **configuration** , sélectionnez **toutes les configurations** si elle n’est pas déjà sélectionnée.

1. Dans le volet gauche, sélectionnez **Propriétés de configuration**  >  **C/C++**  >  **général** .

1. Dans le volet des propriétés, sélectionnez le contrôle de la liste déroulante en regard de la zone d’édition pour **Autres répertoires Include** , puis choisissez **Modifier** .

   ![Modifier la propriété autres répertoires Include](media/mathclient-additional-include-directories-property.png "Modifier la propriété autres répertoires Include")

1. Double-cliquez dans le volet supérieur de la boîte de dialogue **Autres répertoires Include** pour activer un contrôle d’édition. Sinon, choisissez l’icône de dossier pour créer une nouvelle entrée.

1. Dans le contrôle d’édition, spécifiez le chemin de l’emplacement du fichier d'en-tête **MathLibrary.h** . Vous pouvez choisir le contrôle des points de suspension ( **...** ) pour accéder au dossier approprié.

   Vous pouvez également entrer un chemin d’accès relatif à partir de vos fichiers sources du client vers le dossier qui contient les fichiers d’en-tête de DLL. Si vous avez suivi les instructions pour placer votre projet client dans une solution distincte de la DLL, le chemin d’accès relatif doit se présenter comme suit :

   `..\..\MathLibrary\MathLibrary`

   Si vos projets DLL et client se trouvent dans la même solution, le chemin d’accès relatif peut se présenter comme suit :

   `..\MathLibrary`

   Lorsque les projets DLL et client se trouvent dans d’autres dossiers, ajustez le chemin d’accès relatif pour qu’il corresponde. Vous pouvez utiliser le contrôle des points de suspension pour rechercher le dossier.

   ![Ajouter l’emplacement d’en-tête à la propriété autres répertoires Include](media/mathclient-additional-include-directories.png "Ajouter l’emplacement d’en-tête à la propriété autres répertoires Include")

1. Une fois que vous avez entré le chemin d’accès au fichier d’en-tête dans la boîte de dialogue **autres répertoires Include** , choisissez le bouton **OK** . Dans la boîte de dialogue **pages de propriétés** , choisissez le bouton **OK** pour enregistrer vos modifications.

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

Ce code peut être compilé, mais pas lié. Si vous générez l’application cliente maintenant, la liste d’erreurs affiche plusieurs erreurs LNK2019. Cela est dû au fait que votre projet ne contient pas d’informations : vous n’avez pas encore spécifié que votre projet a une dépendance vis-à-vis de la bibliothèque *MathLibrary. lib* . Et, vous n’avez pas indiqué à l’éditeur de liens comment trouver le fichier *MathLibrary. lib* .

Pour résoudre ce problème, vous pouvez copier le fichier de bibliothèque directement dans votre projet d’application cliente. L’éditeur de liens le trouvera et l’utilisera automatiquement. Toutefois, si la bibliothèque et l’application cliente sont en cours de développement, cela peut entraîner des modifications dans une copie qui ne sont pas affichées dans l’autre. Pour éviter ce problème, vous pouvez définir la propriété **dépendances supplémentaires** pour indiquer au système de génération que votre projet dépend de *MathLibrary. lib* . Vous pouvez également définir un chemin d’accès aux **répertoires de bibliothèque supplémentaire** dans votre projet pour inclure le chemin d’accès à la bibliothèque d’origine lorsque vous établissez une liaison.

### <a name="to-add-the-dll-import-library-to-your-project"></a>Pour ajouter la bibliothèque d’importation DLL à votre projet

1. Cliquez avec le bouton droit sur le nœud **MathClient** dans **Explorateur de solutions** , puis choisissez **Propriétés** pour ouvrir la boîte de dialogue **pages de propriétés** .

1. Dans la zone de liste déroulante **configuration** , sélectionnez **toutes les configurations** si elle n’est pas déjà sélectionnée. Elle garantit que toutes les modifications de propriété s’appliquent aux versions Debug et Release.

1. Dans le volet gauche, sélectionnez **Propriétés de configuration** entrée de l'  >  **éditeur de liens**  >  **Input** . Dans le volet des propriétés, sélectionnez le contrôle de la liste déroulante en regard de la zone d’édition pour les **Dépendances supplémentaires** , puis choisissez **Modifier** .

   ![Modifier la propriété dépendances supplémentaires](media/mathclient-additional-dependencies-property.png "Modifier la propriété dépendances supplémentaires")

1. Dans la boîte de dialogue **dépendances supplémentaires** , ajoutez *MathLibrary. lib* à la liste dans le contrôle d’édition supérieur.

   ![Ajouter la dépendance de bibliothèque](media/mathclient-additional-dependencies.png "Ajouter la dépendance de bibliothèque")

1. Choisissez **OK** pour revenir à la boîte de dialogue **Pages de propriétés** .

1. Dans le volet gauche, sélectionnez **Propriétés de configuration**  >  **éditeur de liens**  >  **général** . Dans le volet des propriétés, sélectionnez le contrôle de la liste déroulante en regard de la zone d’édition pour **Répertoires de bibliothèques supplémentaires** , puis choisissez **Modifier** .

   ![Modifier la propriété répertoires de bibliothèque supplémentaires](media/mathclient-additional-library-directories-property.png "Modifier la propriété répertoires de bibliothèque supplémentaires")

1. Double-cliquez dans le volet supérieur de la boîte de dialogue **Répertoires de bibliothèques supplémentaires** pour activer un contrôle d’édition. Dans le contrôle d’édition, spécifiez le chemin de l’emplacement du fichier **MathLibrary.lib** . Par défaut, il se trouve dans un dossier appelé *Debug* directement sous le dossier de la solution dll. Si vous créez une version Release, le fichier est placé dans un dossier appelé *Release* . Vous pouvez utiliser la `$(IntDir)` macro pour que l’éditeur de liens puisse trouver votre dll, quel que soit le type de build que vous créez. Si vous avez suivi les instructions pour placer votre projet client dans une solution distincte du projet DLL, le chemin d’accès relatif doit se présenter comme suit :

   `..\..\MathLibrary\$(IntDir)`

   Si vos projets DLL et client se trouvent dans d’autres emplacements, ajustez le chemin d’accès relatif pour qu’ils correspondent.

   ![Ajouter le répertoire de bibliothèque](media/mathclient-additional-library-directories.png "Ajouter le répertoire de bibliothèque")

1. Une fois que vous avez saisi le chemin du fichier de bibliothèque dans la boîte de dialogue **Répertoires de bibliothèques supplémentaires** , choisissez le bouton **OK** pour revenir à la boîte de dialogue **Pages de propriétés** . Choisissez **OK** pour enregistrer les modifications apportées aux propriétés.

Votre application cliente peut maintenant compiler et lier correctement, mais elle n’a toujours pas tout ce dont elle a besoin pour s’exécuter. Lorsque le système d’exploitation charge votre application, il recherche la DLL MathLibrary. S’il ne la trouve pas dans certains répertoires du système, dans le chemin de l’environnement ou dans le répertoire de l’application locale, le chargement échoue. Selon le système d’exploitation, un message d’erreur semblable à celui-ci s’affiche :

![Erreur MathLibrary DLL introuvable](media/mathclient-system-error-mathlibrary-dll-not-found.png "Erreur MathLibrary DLL introuvable")

Une façon d’éviter ce problème consiste à copier la DLL dans le répertoire qui contient votre exécutable client dans le cadre du processus de création. Vous pouvez ajouter un **événement après génération** à votre projet, pour ajouter une commande qui copie la dll dans votre répertoire de sortie de génération. La commande spécifiée ici copie la DLL uniquement si elle est manquante ou a été modifiée. Il utilise des macros pour copier vers et depuis les emplacements de débogage ou de version, en fonction de votre configuration de Build.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>Pour copier la DLL dans un événement post-build

1. Cliquez avec le bouton droit sur le nœud **MathClient** dans **Explorateur de solutions** , puis choisissez **Propriétés** pour ouvrir la boîte de dialogue **pages de propriétés** .

1. Dans la zone de liste déroulante **configuration** , sélectionnez **toutes les configurations** si elle n’est pas déjà sélectionnée.

1. Dans le volet gauche, sélectionnez **Propriétés de configuration**  >  **événements de build événements**  >  **après génération** .

1. Dans le volet des propriétés, sélectionnez le contrôle d’édition dans le champ **ligne de commande** . Si vous avez suivi les instructions pour placer votre projet client dans une solution distincte du projet DLL, entrez la commande suivante :

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   Si vos projets DLL et client se trouvent dans d’autres répertoires, modifiez le chemin d’accès relatif à la DLL pour qu’il corresponde.

   ![Ajouter la commande après génération](media/mathclient-post-build-command-line.png "Ajouter la commande après génération")

1. Choisissez le bouton **OK** pour enregistrer les changements que vous avez apportés aux propriétés du projet.

Maintenant, votre application cliente a tout ce dont il a besoin pour générer et exécuter. Générez l’application en choisissant **générer**  >  **générer la solution** dans la barre de menus. La fenêtre **sortie** dans Visual Studio doit avoir un aspect similaire à l’exemple suivant, en fonction de votre version de Visual Studio :

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Félicitations, vous avez créé une application qui appelle des fonctions dans votre DLL. Exécutez maintenant votre application pour voir ce qu’elle fait. Dans la barre de menus, choisissez **Déboguer**  >  **exécuter sans débogage** . Visual Studio ouvre une fenêtre de commande dans laquelle le programme doit exécuter. La dernière partie de la sortie doit avoir cette forme :

![Démarrer l’application cliente sans débogage](media/mathclient-run-without-debugging.png "Démarrer l’application cliente sans débogage")

Appuyez sur une touche pour masquer la fenêtre de commande.

Maintenant que vous avez créé une DLL et une application cliente, vous pouvez faire des essais. Essayez de définir des points d’arrêt dans le code de l’application cliente et exécutez l’application dans le débogueur. Regardez ce qui se passe lorsque vous parcourez un appel de bibliothèque. Ajoutez d’autres fonctions à la bibliothèque, ou écrivez une autre application cliente qui utilise votre DLL.

Lorsque vous déployez votre application, vous devez également déployer les DLL qu’elle utilise. La façon la plus simple de rendre les dll que vous créez, ou que vous incluez auprès de tiers, est de les placer dans le même répertoire que votre application. Il est connu sous le nom de *déploiement local* de l’application. Pour plus d’informations sur le déploiement, consultez [Deployment in Visual C++](../windows/deployment-in-visual-cpp.md).

## <a name="see-also"></a>Voir aussi

[Appel de fonctions DLL à partir d’applications Visual Basic](calling-dll-functions-from-visual-basic-applications.md)
