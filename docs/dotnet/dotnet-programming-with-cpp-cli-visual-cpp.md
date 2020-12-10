---
title: Programmation .NET avec C++/CLI
description: Découvrez comment utiliser C++/CLI pour créer des applications et des composants .NET dans Visual Studio.
ms.date: 12/08/2020
helpviewer_keywords:
- programming [C++], .NET programming
- .NET Framework [C++]
- .NET applications [C++]
- Visual C++, .NET programming
ms.openlocfilehash: 80a9743016976e307158608134155dc7272d44a8
ms.sourcegitcommit: 754df5278f795f661d4eeb0d4cacc908aa630159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96933181"
---
# <a name="net-programming-with-ccli"></a>Programmation .NET avec C++/CLI

::: moniker range="msvc-140"

Par défaut, les projets CLR créés avec Visual Studio 2015 ciblent .NET Framework 4.5.2. Vous pouvez cibler .NET Framework 4,6 quand vous créez un nouveau projet. Dans la boîte de dialogue **nouveau projet** , modifiez la version cible du .NET Framework dans la liste déroulante en haut au milieu de la boîte de dialogue. Pour modifier le Framework cible d’un projet existant, fermez le projet, modifiez le fichier projet ( *`.vcxproj`* ) et remplacez la valeur de la version cible du .NET Framework par 4,6. Les modifications prennent effet la prochaine fois que vous ouvrez le projet.

::: moniker-end
::: moniker range="msvc-150"

Dans Visual Studio 2017, le .NET Framework cible par défaut est 4.6.1. Le sélecteur de version de l’infrastructure se trouve au bas de la boîte de dialogue **nouveau projet** .

## <a name="install-ccli-support-in-visual-studio-2017"></a>Installer la prise en charge de C++/CLI dans Visual Studio 2017

C++/CLI lui-même n’est pas installé par défaut lorsque vous installez une charge de travail Visual Studio C++. Pour installer le composant après l’installation de Visual Studio, ouvrez le Visual Studio Installer. Choisissez le bouton **modifier** en regard de votre version installée de Visual Studio. Sélectionnez l’onglet **composants installés** . Faites défiler jusqu’à la section **compilateurs, outils de génération et runtimes** , puis sélectionnez **prise en charge de C++/CLI**. Choisissez **modifier** pour mettre à jour Visual Studio.

::: moniker-end
::: moniker range="msvc-160"

Dans Visual Studio 2019, le Framework cible par défaut pour les projets .NET Core est 5,0. Pour les projets .NET Frameworks, la valeur par défaut est 4.7.2. Le sélecteur de version .NET Framework se trouve dans la page **configurer votre nouveau projet** de la boîte de dialogue **créer un nouveau projet** .
## <a name="install-ccli-support-in-visual-studio-2019"></a>Installer la prise en charge de C++/CLI dans Visual Studio 2019

C++/CLI lui-même n’est pas installé par défaut lorsque vous installez une charge de travail Visual Studio C++. Pour installer le composant après l’installation de Visual Studio, ouvrez le Visual Studio Installer. Choisissez le bouton **modifier** en regard de votre version installée de Visual Studio. Sélectionnez l’onglet **composants installés** . Faites défiler jusqu’à la section **compilateurs, outils de génération et runtimes** , puis sélectionnez la dernière **prise en charge de C++/CLI pour le composant outils de génération V142** . Choisissez **modifier** pour mettre à jour Visual Studio.

::: moniker-end

## <a name="in-this-section"></a>Dans cette section

[Tâches C++/CLI](../dotnet/cpp-cli-tasks.md)

[Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)

[Code pur et vérifiable (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)

[Expressions régulières (C++/CLI)](../dotnet/regular-expressions-cpp-cli.md)

[Gestion de fichiers et e/s (C++/CLI)](../dotnet/file-handling-and-i-o-cpp-cli.md)

[Opérations graphiques (C++/CLI)](../dotnet/graphics-operations-cpp-cli.md)

[Opérations Windows (C++/CLI)](../dotnet/windows-operations-cpp-cli.md)

[Accès aux données à l’aide de ADO.NET (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)

[Interopérabilité avec d’autres langages .NET (C++/CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)

[Sérialisation (C++/CLI)](../dotnet/serialization-cpp-cli.md)

[Types managés (C++/CLI)](../dotnet/managed-types-cpp-cli.md)

[Réflexion (C++/CLI)](../dotnet/reflection-cpp-cli.md)

[Assemblys de nom fort (signature d’assembly) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)

[Debug, classe (C++/CLI)](../dotnet/debug-class-cpp-cli.md)

[Informations de référence sur la bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)

[Bibliothèque de prise en charge C++](../dotnet/cpp-support-library.md)

[Exceptions dans C++/CLI](../dotnet/exceptions-in-cpp-cli.md)

[Boxing (C++/CLI)](../dotnet/boxing-cpp-cli.md)

## <a name="see-also"></a>Voir aussi

[Interopérabilité native et .NET](../dotnet/native-and-dotnet-interoperability.md)
