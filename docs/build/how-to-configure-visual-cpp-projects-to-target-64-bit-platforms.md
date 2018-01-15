---
title: "Comment : configurer des projets Visual C++ pour cibler 64 bits, x64 plateformes | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7e651d28af3bd8635691d6a54d6c4cca8eb8c160
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-configure-visual-c-projects-to-target-64-bit-x64-platforms"></a>Comment : configurer des projets Visual C++ pour cibler 64 bits, x64 plateformes

Vous pouvez utiliser les configurations de projet dans l’IDE de Visual Studio pour configurer des applications C++ pour cibler 64 bits, x64 plateformes. Vous pouvez également migrer des paramètres de projet Win32 dans une configuration de projet 64 bits.  
  
### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>Pour configurer des applications C++ pour qu’elles ciblent des plateformes 64 bits  
  
1.  Ouvrez le projet C++ à configurer.  
  
2.  Ouvrez les pages de propriétés de ce projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../ide/working-with-project-properties.md).  
  
    > [!NOTE]
    >  Pour les projets .NET, assurez-vous que le **propriétés de Configuration** nœud ou l’un de ses nœuds enfants, est sélectionné dans le  **\<Projectname > Pages de propriétés** boîte de dialogue ; sinon, le  **Gestionnaire de configuration** bouton n’est pas disponible.  
  
3.  Choisissez le bouton **Gestionnaire de configurations** pour ouvrir la boîte de dialogue **Gestionnaire de configurations** .  
  
4.  Dans le **plateforme de Solution Active** la liste déroulante, sélectionnez le  **\<nouveau... >** option pour ouvrir la **nouvelle plateforme de Solution** boîte de dialogue.  
  
5.  Dans le **tapez ou sélectionnez la nouvelle plateforme** liste déroulante, sélectionnez une version 64 bits de plateforme de cible.  
  
    > [!NOTE]
    >  Dans la boîte de dialogue **Nouvelle plateforme de solution** , vous pouvez utiliser l’option **Copier les paramètres à partir de** pour copier les paramètres de projet existants dans la nouvelle configuration de projet 64 bits.  
  
6.  Sélectionnez le bouton **OK** . La plateforme que vous avez sélectionnée à l’étape précédente s’affiche sous **Plateforme de la solution active** dans la boîte de dialogue **Gestionnaire de configurations** .  
  
7.  Choisissez le **fermer** situé dans le **Configuration Manager** boîte de dialogue zone, puis choisissez le **OK** situé dans le  **\<NomProjet > Pages de propriétés** boîte de dialogue.  
  
### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>Pour copier des paramètres de projet Win32 dans une configuration de projet 64 bits  
  
-   Quand la boîte de dialogue **Nouvelle plateforme de solution** est ouverte pendant que vous configurez un projet pour cibler une plateforme 64 bits, dans la liste déroulante **Copier les paramètres à partir de** , sélectionnez **Win32**. Ces paramètres de projet sont mis à jour automatiquement au niveau du projet :  
  
    -   L’option [/MACHINE](../build/reference/machine-specify-target-platform.md) de l’Éditeur de liens prend la valeur **/MACHINE:X64**.  
  
    -   L’**Inscription de la sortie** est désactivée. Pour plus d'informations, consultez [Linker Property Pages](../ide/linker-property-pages.md).  
  
    -   L’**Environnement cible** prend la valeur **/env x64**. Pour plus d'informations, consultez [MIDL Property Pages: General](../ide/midl-property-pages-general.md).  
  
    -   L’option**Validation des paramètres** est effacée et réinitialisée à la valeur par défaut. Pour plus d'informations, consultez [MIDL Property Pages: Advanced](../ide/midl-property-pages-advanced.md).  
  
    -   Si vous avez affecté la valeur **/ZI** à l’option **Format des informations de débogage** dans la configuration de projet Win32, elle prend la valeur **/Zi** dans la configuration de projet 64 bits. Pour plus d’informations, consultez l’article [/Z7, /Zi, /ZI (Format des informations de débogage)](../build/reference/z7-zi-zi-debug-information-format.md).  
  
    > [!NOTE]
    >  Aucune de ces propriétés de projet n’est modifiée si elle est substituée au niveau du fichier.  
  
## <a name="see-also"></a>Voir aussi  

[Applications 64 bits de .NET framework](/dotnet/framework/64-bit-apps)   
[Configurer Visual C++ pour 64 bits, x64 cibles](../build/configuring-programs-for-64-bit-visual-cpp.md)   
[Déboguer des applications 64 bits](/visualstudio/debugger/debug-64-bit-applications)