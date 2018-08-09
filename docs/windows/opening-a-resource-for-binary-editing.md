---
title: Ouverture d’une ressource pour l’édition binaire | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- binary data, editing
- resources [Visual Studio], opening for binary editing
ms.assetid: d3cdb0e4-da66-410d-8e49-b29073ff2929
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 26d1b0ae8923835b0ce06c7312fa185693c6586e
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014505"
---
# <a name="opening-a-resource-for-binary-editing"></a>Ouverture d'une ressource à des fins d'édition binaire
### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Pour ouvrir une ressource de bureau Windows pour l’édition binaire  
  
1.  Dans [Affichage des ressources](../windows/resource-view-window.md), sélectionnez le fichier de ressources que vous souhaitez modifier.  
  
    > [!NOTE]
    >  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Cliquez avec le bouton droit sur la ressource et cliquez sur **Ouvrir au format binaire** dans le menu contextuel.  
  
    > [!NOTE]
    >  Si vous utilisez le [affichage des ressources](../windows/resource-view-window.md) fenêtre pour ouvrir une ressource ayant un format que Visual Studio ne reconnaît pas (comme RCDATA ou une ressource personnalisée), la ressource s’ouvre automatiquement dans le **binaire** éditeur.  
  
### <a name="to-open-a-managed-resource-for-binary-editing"></a>Pour ouvrir une ressource managée pour l’édition binaire  
  
1.  Dans **l’Explorateur de solutions**, sélectionnez le fichier de ressources que vous souhaitez modifier.  
  
2.  Cliquez avec le bouton droit sur la ressource et choisissez **Ouvrir avec** dans le menu contextuel.  
  
3.  Dans la boîte de dialogue **Ouvrir avec** , sélectionnez **Éditeur binaire**.  
  
    > [!NOTE]
    >  Vous pouvez utiliser l’ [éditeur d’images](../windows/image-editor-for-icons.md) et l’ [éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans des projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.  
  
    > [!NOTE]
    >  Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).   
  
 ![Éditeur binaire](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")  
Données binaires pour une boîte de dialogue affichée dans l’éditeur binaire  
  
 Seules certaines valeurs ASCII sont représentées dans l’éditeur binaire (0x20 à 0x7E). Les caractères étendus sont affichés sous forme de points dans la section Valeur ASCII de l’éditeur binaire (volet droit). Les caractères « imprimables » sont les valeurs ASCII comprises entre 32 et 126.  
  
> [!NOTE]
>  Si vous souhaitez utiliser le **binaire** éditeur sur une ressource déjà en cours de modification dans une autre fenêtre d’éditeur, fermez l’autre fenêtre d’éditeur tout d’abord.  
  
## <a name="requirements"></a>Configuration requise  
 Aucun.  
  
## <a name="see-also"></a>Voir aussi  
 [Binary Editor](binary-editor.md)