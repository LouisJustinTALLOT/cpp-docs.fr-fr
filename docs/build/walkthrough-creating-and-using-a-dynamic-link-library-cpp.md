---
title: "Procédure pas à pas : Créer et utiliser votre propre bibliothèque de liens dynamiques (C++) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
caps.latest.revision: "36"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bdcc02cf7c86b85684df0e8d8b7a1f0049ff7e25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>Procédure pas à pas : Créer et utiliser votre propre bibliothèque de liens dynamiques (C++)

Cette procédure pas à pas montre comment utiliser l’IDE de Visual Studio pour créer votre propre bibliothèque de liens dynamiques (DLL) écrite en C++ et l’utiliser à partir d’une autre application C++. DLL sont un des types de composants Windows plus utiles. Vous pouvez les utiliser comme un moyen de partager du code et des ressources, pour réduire la taille de vos applications et à faciliter l’utilisation de service et d’étendre vos applications. Dans cette procédure pas à pas, vous créez une DLL qui implémente des fonctions mathématiques et ensuite créez une application console qui utilise les fonctions de la DLL. Avant cela, vous obtenez une présentation de certaines des techniques de programmation et des conventions utilisées dans des DLL Windows.

Cette procédure pas à pas couvre les tâches suivantes :

- Créez un projet DLL dans Visual Studio.

- Ajouter des fonctions exportées et les variables à la DLL.

- Créez un projet d’application console dans Visual Studio.

- Utilisez les fonctions et variables importées à partir de la DLL dans l’application console.

- Exécutez l’application terminée.

Comme une bibliothèque liée statiquement, une DLL _exporte_ variables, des fonctions et des ressources par nom et de votre application _importe_ ces noms à utiliser ces variables, fonctions et ressources. Contrairement à une bibliothèque liée statiquement, Windows connecte à l’importation dans votre application pour les exportations dans une DLL au moment du chargement ou au moment de l’exécution, au lieu de les connecter au moment de la liaison. Windows requiert des informations supplémentaires qui ne fait pas partie du modèle de compilation C++ standard pour établir ces connexions. Le compilateur Visual C++ implémente des extensions spécifiques à Microsoft pour C++ pour fournir ces informations supplémentaires. Nous vous expliquons ces extensions mesure que nous.

Cette procédure pas à pas crée deux solutions de Visual Studio ; une qui génère la DLL et une qui génère l’application cliente. La DLL utilise la convention d’appel C afin qu’il peut être appelée à partir d’applications générées à l’aide d’autres langages, tant que la plateforme et l’appel et conventions de liaison correspondent. Le client app utilise _liaison implicite_, où Windows lie l’application à la DLL au moment du chargement. Cela permet à l’application d’appeler les fonctions fournies par la DLL, tout comme les fonctions dans une bibliothèque liée statiquement.

Cette procédure pas à pas n’aborde pas certaines situations courantes. Il n’affiche pas l’utilisation des DLL C++ par d’autres langages de programmation. Il n’affiche pas la création d’une DLL de ressource uniquement. Il n’affiche également pas l’utilisation de la liaison explicite pour charger la DLL au moment de l’exécution plutôt qu’au moment du chargement. Rassurez-vous, vous pouvez utiliser Visual C++ pour effectuer toutes ces tâches. Pour obtenir des liens vers des informations sur les DLL, consultez [DLL dans Visual C++](../build/dlls-in-visual-cpp.md). Pour plus d’informations sur la liaison implicite et la liaison explicite, consultez [méthode de liaison à utiliser](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use). Pour plus d’informations sur la création de DLL C++ pour une utilisation avec les langages de programmation qui utilisent des conventions de liaison en langage C, consultez [exportation de fonctions C++ à utiliser dans des exécutables en langage C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md). Pour plus d’informations sur la façon de créer des DLL à utiliser avec les langages .NET, consultez [appel à des fonctions DLL à partir d’Applications Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md).

Cette procédure pas à pas utilise Visual Studio 2017, mais le code et la plupart des instructions s’applique aux versions antérieures. Les étapes permettant de créer de nouveaux projets modifié à partir de Visual Studio 2017 version 15.3. Cette procédure pas à pas explique comment créer des projets pour les versions anciennes et récentes. Recherchez les étapes correspondant à votre version de Visual Studio.

