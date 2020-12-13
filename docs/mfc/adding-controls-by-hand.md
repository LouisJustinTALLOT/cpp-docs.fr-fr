---
description: 'En savoir plus sur : ajout de contrôles à la main'
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
ms.openlocfilehash: f6dfa65baa037aa168697aa7abcd3eedc76cc4d2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339079"
---
# <a name="adding-controls-by-hand"></a>Ajout de contrôles manuellement

Vous pouvez [Ajouter des contrôles à une boîte de dialogue à l’aide de l’éditeur de boîtes de dialogue](using-the-dialog-editor-to-add-controls.md) ou les ajouter vous-même, avec le code.

Pour créer vous-même un objet contrôle, vous devez généralement incorporer l’objet contrôle C++ dans une boîte de dialogue C++ ou un objet fenêtre frame. À l’instar de nombreux autres objets de l’infrastructure, les contrôles nécessitent une construction en deux étapes. Vous devez appeler la fonction membre **Create** du contrôle dans le cadre de la création de la boîte de dialogue parente ou de la fenêtre frame. Pour les boîtes de dialogue, cette opération est généralement effectuée dans [OnInitDialog](reference/cdialog-class.md#oninitdialog), et pour les fenêtres Frame, dans [OnCreate](reference/cwnd-class.md#oncreate).

L’exemple suivant montre comment vous pouvez déclarer un `CEdit` objet dans la déclaration de classe d’une classe de boîte de dialogue dérivée, puis appeler la `Create` fonction membre dans `OnInitDialog` . Étant donné que l' `CEdit` objet est déclaré en tant qu’objet incorporé, il est construit automatiquement lorsque l’objet Dialog est construit, mais il doit toujours être initialisé avec sa propre `Create` fonction membre.

[!code-cpp[NVC_MFCControlLadenDialog#1](codesnippet/cpp/adding-controls-by-hand_1.h)]

La `OnInitDialog` fonction suivante définit un rectangle, puis appelle `Create` pour créer le contrôle d’édition Windows et l’attacher à l’objet non initialisé `CEdit` .

[!code-cpp[NVC_MFCControlLadenDialog#2](codesnippet/cpp/adding-controls-by-hand_2.cpp)]

Après avoir créé l’objet de modification, vous pouvez également définir le focus d’entrée sur le contrôle en appelant la `SetFocus` fonction membre. Enfin, vous retournez 0 de `OnInitDialog` pour montrer que vous avez défini le focus. Si vous retournez une valeur différente de zéro, le gestionnaire de boîtes de dialogue définit le focus sur le premier élément de contrôle de la liste d’éléments de boîte de dialogue. Dans la plupart des cas, vous souhaiterez ajouter des contrôles à vos boîtes de dialogue à l’aide de l’éditeur de boîtes de dialogue.

## <a name="see-also"></a>Voir aussi

[Création et utilisation de contrôles](making-and-using-controls.md)<br/>
[Contrôles](controls-mfc.md)<br/>
[CDialog :: OnInitDialog](reference/cdialog-class.md#oninitdialog)
