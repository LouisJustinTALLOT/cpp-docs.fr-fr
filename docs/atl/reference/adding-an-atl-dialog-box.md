---
title: Ajout d’une boîte de dialogue ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding dialog resources
- MFC dialog boxes, ATL dialogs
- dialog boxes, ATL
ms.assetid: 152a378f-7b24-4f66-aeba-c740973f03a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0883b87ce991b08a96b1d10b4acedf8562022a3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361523"
---
# <a name="adding-an-atl-dialog-box"></a>Ajout d’une boîte de dialogue ATL
Pour ajouter une boîte de dialogue ATL à votre projet, votre projet doit être un projet ATL ou un projet MFC qui inclut la prise en charge ATL. Vous pouvez utiliser la [Assistant Projet ATL](../../atl/reference/atl-project-wizard.md) pour créer une application ATL, ou [ajouter un objet ATL à votre application MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) pour implémenter la prise en charge ATL pour une application MFC.  
  
 Par défaut, l’Assistant dialogue ATL implémente une boîte de dialogue dérivée [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md). Cette classe inclut la prise en charge pour l’hébergement de contrôles ActiveX et Windows. Si vous ne souhaitez pas la surcharge de prise en charge du contrôle ActiveX, une fois que l’Assistant a généré votre code, remplacez toutes les instances de `CAxDialogImpl` avec l’option [CSimpleDialog](../../atl/reference/csimpledialog-class.md) ou [CDialogImpl](../../atl/reference/cdialogimpl-class.md) comme classe de base .  
  
> [!NOTE]
>  `CSimpleDialog` crée uniquement des boîtes de dialogue modales qui prennent en charge uniquement des contrôles communs Windows. `CDialogImpl` crée des zones de la boîte de dialogue modale ou non.  
  
### <a name="to-add-an-atl-dialog-resource-to-your-project"></a>Pour ajouter une ressource de boîte de dialogue ATL à votre projet  
  
1.  Créez un projet ATL en utilisant le [Assistant Projet ATL](../../atl/reference/atl-project-wizard.md).  
  
2.  À partir de [affichage de classes](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), cliquez sur le nom du projet, cliquez sur **ajouter** dans le menu contextuel. Cliquez sur **ajouter une classe**.  
  
3.  Dans le volet Modèles de la [ajouter une classe](../../ide/add-class-dialog-box.md) boîte de dialogue, cliquez sur **boîte de dialogue ATL**. Cliquez sur **ouvrir** pour afficher les [Assistant dialogue ATL](../../atl/reference/atl-dialog-wizard.md).  
  
 Pour plus d’informations, consultez [mise en œuvre d’une boîte de dialogue](../../atl/implementing-a-dialog-box.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)   
 [Classes de fenêtre](../../atl/atl-window-classes.md)   
 [Tables des messages](../../atl/message-maps-atl.md)

