---
title: Utilisation d'un contrôle de touche d'accès rapide
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
ms.openlocfilehash: d9178fe989e476111a3da55861642e9aa6311872
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260576"
---
# <a name="using-a-hot-key-control"></a>Utilisation d'un contrôle de touche d'accès rapide

L’utilisation normale d’un contrôle de touche d’accès rapide suit le modèle suivant :

- Le contrôle est créé. Si le contrôle est spécifié dans un modèle de boîte de dialogue, la création est automatique lors de la création de la boîte de dialogue. (Vous devez avoir un [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) membre dans votre classe de boîte de dialogue qui correspond au contrôle de touche d’accès rapide.) Vous pouvez également utiliser le [créer](../mfc/reference/chotkeyctrl-class.md#create) fonction membre pour créer le contrôle en tant que fenêtre enfant de n’importe quelle fenêtre.

- Si vous souhaitez définir une valeur par défaut pour le contrôle, appelez le [fonction membre SetHotKey](../mfc/reference/chotkeyctrl-class.md#sethotkey) fonction membre. Si vous souhaitez interdire certains États MAJ, appelez [SetRules](../mfc/reference/chotkeyctrl-class.md#setrules). Pour les contrôles dans une boîte de dialogue, un bon moment pour ce faire est dans la boîte de dialogue [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) (fonction).

- L’utilisateur interagit avec le contrôle en appuyant sur une combinaison de touches à chaud lorsque le contrôle de touche d’accès rapide a le focus. L’utilisateur indique ensuite que cette tâche est terminée, peut-être en cliquant sur un bouton dans la boîte de dialogue.

- Lorsque votre programme est informé que l’utilisateur a sélectionné une touche d’accès rapide, il doit utiliser la fonction membre [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) pour extraire les valeurs d’état- and -shift clé virtuels le contrôle de touche d’accès rapide.

- Une fois que vous savez ce que l’utilisateur a sélectionné la clé, vous pouvez définir la touche d’accès rapide à l’aide d’une des méthodes décrites dans [définissant une touche d’accès rapide](../mfc/setting-a-hot-key.md).

- Si le contrôle de touche d’accès rapide se trouve dans une boîte de dialogue, elle et la `CHotKeyCtrl` objet sera détruit automatiquement. Si pas, vous devez vous assurer que les deux le contrôle et le `CHotKeyCtrl` objet sont détruits correctement.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
