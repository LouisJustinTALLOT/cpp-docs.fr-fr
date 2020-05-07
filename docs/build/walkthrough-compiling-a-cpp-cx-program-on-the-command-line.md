---
title: "Procédure pas à pas : compilation d'un programme C++/CX sur la ligne de commande"
ms.date: 04/23/2019
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: 83369fc7b458463ea1f44a347bbcd0ca4eb32224
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078205"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>Procédure pas à pas : compilation d'un programme C++/CX sur la ligne de commande

> [!NOTE]
> Pour les nouveaux composants et applications UWP, nous vous recommandons d’utiliser [c++/WinRT](/windows/uwp/cpp-and-winrt-apis/), une projection de langage c++ 17 standard pour les API Windows Runtime. C++/WinRT est disponible dans le kit de développement logiciel (SDK) Windows 10 à partir de la version 1803. C++/WinRT est implémenté entièrement dans les fichiers d’en-tête et est conçu pour vous fournir un accès de première classe à l’API Windows moderne.

Le compilateur Microsoft C++ (MSVC) prend en charge les extensions de composant C++ (C++/CX), qui dispose de types et d’opérateurs supplémentaires pour cibler le modèle de programmation Windows Runtime. Vous pouvez utiliser C++/CX pour générer des applications pour plateforme Windows universelle (UWP) et Windows Desktop. Pour plus d’informations, consultez [la visite guidée de C++/CX](https://msdn.microsoft.com/magazine/dn166929.aspx) et des [extensions de composant pour les plateformes Runtime](../extensions/component-extensions-for-runtime-platforms.md).

Dans cette procédure pas à pas, vous allez créer un programme C++/CX élémentaire à l'aide d'un éditeur de texte, puis le compiler sur la ligne de commande. (Vous pouvez utiliser votre propre programme C++/CX au lieu de taper le programme illustré, ou vous pouvez utiliser un exemple de code C++/CX tiré d'un autre article d'aide. Cette technique est utile pour générer et tester de petits modules qui n’ont pas d’éléments d’interface utilisateur.)

> [!NOTE]
> Vous pouvez également utiliser l'IDE de Visual Studio pour compiler les programmes C++/CX. Étant donné que l’IDE comprend une prise en charge de la conception, du débogage, de l’émulation et du déploiement qui n’est pas disponible sur la ligne de commande, nous vous recommandons d’utiliser l’IDE pour générer des applications plateforme Windows universelle (UWP). Pour plus d’informations, consultez [créer une application UWP en C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

## <a name="prerequisites"></a>Prérequis

Vous comprenez les notions de base du langage C++.

## <a name="compiling-a-ccx-program"></a>Compilation d'un programme C++/CX

Pour activer la compilation pour les/CX C++, vous devez utiliser l’option du compilateur [/ZW](reference/zw-windows-runtime-compilation.md) . Le compilateur MSVC génère un fichier. exe qui cible le Windows Runtime, ainsi que des liens vers les bibliothèques requises.

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>Pour compiler une application C++/CX sur la ligne de commande

1. Ouvrez une fenêtre de **invite de commandes développeur** . (Dans la fenêtre **Démarrer** , ouvrez **applications**. Ouvrez le dossier **Visual Studio Tools** sous votre version de Visual Studio, puis choisissez le raccourci **invite de commandes développeur** .) Pour plus d’informations sur la façon d’ouvrir une fenêtre de Invite de commandes développeur, consultez [utiliser l’ensemble d’outils MSVC à partir de la ligne de commande](building-on-the-command-line.md).

   Des informations d'identification d'administrateur peuvent être nécessaires pour compiler le code, selon la configuration et le système d'exploitation de l'ordinateur. Pour exécuter la fenêtre d’invite de commandes en tant qu’administrateur, ouvrez le menu contextuel pour **invite de commandes développeur** , puis choisissez **exécuter en tant qu’administrateur**.

1. À l’invite de commandes, entrez **Notepad basiccx. cpp**.

   Choisissez **Oui** lorsque vous êtes invité à créer un fichier.

1. Dans le Bloc-notes, tapez les lignes suivantes :

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. Dans la barre de menus, choisissez **fichier** > **Enregistrer**.

   Vous avez créé un fichier source C++ qui utilise l’espace de noms de l' [espace de noms](../cppcx/platform-namespace-c-cx.md) de la plateforme Windows Runtime.

1. À l’invite de commandes, entrez **CL/EHSC/ZW basiccx. cpp/Link/SUBSYSTEM : console**. Le compilateur cl.exe compile le code source en un fichier .obj, puis exécute l'éditeur de liens pour générer un programme exécutable nommé basiccx.exe. (L’option de compilateur [/EHsc](reference/eh-exception-handling-model.md) spécifie le modèle de gestion des exceptions C++ et l’indicateur [/Link](reference/link-pass-options-to-linker.md) spécifie une application console.)

1. Pour exécuter le programme basiccx. exe, à l’invite de commandes, entrez **basiccx**.

   Le programme affiche ce texte puis se ferme :

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>Voir aussi

[Projets et systèmes de build](projects-and-build-systems-cpp.md)<br/>
[Options du compilateur MSVC](reference/compiler-options.md)
