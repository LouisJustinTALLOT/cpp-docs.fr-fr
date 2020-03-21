---
title: Compiler un C++programme/CLI qui cible le CLR
description: Utilisez Microsoft C++ pour créer des programmes et des bibliothèques qui peuvent C++ se connecter à du code natif et à des programmes .net.
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 36c41856dfcdb5c5f50ba59205b4c73c5fde5963
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080017"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>Procédure pas à pas C++: compiler un programme/CLI qui cible le CLR dans Visual Studio

À l' C++aide de la fonction C++ /CLI, vous pouvez créer des programmes qui utilisent C++ des classes .net ainsi que des types natifs. C++/CLI est destiné à être utilisé dans des applications console et dans des dll C++ qui encapsulent du code natif et le rendent accessible à partir de programmes .net. Pour créer une interface utilisateur Windows basée sur .NET, utilisez C# ou Visual Basic.

Pour cette procédure, vous pouvez taper votre propre C++ programme ou utiliser l’un des exemples de programmes. L’exemple de programme que nous utilisons dans cette procédure crée un fichier texte nommé textfile.txt et l’enregistre dans le répertoire du projet.

## <a name="prerequisites"></a>Conditions préalables requises

- Une connaissance des notions de base du langage C++.
- Dans Visual Studio 2017 et versions ultérieures, C++la prise en charge de/CLI est un composant facultatif. Pour l’installer, ouvrez le **Visual Studio installer** à partir du menu Démarrer de Windows. Assurez-vous que l’option **développement bureau avec C++**  vignette est cochée, et dans la section composants **facultatifs** , vérifiez  **C++également prise en charge d'/CLI**.

## <a name="create-a-new-project"></a>Création d'un projet

Les étapes suivantes varient légèrement selon la version de Visual Studio que vous utilisez. Vérifiez que vous avez sélectionné la bonne version dans le sélecteur de version situé en haut à gauche de la page.

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>Pour créer un C++projet/CLI dans Visual Studio 2019

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le haut pour ouvrir la boîte de dialogue **créer un nouveau projet** .

1. En haut de la boîte de dialogue, tapez **CLR** dans la zone de recherche, puis choisissez **projet vide CLR** dans la liste des résultats.

1. Choisissez le bouton **Créer** pour créer le projet.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>Pour créer un C++projet/CLI dans Visual Studio 2017

1. Créez un projet. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

1. Dans les types de projets Visual C++, cliquez sur **CLR**, puis sur **Projet vide CLR**.

1. Tapez un nom de projet. Par défaut, la solution qui contient le projet porte le même nom que le nouveau projet, mais vous pouvez entrer un autre nom. Si vous le souhaitez, vous pouvez indiquer un emplacement différent pour le projet.

1. Cliquez sur **OK** pour créer le projet.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>Pour créer un C++projet/CLI dans Visual Studio 2015

1. Créez un projet. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

1. Dans les types de projets Visual C++, cliquez sur **CLR**, puis sur **Projet vide CLR**.

1. Tapez un nom de projet. Par défaut, la solution qui contient le projet porte le même nom que le nouveau projet, mais vous pouvez entrer un autre nom. Si vous le souhaitez, vous pouvez indiquer un emplacement différent pour le projet.

1. Cliquez sur **OK** pour créer le projet.

::: moniker-end

## <a name="add-a-source-file"></a>Ajouter un fichier source

1. Si **l’Explorateur de solutions** n’est pas visible, cliquez sur **Explorateur de solutions** dans le menu **Affichage**.

1. Ajoutez un nouveau fichier source au projet :

   - Cliquez avec le bouton droit sur le dossier **Fichiers sources** dans l’**Explorateur de solutions**, pointez sur **Ajouter**, puis cliquez sur **Nouvel élément**.

   - Cliquez sur **Fichier C++ (.cpp)** , tapez un nom de fichier, puis cliquez **Ajouter**.

   Le fichier **.cpp** apparaît dans le dossier **Fichiers sources** de l’**Explorateur de solutions**. Dans la fenêtre à onglets qui s’affiche, tapez le code souhaité dans ce fichier.

1. Cliquez dans l’onglet nouvellement créé dans Visual Studio et tapez un programme Visual C++ valide, ou copiez et collez l’un des exemples de programmes.

   Vous pouvez par exemple utiliser l’exemple de programme [Guide pratique pour écrire un fichier texte (C++/CLI)](how-to-write-a-text-file-cpp-cli.md) (dans le nœud **Gestion de fichiers et E/S** du guide de programmation).

   Si vous avez recours à l’exemple de programme, notez que vous devez utiliser le mot clé `gcnew` à la place de `new` pour créer un objet .NET, et que `gcnew` retourne un handle (`^`) au lieu d’un pointeur (`*`) :

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Pour plus d’informations C++sur la syntaxe/CLI, consultez [extensions de composant pour les plateformes Runtime](../extensions/component-extensions-for-runtime-platforms.md).

1. Dans le menu **Générer**, cliquez sur **Générer la solution**.

   La fenêtre **Sortie** affiche des informations sur la progression de la compilation, comme l’emplacement du journal de génération, et un message indiquant l’état de la build.

   Si vous modifiez et exécutez le programme sans effectuer de génération, une boîte de dialogue peut indiquer que le projet est obsolète. Cochez la case dans cette boîte de dialogue avant de cliquer sur **OK** si vous souhaitez que Visual Studio utilise toujours les versions actuelles des fichiers au lieu de vous le demander chaque fois qu’il génère l’application.

1. Dans le menu **Déboguer**, cliquez sur **Démarrer sans débogage**.

1. Quand vous exécutez l’exemple de programme, une fenêtre de commande s’affiche et indique que le fichier texte a été créé.

   Le fichier texte **textfile.txt** se trouve désormais dans votre répertoire de projet. Vous pouvez ouvrir ce fichier à l’aide du Bloc-notes.

   > [!NOTE]
   > Si vous choisissez le modèle Projet vide CLR, l’option de compilateur `/clr` est définie automatiquement. Pour le vérifier, cliquez avec le bouton droit sur le projet dans **l’Explorateur de solutions**, cliquez sur **Propriétés**, puis examinez l’option **Prise en charge du Common Language Runtime** dans le nœud  **Général** de **Propriétés de configuration**.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Projets et systèmes de build](../build/projects-and-build-systems-cpp.md)<br/>
