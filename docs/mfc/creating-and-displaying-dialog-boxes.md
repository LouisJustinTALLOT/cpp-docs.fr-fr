---
title: Création et affichage de boîtes de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
ms.openlocfilehash: 649d64f8e8b894027b9d6850b62d357d79c1dafa
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616273"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Création et affichage de boîtes de dialogue

La création d’un objet de boîte de dialogue est une opération en deux phases. Tout d’abord, construisez l’objet Dialog, puis créez la fenêtre de dialogue. Les boîtes de dialogue modales et non modales diffèrent quelque peu dans le processus utilisé pour les créer et les afficher. Le tableau suivant indique comment les boîtes de dialogue modales et non modales sont normalement construites et affichées.

### <a name="dialog-creation"></a>Création de dialogue

|Type de dialogue|Comment le créer|
|-----------------|----------------------|
|[Non modale](creating-modeless-dialog-boxes.md)|Construisez `CDialog` , puis appelez la `Create` fonction membre.|
|[Exigeant](creating-modal-dialog-boxes.md)|Construisez `CDialog` , puis appelez la `DoModal` fonction membre.|

Si vous le souhaitez, vous pouvez créer votre boîte de dialogue à partir d’un [modèle de boîte de dialogue en mémoire](using-a-dialog-template-in-memory.md) que vous avez construit plutôt qu’à partir d’une ressource de modèle de boîte de dialogue. Il s’agit toutefois d’une rubrique avancée.

## <a name="see-also"></a>Voir aussi

[Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)
