---
title: Ajout d’une boîte de dialogue ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
ms.openlocfilehash: 71290cf0763ac6594985acc4cb11562efe7028e6
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91499366"
---
# <a name="adding-an-atl-dialog-box"></a>Ajout d’une boîte de dialogue ATL

Pour ajouter une boîte de dialogue ATL à votre projet, votre projet doit être un projet ATL ou un projet MFC qui prend en charge ATL. Vous pouvez utiliser l' [Assistant Projet ATL](../../atl/reference/atl-project-wizard.md) pour créer une application ATL, ou [Ajouter un objet ATL à votre application MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) pour implémenter la prise en charge ATL pour une application MFC.

Par défaut, l’Assistant boîte de dialogue ATL implémente une boîte de dialogue dérivée de [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Cette classe prend en charge l’hébergement de contrôles ActiveX et Windows. Si vous ne souhaitez pas la surcharge de la prise en charge des contrôles ActiveX, une fois que l’Assistant a généré votre code, remplacez toutes les instances de `CAxDialogImpl` par [CSimpleDialog](../../atl/reference/csimpledialog-class.md) ou [CDialogImpl](../../atl/reference/cdialogimpl-class.md) comme classe de base.

> [!NOTE]
> `CSimpleDialog` crée uniquement des boîtes de dialogue modales qui prennent uniquement en charge les contrôles communs Windows. `CDialogImpl` crée des boîtes de dialogue modales ou non modales.

## <a name="to-add-an-atl-dialog-resource-to-your-project"></a>Pour ajouter une ressource de boîte de dialogue ATL à votre projet

1. Créez un projet ATL à l’aide de l' [Assistant Projet ATL](../../atl/reference/atl-project-wizard.md).

1. Dans [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Ajouter** dans le menu contextuel. Cliquez sur **Ajouter une classe**.

1. Dans le volet **modèles** de la boîte de dialogue [Ajouter une classe](../../ide/adding-a-class-visual-cpp.md#add-class-dialog-box) , cliquez sur boîte de **dialogue ATL**. Cliquez sur **ouvrir** pour afficher l ['Assistant boîte de dialogue ATL](../../atl/reference/atl-dialog-wizard.md).

Pour plus d’informations, consultez [implémentation d’une boîte de dialogue](../../atl/implementing-a-dialog-box.md).

## <a name="see-also"></a>Voir aussi

[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[classes de fenêtre](../../atl/atl-window-classes.md)<br/>
[Tables des messages](../../atl/message-maps-atl.md)