## <a name="prerequisites"></a>Prérequis

- Un ordinateur qui exécute Microsoft Windows 7 ou versions ultérieures. Nous vous recommandons de Windows 10 pour la meilleure expérience de développement.

- Une copie de Visual Studio 2017. Pour plus d’informations sur la façon de télécharger et installer Visual Studio, consultez [installer Visual 2017 de Studio](/visualstudio/install/install-visual-studio). Lorsque vous exécutez le programme d’installation, assurez-vous que le **bureau développement avec C++** la charge de travail est activée. Ne vous inquiétez pas si vous n’avez pas installé cette charge de travail lorsque vous avez installé Visual Studio. Vous pouvez exécuter le programme d’installation à nouveau et installez-le maintenant.

   ![Développement de bureau avec C++](media/desktop-development-with-cpp.png "bureau développement avec C++")

- Une connaissance des notions de base de l’utilisation de l’IDE de Visual Studio. Si vous avez utilisé avant les applications de bureau Windows, vous pouvez probablement suivre. Pour obtenir une présentation, consultez [visite guidée des fonctionnalités IDE de Visual Studio](/visualstudio/ide/visual-studio-ide).

- Une connaissance des suffisamment des notions de base du langage C++ pour effectuer la procédure. Ne vous inquiétez pas, nous n’ont aucun effet trop compliqué.

## <a name="create-the-dll-project"></a>Créer le projet DLL

Dans cet ensemble de tâches, vous créez un projet pour votre DLL, ajoutez le code et générez. Pour commencer, démarrez l’IDE Visual Studio et connectez-vous si vous avez besoin. Les instructions pour Visual Studio 2017 version 15.3 en premier. Instructions pour les versions antérieures sont fournis plus loin, donc ignorer si vous devez.

### <a name="to-create-a-dll-project-in-visual-studio-2017-version-153-or-later"></a>Pour créer un projet DLL dans Visual Studio 2017 version 15,3 ou version ultérieure

1. Dans la barre de menus, choisissez **fichier**, **nouveau**, **projet** pour ouvrir le **nouveau projet** boîte de dialogue.

1. Dans le volet gauche de la **nouveau projet** boîte de dialogue, développez **installé** et **Visual C++** si nécessaire, puis choisissez **Windows Desktop**. Dans le volet central, sélectionnez **Assistant du bureau Windows**. Entrez `MathLibrary` dans les **nom** pour spécifier un nom pour le projet.

   ![Nommez le projet MathLibrary](media/mathlibrary-new-project-name-153.png "nommez le projet MathLibrary")

1. Choisissez le **OK** bouton pour fermer la **nouveau projet** boîte de dialogue et démarrer le **projet de bureau Windows** Assistant.

1. Dans le **projet de bureau Windows** Assistant sous **type d’Application**, sélectionnez **bibliothèque de liens dynamiques (.dll)**.

   ![Créer des DLL dans l’Assistant de projet de bureau Windows](media/mathlibrary-desktop-project-wizard-dll.png "créer des DLL dans l’Assistant de projet de bureau Windows")

1. Choisissez le bouton **OK** pour créer le projet.

