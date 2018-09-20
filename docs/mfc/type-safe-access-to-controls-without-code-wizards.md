---
title: Accès de type sécurisé aux contrôles sans Assistants Code | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2685c946b9ee1c738ee83f9413b7fd955857febb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438338"
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>Accès de type sécurisé aux contrôles sans Assistants Code

La première approche pour la création d’accès de type sécurisé aux contrôles utilise une fonction membre inline pour effectuer un cast de type de retour de la classe `CWnd`de `GetDlgItem` fonction membre vers le type de contrôle C++ approprié, comme dans cet exemple :

[!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]

Vous pouvez ensuite utiliser cette fonction membre pour le contrôle d’accès de manière sécurisée avec un code similaire à ce qui suit :

[!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Accès de type sécurisé aux contrôles d’une boîte de dialogue](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Accès de type sécurisé aux contrôles avec Assistants Code](../mfc/type-safe-access-to-controls-with-code-wizards.md)

