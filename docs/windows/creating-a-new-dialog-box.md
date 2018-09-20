---
title: Création d’une boîte de dialogue (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fae55d0b4ce4a766952afcec7f78ec6b20fbb258
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426638"
---
# <a name="creating-a-new-dialog-box-c"></a>Création d’une boîte de dialogue (C++)

### <a name="to-create-a-new-dialog-box"></a>Pour créer une nouvelle boîte de dialogue

1. Dans [affichage des ressources](../windows/resource-view-window.md), avec le bouton droit de votre fichier .rc, puis choisissez **ajouter une ressource** dans le menu contextuel.

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

2. Dans le **ajouter une ressource** boîte de dialogue, sélectionnez **boîte de dialogue** dans le **Type de ressource** liste, puis cliquez sur **New**.

   Si un signe plus (**+**) apparaît en regard du **boîte de dialogue** type de ressource, cela signifie que les modèles de boîte de dialogue sont disponibles. Cliquez sur le signe plus pour développer la liste des modèles, sélectionnez un modèle, puis cliquez sur **New**.

   La nouvelle boîte de dialogue s’ouvre dans le **boîte de dialogue** éditeur.

   Vous pouvez également [ouvrir les boîtes de dialogue existantes dans l’éditeur de boîte de dialogue Modifier](../windows/viewing-and-editing-resources-in-a-resource-editor.md).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Guide pratique pour créer une ressource](../windows/how-to-create-a-resource.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)