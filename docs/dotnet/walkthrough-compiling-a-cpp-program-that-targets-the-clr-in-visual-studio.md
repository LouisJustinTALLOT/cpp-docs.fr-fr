---
title: Compiler un C + c++ / CLI programme qui cible le CLR
ms.date: 09/17/2018
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: fcac0079185b6ceef981b9acfeb555ef29d464e0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034668"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>Procédure pas à pas : Compiler un C + c++ / CLI programme qui cible le CLR dans Visual Studio

À l’aide de C++ / c++ / extensions de langage CLI vous pouvez créer des programmes C++ qui utilisent des classes .NET et les compiler à l’aide de l’environnement de développement Visual Studio.

Pour cette procédure, vous pouvez taper votre propre programme C++ ou utiliser un des exemples de programmes. L’exemple de programme que nous utilisons dans cette procédure crée un fichier texte nommé textfile.txt et l’enregistre dans le répertoire du projet.

## <a name="prerequisites"></a>Prérequis

Ces rubriques partent du principe que vous avez des notions de base du langage C++.

### <a name="to-create-a-new-project-in-visual-studio-and-add-a-new-source-file"></a>Pour créer un projet dans Visual Studio et ajouter un nouveau fichier source

1. Créer un nouveau projet. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

1. Dans les types de projets Visual C++, cliquez sur **CLR**, puis sur **Projet vide CLR**.

   > [!NOTE]
   > Si le type **Projet vide CLR** est manquant (Visual Studio 2017 uniquement), sélectionnez **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Installez l’option située sous **Développement Desktop en C++** dans la section des composants **Facultatifs**, nommée **Prise en charge de C++/CLI**.<br/>

1. Tapez un nom de projet.

   Par défaut, la solution qui contient le projet porte le même nom que le nouveau projet, mais vous pouvez entrer un autre nom. Si vous le souhaitez, vous pouvez indiquer un emplacement différent pour le projet.

   Cliquez sur **OK** pour créer le projet.

1. Si **l’Explorateur de solutions** n’est pas visible, cliquez sur **Explorateur de solutions** dans le menu **Affichage**.

1. Ajoutez un nouveau fichier source au projet :

   - Cliquez avec le bouton droit sur le dossier **Fichiers sources** dans l’**Explorateur de solutions**, pointez sur **Ajouter**, puis cliquez sur **Nouvel élément**.

   - Cliquez sur **Fichier C++ (.cpp)**, tapez un nom de fichier, puis cliquez **Ajouter**.

   Le fichier **.cpp** apparaît dans le dossier **Fichiers sources** de l’**Explorateur de solutions**. Dans la fenêtre à onglets qui s’affiche, tapez le code souhaité dans ce fichier.

1. Cliquez dans l’onglet nouvellement créé dans Visual Studio et tapez un programme Visual C++ valide, ou copiez et collez l’un des exemples de programmes.

   Par exemple, vous pouvez utiliser l’exemple de programme [Procédure : écrire un fichier texte (C++/CLI)](how-to-write-a-text-file-cpp-cli.md) (dans le nœud **Gestion des fichiers et E/S** du guide de programmation).

   Si vous avez recours à l’exemple de programme, notez que vous devez utiliser le mot clé `gcnew` à la place de `new` pour créer un objet .NET, et que `gcnew` retourne un handle (`^`) au lieu d’un pointeur (`*`) :

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Pour plus d’informations sur la nouvelle syntaxe Visual C++, consultez [Extensions de composant pour les plateformes Runtime](../extensions/component-extensions-for-runtime-platforms.md).

1. Dans le menu **Générer** , cliquez sur **Générer la solution**.

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