> [!NOTE]
> Étapes supplémentaires sont nécessaires pour résoudre un problème dans Visual Studio 2017 version 15.3. Suivez ces instructions si vous avez besoin effectuer cette modification.
>
>1. Dans **l’Explorateur de solutions**, si elle n’est pas déjà sélectionné, sélectionnez le **MathLibrary** projet sous **Solution 'MathLibrary'**.
>
>1. Dans la barre de menus, choisissez **Projet**, **Propriétés**.
>
>1. Dans le volet gauche de la **Pages de propriétés** boîte de dialogue, sélectionnez **préprocesseur** sous **propriétés de Configuration**, **C/C++**. Vérifier le contenu de la **définitions de préprocesseur** propriété.<br/><br/>![Vérifiez la propriété de définitions de préprocesseur](media/mathlibrary-153bug-preprocessor-definitions-check.png "Vérifiez la propriété de définitions de préprocesseur")<br/><br/>Si vous voyez **MATHLIBRARY &#95; EXPORTATIONS** dans les **définitions de préprocesseur** liste, vous n’avez pas besoin de rien modifier. Si vous voyez **MathLibrary &#95; EXPORTATIONS** à la place, puis continuer à suivre ces étapes.
>
>1. En haut de la **Pages de propriétés** boîte de dialogue Modifier le **Configuration** liste déroulante **toutes les Configurations**.
>
>1. Dans le volet des propriétés, sélectionnez le contrôle de liste déroulante en regard de la zone d’édition pour **définitions de préprocesseur**, puis choisissez **modifier**.<br/><br/>![Modifier la propriété de définitions de préprocesseur](media/mathlibrary-153bug-preprocessor-definitions-property.png "modifier la propriété de définitions de préprocesseur")
>
>1. Dans le volet supérieur de la **définitions de préprocesseur** boîte de dialogue, ajoutez un nouveau symbole, `MATHLIBRARY_EXPORTS`.<br/><br/>![Ajoutez le symbole MATHLIBRARY_EXPORTS](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "ajouter le symbole MATHLIBRARY_EXPORTS")
>
>1. Choisissez **OK** pour faire disparaître la **définitions de préprocesseur** boîte de dialogue, puis choisissez **OK** pour enregistrer les modifications apportées aux propriétés du projet.

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>Pour créer un projet de DLL dans les versions antérieures de Visual Studio

1. Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.

1. Dans le volet gauche de la **nouveau projet** boîte de dialogue, développez **installé**, **modèles**, puis sélectionnez **Visual C++**, puis, dans le centre volet, sélectionnez **Application Console Win32**. Entrez `MathLibrary` dans les **nom** modifier la zone pour spécifier un nom pour le projet.

   ![Nommez le projet MathLibrary](media/mathlibrary-project-name.png "nommez le projet MathLibrary")

1. Choisissez le **OK** bouton pour fermer la **nouveau projet** boîte de dialogue et démarrer le **Assistant Application Win32**.

   ![Présentation de l’Assistant Application Win32](media/mathlibrary-project-wizard-1.png "présentation de l’Assistant Application Win32")

1. Choisissez le bouton **Suivant**. Sur le **paramètres de l’Application** sous **type d’Application**, sélectionnez **DLL**.

   ![Créer des DLL dans l’Assistant Application Win32](media/mathlibrary-project-wizard-2.png "créer des DLL dans l’Assistant Application Win32")

1. Choisissez le bouton **Terminer** pour créer le projet.

Lorsque l’Assistant a terminé la solution, vous pouvez voir les fichiers projet et source générés dans le **l’Explorateur de solutions** fenêtre dans Visual Studio.

![Généré la solution dans Visual Studio](media/mathlibrary-solution-explorer-153.png "généré la solution dans Visual Studio")

Droit à présent, cette DLL ne fait pas grand-chose très. Ensuite, vous créez un fichier d’en-tête pour déclarer les fonctions de votre DLL exporte et ajoutez les définitions de fonction à la DLL pour le rendre plus utile.

### <a name="to-add-a-header-file-to-the-dll"></a>Pour ajouter un fichier d’en-tête à la DLL

1. Pour créer un fichier d’en-tête pour vos fonctions, dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.

1. Dans le **ajouter un nouvel élément** boîte de dialogue, dans le volet gauche, sélectionnez **Visual C++**. Dans le volet central, sélectionnez **Fichier d’en-tête (.h)**. Spécifiez `MathLibrary.h` comme nom pour le fichier d’en-tête.

   ![En-tête d’ajouter dans la boîte de dialogue Ajouter un nouvel élément](media/mathlibrary-add-new-item-header-file.png "Add fichier d’en-tête dans la boîte de dialogue Ajouter un nouvel élément")

1. Choisissez le **ajouter** bouton pour générer un fichier d’en-tête vierge s’affiche dans une nouvelle fenêtre d’éditeur.

   ![Fichier MathLibrary.h vide dans l’éditeur](media/edit-empty-mathlibrary-header.png "fichier MathLibrary.h vide dans l’éditeur")

1. Remplacez le contenu du fichier d’en-tête avec ce code :

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

