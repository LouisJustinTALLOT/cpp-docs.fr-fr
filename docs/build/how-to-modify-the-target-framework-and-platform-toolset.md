---
title: "comment&#160;: modifier la version cible de .Net Framework et l&#39;ensemble d&#39;outils de la plateforme | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "msbuild.cpp.howto.modifytargetframeworkandplatformtoolset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MSBuild (C++), comment : modifier la version cible de .Net Framework et l'ensemble d'outils de plateforme"
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
caps.latest.revision: 32
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 32
---
# comment&#160;: modifier la version cible de .Net Framework et l&#39;ensemble d&#39;outils de la plateforme
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Vous pouvez modifier les paramètres de projet [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] pour cibler d'autres versions du .NET Framework et utiliser d'autres ensembles d'outils de plateforme. Par défaut, le système de projet utilise la version du. Net Framework et la version de l'ensemble d'outils qui correspondent à la version de Visual Studio que vous utilisez pour créer le projet. Vous pouvez changer l'ensemble d'outils de plateforme cible en modifiant les propriétés du projet. Vous pouvez changer la version cible du .Net Framework en modifiant le fichier projet \(.vcxproj\). Vous n'avez pas besoin de conserver une base de code distincte pour chaque cible de compilation.  
  
> [!IMPORTANT]
>  Certaines éditions ne prennent pas en charge les versions cibles du. Net Framework modifiées ou les ensembles d'outils de plateforme. Pour plus d’informations sur la compatibilité, consultez [Portage, migration et mise à niveau des projets Visual Studio](../Topic/Porting,%20Migrating,%20and%20Upgrading%20Visual%20Studio%20Projects.md).  
  
 Lorsque vous changez le Framework cible, remplacez également l'ensemble d'outils de plateforme par une version qui prend en charge ce Framework. Par exemple, pour cibler le .NET Framework 4.5, vous devez utiliser un ensemble d’outils de plateforme compatible, comme Visual Studio 2015 \(v140\), Visual Studio 2013 \(v120\) ou Visual Studio 2012 \(v110\). Vous pouvez utiliser l'ensemble d'outils de plateforme **Windows7.1SDK** pour cibler les .NET Framework 2.0, 3.0, 3.5 et 4 et les plateformes x86, Itanium et x64.  
  
> [!NOTE]
>  Pour modifier l'ensemble d'outils de la plateforme cible, la version associée de Visual Studio ou le Kit de développement logiciel \(SDK\) Windows Platform doit être installé sur votre ordinateur. Par exemple, pour cibler la plateforme Itanium avec l’ensemble d’outils de plateforme **Kit de développement logiciel \(SDK\) Windows 7.1**, vous devez avoir installé [Microsoft Windows SDK pour Windows 7 et .NET Framework 4 SP1](http://www.microsoft.com/download/details.aspx?id=8279). Vous pouvez cependant utiliser une autre version compatible de Visual Studio pour effectuer votre travail de développement, à condition de cibler la version du .NET Framework et l’ensemble d’outils de plateforme corrects.  
  
 Vous pouvez étendre davantage la plateforme cible en créant un ensemble d'outils de plateforme personnalisé. Pour plus d’informations, consultez [Multiciblage natif C\+\+](http://go.microsoft.com/fwlink/?LinkId=196619) sur le blog de Visual C\+\+.  
  
### Pour changer la version cible du .Net Framework  
  
1.  Dans Visual Studio, dans l’**Explorateur de solutions**, sélectionnez votre projet. Sur la barre de menus, ouvrez le menu **Projet** et choisissez **Décharger le projet**. Le fichier de projet \(.vcxproj\) de votre projet est alors déchargé.  
  
    > [!NOTE]
    >  Le projet C\+\+ ne peut pas être chargé pendant que le fichier projet est en cours de modification dans Visual Studio. Toutefois, vous pouvez utiliser un autre éditeur tel que le Bloc\-notes pour modifier le fichier projet lorsque le projet est chargé dans Visual Studio. Visual Studio détecte que le fichier projet a changé et vous invite à recharger le projet.  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Ouvrir**, **Fichier**. Dans la boîte de dialogue **Ouvrir un fichier**, accédez à votre dossier de projet, puis ouvrez le fichier projet \(.vcxproj\).  
  
3.  Dans le fichier projet, recherchez l'entrée correspondant à la version du Framework cible. Par exemple, si votre projet est destiné à utiliser .NET Framework 4.5, recherchez `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` dans l'élément `<PropertyGroup Label="Globals">` de l'élément `<Project>`. Si l'élément `<TargetFrameworkVersion>` n'est pas présent, votre projet n'utilise pas le .NET Framework et aucune modification n'est requise.  
  
4.  Remplacez la valeur par la version du .NET Framework de votre choix, comme v3.5 ou v4.  
  
5.  Enregistrez les modifications et fermez l'éditeur.  
  
6.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel de votre projet et choisissez **Recharger le projet**.  
  
7.  Pour vérifier la modification, dans l’**Explorateur de solutions**, cliquez avec le bouton droit pour ouvrir le menu contextuel pour votre projet \(et non pas pour votre solution\), puis choisissez **Propriétés** pour ouvrir la boîte de dialogue **Pages de propriétés** de votre projet. Dans le volet gauche de la boîte de dialogue, développez **Propriétés de configuration**, puis sélectionnez **Général**. Vérifiez que **Version du .NET Framework cible** indique la nouvelle version du .NET Framework.  
  
### Pour modifier l'ensemble d'outils du projet  
  
1.  Dans Visual Studio, dans l'**Explorateur de solutions**, ouvrez le menu contextuel pour votre projet \(et non pas pour votre solution\), puis choisissez **Propriétés** pour ouvrir la boîte de dialogue **Pages de propriétés** de votre projet.  
  
2.  Dans la boîte de dialogue **Pages de propriétés**, ouvrez la liste déroulante **Configuration** puis sélectionnez **Toutes les configurations**.  
  
3.  Dans le volet gauche de la boîte de dialogue, développez **Propriétés de configuration**, puis sélectionnez **Général**.  
  
4.  Dans le volet droit, sélectionnez **Ensemble d'outils de plateforme**, puis sélectionnez l'ensemble d'outils de votre choix dans la liste déroulante. Par exemple, si vous avez installé l'ensemble d'outils [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)], sélectionnez **Visual Studio 2010 \(v100\)** pour l'utiliser pour votre projet.  
  
5.  Sélectionnez le bouton **OK**.  
  
## Voir aussi  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)