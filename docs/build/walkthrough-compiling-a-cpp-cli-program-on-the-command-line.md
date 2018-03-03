---
title: "Procédure pas à pas : Compilation d’un c++ / CLI des programme sur la ligne de commande | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d509bc9890f4fa5ccebbd6ae3d1e3bcb3dbb0d93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Procédure pas à pas : compilation d'un programme C++/CLI sur la ligne de commande
Vous pouvez créer des programmes Visual C++ qui ciblent le Common Language Runtime (CLR) et utilisent le .NET Framework, et vous pouvez les générer à partir de la ligne de commande. Visual C++ prend en charge le langage de programmation C++/CLI, qui possède des types et opérateurs supplémentaires pour cibler le modèle de programmation .NET. Pour obtenir une présentation C + c++ / langage CLI, consultez [C++ pur : Hello, C + c++ / CLI](http://msdn.microsoft.com/magazine/cc163681.aspx). Pour plus d’informations, consultez [programmation .NET avec C++ / CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
 Dans cette procédure pas à pas, vous allez créer un programme C++/CLI élémentaire à l'aide d'un éditeur de texte, puis le compiler sur la ligne de commande. (Vous pouvez utiliser votre propre programme C++/CLI au lieu de taper le programme illustré, ou vous pouvez utiliser un exemple de code C++/CLI tiré d'un autre article d'aide. Cette technique est utile pour générer et tester des petits modules qui ne contiennent pas d'éléments d'interface utilisateur).  
  
> [!NOTE]
>  Vous pouvez également utiliser l'IDE de Visual Studio pour compiler les programmes C++/CLI. Pour plus d’informations, consultez [procédure pas à pas : compilation d’un programme C++ qui cible le CLR dans Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Vous devez posséder des notions de base du langage C++.  
  
## <a name="compiling-a-ccli-program"></a>Compilation d'un programme C++/CLI  
 La procédure suivante illustre la compilation d'une application de console C++/CLI qui utilise des classes .NET Framework.  
  
 Pour activer la compilation pour du code c++ / CLI, vous devez utiliser le [/CLR](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur. Le compilateur Visual C++ génère un fichier .exe qui contient du code MSIL (ou du code mixte MSIL/natif) et le lie aux bibliothèques .NET Framework nécessaires.  
  
#### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Pour compiler une application C++/CLI sur la ligne de commande  
  
1.  Ouvrir un **invite de commandes développeur** fenêtre. Pour obtenir des instructions, consultez [pour ouvrir une fenêtre d’invite de commandes développeur](../build/building-on-the-command-line.md#developer_command_prompt).  
  
     Des informations d'identification d'administrateur peuvent être nécessaires pour compiler le code, selon la configuration et le système d'exploitation de l'ordinateur. Pour exécuter la fenêtre d’invite de commandes en tant qu’administrateur, cliquez sur pour ouvrir le menu contextuel de l’invite de commandes, puis choisissez **plus**, **exécuter en tant qu’administrateur**.  
  
2.  À l’invite de commandes, entrez **bloc-notes basicclr.cpp**.  
  
     Choisissez **Oui** lorsque vous êtes invité à créer un fichier.  
  
3.  Dans le Bloc-notes, tapez les lignes suivantes :  
  
    ```  
    int main()  
    {  
        System::Console::WriteLine("This is a C++/CLI program.");  
    }  
    ```  
  
4.  Dans la barre de menus, choisissez **fichier**, **enregistrer**.  
  
     Vous venez de créer un fichier source Visual C++ qui utilise une classe .NET Framework (<xref:System.Console>) dans l'espace de noms <xref:System>.  
  
5.  À l’invite de commandes, entrez **cl /clr basicclr.cpp**. Le compilateur cl.exe compile le code source en un fichier .obj qui contient du code MSIL, puis exécute l'éditeur de liens pour générer un programme exécutable nommé basicclr.exe.  
  
6.  Pour exécuter le programme basicclr.exe, à l’invite de commandes, entrez **basicclr**.  
  
     Le programme affiche ce texte puis se ferme :  
  
    ```Output  
    This is a C++/CLI program.  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du langage C++](../cpp/cpp-language-reference.md)   
 [Génération de programmes C/C++](../build/building-c-cpp-programs.md)   
 [Options du compilateur](../build/reference/compiler-options.md)