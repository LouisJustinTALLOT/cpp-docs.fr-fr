---
title: Accès de type sécurisé aux contrôles avec Assistants Code
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: ee7c49f75dcdc2b6c32f2b391ace7260b46d197b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507896"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Accès de type sécurisé aux contrôles avec Assistants Code

Si vous êtes familiarisé avec les fonctionnalités DDX, vous pouvez utiliser la propriété Control dans l' [Assistant Ajout de variable membre](../ide/adding-a-member-variable-visual-cpp.md#add-member-variable-wizard) pour créer un accès de type sécurisé. Cette approche est plus facile que de créer des contrôles sans assistants code.

Si vous souhaitez simplement accéder à la valeur d’un contrôle, DDX le fournit. Si vous souhaitez faire plus que accéder à la valeur d’un contrôle, utilisez l’Assistant Ajout de variable membre pour ajouter une variable membre de la classe appropriée à votre classe de boîte de dialogue. Attachez cette variable membre à la propriété de contrôle.

Les variables membres peuvent avoir une propriété de contrôle au lieu d’une propriété de valeur. La propriété Value fait référence au type de données retourné par le contrôle, tel que `CString` ou **`int`** . La propriété de contrôle permet un accès direct au contrôle via un membre de données dont le type est l’une des classes de contrôle dans MFC, tel que `CButton` ou `CEdit` .

> [!NOTE]
> Pour un contrôle donné, vous pouvez, si vous le souhaitez, avoir plusieurs variables membres avec la propriété Value et au plus une variable membre avec la propriété Control. Vous ne pouvez avoir qu’un seul objet MFC mappé à un contrôle, car plusieurs objets attachés à un contrôle, ou toute autre fenêtre, aboutissent à une ambiguïté dans la table des messages.

Vous pouvez utiliser cet objet pour appeler n’importe quelle fonction membre pour l’objet de contrôle. De tels appels affectent le contrôle dans la boîte de dialogue. Par exemple, pour un contrôle de case à cocher représenté par une variable *m_Checkbox*, de type `CButton` , vous pouvez appeler :

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

Ici, la variable membre *m_Checkbox* remplit le même objectif que la fonction membre `GetMyCheckbox` indiquée dans l’accès de [type sécurisé aux contrôles sans assistants code](../mfc/type-safe-access-to-controls-without-code-wizards.md). Si la case à cocher n’est pas une case à cocher automatique, vous avez toujours besoin d’un gestionnaire dans votre classe de boîte de dialogue pour le BN_CLICKED message de notification de contrôle lorsque l’utilisateur clique sur le bouton.

Pour plus d’informations sur les contrôles, consultez [contrôles](../mfc/controls-mfc.md).

## <a name="see-also"></a>Voir aussi

[Accès de type sécurisé aux contrôles dans une boîte de dialogue](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Utilisation des boîtes de dialogue dans MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Accès de type sécurisé aux contrôles sans assistants code](../mfc/type-safe-access-to-controls-without-code-wizards.md)
