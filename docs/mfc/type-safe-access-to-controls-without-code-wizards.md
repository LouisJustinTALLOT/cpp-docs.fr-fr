---
title: Accès de type sécurisé aux contrôles sans Assistants Code
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
ms.openlocfilehash: 5b4b604bf42a327edf3ac7a83dcfc42a5e0d8c54
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180809"
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>Accès de type sécurisé aux contrôles sans Assistants Code

La première approche pour la création d’accès de type sécurisé aux contrôles utilise une fonction membre inline pour effectuer un cast de type de retour de la classe `CWnd`de `GetDlgItem` fonction membre vers le type de contrôle C++ approprié, comme dans cet exemple :

[!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]

Vous pouvez ensuite utiliser cette fonction membre pour le contrôle d’accès de manière sécurisée avec un code similaire à ce qui suit :

[!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Accès de type sécurisé aux contrôles d’une boîte de dialogue](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Accès de type sécurisé aux contrôles avec Assistants Code](../mfc/type-safe-access-to-controls-with-code-wizards.md)
