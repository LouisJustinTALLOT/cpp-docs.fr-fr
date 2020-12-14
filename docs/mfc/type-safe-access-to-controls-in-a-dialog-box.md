---
description: 'En savoir plus sur les éléments suivants : Type-Safe l’accès aux contrôles dans une boîte de dialogue'
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
ms.openlocfilehash: 1c8b3482ee723e95142c9cd19fa6068f32f4ebd0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263827"
---
# <a name="type-safe-access-to-controls-in-a-dialog-box"></a>Accès de type sécurisé aux contrôles d'une boîte de dialogue

Les contrôles d'une boîte de dialogue peuvent utiliser les interfaces des classes de contrôles MFC telles que `CListBox` et `CEdit`. Vous pouvez créer un objet contrôle et l'attacher à un contrôle de boîte de dialogue. Vous pouvez ensuite accéder au contrôle via son interface de classe, en appelant des fonctions membres pour agir sur le contrôle. Les méthodes décrites ici sont conçues pour vous donner un accès de type sécurisé à un contrôle. Ceci est particulièrement utile pour les contrôles tels que les zones d'édition et les zones de liste.

Vous disposez de deux méthodes pour établir une connexion entre un contrôle d'une boîte de dialogue et une variable membre de contrôle C++ dans une classe dérivée de `CDialog` :

- [Sans Assistants Code](../mfc/type-safe-access-to-controls-without-code-wizards.md)

- [Avec des Assistants Code](../mfc/type-safe-access-to-controls-with-code-wizards.md)

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)
