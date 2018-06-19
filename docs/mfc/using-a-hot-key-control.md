---
title: À l’aide d’un contrôle de touche d’accès rapide | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHotKeyCtrl class [MFC], using
- hot key controls
ms.assetid: cdd6524b-cc43-447f-b151-164273559685
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4442d45cffdae63600fa3a405e29a139b149175
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382942"
---
# <a name="using-a-hot-key-control"></a>Utilisation d'un contrôle de touche d'accès rapide
L’utilisation typique d’un contrôle de touche d’accès rapide suit le modèle suivant :  
  
-   Le contrôle est créé. Si le contrôle est spécifié dans un modèle de boîte de dialogue, la création est automatique lors de la création de la boîte de dialogue. (Vous devez disposer d’un [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) membre dans votre classe de boîte de dialogue qui correspond à la clé contrôle d’accès rapide.) Vous pouvez également utiliser le [créer](../mfc/reference/chotkeyctrl-class.md#create) fonction membre pour créer le contrôle en tant que fenêtre enfant de n’importe quelle fenêtre.  
  
-   Si vous souhaitez définir une valeur par défaut pour le contrôle, appelez le [fonction membre SetHotKey](../mfc/reference/chotkeyctrl-class.md#sethotkey) fonction membre. Si vous souhaitez interdire certains États MAJ, appelez [SetRules](../mfc/reference/chotkeyctrl-class.md#setrules). Pour les contrôles dans une boîte de dialogue, judicieux de procéder est dans la boîte de dialogue [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) (fonction).  
  
-   L’utilisateur interagit avec le contrôle en appuyant sur une combinaison de touches à chaud lorsque le contrôle de touche à chaud a le focus. L’utilisateur indique ensuite que cette tâche est terminée, peut-être en cliquant sur un bouton dans la boîte de dialogue.  
  
-   Lorsque votre programme est informé que l’utilisateur a sélectionné une touche d’accès rapide, il doit utiliser la fonction membre [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) pour récupérer les valeurs d’état clé et MAJ virtuels à partir du contrôle de clé à chaud.  
  
-   Une fois que vous savez ce que l’utilisateur a sélectionné de clé, vous pouvez définir la touche d’accès rapide à l’aide d’une des méthodes décrites dans [définition d’une touche d’accès rapide](../mfc/setting-a-hot-key.md).  
  
-   Si le contrôle de clé à chaud est dans une boîte de dialogue, elle et `CHotKeyCtrl` objet sera détruit automatiquement. Si pas, vous devez vous assurer que les deux le contrôle et la `CHotKeyCtrl` objet sont détruits correctement.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

