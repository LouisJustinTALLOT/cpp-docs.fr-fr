---
title: Accès de type sécurisé aux contrôles avec Assistants Code
ms.date: 11/04/2016
helpviewer_keywords:
- DDX (dialog data exchange), access to controls
- code wizards
- dialog boxes [MFC], access to controls
- dialog box controls [MFC], accessing
ms.assetid: b8874393-ee48-4124-8d78-e3648a7e29b9
ms.openlocfilehash: b49c1b6f21dfe5270e40649241812320303ad411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370913"
---
# <a name="type-safe-access-to-controls-with-code-wizards"></a>Accès de type sécurisé aux contrôles avec Assistants Code

Si vous connaissez les fonctionnalités DDX, vous pouvez utiliser la propriété Control dans [l’Assistant Variable De membre Ajouter](../ide/add-member-variable-wizard.md) pour créer un accès sans danger. Cette approche est plus facile que de créer des contrôles sans assistants de code.

Si vous voulez simplement accéder à la valeur d’un contrôle, DDX le fournit. Si vous voulez faire plus que d’accéder à la valeur d’un contrôle, utilisez l’assistant variable Add Member pour ajouter une variable de membre de la classe appropriée à votre classe de dialogue. Attachez cette variable de membre à la propriété Control.

Les variables des membres peuvent avoir une propriété de contrôle au lieu d’une propriété de valeur. La propriété Value se réfère au type de données `CString` retournées du contrôle, telles que ou **int**. La propriété Control permet un accès direct au contrôle par l’intermédiaire d’un `CButton` `CEdit`membre de données dont le type est l’une des classes de contrôle de MFC, comme ou .

> [!NOTE]
> Pour un contrôle donné, vous pouvez, si vous le souhaitez, avoir plusieurs variables de membre avec la propriété De valeur et tout au plus une variable de membre avec la propriété de contrôle. Vous ne pouvez avoir qu’un seul objet MFC cartographié à un contrôle parce que plusieurs objets attachés à un contrôle, ou toute autre fenêtre, conduirait à une ambiguïté dans la carte de message.

Vous pouvez utiliser cet objet pour appeler n’importe quelle fonction de membre pour l’objet de commande. De tels appels affectent le contrôle dans la boîte de dialogue. Par exemple, pour un contrôle de la *m_Checkbox*case à cocher `CButton`représenté par une m_Checkbox variable, du type, vous pouvez appeler :

[!code-cpp[NVC_MFCControlLadenDialog#52](../mfc/codesnippet/cpp/type-safe-access-to-controls-with-code-wizards_1.cpp)]

Ici, la variable du membre *m_Checkbox* sert le `GetMyCheckbox` même but que la fonction membre indiquée dans [Type-Safe Access to Controls Without Code Wizards](../mfc/type-safe-access-to-controls-without-code-wizards.md). Si la case à cocher n’est pas une case à cocher automatique, vous auriez toujours besoin d’un gestionnaire dans votre classe de dialogue pour le message de contrôle-notification BN_CLICKED lorsque le bouton est cliqué.

Pour plus d’informations sur les contrôles, voir [Contrôles](../mfc/controls-mfc.md).

## <a name="see-also"></a>Voir aussi

[Accès de type-sûr aux contrôles dans une boîte de dialogue](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Utilisation des boîtes de dialogue dans MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Accès de type sécurisé aux contrôles sans Assistants Code](../mfc/type-safe-access-to-controls-without-code-wizards.md)
