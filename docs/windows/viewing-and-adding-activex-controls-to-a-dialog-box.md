---
title: Affichage et ajout de contrôles ActiveX dans une boîte de dialogue | Microsoft Docs
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
- Insert ActiveX Control command
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 91a010c9ffe1f05780c25fc6d6ec96d2619a8019
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202761"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box"></a>Affichage et ajout de contrôles ActiveX dans une boîte de dialogue

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
   > Vous pouvez ajouter des contrôles ActiveX à la fenêtre [Boîte à outils](/visualstudio/ide/reference/toolbox). Pour plus d’informations, consultez [gestion des éléments et des onglets dans la boîte à outils](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

   > [!CAUTION]
   > Il se peut que la distribution de tous les contrôles ActiveX sur votre système ne soit pas autorisée juridiquement. Reportez-vous au contrat de licence du logiciel qui a installé les contrôles ou contactez l’éditeur du logiciel.

   Vous pouvez placer des contrôles dans le **boîte à outils** fenêtre pour pouvoir accéder facilement. Pour plus d’informations, consultez [boîte de dialogue Personnaliser la boîte à outils](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)  
[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)  
[Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)