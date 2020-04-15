---
title: Compiler un programme C++/CLI qui cible le CLR
description: Utilisez Microsoft CMD pour créer des programmes et des bibliothèques qui peuvent connecter des programmes CMD et .NET natifs.
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 0d661d9e77211a0e49f8695ad713b607377a236a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371812"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>Procédure pas à pas : Compilez un programme CMD/CLI qui cible le CLR en studio visuel

En utilisant les programmes CMD/CLI, vous pouvez créer des programmes CMD qui utilisent des classes .NET ainsi que des types CMD natifs. L’IMC est destiné à être utilisé dans les applications de consoles et dans les DL Qui enveloppent le code CMD natif et le rendent accessible à partir de programmes .NET. Pour créer une interface utilisateur Windows basée sur .NET, utilisez C ou Visual Basic.

Pour cette procédure, vous pouvez taper votre propre programme CMD ou utiliser l’un des programmes d’échantillons. L’exemple de programme que nous utilisons dans cette procédure crée un fichier texte nommé textfile.txt et l’enregistre dans le répertoire du projet.

## <a name="prerequisites"></a>Prérequis

- Une connaissance des notions de base du langage C++.
- Dans Visual Studio 2017 et plus tard, le support C/CLI est un composant optionnel. Pour l’installer, ouvrez **l’installateur Visual Studio** à partir du menu Windows Start. Assurez-vous que le développement de bureau avec la tuile **CMD** est vérifié, et dans la section composants **facultatifs,** vérifiez également **le support CMD/CLI**.

## <a name="create-a-new-project"></a>Création d'un projet

Les étapes suivantes varient légèrement selon la version de Visual Studio que vous utilisez. Pour voir la documentation de votre version préférée de Visual Studio, utilisez le contrôle du sélecteur **Version.** On le trouve en haut de la table des contenus sur cette page.

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>Créer un projet CMD/CLI dans Visual Studio 2019

1. Dans **Solution Explorer**, cliquez à droite sur le dessus pour ouvrir la boîte de dialogue Create a New **Project.**

1. En haut du dialogue, tapez **CLR** dans la boîte de recherche, puis choisissez **CLR Empty Project** dans la liste des résultats.

1. Choisissez le bouton **Créer** pour créer le projet.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>Créer un projet CMD/CLI dans Visual Studio 2017

1. Créez un projet. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

1. Dans les types de projets Visual C++, cliquez sur **CLR**, puis sur **Projet vide CLR**.

1. Tapez un nom de projet. Par défaut, la solution qui contient le projet porte le même nom que le nouveau projet, mais vous pouvez entrer un autre nom. Si vous le souhaitez, vous pouvez indiquer un emplacement différent pour le projet.

1. Cliquez sur **OK** pour créer le projet.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>Créer un projet CMD/CLI dans Visual Studio 2015

1. Créez un projet. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

1. Dans les types de projets Visual C++, cliquez sur **CLR**, puis sur **Projet vide CLR**.

1. Tapez un nom de projet. Par défaut, la solution qui contient le projet porte le même nom que le nouveau projet, mais vous pouvez entrer un autre nom. Si vous le souhaitez, vous pouvez indiquer un emplacement différent pour le projet.

1. Cliquez sur **OK** pour créer le projet.

::: moniker-end

## <a name="add-a-source-file"></a>Ajouter un fichier source

1. Si **l’Explorateur de solutions** n’est pas visible, cliquez sur **Explorateur de solutions** dans le menu **Affichage**.

1. Ajoutez un nouveau fichier source au projet :

   - Cliquez à droite sur le dossier **Source Files** dans **Solution Explorer**, pointez pour **ajouter**, et cliquez sur **Nouvel article**.

   - Cliquez sur **Fichier C++ (.cpp)**, tapez un nom de fichier, puis cliquez **Ajouter**.

   Le fichier **.cpp** apparaît dans le dossier **Source Files** dans **Solution Explorer** et une fenêtre tabbed apparaît là où vous tapez le code que vous voulez dans ce fichier.

1. Cliquez dans l’onglet nouvellement créé dans Visual Studio et tapez un programme Visual C++ valide, ou copiez et collez l’un des exemples de programmes.

   Vous pouvez par exemple utiliser l’exemple de programme [Guide pratique pour écrire un fichier texte (C++/CLI)](how-to-write-a-text-file-cpp-cli.md) (dans le nœud **Gestion de fichiers et E/S** du guide de programmation).

   Si vous avez recours à l’exemple de programme, notez que vous devez utiliser le mot clé `gcnew` à la place de `new` pour créer un objet .NET, et que `gcnew` retourne un handle (`^`) au lieu d’un pointeur (`*`) :

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   Pour plus d’informations sur la syntaxe C/CLI, voir [Extensions de composants pour les plates-formes Runtime](../extensions/component-extensions-for-runtime-platforms.md).

1. Dans le menu **Générer**, cliquez sur **Générer la solution**.

   La fenêtre **Sortie** affiche des informations sur la progression de la compilation, comme l’emplacement du journal de génération, et un message indiquant l’état de la build.

   Si vous modifiez et exécutez le programme sans effectuer de génération, une boîte de dialogue peut indiquer que le projet est obsolète. Cochez la case dans cette boîte de dialogue avant de cliquer sur **OK** si vous souhaitez que Visual Studio utilise toujours les versions actuelles des fichiers au lieu de vous le demander chaque fois qu’il génère l’application.

1. Dans le menu **Déboguer**, cliquez sur **Démarrer sans débogage**.

1. Quand vous exécutez l’exemple de programme, une fenêtre de commande s’affiche et indique que le fichier texte a été créé.

   Le fichier texte **textfile.txt** se trouve désormais dans votre répertoire de projet. Vous pouvez ouvrir ce fichier à l’aide du Bloc-notes.

   > [!NOTE]
   > Si vous choisissez le modèle Projet vide CLR, l’option de compilateur `/clr` est définie automatiquement. Pour le vérifier, cliquez avec le bouton droit sur le projet dans **l’Explorateur de solutions**, cliquez sur **Propriétés**, puis examinez l’option **Prise en charge du Common Language Runtime** dans le nœud ** Général** de **Propriétés de configuration**.

## <a name="see-also"></a>Voir aussi

[Référence linguistique de CMD](../cpp/cpp-language-reference.md)<br/>
[Projets et systèmes de build](../build/projects-and-build-systems-cpp.md)<br/>
