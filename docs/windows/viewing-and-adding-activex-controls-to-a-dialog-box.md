---
title: Affichage et ajout de contrôles ActiveX dans une boîte de dialogue (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.controls.activex
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1eccaaff3f89b6353bd38e316ad515edc59eb9ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427405"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box-c"></a>Affichage et ajout de contrôles ActiveX dans une boîte de dialogue (C++)

Avec Visual Studio, vous pouvez insérer des contrôles ActiveX dans votre boîte de dialogue.

### <a name="to-see-the-activex-controls-you-have-available"></a>Pour afficher les contrôles ActiveX disponibles

1. Ouvrez une boîte de dialogue dans l’Éditeur de boîtes de dialogue.

2. Cliquez avec le bouton droit n’importe où dans le corps de la boîte de dialogue.

3. Dans le menu contextuel, cliquez sur **Insérer un contrôle ActiveX**.

   La boîte de dialogue [Insérer un contrôle ActiveX](../windows/insert-activex-control-dialog-box.md) apparaît et affiche tous les contrôles ActiveX disponibles sur votre système. En bas de la boîte de dialogue figure le chemin d’accès au fichier de contrôle ActiveX.

### <a name="to-add-an-activex-control-to-a-dialog-box"></a>Pour ajouter un contrôle ActiveX à une boîte de dialogue

1. Dans la boîte de dialogue [Insérer un contrôle ActiveX](../windows/insert-activex-control-dialog-box.md), sélectionnez le contrôle que vous souhaitez ajouter à votre boîte de dialogue, puis cliquez sur **OK**.

   Le contrôle apparaît dans la boîte de dialogue, où vous pouvez le modifier ou créer des gestionnaires comme vous le feriez pour n’importe quel autre contrôle.

   > [!NOTE]
   > Vous pouvez ajouter des contrôles ActiveX à la fenêtre [Boîte à outils](/visualstudio/ide/reference/toolbox).

   > [!CAUTION]
   > Il se peut que la distribution de tous les contrôles ActiveX sur votre système ne soit pas autorisée juridiquement. Reportez-vous au contrat de licence du logiciel qui a installé les contrôles ou contactez l’éditeur du logiciel.

   Vous pouvez placer des contrôles dans le **boîte à outils** fenêtre pour pouvoir accéder facilement. Pour plus d'informations, consultez [Boîte à outils](/visualstudio/ide/reference/toolbox).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)