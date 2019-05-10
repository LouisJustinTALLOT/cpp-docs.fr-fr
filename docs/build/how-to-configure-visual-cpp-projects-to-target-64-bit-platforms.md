---
title: 'Procédure : Configurer Visual Studio C++ des projets à une cible 64 bits, x64 plateformes'
ms.date: 11/04/2016
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
ms.openlocfilehash: a063c2f333a755ab86a4f91c9d14d0c65a6d1414
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446396"
---
# <a name="how-to-configure-visual-studio-c-projects-to-target-64-bit-x64-platforms"></a>Procédure : Configurer Visual Studio C++ des projets à une cible 64 bits, x64 plateformes

Vous pouvez utiliser les configurations de projet dans l’IDE Visual Studio pour configurer des applications C++ pour cibler les 64 bits, x64 plateformes. Vous pouvez également migrer des paramètres de projet Win32 dans une configuration de projet 64 bits.

### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>Pour configurer des applications C++ pour qu’elles ciblent des plateformes 64 bits

1. Ouvrez le projet C++ à configurer.

1. Ouvrez les pages de propriétés de ce projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](working-with-project-properties.md).

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

  - L’option [/MACHINE](reference/machine-specify-target-platform.md) de l’Éditeur de liens prend la valeur **/MACHINE:X64**.

  - L’**Inscription de la sortie** est désactivée. Pour plus d'informations, consultez [Linker Property Pages](reference/linker-property-pages.md).

  - L’**Environnement cible** prend la valeur **/env x64**. Pour plus d’informations, consultez [Pages de propriétés MIDL : Général](reference/midl-property-pages-general.md).

  - L’option**Validation des paramètres** est effacée et réinitialisée à la valeur par défaut. Pour plus d’informations, consultez [Pages de propriétés MIDL : Advanced](reference/midl-property-pages-advanced.md).

  - Si vous avez affecté la valeur **/ZI** à l’option **Format des informations de débogage** dans la configuration de projet Win32, elle prend la valeur **/Zi** dans la configuration de projet 64 bits. Pour plus d’informations, consultez l’article [/Z7, /Zi, /ZI (Format des informations de débogage)](reference/z7-zi-zi-debug-information-format.md).

  > [!NOTE]
  > Aucune de ces propriétés de projet n’est modifiée si elle est substituée au niveau du fichier.

## <a name="see-also"></a>Voir aussi

[Configurer des projets C++ pour x64 64 64 bits, cibles](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Déboguer des applications 64 bits](/visualstudio/debugger/debug-64-bit-applications)