Ce fichier d’en-tête déclare certaines fonctions pour produire une séquence de Fibonacci généralisée, donnés deux valeurs initiales. Un appel à `fibonacci_init(1, 1)` génère la séquence de nombre de Fibonacci familier.

Notez que les instructions de préprocesseur en haut du fichier. Par défaut, le modèle de projet pour une DLL ajoute  ***NOM_PROJET*&#95; EXPORTATIONS** pour les macros de préprocesseur définies pour le projet de DLL. Dans cet exemple, Visual Studio définit **MATHLIBRARY &#95; EXPORTATIONS** lorsque votre projet MathLibrary DLL est générée. (L’Assistant dans Visual Studio 2017 version 15.3 ne force pas cette définition de symbole en majuscules. Si vous nommez votre projet « MathLibrary », le symbole défini est MathLibrary &#95; EXPORTATIONS au lieu de MATHLIBRARY &#95; EXPORTE. That's Pourquoi existe-t-il des étapes supplémentaires ci-dessus pour ajouter ce symbole.)

Lorsque le **MATHLIBRARY &#95; EXPORTATIONS** macro est définie, le **MATHLIBRARY &#95; API** macro définit le `__declspec(dllexport)` modificateur sur les déclarations de fonction. Ce modificateur indique au compilateur et l’éditeur de liens pour exporter une fonction ou une variable à partir de la DLL afin qu’il peut être utilisé par d’autres applications. Lorsque **MATHLIBRARY &#95; EXPORTATIONS** n’est pas défini, par exemple, lorsque le fichier d’en-tête est inclus dans une application cliente, **MATHLIBRARY &#95; API** s’applique le `__declspec(dllimport)` modificateur aux déclarations. Ce modificateur optimise l’importation de la fonction ou une variable dans une application. Pour plus d’informations, consultez [dllexport, dllimport](../cpp/dllexport-dllimport.md).

### <a name="to-add-an-implementation-to-the-dll"></a>Pour ajouter une implémentation à la DLL

1. Dans la fenêtre de l’éditeur, sélectionnez l’onglet pour **MathLibrary.cpp** si elle est déjà ouverte. Dans le cas contraire, dans **l’Explorateur de solutions**, ouvrez **MathLibrary.cpp** dans les **fichiers sources** dossier de la **MathLibrary** projet.

1. Dans l’éditeur, remplacez le contenu du fichier MathLibrary.cpp par le code suivant :

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h"
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

Pour vérifier que tout fonctionne jusqu'à présent, compilez la bibliothèque de liens dynamiques. Pour compiler, choisissez **générer**, **générer la Solution** sur la barre de menus. La sortie doit ressembler à ceci :

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Félicitations, vous avez créé une DLL à l’aide de Visual C++. Ensuite, vous allez créer une application cliente qui utilise les fonctions exportées par la DLL.

## <a name="create-a-client-app-that-uses-the-dll"></a>Créer une application cliente qui utilise la DLL

Lorsque vous créez une DLL, vous devez penser sur l’utilisation de votre DLL. Pour compiler le code qui appelle les fonctions exportées par une DLL, les déclarations doivent être incluses dans le code source du client. Au moment de la liaison, lorsque ces appels aux fonctions DLL sont résolus, l’éditeur de liens doit avoir un *bibliothèque d’importation*, un type spécial de fichier de bibliothèque qui contient des informations sur la façon de rechercher les fonctions, au lieu du code réel pour Windows. Et en cours d’exécution, la DLL doit être disponible pour le client, dans le système d’exploitation ne peut trouver un emplacement.

Utiliser une DLL, si votre propre ou d’une DLL tierce, votre projet d’application cliente doit être en mesure de trouver les en-têtes qui déclare la DLL exporte, les bibliothèques d’importation pour l’éditeur de liens et que la DLL elle-même. Un pour ce faire consiste à copier tous ces fichiers dans votre projet client. Pour les DLL tierces qui sont peu susceptibles de changer pendant que votre client est en cours de développement, cela peut être la meilleure façon de les utiliser. Toutefois, lorsque vous créez également la DLL, il est préférable éviter la duplication. Si vous effectuez une copie des fichiers DLL qui sont en cours de développement, vous pouvez accidentellement modifier un fichier d’en-tête dans une seule copie, mais pas dans l’autre, ou utiliser une bibliothèque de plus à jour. Pour éviter ce problème, nous vous recommandons de que définir le chemin d’accès include dans votre projet de client à inclure les fichiers d’en-tête DLL à partir du projet DLL. En outre, définissez le chemin d’accès de bibliothèque dans votre projet de client à inclure les bibliothèques d’importation DLL à partir du projet DLL. Et pour finir, copiez la DLL générée à partir du projet DLL dans votre répertoire de sortie de génération. Cela garantit que votre application cliente utilise le même code DLL que vous générez.

