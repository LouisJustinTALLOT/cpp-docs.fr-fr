---
title: 'Comment : créer des Applications Console CLR (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- console applications, templates
- CLR console applications, project template
ms.assetid: e89bce3c-706f-4ae0-8a90-cb1a0f674e70
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3257d690ac949edff7958615656db052c3468c01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132568"
---
# <a name="how-to-create-clr-console-applications-ccli"></a>Comment : créer des applications console CLR (C++/CLI)
Vous pouvez utiliser le modèle Application console pour créer un projet d’application console qui a déjà les références et les fichiers principaux d’un projet.  
  
 En général, une application console est compilée en un fichier exécutable autonome, mais elle n’a pas d’interface utilisateur graphique. Un utilisateur exécute l’application console à l’invite de commandes et utilise l’invite de commandes pour émettre des instructions destinées à l’application en cours d’exécution. L’application fournit également des informations de sortie, toujours à l’invite de commandes. L’interactivité directe d’une application console constitue un bon moyen d’apprendre les techniques de programmation sans se soucier de l’implémentation d’une interface utilisateur.  
  
 Quand vous utilisez le modèle Application console pour créer un projet, il ajoute automatiquement ces références et ces fichiers :  
  
-   Références à ces espaces de noms .NET Framework :  
  
    -   [System](https://msdn.microsoft.com/en-us/library/system.appdomainmanager.appdomainmanager.aspx): contient des classes fondamentales et des classes de base qui définissent des valeurs et des types de données de référence, des événements et des gestionnaires d’événements, des interfaces, des attributs et des exceptions de traitement couramment utilisés.  
  
    -   mscorlib  : DLL de l’assembly qui prend en charge le développement .NET Framework.  
  
-   Fichiers sources :  
  
    -   Console (fichier .cpp) : le fichier source et le point d’entrée principal entrée dans l’application que vous venez de créer. Il identifie le fichier .dll du projet et l’espace de noms du projet. Fournissez votre propre code dans ce fichier.  
  
    -   AssemblyInfo.cpp : contient des attributs, fichiers, ressources, types, informations de contrôle de version, informations de signature, etc., que vous pouvez utiliser pour modifier les métadonnées de l’assembly du projet. Pour plus d’informations, consultez [contenu d’un Assembly](/dotnet/framework/app-domains/assembly-contents).  
  
    -   Stdafx.cpp : utilisé pour générer un fichier d’en-tête précompilé nommé Win32.pch et un fichier de types précompilé nommé StdAfx.obj.  
  
-   Fichiers d’en-tête :  
  
    -   Stdafx.h : utilisé pour générer un fichier d’en-tête précompilé nommé Win32.pch et un fichier de types précompilé nommé StdAfx.obj.  
  
    -   resource.h : un fichier include généré pour app.rc.  
  
-   Fichiers de ressources :  
  
    -   app.rc : le fichier de script de ressources d’un programme.  
  
    -   app.ico : le fichier icône d’un programme.  
  
-   ReadMe.txt : décrit les fichiers du projet.  
  
## <a name="to-create-a-common-language-runtime-clr-console-app-project"></a>Pour créer un projet d’application console CLR (Common Language Runtime)  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet** , sous **Modèles installés**, sélectionnez le nœud **Visual C++** , sélectionnez le nœud **CLR** , puis sélectionnez le modèle Application console.  
  
3.  Dans la zone **Nom** , entrez un nom unique pour votre application.  
  
     Vous pouvez spécifier d’autres paramètres pour le projet et la solution, mais ils ne sont pas obligatoires.  
  
4.  Sélectionnez le bouton **OK** .  
  
## <a name="see-also"></a>Voir aussi  
 [Projets CLR](../ide/files-created-for-clr-projects.md)   


