---
title: "Procédure pas à pas : compilation d'un programme C++/CLI sur la ligne de commande"
ms.date: 09/24/2018
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: e8841600fd61aacfe5b942ac4a4305619dff7e90
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451023"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Procédure pas à pas : compilation d'un programme C++/CLI sur la ligne de commande

Vous pouvez créer des programmes Visual C++ qui ciblent le Common Language Runtime (CLR) et utilisent le .NET Framework, et vous pouvez les générer à partir de la ligne de commande. Visual C++ prend en charge le langage de programmation C++/CLI, qui possède des types et opérateurs supplémentaires pour cibler le modèle de programmation .NET. Pour des informations générales sur le C++ / c++ / langue de l’interface CLI, consultez [programmation .NET avec C++ / c++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

Dans cette procédure pas à pas, vous allez créer un programme C++/CLI élémentaire à l'aide d'un éditeur de texte, puis le compiler sur la ligne de commande. (Vous pouvez utiliser votre propre programme C++/CLI au lieu de taper le programme illustré, ou vous pouvez utiliser un exemple de code C++/CLI tiré d'un autre article d'aide. Cette technique est utile pour générer et tester des petits modules qui ont des éléments d’interface utilisateur).

> [!NOTE]
> Vous pouvez également utiliser l'IDE de Visual Studio pour compiler les programmes C++/CLI. Pour plus d’informations, consultez [procédure pas à pas : compilation d’un programme C++ qui cible le CLR dans Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md).

## <a name="prerequisites"></a>Prérequis

Vous comprenez les notions de base du langage C++.

## <a name="compiling-a-ccli-program"></a>Compilation d'un programme C++/CLI

La procédure suivante illustre la compilation d'une application de console C++/CLI qui utilise des classes .NET Framework.

Pour activer la compilation pour C / c++ / CLI, vous devez utiliser le [/CLR](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur. Le compilateur Visual C++ génère un fichier .exe qui contient du code MSIL (ou du code mixte MSIL/natif) et le lie aux bibliothèques .NET Framework nécessaires.

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Pour compiler une application C++/CLI sur la ligne de commande

1. Ouvrir un **invite de commandes développeur** fenêtre. Pour obtenir des instructions spécifiques, consultez [pour ouvrir une fenêtre d’invite de commandes développeur](../build/building-on-the-command-line.md#developer_command_prompt).

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
[Génération de programmes C/C++](../build/building-c-cpp-programs.md)<br/>
[Options du compilateur](../build/reference/compiler-options.md)
