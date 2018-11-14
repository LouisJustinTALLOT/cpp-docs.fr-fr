---
title: 'Comment : configurer des projets Visual C++ pour cibler les 64 bits, x64 plateformes'
ms.date: 11/04/2016
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
ms.openlocfilehash: c0c734648b084c3f58577cb56984e3ea003a6a8e
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523935"
---
# <a name="how-to-configure-visual-c-projects-to-target-64-bit-x64-platforms"></a>Comment : configurer des projets Visual C++ pour cibler les 64 bits, x64 plateformes

Vous pouvez utiliser les configurations de projet dans l’IDE Visual Studio pour configurer des applications C++ pour cibler les 64 bits, x64 plateformes. Vous pouvez également migrer des paramètres de projet Win32 dans une configuration de projet 64 bits.

### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>Pour configurer des applications C++ pour qu’elles ciblent des plateformes 64 bits

1. Ouvrez le projet C++ à configurer.

1. Ouvrez les pages de propriétés de ce projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../ide/working-with-project-properties.md).

   > [!NOTE]
   > Pour les projets .NET, assurez-vous que le **propriétés de Configuration** nœud ou l’un de ses nœuds enfants, est sélectionné dans le  **\<nom_projet > Pages de propriétés** boîte de dialogue ; sinon, le  **Configuration Manager** bouton reste indisponible.

1. Choisissez le bouton **Gestionnaire de configurations** pour ouvrir la boîte de dialogue **Gestionnaire de configurations** .

1. Dans le **plateforme de Solution Active** liste déroulante, sélectionnez le  **\<nouveau... >** option pour ouvrir la **nouvelle plateforme de Solution** boîte de dialogue.

1. Dans le **tapez ou sélectionnez la nouvelle plateforme** liste déroulante, sélectionnez une version 64 bits cible plateforme.

   > [!NOTE]
   > Dans la boîte de dialogue **Nouvelle plateforme de solution** , vous pouvez utiliser l’option **Copier les paramètres à partir de** pour copier les paramètres de projet existants dans la nouvelle configuration de projet 64 bits.

1. Sélectionnez le bouton **OK** . La plateforme que vous avez sélectionnée à l’étape précédente s’affiche sous **Plateforme de la solution active** dans la boîte de dialogue **Gestionnaire de configurations** .

1. Choisissez le **fermer** situé dans le **Configuration Manager** boîte de dialogue zone, puis choisissez le **OK** situé dans le  **\<NomProjet > Pages de propriétés** boîte de dialogue.

### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>Pour copier des paramètres de projet Win32 dans une configuration de projet 64 bits

- Quand la boîte de dialogue **Nouvelle plateforme de solution** est ouverte pendant que vous configurez un projet pour cibler une plateforme 64 bits, dans la liste déroulante **Copier les paramètres à partir de** , sélectionnez **Win32**. Ces paramètres de projet sont mis à jour automatiquement au niveau du projet :

  - L’option [/MACHINE](../build/reference/machine-specify-target-platform.md) de l’Éditeur de liens prend la valeur **/MACHINE:X64**.

  - L’**Inscription de la sortie** est désactivée. Pour plus d'informations, consultez [Linker Property Pages](../ide/linker-property-pages.md).

  - L’**Environnement cible** prend la valeur **/env x64**. Pour plus d'informations, consultez [MIDL Property Pages: General](../ide/midl-property-pages-general.md).

  - L’option**Validation des paramètres** est effacée et réinitialisée à la valeur par défaut. Pour plus d'informations, consultez [MIDL Property Pages: Advanced](../ide/midl-property-pages-advanced.md).

  - Si vous avez affecté la valeur **/ZI** à l’option **Format des informations de débogage** dans la configuration de projet Win32, elle prend la valeur **/Zi** dans la configuration de projet 64 bits. Pour plus d’informations, consultez l’article [/Z7, /Zi, /ZI (Format des informations de débogage)](../build/reference/z7-zi-zi-debug-information-format.md).

  > [!NOTE]
  > Aucune de ces propriétés de projet n’est modifiée si elle est substituée au niveau du fichier.

## <a name="see-also"></a>Voir aussi

[Applications 64 bits de .NET framework](/dotnet/framework/64-bit-apps)<br/>
[Configurer Visual C++ pour des cibles x64 64 bits](../build/configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Déboguer des applications 64 bits](/visualstudio/debugger/debug-64-bit-applications)