### <a name="to-create-a-client-app-in-visual-studio-2017-version-153-or-later"></a>Pour créer une application cliente dans Visual Studio 2017 version 15,3 ou version ultérieure

1. Pour créer une application C++ qui utilise la DLL que vous venez de créer, dans la barre de menus, choisissez **fichier**, **nouveau**, **projet**.

1. Dans le volet gauche de la **nouveau projet** boîte de dialogue, sélectionnez **Windows Desktop** sous **installé**, **Visual C++**. Dans le volet central, sélectionnez **Assistant du bureau Windows**. Spécifiez le nom du projet, `MathClient`, dans le **nom** zone d’édition.

   ![Nommez le projet client](media/mathclient-new-project-name-153.png "nommez le projet client")

1. Choisissez **OK** pour démarrer le **projet de bureau Windows** Assistant. Dans l’Assistant, choisissez **OK** pour créer le projet d’application cliente.

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>Pour créer une application cliente dans les versions antérieures de Visual Studio 2017

1. Pour créer une application C++ qui utilise la DLL que vous venez de créer, dans la barre de menus, choisissez **fichier**, **nouveau**, **projet**.

1. Dans le volet gauche de la **nouveau projet** boîte de dialogue, sélectionnez **Win32** sous **installé**, **modèles**, **deVisualC++**. Dans le volet central, sélectionnez **Application console Win32**. Spécifiez le nom du projet, `MathClient`, dans le **nom** zone d’édition.

   ![Nommez le projet client](media/mathclient-project-name.png "nommez le projet client")

1. Choisissez le **OK** bouton pour fermer la **nouveau projet** boîte de dialogue et démarrer le **Assistant Application Win32**. Dans la page **Vue d'ensemble** de la boîte de dialogue **Assistant Application Win32** , choisissez le bouton **Suivant** .

1. Sur le **paramètres de l’Application** sous **type d’Application**, sélectionnez **application Console** si elle n’est pas déjà sélectionnée.

1. Choisissez le bouton **Terminer** pour créer le projet.

Lorsque l’Assistant se termine, un projet d’application console minimal est créé pour vous. Le nom du fichier source principal est le même que le nom du projet que vous avez entrées précédemment. Dans cet exemple, il est nommé **MathClient.cpp**. Vous pouvez le générer, mais il n’utilise pas encore votre DLL.

Ensuite, pour appeler les fonctions MathLibrary dans votre code source, votre projet doit inclure le fichier MathLibrary.h. Vous pouvez copier ce fichier d’en-tête dans votre projet d’application cliente, puis ajoutez-le au projet en tant qu’un élément existant. Cela peut être un bon choix pour des bibliothèques tierces. Toutefois, si vous travaillez sur le code de la DLL en même temps que votre client, qui peut entraîner des modifications dans le fichier d’un en-tête qui ne sont pas répercutées dans les autres. Pour éviter ce problème, vous pouvez modifier le **autres répertoires Include** chemin d’accès dans votre projet à inclure le chemin d’accès à l’en-tête d’origine.

### <a name="to-add-the-dll-header-to-your-include-path"></a>Pour ajouter l’en-tête DLL à votre chemin d’accès include

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le **MathClient** projet.

1. Dans le **Configuration** zone de liste déroulante, sélectionnez **toutes les Configurations** si elle n’est pas déjà sélectionnée.

1. Dans le volet gauche, sélectionnez **général** sous **propriétés de Configuration**, **C/C++**.

1. Dans le volet Propriétés, sélectionnez le contrôle de liste déroulante à côté du **autres répertoires Include** zone d’édition, puis choisissez **modifier**.

   ![Modifiez la propriété autres répertoires Include](media/mathclient-additional-include-directories-property.png "modifier la propriété autres répertoires Include")

