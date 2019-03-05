---
title: Accès de type sécurisé aux contrôles d'une boîte de dialogue
ms.date: 11/04/2016
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- Windows common controls [MFC], in dialog boxes
- safe access to dialog box controls
- dialog boxes [MFC], type-safe access to controls
- controls [MFC], accessing in dialog boxes
- type-safe access to dialog box controls
- MFC dialog boxes [MFC], type-safe access to controls
ms.assetid: 67021025-dd93-4d6a-8bed-a1348fe50685
ms.openlocfilehash: 9b8e5aef61d1a7c7277f2a6bd37b81bd156bb837
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264155"
---
# <a name="type-safe-access-to-controls-in-a-dialog-box"></a>Accès de type sécurisé aux contrôles d'une boîte de dialogue

Les contrôles d'une boîte de dialogue peuvent utiliser les interfaces des classes de contrôles MFC telles que `CListBox` et `CEdit`. Vous pouvez créer un objet contrôle et l'attacher à un contrôle de boîte de dialogue. Vous pouvez ensuite accéder au contrôle via son interface de classe, en appelant des fonctions membres pour agir sur le contrôle. Les méthodes décrites ici sont conçues pour vous donner un accès de type sécurisé à un contrôle. Ceci est particulièrement utile pour les contrôles tels que les zones d'édition et les zones de liste.

Vous disposez de deux méthodes pour établir une connexion entre un contrôle d'une boîte de dialogue et une variable membre de contrôle C++ dans une classe dérivée de `CDialog` :

- [Sans Assistants Code](../mfc/type-safe-access-to-controls-without-code-wizards.md)

- [Aide des Assistants Code](../mfc/type-safe-access-to-controls-with-code-wizards.md)

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)
