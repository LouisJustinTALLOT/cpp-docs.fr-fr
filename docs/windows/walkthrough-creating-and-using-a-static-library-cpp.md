---
title: 'Procédure pas à pas : Création et utilisation d’une bibliothèque statique (C++) | Microsoft Docs'
ms.custom: get-started-article
ms.date: 07/12/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [C++], static
- static libraries [C++]
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1bcbf5747b667615c96ced3488e16f2a8fc0ef2d
ms.sourcegitcommit: 9ad287c88bdccee2747832659fe50c2e5d682a0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2018
ms.locfileid: "39034801"
---
# <a name="walkthrough-creating-and-using-a-static-library-c"></a>Procédure pas à pas : création et utilisation d’une bibliothèque statique (C++)
Cette procédure pas à pas montre comment créer une bibliothèque statique (fichier .lib) à utiliser avec des applications C++. L’utilisation d’une bibliothèque statique est un excellent moyen de réutiliser le code. Au lieu d'implémenter les mêmes routines dans chaque application qui requiert les fonctionnalités, vous les écrivez une fois pour toutes dans une bibliothèque statique et vous y faites référence dans les applications. Le code lié à partir d'une bibliothèque statique devient partie intégrante de votre application. Il n'est pas nécessaire d'installer un autre fichier pour utiliser le code.  
  
 Cette procédure pas à pas couvre les tâches suivantes :  
  
