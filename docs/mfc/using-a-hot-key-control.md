---
description: 'En savoir plus sur : utilisation d’un contrôle de touche d’accès rapide'
title: Utilisation d'un contrôle de touche d'accès rapide
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
ms.openlocfilehash: 078cd4b3d4746723d5996959edad20dd44e9abec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202702"
---
# <a name="using-a-hot-key-control"></a>Utilisation d'un contrôle de touche d'accès rapide

L’utilisation classique d’un contrôle de touche d’accès rapide suit le modèle ci-dessous :

- Le contrôle est créé. Si le contrôle est spécifié dans un modèle de boîte de dialogue, la création est automatique lors de la création de la boîte de dialogue. (Vous devez avoir un membre [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) dans votre classe de boîte de dialogue qui correspond au contrôle de touche d’accès rapide.) Vous pouvez également utiliser la fonction membre [Create](../mfc/reference/chotkeyctrl-class.md#create) pour créer le contrôle en tant que fenêtre enfant de n’importe quelle fenêtre.

- Si vous souhaitez définir une valeur par défaut pour le contrôle, appelez la fonction membre [SetHotKey](../mfc/reference/chotkeyctrl-class.md#sethotkey) . Si vous souhaitez interdire certains États de décalage, appelez [SetRules](../mfc/reference/chotkeyctrl-class.md#setrules). Pour les contrôles d’une boîte de dialogue, il est recommandé de le faire dans la fonction [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) de la boîte de dialogue.

- L’utilisateur interagit avec le contrôle en appuyant sur une combinaison de touches d’accès rapide lorsque le contrôle de touche d’accès rapide a le focus. L’utilisateur indique ensuite que cette tâche est terminée, par exemple en cliquant sur un bouton dans la boîte de dialogue.

- Lorsque votre programme est informé que l’utilisateur a sélectionné une touche d’accès rapide, il doit utiliser la fonction membre [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) pour récupérer les valeurs de la clé virtuelle et de l’état de décalage à partir du contrôle de touche d’accès rapide.

- Une fois que vous connaissez la clé sélectionnée par l’utilisateur, vous pouvez définir la touche d’accès rapide à l’aide de l’une des méthodes décrites dans [définition d’une touche d’accès rapide](../mfc/setting-a-hot-key.md).

- Si le contrôle de touche d’accès rapide se trouve dans une boîte de dialogue, et que l' `CHotKeyCtrl` objet est détruit automatiquement. Si ce n’est pas le cas, vous devez vous assurer que le contrôle et l' `CHotKeyCtrl` objet sont correctement détruits.

## <a name="see-also"></a>Voir aussi

[Utilisation de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
