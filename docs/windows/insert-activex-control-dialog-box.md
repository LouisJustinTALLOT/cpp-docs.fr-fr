---
title: Insérer le contrôle ActiveX, boîte de dialogue (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- Insert ActiveX Control dialog box [C++]
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: 06638ea3-0726-40da-a989-9b89292d0e3d
ms.openlocfilehash: 495245141b62850067196c81bfe4c6f984dcfa88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592749"
---
# <a name="insert-activex-control-dialog-box-c"></a>Insérer le contrôle ActiveX, boîte de dialogue (C++)

Cette boîte de dialogue vous permet de [insérer des contrôles ActiveX dans votre boîte de dialogue](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md) tout en utilisant le [éditeur de boîte de dialogue](../windows/dialog-editor.md).

### <a name="activex-control"></a>Contrôle ActiveX

Affiche une liste de contrôles Active X. Insertion d’un contrôle à partir de cette boîte de dialogue ne génère pas une classe wrapper. Si vous avez besoin d’une classe wrapper, utilisez [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code) pour en créer une (pour plus d’informations, consultez [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md)). Si un contrôle ActiveX n’apparaît pas dans cette boîte de dialogue, essayez d’installer le contrôle selon les instructions du fournisseur.

### <a name="path"></a>Chemin d’accès

Affiche le fichier dans lequel le contrôle ActiveX est trouvé.

Vous pouvez placer des contrôles dans le **boîte à outils** fenêtre pour pouvoir accéder facilement. Pour plus d'informations, consultez [Boîte à outils](/visualstudio/ide/reference/).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de boîtes de dialogue, onglet de la boîte à outils](../windows/dialog-editor-tab-toolbox.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)