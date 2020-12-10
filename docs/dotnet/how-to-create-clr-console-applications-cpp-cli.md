---
title: 'Comment : créer des applications console CLR (C++/CLI)'
description: Découvrez comment créer des projets d’application console CLR pour utiliser C++/CLI dans Visual Studio.
ms.date: 12/08/2020
helpviewer_keywords:
- console applications, templates
- CLR console applications, project template
ms.openlocfilehash: ef74ca4cc31884543ff18d63d981504f36d1838e
ms.sourcegitcommit: 754df5278f795f661d4eeb0d4cacc908aa630159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96933220"
---
# <a name="how-to-create-clr-console-applications-ccli"></a>Comment : créer des applications console CLR (C++/CLI)

::: moniker range="msvc-140"

Vous pouvez utiliser le modèle  **application console CLR** dans la boîte de dialogue **nouveau projet** pour créer un projet d’application console qui a déjà des références et des fichiers de projet essentiels.

::: moniker-end
::: moniker range="msvc-150"

Vous pouvez utiliser le modèle **application console CLR** dans la boîte de dialogue **nouveau projet** pour créer un projet d’application console qui a déjà des références et des fichiers de projet essentiels.

La prise en charge de c++/CLI n’est pas installée par défaut lorsque vous installez une charge de travail Visual Studio C++. Si vous ne voyez pas un en-tête CLR sous Visual C++ dans la boîte de dialogue **nouveau projet** , vous devrez peut-être installer la prise en charge de C++/CLI. Pour plus d’informations, consultez [programmation .net avec C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

::: moniker-end
::: moniker range="msvc-160"

Vous pouvez utiliser le modèle **application console CLR (.NET Framework)** dans la boîte de dialogue **créer un nouveau projet** pour créer un projet d’application console qui a déjà des références et des fichiers de projet essentiels.

La prise en charge de c++/CLI n’est pas installée par défaut lorsque vous installez une charge de travail Visual Studio C++. Si les modèles de projet CLR ne s’affichent pas dans la boîte de dialogue  **créer un nouveau projet** , vous devrez peut-être installer la prise en charge de C++/CLI. Pour plus d’informations, consultez [programmation .net avec C++/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

::: moniker-end

En général, une application console est compilée en un fichier exécutable autonome, mais elle n’a pas d’interface utilisateur graphique. Les utilisateurs exécutent l’application console à partir d’une invite de commandes. Ils peuvent utiliser la ligne de commande pour émettre des instructions pour l’application en cours d’exécution. L’application fournit des informations de sortie sous forme de texte dans la fenêtre de commande. Le retour immédiat d’une application console en fait un excellent moyen d’apprendre la programmation. Vous n’avez pas besoin de vous soucier de l’implémentation d’une interface utilisateur graphique.

::: moniker range="msvc-140"

Lorsque vous utilisez le modèle d’application console CLR pour créer un projet, il ajoute automatiquement ces références et ces fichiers :

- Références à ces espaces de noms .NET Framework :

  - <xref:System>, <xref:System.Data> , <xref:System.Xml> : Ces références contiennent les classes fondamentales qui définissent des types, des événements, des interfaces, des attributs et des exceptions couramment utilisés.

  - *`mscorlib.dll`*: DLL d’assembly qui prend en charge le développement de .NET Framework.

- Fichiers sources :

  - *`ConsoleApplicationName.cpp`*: Le fichier source principal et le point d’entrée dans l’application. Ce fichier porte le nom de base que vous avez spécifié pour votre projet. Il identifie le fichier DLL du projet et l’espace de noms du projet. Fournissez votre propre code dans ce fichier.

  - *`AssemblyInfo.cpp`*: Contient des attributs et des paramètres que vous pouvez utiliser pour modifier les métadonnées de l’assembly du projet. Pour plus d’informations, consultez contenu de l' [assembly](/dotnet/framework/app-domains/assembly-contents).

  - *`stdafx.cpp`*: Utilisé pour générer un fichier d’en-tête précompilé nommé *`ConsoleApplicationName.pch`* et un fichier de types précompilé nommé *`stdafx.obj`* .

- Fichiers d’en-tête :

  - *`stdafx.h`*: Utilisé pour générer un fichier d’en-tête précompilé nommé *`ConsoleApplicationName.pch`* et un fichier de types précompilé nommé *`stdafx.obj`* .

  - *`resource.h`*: Un fichier Include généré pour *`app.rc`* .

- Les fichiers de ressources :

  - *`app.rc`*: Fichier de script de ressources d’un programme.

  - *`app.ico`*: Le fichier icône d’un programme.

- *`ReadMe.txt`*: Décrit les fichiers du projet.

::: moniker-end
::: moniker range=">=msvc-150"

Quand vous utilisez le modèle d’application console CLR pour créer un projet, il ajoute automatiquement ces références et ces fichiers :

- Références à ces espaces de noms .NET Framework :

  - <xref:System>, <xref:System.Data> , <xref:System.Xml> : Ces références contiennent les classes fondamentales qui définissent des types, des événements, des interfaces, des attributs et des exceptions couramment utilisés.

  - *`mscorlib.dll`*: DLL d’assembly qui prend en charge le développement de .NET Framework.

- Fichiers sources :

  - *`ConsoleApplicationName.cpp`*: Le fichier source principal et le point d’entrée dans l’application. Ce fichier porte le nom de base que vous avez spécifié pour votre projet. Il identifie le fichier DLL du projet et l’espace de noms du projet. Fournissez votre propre code dans ce fichier.

  - *`AssemblyInfo.cpp`*: Contient des attributs et des paramètres que vous pouvez utiliser pour modifier les métadonnées de l’assembly du projet. Pour plus d’informations, consultez contenu de l' [assembly](/dotnet/framework/app-domains/assembly-contents).

  - *`pch.cpp`*: Utilisé pour générer un fichier d’en-tête précompilé nommé *`ConsoleApplicationName.pch`* et un fichier de types précompilé nommé *`pch.obj`* .

- Fichiers d’en-tête :

  - *`pch.h`*: Utilisé pour générer un fichier d’en-tête précompilé nommé *`ConsoleApplicationName.pch`* et un fichier de types précompilé nommé *`pch.obj`* .

  - *`Resource.h`*: Un fichier Include généré pour *`app.rc`* .

- Les fichiers de ressources :

  - *`app.rc`*: Fichier de script de ressources d’un programme.

  - *`app.ico`*: Le fichier icône d’un programme.

::: moniker-end

## <a name="to-create-a-clr-console-app-project"></a>Pour créer un projet d’application console CLR

::: moniker range="msvc-140"

1. Dans la barre de menus, choisissez **fichier** > **nouveau** > **projet**.

1. Dans la boîte de dialogue **nouveau projet** , sélectionnez **Installed** le > nœud **modèles** installés > **Visual C++** > **CLR** , puis sélectionnez le modèle **application console CLR** .

1. Dans la zone **Nom** , entrez un nom unique pour votre application.

   Vous pouvez spécifier d’autres paramètres de projet et de solution, mais ils ne sont pas requis.

1. Choisissez le bouton **OK** pour générer le projet et les fichiers sources.

::: moniker-end
::: moniker range="msvc-150"

1. Dans la barre de menus, choisissez **fichier** > **nouveau** > **projet**.

1. Dans la boîte de dialogue **nouveau projet** , sélectionnez le nœud **installé** > **Visual C++** > **CLR** , puis sélectionnez le modèle **application console CLR** .

1. Dans la zone **Nom** , entrez un nom unique pour votre application.

   Vous pouvez spécifier d’autres paramètres de projet et de solution, mais ils ne sont pas requis.

1. Choisissez le bouton **OK** pour générer le projet et les fichiers sources.

::: moniker-end
::: moniker range="msvc-160"

1. Dans la barre de menus, choisissez **fichier** > **nouveau** > **projet**.

1. Dans la boîte de dialogue **créer un nouveau projet** , entrez « console CLR » dans la zone de recherche. Sélectionnez le modèle **application console CLR (.NET Framework)** , puis choisissez **suivant**.

1. Dans la zone **Nom** , entrez un nom unique pour votre application.

   Vous pouvez spécifier d’autres paramètres de projet et de solution, mais ils ne sont pas requis.

1. Cliquez sur le bouton **créer** pour générer le projet et les fichiers sources.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Projets CLR](../build/reference/files-created-for-clr-projects.md)
