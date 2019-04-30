---
title: Ajout de contrôles manuellement
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
ms.openlocfilehash: c70539b49fcf2aa87f0bee375a87b38277b6ed42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394804"
---
# <a name="adding-controls-by-hand"></a>Ajout de contrôles manuellement

Vous pouvez soit [ajouter des contrôles à une boîte de dialogue avec l’éditeur de boîtes de dialogue](../mfc/using-the-dialog-editor-to-add-controls.md) ou les ajouter vous-même, avec le code.

Pour créer un objet de contrôle vous-même, vous incorporez généralement l’objet de contrôle C++ dans une boîte de dialogue C++ ou un objet fenêtre frame. Comme de nombreux autres objets dans le framework, les contrôles nécessitent construction en deux étapes. Vous devez appeler le contrôle **créer** fonction membre dans le cadre de la création de la fenêtre de zone ou le frame de boîte de dialogue parent. Pour les boîtes de dialogue, cela se fait généralement [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)et pour les fenêtres frame, dans [OnCreate](../mfc/reference/cwnd-class.md#oncreate).

L’exemple suivant montre comment vous pouvez déclarer un `CEdit` dans la déclaration de classe d’une classe de boîte de dialogue dérivée de l’objet, puis appelez le `Create` fonction membre dans `OnInitDialog`. Étant donné que le `CEdit` objet est déclaré en tant qu’objet incorporé, il est construit automatiquement lorsque l’objet de la boîte de dialogue est construit, mais il doit toujours être initialisé avec sa propre `Create` fonction membre.

[!code-cpp[NVC_MFCControlLadenDialog#1](../mfc/codesnippet/cpp/adding-controls-by-hand_1.h)]

Ce qui suit `OnInitDialog` fonction définit un rectangle, puis appelle `Create` pour créer le contrôle d’édition Windows et l’attacher à la non initialisé `CEdit` objet.

[!code-cpp[NVC_MFCControlLadenDialog#2](../mfc/codesnippet/cpp/adding-controls-by-hand_2.cpp)]

Après avoir créé l’objet de modification, vous pouvez également définir le focus d’entrée au contrôle en appelant le `SetFocus` fonction membre. Enfin, vous retournez 0 de `OnInitDialog` pour montrer que vous définissez le focus. Si vous retournez une valeur différente de zéro, le Gestionnaire de boîte de dialogue définit le focus sur le premier élément de contrôle dans la liste d’éléments de boîte de dialogue. Dans la plupart des cas, vous souhaiterez ajouter des contrôles à vos boîtes de dialogue avec l’éditeur de boîtes de dialogue.

## <a name="see-also"></a>Voir aussi

[Création et utilisation de contrôles](../mfc/making-and-using-controls.md)<br/>
[Contrôles](../mfc/controls-mfc.md)<br/>
[CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)
