---
description: 'En savoir plus sur : Comment : configurer des projets Visual Studio C++ pour cibler des plateformes x64 64 bits'
title: 'Comment : configurer des projets Visual Studio C++ pour cibler des plateformes x64 64 bits'
ms.date: 11/04/2016
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
ms.openlocfilehash: 717f9db302f4a7bfef12d30830336b22f9fc5169
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156370"
---
# <a name="how-to-configure-visual-studio-c-projects-to-target-64-bit-x64-platforms"></a>Comment : configurer des projets Visual Studio C++ pour cibler des plateformes x64 64 bits

Vous pouvez utiliser les configurations de projet dans l’IDE de Visual Studio pour configurer des applications C++ afin de cibler des plateformes x64 64 bits. Vous pouvez également migrer des paramètres de projet Win32 dans une configuration de projet 64 bits.

### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>Pour configurer des applications C++ pour qu’elles ciblent des plateformes 64 bits

1. Ouvrez le projet C++ à configurer.

1. Ouvrez les pages de propriétés de ce projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](working-with-project-properties.md).

   > [!NOTE]
   > Pour les projets .NET, assurez-vous que le nœud **Propriétés de configuration** , ou l’un de ses nœuds enfants, est sélectionné dans la boîte de dialogue **\<Projectname> pages de propriétés** ; sinon, le bouton **Configuration Manager** reste indisponible.

1. Choisissez le bouton **Gestionnaire de configurations** pour ouvrir la boîte de dialogue **Gestionnaire de configurations** .

1. Dans la liste déroulante plateforme de la **solution active** , sélectionnez l' **\<New...>** option permettant d’ouvrir la boîte de dialogue **nouvelle plateforme de solution** .

1. Dans la liste déroulante **tapez ou sélectionnez la nouvelle plateforme** , sélectionnez une plateforme cible 64 bits.

   > [!NOTE]
   > Dans la boîte de dialogue **Nouvelle plateforme de solution** , vous pouvez utiliser l’option **Copier les paramètres à partir de** pour copier les paramètres de projet existants dans la nouvelle configuration de projet 64 bits.

1. Choisissez le bouton **OK**. La plateforme que vous avez sélectionnée à l’étape précédente s’affiche sous **Plateforme de la solution active** dans la boîte de dialogue **Gestionnaire de configurations** .

1. Choisissez le bouton **Fermer** dans la boîte de dialogue **Configuration Manager** , puis choisissez le bouton **OK** dans la boîte de dialogue pages de **\<Projectname> Propriétés** .

### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>Pour copier des paramètres de projet Win32 dans une configuration de projet 64 bits

- Quand la boîte de dialogue **Nouvelle plateforme de solution** est ouverte pendant que vous configurez un projet pour cibler une plateforme 64 bits, dans la liste déroulante **Copier les paramètres à partir de** , sélectionnez **Win32**. Ces paramètres de projet sont mis à jour automatiquement au niveau du projet :

  - L’option [/MACHINE](reference/machine-specify-target-platform.md) de l’Éditeur de liens prend la valeur **/MACHINE:X64**.

  - L’**Inscription de la sortie** est désactivée. Pour plus d’informations, consultez pages de propriétés de l' [éditeur de liens](reference/linker-property-pages.md).

  - L’**Environnement cible** prend la valeur **/env x64**. Pour plus d’informations, consultez [pages de propriétés MIDL](reference/midl-property-pages.md).

  - L’option **Validation des paramètres** est effacée et réinitialisée à la valeur par défaut. Pour plus d’informations, consultez [pages de propriétés MIDL](reference/midl-property-pages.md).

  - Si vous avez affecté la valeur **/ZI** à l’option **Format des informations de débogage** dans la configuration de projet Win32, elle prend la valeur **/Zi** dans la configuration de projet 64 bits. Pour plus d’informations, consultez l’article [/Z7, /Zi, /ZI (Format des informations de débogage)](reference/z7-zi-zi-debug-information-format.md).

  > [!NOTE]
  > Aucune de ces propriétés de projet n’est modifiée si elle est substituée au niveau du fichier.

## <a name="see-also"></a>Voir aussi

[Configurer des projets C++ pour des cibles x64 64 bits](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Déboguer des applications 64 bits](/visualstudio/debugger/debug-64-bit-applications)
