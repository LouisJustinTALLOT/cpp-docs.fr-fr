---
description: 'En savoir plus sur les éléments suivants : Type-Safe l’accès aux contrôles sans assistants code'
title: Accès de type sécurisé aux contrôles sans Assistants Code
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
ms.openlocfilehash: 1e59353a17f0d841cd69fa64f792dcc7cdbfa6ad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263775"
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>Accès de type sécurisé aux contrôles sans Assistants Code

La première approche pour créer un accès de type sécurisé aux contrôles utilise une fonction membre Inline pour effectuer un cast du type de retour de la fonction membre de la classe `CWnd` `GetDlgItem` vers le type de contrôle C++ approprié, comme dans cet exemple :

[!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]

Vous pouvez ensuite utiliser cette fonction membre pour accéder au contrôle de façon sécurisée avec du code similaire à ce qui suit :

[!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Accès de type sécurisé aux contrôles dans une boîte de dialogue](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Accès de type sécurisé aux contrôles à l’aide des assistants code](../mfc/type-safe-access-to-controls-with-code-wizards.md)