1. Double-cliquez dans le volet supérieur de la **autres répertoires Include** boîte de dialogue pour activer un contrôle d’édition.

1. Dans le contrôle d’édition, spécifiez le chemin d’accès à l’emplacement de la **MathLibrary.h** fichier d’en-tête. Dans ce cas, vous pouvez utiliser un chemin d’accès relatif :

   `..\..\MathLibrary\MathLibrary`

   ![Ajouter l’emplacement de l’en-tête dans la propriété autres répertoires Include](media/mathclient-additional-include-directories.png "ajouter l’emplacement de l’en-tête dans la propriété autres répertoires Include")

1. Une fois que vous avez entré le chemin d’accès au fichier d’en-tête dans le **autres répertoires Include** boîte de dialogue, choisissez le **OK** bouton pour revenir à la **Pages de propriétés** boîte de dialogue, et puis choisissez le **OK** bouton pour enregistrer vos modifications.

Vous pouvez maintenant inclure le **MathLibrary.h** de fichiers et utiliser les fonctions qu’il déclare dans votre application cliente. Remplacez le contenu de **MathClient.cpp** à l’aide de ce code :

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
#include "stdafx.h"
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

Ce code peut être compilé, mais pas lié, car l’éditeur de liens ne peut pas trouver la bibliothèque d’importation requise pour générer l’application encore. L’éditeur de liens doit être en mesure de trouver le fichier MathLibrary.lib pour lier correctement. Vous devez ajouter le fichier MathLibrary.lib à la build en définissant le **dépendances supplémentaires** propriété. Une fois encore, vous pouvez copier le fichier de bibliothèque dans votre projet d’application cliente, mais si la bibliothèque et l’application cliente sont en cours de développement, qui peut entraîner des modifications dans une copie qui ne sont pas répercutées dans l’autre. Pour éviter ce problème, vous pouvez modifier le **répertoires de bibliothèques supplémentaires** chemin d’accès dans votre projet à inclure le chemin d’accès à la bibliothèque d’origine lorsque vous créez un lien.

### <a name="to-add-the-dll-import-library-to-your-project"></a>Pour ajouter la bibliothèque d’importation DLL à votre projet

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le **MathClient** projet.

1. Dans le **Configuration** zone de liste déroulante, sélectionnez **toutes les Configurations** si elle n’est pas déjà sélectionnée.

1. Dans le volet gauche, sélectionnez **entrée** sous **propriétés de Configuration**, **l’éditeur de liens**. Dans le volet Propriétés, sélectionnez le contrôle de liste déroulante à côté du **dépendances supplémentaires** zone d’édition, puis choisissez **modifier**.

   ![Modifier la propriété Dépendances supplémentaires](media/mathclient-additional-dependencies-property.png "modifier la propriété Dépendances supplémentaires")

1. Dans le **dépendances supplémentaires** boîte de dialogue, ajoutez `MathLibrary.lib` à la liste dans la partie supérieure de contrôle edit.

   ![Ajoutez la dépendance de bibliothèque](media/mathclient-additional-dependencies.png "ajouter la dépendance de bibliothèque")

1. Choisissez **OK** pour revenir à la **Pages de propriétés** boîte de dialogue.

1. Dans le volet gauche, sélectionnez **général** sous **propriétés de Configuration**, **l’éditeur de liens**. Dans le volet Propriétés, sélectionnez le contrôle de liste déroulante à côté du **répertoires de bibliothèques supplémentaires** zone d’édition, puis choisissez **modifier**.

   ![Modifiez la propriété répertoires de bibliothèques supplémentaires](media/mathclient-additional-library-directories-property.png "modifier la propriété de répertoires de bibliothèques supplémentaires")

1. Double-cliquez dans le volet supérieur de la **répertoires de bibliothèques supplémentaires** boîte de dialogue pour activer un contrôle d’édition. Dans le contrôle d’édition, spécifiez le chemin d’accès à l’emplacement de la **MathLibrary.lib** fichier. Entrez cette valeur pour utiliser une macro qui fonctionne pour les versions Debug et les versions Release :

   `..\..\MathLibrary\$(IntDir)`

   ![Ajoutez le répertoire des bibliothèques](media/mathclient-additional-library-directories.png "ajouter le répertoire des bibliothèques")

