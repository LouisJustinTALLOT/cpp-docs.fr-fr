---
description: En savoir plus sur les boîtes de dialogue modales et non modales
title: Boîtes de dialogue modales et non modales
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: 11320c2efcb323fe839afecb6165409285f442aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251139"
---
# <a name="modal-and-modeless-dialog-boxes"></a>Boîtes de dialogue modales et non modales

Vous pouvez utiliser la classe [CDialog](reference/cdialog-class.md) pour gérer deux types de boîtes de dialogue :

- *Boîtes de dialogue modales*, qui requièrent que l’utilisateur réponde avant de poursuivre le programme

- *Boîtes de dialogue non modales*, qui restent à l’écran et peuvent être utilisées à tout moment, mais permettent à d’autres activités de l’utilisateur

La modification des ressources et les procédures de création d’un modèle de boîte de dialogue sont les mêmes pour les boîtes de dialogue modales et non modales.

La création d’une boîte de dialogue pour votre programme requiert les étapes suivantes :

1. Utilisez l' [éditeur de boîtes](../windows/dialog-editor.md) de dialogue pour concevoir la boîte de dialogue et créer sa ressource de modèle de boîte de dialogue.

1. Créer une classe de dialogue.

1. Connectez les [contrôles de la ressource de boîte de dialogue aux gestionnaires de messages](../windows/adding-editing-or-deleting-controls.md) dans la classe dialog.

1. Ajoutez des membres de données associés aux contrôles de la boîte de dialogue et spécifiez les [validations](dialog-data-validation.md) d' [échange de données](dialog-data-exchange.md) de boîtes de dialogue et de boîtes de dialogue pour les contrôles.

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](dialog-boxes.md)<br/>
[Utilisation des boîtes de dialogue dans MFC](life-cycle-of-a-dialog-box.md)