-   [Création d’un projet de bibliothèque statique](#CreateLibProject)  
  
-   [Ajout d’une classe à la bibliothèque statique](#AddClassToLib)  
  
-   [Création d’une application console C++ qui fait référence à la bibliothèque statique](#CreateAppToRefTheLib)  
  
-   [Utilisation des fonctionnalités de la bibliothèque statique dans l’application](#UseLibInApp)  
  
-   [Exécution de l’application](#RunApp)  
  
## <a name="prerequisites"></a>Prérequis  
 Une connaissance des notions de base du langage C++.  
  
##  <a name="CreateLibProject"></a> Création d’un projet de bibliothèque statique  
  
#### <a name="to-create-a-static-library-project"></a>Pour créer un projet de bibliothèque statique  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2. Dans le volet gauche de la **nouveau projet** boîte de dialogue, développez **installé, Visual C++**, puis sélectionnez **Windows Desktop**.
  
3. Dans le volet central, sélectionnez **Windows Desktop Assistant**.  
  
4.  Spécifiez un nom pour le projet, par exemple **MathFuncsLib**, dans la zone **Nom** . Spécifiez un nom pour la solution, par exemple **StaticLibrary**, dans la zone **Nom de la solution** . Sélectionnez le bouton **OK** .  
  
5. Sous **type d’Application**, sélectionnez la bibliothèque statique (.lib).  
  
6. Sous **des Options supplémentaires**, décochez la case la **en-tête précompilé** case à cocher.
  
7. Choisissez **OK** pour créer le projet.  
 
##  <a name="AddClassToLib"></a> Ajout d’une classe à la bibliothèque statique  
  
#### <a name="to-add-a-class-to-the-static-library"></a>Pour ajouter une classe à la bibliothèque statique  
  
1.  Pour créer un fichier d’en-tête pour une nouvelle classe, ouvrez le menu contextuel du projet **MathFuncsLib** dans l’ **Explorateur de solutions**, puis sélectionnez **Ajouter**, **Nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , dans le volet gauche, sous **Visual C++**, sélectionnez **Code**. Dans le volet central, sélectionnez **Fichier d’en-tête (.h)**. Spécifiez un nom pour le fichier d’en-tête, par exemple **MathFuncsLib.h**, puis sélectionnez le bouton **Ajouter** . Un fichier d’en-tête vierge s’affiche.  
  
2.  Ajoutez une classe nommée **MyMathFuncs** pour effectuer des opérations mathématiques courantes, comme l’addition, la soustraction, la multiplication et la division. Le code doit se présenter comme suit :  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]  
  
3.  Pour créer un fichier source pour la nouvelle classe, ouvrez le menu contextuel du projet **MathFuncsLib** dans l’ **Explorateur de solutions**, puis sélectionnez **Ajouter**, **Nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , dans le volet gauche, sous **Visual C++**, sélectionnez **Code**. Dans le volet central, sélectionnez **Fichier C++ (.cpp)**. Spécifiez un nom pour le fichier source, par exemple **MathFuncsLib.cpp**, puis sélectionnez le bouton **Ajouter** . Un fichier source vide s’affiche.  
  
4.  Utilisez ce fichier source pour implémenter les fonctionnalités pour **MyMathFuncs**. Le code doit se présenter comme suit :  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]  
  
5.  Compilez la bibliothèque statique en sélectionnant **Générer**, puis **Générer la solution** dans la barre de menus. Cela crée une bibliothèque statique qui peut être utilisée par d'autres programmes.  
  
    > [!NOTE]
    >  Lorsque vous générez un projet sur la ligne de commande Visual Studio, vous devez générer le programme en deux étapes. Commencez par exécuter **cl /c /EHsc MathFuncsLib.cpp** pour compiler le code et pour créer un fichier objet nommé **MathFuncsLib.obj**. (Le **cl** commande appelle le compilateur, Cl.exe et le **/c** option spécifie la compilation sans liaison. Pour plus d’informations, consultez [/c (compiler sans liaison)](../build/reference/c-compile-without-linking.md).) Ensuite, exécutez **lib MathFuncsLib.obj** pour lier le code et créer la bibliothèque statique **MathFuncsLib.lib**. (La commande **lib** appelle le gestionnaire de bibliothèque Lib.exe. Pour plus d’informations, consultez [LIB Reference](../build/reference/lib-reference.md).)  
  
##  <a name="CreateAppToRefTheLib"></a> Création d’une application console C++ qui fait référence à la bibliothèque statique  
  
#### <a name="to-create-a-c-console-app-that-references-the-static-library"></a>Pour créer une application console C++ qui fait référence à la bibliothèque statique  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2. Dans le volet gauche de la **nouveau projet** boîte de dialogue, développez **installé, Visual C++**, puis sélectionnez **Windows Desktop**.  

3. Dans le volet central, sélectionnez **Windows Desktop Assistant**.  
  
4.  Spécifiez un nom pour le projet, par exemple **MyExecRefsLib**, dans la zone **Nom** . Dans la liste déroulante, en regard de **Solution**, sélectionnez **Ajouter à la solution**. Le nouveau projet est ajouté à la solution qui contient la bibliothèque statique. Sélectionnez le bouton **OK** .  
5. Sous **type d’Application**, sélectionnez **Application Console (.exe)**.

6. Sous **Additioal Options**, décochez la case la **en-tête précompilé** case à cocher.

7. Choisissez **OK** pour créer le projet.  
  
##  <a name="UseLibInApp"></a> Utilisation des fonctionnalités de la bibliothèque statique dans l’application  
  
#### <a name="to-use-the-functionality-from-the-static-library-in-the-app"></a>Pour utiliser les fonctionnalités de la bibliothèque statique dans l’application  
  
1.  Une fois que vous avez créé une application console, un programme vide est créé à votre intention. Le nom du fichier source est identique au nom que vous avez choisi précédemment. Dans cet exemple, il est nommé **MyExecRefsLib.cpp**.  
  
2.  Avant de pouvoir utiliser les routines mathématiques dans la bibliothèque statique, vous devez la référencer. Pour ce faire, ouvrez le menu contextuel du projet MyExecRefsLib dans **l’Explorateur de solutions**, puis choisissez **ajouter, référence**.  
  
3.  La boîte de dialogue **Ajouter une référence** répertorie les bibliothèques que vous pouvez référencer. L’onglet **Projets** répertorie tous les projets de la solution actuelle et toutes les bibliothèques qu’ils contiennent. Sous l’onglet **Projets** , cochez la case **MathFuncsLib** , puis sélectionnez le bouton **OK** .  
  
4.  Pour faire référence au fichier d’en-tête **MathFuncsLib.h** , vous devez modifier le chemin des répertoires inclus. Dans la boîte de dialogue **Pages de propriétés** de **MyExecRefsLib**, développez le nœud **Propriétés de configuration** , développez **C/C++** , puis sélectionnez **Général**. En regard de **Autres répertoires Include**, spécifiez le chemin du répertoire **MathFuncsLib** ou accédez à ce dernier.  
  
     Pour rechercher le chemin d’accès du répertoire, ouvrez la liste déroulante des valeurs de propriété, puis sélectionnez **Modifier**. Dans le **autres répertoires Include** boîte de dialogue, dans la zone de texte, sélectionnez une ligne vierge, puis choisissez le bouton de sélection (**...** ) à la fin de la ligne. Dans la boîte de dialogue **Sélectionner un répertoire** , sélectionnez le répertoire **MathFuncsLib** , puis choisissez le bouton **Sélectionner un dossier** pour enregistrer votre sélection et fermer la boîte de dialogue. Dans la boîte de dialogue **Autres répertoires Include** , choisissez le bouton **OK** puis, dans la boîte de dialogue **Pages de propriétés** , choisissez le bouton **OK** pour enregistrer les modifications apportées au projet.  
  
5.  Vous pouvez maintenant utiliser la classe **MyMathFuncs** dans cette application. Pour cela, remplacez le contenu de **MyExecRefsLib.cpp** par le code suivant :  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]  
  
6.  Générez le fichier exécutable en sélectionnant **Générer**, **Générer la solution** dans la barre de menus.  
  
##  <a name="RunApp"></a> Exécution de l’application  
  
#### <a name="to-run-the-app"></a>Pour exécuter l’application  
  
1.  Assurez-vous que **MyExecRefsLib** est sélectionné comme projet par défaut en ouvrant le menu contextuel pour **MyExecRefsLib** dans l’ **Explorateur de solutions**, puis en choisissant **Définir comme projet de démarrage**.  
  
2.  Pour exécuter le projet, dans la barre de menus, choisissez **Exécuter sans débogage**dans le menu **Débogage**. La sortie doit ressembler à ceci :  
  
    ```Output  
    a + b = 106.4  
    a - b = -91.6  
    a * b = 732.6  
    a / b = 0.0747475  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : création et utilisation d’une bibliothèque de liens dynamiques (C++)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)   
 [Applications de bureau (Visual C++)](../windows/desktop-applications-visual-cpp.md)
