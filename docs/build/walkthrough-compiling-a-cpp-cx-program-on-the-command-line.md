---
title: 'Procédure pas à pas : Compilation de C++ / c++ / programme CX sur la ligne de commande'
ms.date: 04/23/2019
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: cbf5a48de3c029e36fc6daabe2b3f0db55dc173c
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877166"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>Procédure pas à pas : Compilation de C++ / c++ / programme CX sur la ligne de commande

> [!NOTE] 
> Pour les nouvelles applications UWP et des composants, nous vous recommandons d’utiliser [ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), une standard C ++ 17 projection de langage pour Windows Runtime APIs. C++ / c++ / WinRT est disponible dans le SDK Windows 10 à partir de la version 1803 qui interviennent. C++ / c++ / WinRT est entièrement implémentée dans les fichiers d’en-tête et est conçu pour vous permettre d’accès idéal à l’API Windows moderne.

Microsoft C++ prend en charge du compilateur (MSVC) C++ extensions du composant (C++/CX), qui a des types et opérateurs supplémentaires pour cibler le modèle de programmation Windows Runtime. Vous pouvez utiliser C++/CX pour créer des applications pour la plateforme universelle Windows (UWP) et le bureau de Windows. Pour plus d’informations, consultez [une visite guidée de c++ c++ / CX](https://msdn.microsoft.com/magazine/dn166929.aspx) et [Extensions du composant pour les plateformes Runtime](../extensions/component-extensions-for-runtime-platforms.md).

Dans cette procédure pas à pas, vous allez créer un programme C++/CX élémentaire à l'aide d'un éditeur de texte, puis le compiler sur la ligne de commande. (Vous pouvez utiliser votre propre programme C++/CX au lieu de taper le programme illustré, ou vous pouvez utiliser un exemple de code C++/CX tiré d'un autre article d'aide. Cette technique est utile pour générer et tester des petits modules qui ont des éléments d’interface utilisateur).

> [!NOTE]
> Vous pouvez également utiliser l'IDE de Visual Studio pour compiler les programmes C++/CX. Étant donné que l’IDE inclut la conception, le débogage, l’émulation et la prise en charge de déploiement qui n’est pas disponible sur la ligne de commande, nous vous recommandons d’utiliser l’IDE pour créer des applications de plateforme universelle Windows (UWP). Pour plus d’informations, consultez [créer une application UWP en C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

## <a name="prerequisites"></a>Prérequis

Vous comprenez les notions de base du langage C++.

## <a name="compiling-a-ccx-program"></a>Compilation d'un programme C++/CX

Pour activer la compilation pour C / c++ / CX, vous devez utiliser le [/ZW](reference/zw-windows-runtime-compilation.md) option du compilateur. Le compilateur MSVC génère un fichier .exe qui cible le Runtime de Windows et des liens vers les bibliothèques requises.

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>Pour compiler une application C++/CX sur la ligne de commande

1. Ouvrir un **invite de commandes développeur** fenêtre. (Sur le **Démarrer** fenêtre, ouvrez **applications**. Ouvrez le **Visual Studio Tools** dossier sous votre version de Visual Studio, puis choisissez le **invite de commandes développeur** contextuel.) Pour plus d’informations sur la façon d’ouvrir une fenêtre d’invite de commandes développeur, consultez [utiliser l’ensemble d’outils MSVC à partir de la ligne de commande](building-on-the-command-line.md).

   Des informations d'identification d'administrateur peuvent être nécessaires pour compiler le code, selon la configuration et le système d'exploitation de l'ordinateur. Pour exécuter la fenêtre d’invite de commandes en tant qu’administrateur, ouvrez le menu contextuel pour **invite de commandes développeur** , puis **exécuter en tant qu’administrateur**.

1. À l’invite de commandes, entrez **notepad basiccx.cpp**.

   Choisissez **Oui** lorsque vous êtes invité à créer un fichier.

1. Dans le Bloc-notes, tapez les lignes suivantes :

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. Dans la barre de menus, choisissez **fichier** > **enregistrer**.

   Vous avez créé un C++ fichier source qui utilise le Runtime Windows [espace de noms Platform](../cppcx/platform-namespace-c-cx.md) espace de noms.

1. À l’invite de commandes, entrez **cl /EHsc /ZW basiccx.cpp /link/SUBSYSTEM : console**. Le compilateur cl.exe compile le code source en un fichier .obj, puis exécute l'éditeur de liens pour générer un programme exécutable nommé basiccx.exe. (Le [/EHsc](reference/eh-exception-handling-model.md) option du compilateur spécifie le modèle de gestion des exceptions C++ et le [/link,](reference/link-pass-options-to-linker.md) indicateur spécifie une application console.)

1. Pour exécuter le programme basiccx.exe, à l’invite de commandes, entrez **basiccx**.

   Le programme affiche ce texte puis se ferme :

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>Voir aussi

[Projets et systèmes de build](projects-and-build-systems-cpp.md)<br/>
[Options du compilateur MSVC](reference/compiler-options.md)
