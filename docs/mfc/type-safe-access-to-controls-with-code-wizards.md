---
title: Accès de type sécurisé aux contrôles avec Assistants Code | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88f86a8f22bae990261be5150755a26d50d4bef8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950459"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Accès de type sécurisé aux contrôles avec Assistants Code
Si vous êtes familiarisé avec les fonctionnalités DDX, vous pouvez utiliser la propriété du contrôle dans le [Assistant Ajout de Variable membre](../ide/add-member-variable-wizard.md) pour créer l’accès de type sécurisé. Cette approche est plus facile que la création de contrôles sans Assistants code.  
  
 Si vous souhaitez simplement accéder à la valeur d’un contrôle, DDX la fournit. Si vous voulez plus qu’accéder à la valeur d’un contrôle, utilisez l’Assistant Ajout de Variable membre pour ajouter une variable membre de la classe appropriée à votre classe de boîte de dialogue. Attachez cette variable membre à la propriété du contrôle.  
  
 Variables membres peuvent avoir une propriété de contrôle au lieu d’une propriété de valeur. La propriété de valeur fait référence au type de données retournées par le contrôle, telles que `CString` ou **int**. La propriété Control permet un accès direct au contrôle via un membre de données dont le type est une des classes de contrôles dans MFC, telles que `CButton` ou `CEdit`.  
  
> [!NOTE]
>  Pour un contrôle donné, vous pouvez, si vous le souhaitez, avoir plusieurs variables membres avec la propriété Value et au plus une variable membre avec la propriété du contrôle. Vous pouvez avoir qu’un seul objet MFC mappé à un contrôle, car plusieurs objets attachés à un contrôle, ou toute autre fenêtre, peuvent engendrer une ambiguïté dans la table des messages.  
  
 Vous pouvez utiliser cet objet pour appeler des fonctions membres de l’objet contrôle. Ces appels affectent le contrôle dans la boîte de dialogue. Par exemple, pour un contrôle de case à cocher représenté par une variable *m_Checkbox*, de type `CButton`, vous pouvez appeler :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]  
  
 Ici, la variable membre *m_Checkbox* remplit la même fonction que la fonction membre `GetMyCheckbox` illustré [accès de Type sécurisé aux contrôles sans Assistants de Code](../mfc/type-safe-access-to-controls-without-code-wizards.md). Si la case à cocher n’est pas une case à cocher automatique, vous déclenchera un gestionnaire dans votre classe de boîte de dialogue pour le message de notification de contrôle BN_CLICKED lorsque le bouton est activé.  
  
 Pour plus d’informations sur les contrôles, consultez [contrôles](../mfc/controls-mfc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Accès de type sécurisé aux contrôles dans une boîte de dialogue](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)   
 [Accès de type sécurisé aux contrôles sans Assistants Code](../mfc/type-safe-access-to-controls-without-code-wizards.md)

