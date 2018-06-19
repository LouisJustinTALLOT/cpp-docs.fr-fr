---
title: Ouverture d’une ressource pour l’édition binaire | Documents Microsoft
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
ms.openlocfilehash: c09cd825a5974422eaf757419f4ce890f5123100
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878484"
---
# <a name="opening-a-resource-for-binary-editing"></a>Ouverture d'une ressource à des fins d'édition binaire
### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Pour ouvrir une ressource de bureau Windows pour l’édition binaire  
  
1.  Dans [Affichage des ressources](../windows/resource-view-window.md), sélectionnez le fichier de ressources que vous souhaitez modifier.  
  
    > [!NOTE]
    >  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Cliquez avec le bouton droit sur la ressource et cliquez sur **Ouvrir au format binaire** dans le menu contextuel.  
  
    > [!NOTE]
    >  Si vous utilisez la fenêtre [Affichage des ressources](../windows/resource-view-window.md) pour ouvrir une ressource ayant un format que Visual Studio ne reconnaît pas (comme RCDATA ou une ressource personnalisée), la ressource s’ouvre automatiquement dans l’éditeur binaire.  
  
### <a name="to-open-a-managed-resource-for-binary-editing"></a>Pour ouvrir une ressource managée pour l’édition binaire  
  
1.  Dans l’Explorateur de solutions, sélectionnez le fichier de ressources que vous souhaitez modifier.  
  
2.  Cliquez avec le bouton droit sur la ressource et choisissez **Ouvrir avec** dans le menu contextuel.  
  
3.  Dans la boîte de dialogue **Ouvrir avec** , sélectionnez **Éditeur binaire**.  
  
    > [!NOTE]
    >  Vous pouvez utiliser l’ [éditeur d’images](../windows/image-editor-for-icons.md) et l’ [éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans des projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.  
  
    > [!NOTE]
    >  Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).   
  
 ![Éditeur binaire](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")  
Données binaires pour une boîte de dialogue affichée dans l’éditeur binaire  
  
 Seules certaines valeurs ASCII sont représentées dans l’éditeur binaire (0x20 à 0x7E). Les caractères étendus sont affichés sous forme de points dans la section Valeur ASCII de l’éditeur binaire (volet droit). Les caractères « imprimables » sont les valeurs ASCII comprises entre 32 et 126.  
  
> [!NOTE]
>  Si vous souhaitez utiliser l’éditeur binaire sur une ressource déjà en cours de modification dans une autre fenêtre d’éditeur, fermez d’abord l’autre fenêtre d’éditeur.  
  
 **Spécifications**  
  
 Aucun  
  
## <a name="see-also"></a>Voir aussi  
 [Binary Editor](binary-editor.md)