1. Une fois que vous avez entré le chemin d’accès au fichier de bibliothèque dans le **répertoires de bibliothèques supplémentaires** boîte de dialogue, choisissez le **OK** bouton pour revenir à la **Pages de propriétés** boîte de dialogue.

Votre application cliente peut maintenant compiler et lier correctement, mais il n’a toujours pas tout ce dont il a besoin pour s’exécuter. Lorsque le système d’exploitation charge votre application, il recherche la DLL MathLibrary. Si elle ne peut pas trouver la DLL dans le répertoire de l’application locale, le chemin d’accès de l’environnement ou certains répertoires du système, le chargement échoue. Un pour éviter ce problème consiste à copier la DLL dans le répertoire qui contient votre fichier exécutable du client dans le cadre du processus de génération. Pour copier la DLL, vous pouvez ajouter un **événement post-Build** à votre projet, pour ajouter une commande qui copie la DLL dans votre répertoire de sortie de génération. La commande spécifiée ici copie la DLL uniquement s’il est manquant ou a changé et utilise les macros pour copier vers et depuis les emplacements corrects de versions commerciales ou de débogage pour votre configuration.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>Pour copier la DLL dans un événement post-build

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le **MathClient** projet si elle n’est pas déjà ouverte.

1. Dans la zone de liste déroulante de Configuration, sélectionnez **toutes les Configurations** si elle n’est pas déjà sélectionnée.

1. Dans le volet gauche, sélectionnez **événement post-Build** sous **propriétés de Configuration**, **des événements de Build**.

1. Dans le volet des propriétés, sélectionnez le contrôle d’édition dans le **ligne de commande** et puis entrez cette commande :

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![Ajoutez la commande post-build](media/mathclient-post-build-command-line.png "ajouter la commande post-build")

1. Choisissez le **OK** bouton pour enregistrer les modifications apportées aux propriétés du projet.

Votre application cliente a maintenant tout ce dont il a besoin pour générer et exécuter. Générez l’application en choisissant **générer**, **générer la Solution** sur la barre de menus. Le **sortie** fenêtre dans Visual Studio doit contenir quelque chose comme ceci :

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>stdafx.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

Félicitations, vous avez créé une application qui appelle des fonctions dans votre DLL. Maintenant, exécutez votre application pour voir ce qu’il fait. Dans la barre de menus, choisissez **déboguer**, **démarrer sans débogage**. Visual Studio ouvre une fenêtre de commande pour le programme à exécuter. La dernière partie de la sortie doit ressembler à ceci :

![Démarrer l’application cliente sans débogage](media/mathclient-run-without-debugging.png "démarrer l’application cliente sans débogage")

Appuyez sur n’importe quelle touche pour fermer la fenêtre de commande.

Maintenant que vous avez créé une DLL et une application cliente, vous pouvez faire des essais. Essayez de définir des points d’arrêt dans le code de l’application cliente et exécuter l’application dans le débogueur. Consultez que se passe-t-il lorsque vous parcourez un appel de la bibliothèque. Ajouter d’autres fonctions à la bibliothèque, ou d’écriture d’une autre application cliente qui utilise votre DLL.

Lorsque vous déployez votre application, vous devez également déployer les DLL, il utilise. La façon la plus simple pour rendre les DLL que vous générez ou que vous incluez de tiers à votre application consiste à les placer dans le même répertoire que votre application, également appelé *déploiement d’app-local*. Pour plus d’informations sur le déploiement, consultez [déploiement dans Visual C++](..\ide\deployment-in-visual-cpp.md).

## <a name="see-also"></a>Voir aussi

[DLL dans Visual C++](../build/dlls-in-visual-cpp.md)  
[Déploiement d’Applications de bureau](../ide/deploying-native-desktop-applications-visual-cpp.md)  
[Procédure pas à pas : déploiement de votre programme (C++)](../ide/walkthrough-deploying-your-program-cpp.md)  
[Appel de fonctions de la DLL à partir d’applications Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md)