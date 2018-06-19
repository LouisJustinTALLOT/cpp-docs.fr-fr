---
title: Les Types associés aux objets d’Interface utilisateur de messages | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.uiobject.msgs
dev_langs:
- C++
helpviewer_keywords:
- message types and user interface objects [MFC]
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14a2309556ca6c5204247ccbe916aebe472a1da1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373422"
---
# <a name="message-types-associated-with-user-interface-objects"></a>Types de messages associés aux objets interface utilisateur
Le tableau suivant présente les types d’objets que vous pouvez utiliser et les types de messages qui s’y rapportent.  
  
### <a name="user-interface-objects-and-associated-messages"></a>Objets d’Interface utilisateur et les Messages associés  
  
|ID d’objet|Messages|  
|---------------|--------------|  
|Nom de classe, qui représente la fenêtre|Messages Windows appropriés pour une [CWnd](../../mfc/reference/cwnd-class.md)-classe dérivée : une boîte de dialogue, la fenêtre, la fenêtre enfant, la fenêtre enfant MDI ou fenêtre frame au premier plan.|  
|Identificateur de menu ou d’accélérateur|-   **COMMANDE** message (exécute la fonction de programme).<br />-   **UPDATE_COMMAND_UI** message (dynamiquement des mises à jour l’élément de menu).|  
|Identificateur de contrôle|Messages de notification de contrôle pour le type de contrôle sélectionné.|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage des Messages à des fonctions](../../mfc/reference/mapping-messages-to-functions.md)   
 [Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Ajout d’une classe](../../ide/adding-a-class-visual-cpp.md)   
 [Ajout d’une fonction membre](../../ide/adding-a-member-function-visual-cpp.md)   
 [Ajout d’une Variable membre](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Une fonction virtuelle de substitution](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Gestionnaire de messages MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navigation dans la Structure de classe](../../ide/navigating-the-class-structure-visual-cpp.md)
