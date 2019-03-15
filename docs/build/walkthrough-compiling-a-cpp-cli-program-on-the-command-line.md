---
title: 'Procédure pas à pas : Compilation de C++ / c++ / CLI des programme sur la ligne de commande'
ms.date: 09/24/2018
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: c90d2c915db7264dc1b4e4807803e063c2a24fc7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811925"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Procédure pas à pas : Compilation de C++ / c++ / CLI des programme sur la ligne de commande

Vous pouvez créer des programmes Visual C++ qui ciblent le Common Language Runtime (CLR) et utilisent le .NET Framework, et vous pouvez les générer à partir de la ligne de commande. Visual C++ prend en charge le langage de programmation C++/CLI, qui possède des types et opérateurs supplémentaires pour cibler le modèle de programmation .NET. Pour des informations générales sur le C++ / c++ / langue de l’interface CLI, consultez [programmation .NET avec C++ / c++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Dans cette procédure pas à pas, vous allez créer un programme C++/CLI élémentaire à l'aide d'un éditeur de texte, puis le compiler sur la ligne de commande. (Vous pouvez utiliser votre propre programme C++/CLI au lieu de taper le programme illustré, ou vous pouvez utiliser un exemple de code C++/CLI tiré d'un autre article d'aide. Cette technique est utile pour générer et tester des petits modules qui ont des éléments d’interface utilisateur).

## <a name="prerequisites"></a>Prérequis

Vous comprenez les notions de base du langage C++.

## <a name="compiling-a-ccli-program"></a>Compilation d'un programme C++/CLI

La procédure suivante illustre la compilation d'une application de console C++/CLI qui utilise des classes .NET Framework.

Pour activer la compilation pour C / c++ / CLI, vous devez utiliser le [/CLR](reference/clr-common-language-runtime-compilation.md) option du compilateur. Le compilateur MSVC génère un fichier .exe qui contient du code MSIL, ou en mode mixte MSIL et le code natif et des liens vers les bibliothèques requises de .NET Framework.

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Pour compiler une application C++/CLI sur la ligne de commande

1. Ouvrir un **invite de commandes développeur** fenêtre. Pour obtenir des instructions spécifiques, consultez [pour ouvrir une fenêtre d’invite de commandes développeur](building-on-the-command-line.md#developer_command_prompt).

   Des informations d'identification d'administrateur peuvent être nécessaires pour compiler le code, selon la configuration et le système d'exploitation de l'ordinateur. Pour exécuter la fenêtre d’invite de commandes en tant qu’administrateur, cliquez sur pour ouvrir le menu contextuel de l’invite de commandes, puis choisissez **plus** > **exécuter en tant qu’administrateur**.

1. À l'invite de commandes, entrez `notepad basicclr.cpp`.

   Choisissez **Oui** lorsque vous êtes invité à créer un fichier.

1. Dans le Bloc-notes, tapez les lignes suivantes :

   ```cpp
   int main()
   {
       System::Console::WriteLine("This is a C++/CLI program.");
   }
   ```

1. Dans la barre de menus, choisissez **fichier** > **enregistrer**.

   Vous avez créé un fichier source Visual C++ qui utilise une classe .NET Framework (<xref:System.Console>) dans le <xref:System> espace de noms.

1. À l'invite de commandes, entrez `cl /clr basicclr.cpp`. Le compilateur cl.exe compile le code source en un fichier .obj qui contient du code MSIL, puis exécute l'éditeur de liens pour générer un programme exécutable nommé basicclr.exe.

1. Pour exécuter le programme basicclr.exe, à l'invite de commandes, entrez `basicclr`.

   Le programme affiche ce texte puis se ferme :

   ```Output
   This is a C++/CLI program.
   ```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Projets et des systèmes de génération](projects-and-build-systems-cpp.md)<br/>
[Options du compilateur MSVC](reference/compiler-options.md)
