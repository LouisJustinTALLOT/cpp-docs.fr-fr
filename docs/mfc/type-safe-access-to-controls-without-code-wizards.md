---
title: Accès de type sécurisé aux contrôles sans Assistants Code | Documents Microsoft
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
ms.openlocfilehash: bb861995c16411bb58e3051c5ffc78f75931ae8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385763"
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>Accès de type sécurisé aux contrôles sans Assistants Code
La première approche pour la création d’accès de type sécurisé aux contrôles utilise une fonction membre inline pour effectuer un cast de type de retour de la classe `CWnd`de `GetDlgItem` fonction membre vers le type de contrôle C++ approprié, comme dans cet exemple :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]  
  
 Vous pouvez ensuite utiliser cette fonction membre pour accéder au contrôle de manière sécurisée avec un code similaire à ce qui suit :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Accès de type sécurisé aux contrôles dans une boîte de dialogue](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [Accès de type sécurisé aux contrôles avec Assistants Code](../mfc/type-safe-access-to-controls-with-code-wizards.md)

