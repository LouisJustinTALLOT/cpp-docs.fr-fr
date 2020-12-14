---
description: 'En savoir plus sur : création et affichage de boîtes de dialogue'
title: Création et affichage de boîtes de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
ms.openlocfilehash: 9865e43392021cc7ba1349a73bffb8e47f4cca9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309822"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Création et affichage de boîtes de dialogue

La création d’un objet de boîte de dialogue est une opération en deux phases. Tout d’abord, construisez l’objet Dialog, puis créez la fenêtre de dialogue. Les boîtes de dialogue modales et non modales diffèrent quelque peu dans le processus utilisé pour les créer et les afficher. Le tableau suivant indique comment les boîtes de dialogue modales et non modales sont normalement construites et affichées.

### <a name="dialog-creation"></a>Création de dialogue

|Type de dialogue|Comment le créer|
|-----------------|----------------------|
|[Non modale](creating-modeless-dialog-boxes.md)|Construisez `CDialog` , puis appelez la `Create` fonction membre.|
|[Modal](creating-modal-dialog-boxes.md)|Construisez `CDialog` , puis appelez la `DoModal` fonction membre.|

Si vous le souhaitez, vous pouvez créer votre boîte de dialogue à partir d’un [modèle de boîte de dialogue en mémoire](using-a-dialog-template-in-memory.md) que vous avez construit plutôt qu’à partir d’une ressource de modèle de boîte de dialogue. Il s’agit toutefois d’une rubrique avancée.

## <a name="see-also"></a>Voir aussi

[Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)
