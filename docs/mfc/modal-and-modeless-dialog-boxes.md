---
title: Boîtes de dialogue modales et non modales
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: 7e1dc9c40f60dc46117ee0673a038d5a63df7680
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528360"
---
# <a name="modal-and-modeless-dialog-boxes"></a>Boîtes de dialogue modales et non modales

Vous pouvez utiliser la classe [CDialog](../mfc/reference/cdialog-class.md) pour gérer deux types de boîtes de dialogue :

- *Boîtes de dialogue modales*, ce qui oblige l’utilisateur à répondre avant de poursuivre le programme

- *Boîtes de dialogue non modale*, qui restent sur l’écran et sont disponibles pour une utilisation à tout moment, mais autoriser d’autres activités des utilisateurs

La modification des ressources et les procédures de création d’un modèle de boîte de dialogue sont les mêmes pour les boîtes de dialogue modales et non modales.

Création d’une boîte de dialogue pour votre programme, effectuez les étapes suivantes :

1. Utilisez le [éditeur de boîte de dialogue](../windows/dialog-editor.md) pour concevoir la boîte de dialogue et créer sa ressource modèle de boîte de dialogue.

1. Créez une classe de boîte de dialogue.

1. Connecter le [des contrôles de la ressource de la boîte de dialogue pour les gestionnaires de messages](../windows/adding-event-handlers-for-dialog-box-controls.md) dans la classe de boîte de dialogue.

1. Ajouter des membres de données associées aux contrôles de la boîte de dialogue et spécifier [échange de données de boîtes de dialogue](../mfc/dialog-data-exchange.md) et [des validations de données de boîte de dialogue](../mfc/dialog-data-validation.md) pour les contrôles.

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)<br/>
[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

