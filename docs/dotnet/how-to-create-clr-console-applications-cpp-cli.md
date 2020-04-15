---
title: 'Comment : créer des applications console CLR (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- console applications, templates
- CLR console applications, project template
ms.assetid: e89bce3c-706f-4ae0-8a90-cb1a0f674e70
ms.openlocfilehash: 86e5abe330b0edc514fed74a12188ab73e8bfdd8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368536"
---
# <a name="how-to-create-clr-console-applications-ccli"></a>Comment : créer des applications console CLR (C++/CLI)

Vous pouvez utiliser le modèle Application console pour créer un projet d’application console qui a déjà les références et les fichiers principaux d’un projet.

En général, une application console est compilée en un fichier exécutable autonome, mais elle n’a pas d’interface utilisateur graphique. Un utilisateur exécute l’application console à l’invite de commandes et utilise l’invite de commandes pour émettre des instructions destinées à l’application en cours d’exécution. L’application fournit également des informations de sortie, toujours à l’invite de commandes. L’interactivité directe d’une application console constitue un bon moyen d’apprendre les techniques de programmation sans se soucier de l’implémentation d’une interface utilisateur.

Quand vous utilisez le modèle Application console pour créer un projet, il ajoute automatiquement ces références et ces fichiers :

- Références à ces espaces de noms .NET Framework :

  - <xref:System.AppDomainManager>—Contient des classes fondamentales et des classes de base qui définissent les valeurs couramment utilisées et les types de données de référence, les événements et les gestionnaires d’événements, les interfaces, les attributs et les exceptions de traitement.

  - mscorlib  : DLL de l’assembly qui prend en charge le développement .NET Framework.

- Fichiers sources :

  - Console (fichier .cpp) : le fichier source et le point d’entrée principal entrée dans l’application que vous venez de créer. Il identifie le fichier .dll du projet et l’espace de noms du projet. Fournissez votre propre code dans ce fichier.

  - AssemblyInfo.cpp : contient des attributs, fichiers, ressources, types, informations de contrôle de version, informations de signature, etc., que vous pouvez utiliser pour modifier les métadonnées de l’assembly du projet. Pour plus d’informations, voir [Contenus de l’Assemblée](/dotnet/framework/app-domains/assembly-contents).

  - Stdafx.cpp : utilisé pour générer un fichier d’en-tête précompilé nommé Win32.pch et un fichier de types précompilé nommé StdAfx.obj.

- Fichiers d’en-tête :

  - Stdafx.h : utilisé pour générer un fichier d’en-tête précompilé nommé Win32.pch et un fichier de types précompilé nommé StdAfx.obj.

  - resource.h : un fichier include généré pour app.rc.

- Les fichiers de ressources :

  - app.rc : le fichier de script de ressources d’un programme.

  - app.ico : le fichier icône d’un programme.

- ReadMe.txt : décrit les fichiers du projet.

## <a name="to-create-a-common-language-runtime-clr-console-app-project"></a>Pour créer un projet d’application console CLR (Common Language Runtime)

1. Dans le menu principal, sélectionnez **Fichier**, **Nouveau**, **Projet**.

1. Dans la boîte de dialogue **Nouveau projet** , sous **Modèles installés**, sélectionnez le nœud **Visual C++** , sélectionnez le nœud **CLR** , puis sélectionnez le modèle Application console.

1. Dans la zone **Nom** , entrez un nom unique pour votre application.

   Vous pouvez spécifier d’autres paramètres pour le projet et la solution, mais ils ne sont pas obligatoires.

1. Choisissez le bouton **OK**.

## <a name="see-also"></a>Voir aussi

[Projets CLR](../build/reference/files-created-for-clr-projects.md)
