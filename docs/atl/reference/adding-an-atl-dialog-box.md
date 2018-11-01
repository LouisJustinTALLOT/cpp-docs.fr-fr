---
title: Ajout d’une boîte de dialogue ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
ms.openlocfilehash: ee6f6b1b83c625b30b601275084550309e0e7c68
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495366"
---
# <a name="adding-an-atl-dialog-box"></a>Ajout d’une boîte de dialogue ATL

Pour ajouter une boîte de dialogue ATL à votre projet, votre projet doit être un projet ATL ou un projet MFC qui inclut la prise en charge ATL. Vous pouvez utiliser [l’Assistant Projet ATL](../../atl/reference/atl-project-wizard.md) pour créer une application ATL ou [ajouter un objet ATL à votre application MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) pour implémenter la prise en charge ATL dans une application MFC.

Par défaut, l’Assistant dialogue ATL implémente une boîte de dialogue dérivée de [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Cette classe inclut la prise en charge pour l’hébergement de contrôles ActiveX et Windows. Si vous ne souhaitez pas la surcharge liée à la prise en charge du contrôle ActiveX, une fois que l’Assistant a généré votre code, remplacez toutes les instances de `CAxDialogImpl` avec soit [CSimpleDialog](../../atl/reference/csimpledialog-class.md) ou [CDialogImpl](../../atl/reference/cdialogimpl-class.md) comme classe de base .

> [!NOTE]
> `CSimpleDialog` crée uniquement des boîtes de dialogue modales qui prennent en charge uniquement des contrôles communs Windows. `CDialogImpl` crée des zones de la boîte de dialogue modale ou non modale.

## <a name="to-add-an-atl-dialog-resource-to-your-project"></a>Pour ajouter une ressource de boîte de dialogue ATL à votre projet

1. Créez un projet ATL à l’aide du [Assistant Projet ATL](../../atl/reference/atl-project-wizard.md).

1. À partir de [affichage de classes](/visualstudio/ide/viewing-the-structure-of-code), cliquez sur le nom du projet et cliquez sur **ajouter** dans le menu contextuel. Cliquez sur **ajouter une classe**.

1. Dans le **modèles** volet de la [ajouter une classe](../../ide/add-class-dialog-box.md) boîte de dialogue, cliquez sur **boîte de dialogue ATL**. Cliquez sur **Open** pour afficher le [Assistant dialogue ATL](../../atl/reference/atl-dialog-wizard.md).

Pour plus d’informations, consultez [mise en œuvre d’une boîte de dialogue](../../atl/implementing-a-dialog-box.md).

## <a name="see-also"></a>Voir aussi

[Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)<br/>
[Classes de fenêtre](../../atl/atl-window-classes.md)<br/>
[Tables des messages](../../atl/message-maps-atl.md)
