---
title: Affichage et ajout de contrôles ActiveX dans une boîte de dialogue (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
ms.openlocfilehash: 139407ec1d4e1bfad6bb06854dc24b86ce7014e8
ms.sourcegitcommit: b488462a6e035131121e6f32d8f3b108cc798b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55293609"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box-c"></a>Affichage et ajout de contrôles ActiveX dans une boîte de dialogue (C++)

Avec Visual Studio, vous pouvez insérer des contrôles ActiveX dans votre boîte de dialogue.

Le **insérer un contrôle ActiveX** boîte de dialogue permet d’insérer des contrôles ActiveX dans votre boîte de dialogue lors de l’utilisation du [éditeur de boîte de dialogue](../windows/dialog-editor.md). Cette boîte de dialogue contient les propriétés suivantes :

|Propriété|Description|
|---|---|
|**Contrôle ActiveX**|Affiche une liste de contrôles Active X. Insertion d’un contrôle à partir de cette boîte de dialogue ne génère pas une classe wrapper. Si vous avez besoin d’une classe wrapper, utilisez [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code) pour en créer une (pour plus d’informations, consultez [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md)). Si un contrôle ActiveX n’apparaît pas dans cette boîte de dialogue, essayez d’installer le contrôle selon les instructions du fournisseur.|
|**Chemin d’accès**|Affiche le fichier dans lequel le contrôle ActiveX est trouvé.|

Vous pouvez placer des contrôles dans le **boîte à outils** fenêtre pour pouvoir accéder facilement. Pour plus d'informations, consultez [Boîte à outils](/visualstudio/ide/reference/).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-see-the-activex-controls-you-have-available"></a>Pour afficher les contrôles ActiveX disponibles

1. Ouvrez une boîte de dialogue dans l’Éditeur de boîtes de dialogue.

1. Avec le bouton droit n’importe où dans le corps de la boîte de dialogue.

1. Dans le menu contextuel, sélectionnez **insérer un contrôle ActiveX**.

   Le **insérer un contrôle ActiveX** boîte de dialogue apparaît, affichant tous les contrôles ActiveX sur votre système. En bas de la boîte de dialogue figure le chemin d’accès au fichier de contrôle ActiveX.

## <a name="to-add-an-activex-control-to-a-dialog-box"></a>Pour ajouter un contrôle ActiveX à une boîte de dialogue

1. Dans le **insérer un contrôle ActiveX** boîte de dialogue, sélectionnez le contrôle que vous souhaitez ajouter à votre boîte de dialogue, puis sélectionnez **OK**.

   Le contrôle apparaît dans la boîte de dialogue, où vous pouvez le modifier ou créer des gestionnaires comme vous le feriez pour n’importe quel autre contrôle.

   > [!NOTE]
   > Vous pouvez ajouter des contrôles ActiveX à la fenêtre [Boîte à outils](/visualstudio/ide/reference/toolbox).

   > [!CAUTION]
   > Il se peut que la distribution de tous les contrôles ActiveX sur votre système ne soit pas autorisée juridiquement. Reportez-vous au contrat de licence du logiciel qui a installé les contrôles ou contactez l’éditeur du logiciel.

   Vous pouvez placer des contrôles dans le **boîte à outils** fenêtre pour pouvoir accéder facilement. Pour plus d'informations, consultez [Boîte à outils](/visualstudio/ide/reference/toolbox).

## <a name="to-edit-properties-for-an-activex-control"></a>Pour modifier les propriétés pour un contrôle ActiveX

Contrôles ActiveX fournis par des fabricants indépendants peuvent sont équipés à leurs propriétés et leurs caractéristiques. Propriétés pour les contrôles ActiveX sont affichées dans le **propriétés** fenêtre. En outre, les pages de propriétés créées par les auteurs du contrôle ActiveX sont affichées dans le **Pages de propriétés** boîte de dialogue (pour afficher le **Page de propriétés** pour un contrôle ActiveX spécifique, cliquez sur le  **Page de propriétés** situé dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window)).

Plusieurs onglets s’affichent dans la page de propriétés pour un contrôle ActiveX, selon les feuilles de propriétés qui font partie du contrôle ActiveX.

> [!NOTE]
> La procédure suivante s’applique à l’utilisation de la page de propriétés pour modifier des contrôles ActiveX. Vous pouvez également parcourir et modifier les propriétés ActiveX dans le nouveau **propriétés** fenêtre.

1. Sélectionnez le **ActiveX** contrôle.

1. Sur le **vue** menu, sélectionnez **Page de propriétés** et afficher les propriétés.

1. Apportez les modifications nécessaires dans la page de propriétés.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Conteneurs de contrôles ActiveX](../mfc/activex-control-containers.md)<br/>
[Affichage et ajout de contrôles ActiveX dans une boîte de dialogue](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)<br/>
[Éditeur de boîtes de dialogue, onglet de la boîte à outils](../windows/dialog-editor-tab-toolbox.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
