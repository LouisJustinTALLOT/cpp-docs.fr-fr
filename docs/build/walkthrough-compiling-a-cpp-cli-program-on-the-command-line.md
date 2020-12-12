---
description: 'En savoir plus sur : procédure pas à pas : compilation d’un programme C++/CLI sur la ligne de commande'
title: "Procédure pas à pas : compilation d'un programme C++/CLI sur la ligne de commande"
ms.date: 04/23/2019
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: 075ac90f08f62fb75c9a220b398f34841eafa60d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198997"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Procédure pas à pas : compilation d'un programme C++/CLI sur la ligne de commande

Vous pouvez créer des programmes Visual C++ qui ciblent le Common Language Runtime (CLR) et utilisent le .NET Framework, et vous pouvez les générer à partir de la ligne de commande. Visual C++ prend en charge le langage de programmation C++/CLI, qui possède des types et opérateurs supplémentaires pour cibler le modèle de programmation .NET. Pour obtenir des informations générales sur le langage C++/CLI, consultez [programmation .net avec c++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Dans cette procédure pas à pas, vous allez créer un programme C++/CLI élémentaire à l'aide d'un éditeur de texte, puis le compiler sur la ligne de commande. (Vous pouvez utiliser votre propre programme C++/CLI au lieu de taper le programme illustré, ou vous pouvez utiliser un exemple de code C++/CLI tiré d'un autre article d'aide. Cette technique est utile pour générer et tester de petits modules qui n’ont pas d’éléments d’interface utilisateur.)

## <a name="prerequisites"></a>Prérequis

Vous comprenez les notions de base du langage C++.

## <a name="compiling-a-ccli-program"></a>Compilation d'un programme C++/CLI

La procédure suivante illustre la compilation d'une application de console C++/CLI qui utilise des classes .NET Framework.

Pour activer la compilation pour C++/CLI, vous devez utiliser l’option du compilateur [/CLR](reference/clr-common-language-runtime-compilation.md) . Le compilateur MSVC génère un fichier. exe contenant du code MSIL, ou du code MSIL mixte et du code natif, ainsi que des liens vers les bibliothèques .NET Framework requises.

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Pour compiler une application C++/CLI sur la ligne de commande

1. Ouvrez une fenêtre de **invite de commandes développeur** . Pour obtenir des instructions spécifiques, consultez [pour ouvrir une fenêtre d’invite de commandes développeur](building-on-the-command-line.md#developer_command_prompt).

   Des informations d'identification d'administrateur peuvent être nécessaires pour compiler le code, selon la configuration et le système d'exploitation de l'ordinateur. Pour exécuter la fenêtre d’invite de commandes en tant qu’administrateur, cliquez avec le bouton droit pour ouvrir le menu contextuel de l’invite de commandes, puis choisissez **plus**  >  **exécuter en tant qu’administrateur**.

1. À l'invite de commandes, entrez `notepad basicclr.cpp`.

   Choisissez **Oui** lorsque vous êtes invité à créer un fichier.

1. Dans le Bloc-notes, tapez les lignes suivantes :

   ```cpp
   int main()
   {
       System::Console::WriteLine("This is a C++/CLI program.");
   }
   ```

1. Dans la barre de menus, choisissez **fichier**  >  **Enregistrer**.

   Vous avez créé un Visual C++ fichier source qui utilise une classe .NET Framework ( <xref:System.Console> ) dans l' <xref:System> espace de noms.

1. À l'invite de commandes, entrez `cl /clr basicclr.cpp`. Le compilateur cl.exe compile le code source en un fichier .obj qui contient du code MSIL, puis exécute l'éditeur de liens pour générer un programme exécutable nommé basicclr.exe.

1. Pour exécuter le programme basicclr.exe, à l'invite de commandes, entrez `basicclr`.

   Le programme affiche ce texte puis se ferme :

   ```Output
   This is a C++/CLI program.
   ```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Projets et systèmes de build](projects-and-build-systems-cpp.md)<br/>
[Options du compilateur MSVC](reference/compiler-options.md)
