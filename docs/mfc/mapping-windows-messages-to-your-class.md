---
title: Mappage des Messages Windows à votre classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 398888a858165197c6e35be791169a9311f3014b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346267"
---
# <a name="mapping-windows-messages-to-your-class"></a>Mappage des messages Windows à votre classe
Si vous avez besoin de votre boîte de dialogue pour traiter les messages Windows, remplacez les fonctions de gestionnaire approprié. Pour ce faire, utilisez la fenêtre Propriétés pour [mapper les messages](../mfc/reference/mapping-messages-to-functions.md) à la classe de boîte de dialogue. Il écrit une entrée de table des messages pour chaque message et ajoute les fonctions membres de gestionnaire de messages à la classe. Utilisez l’éditeur de code source Visual C++ pour écrire du code dans les gestionnaires de messages.  
  
 Vous pouvez également remplacer des fonctions membres de [CDialog](../mfc/reference/cdialog-class.md) et ses classes de base, en particulier [CWnd](../mfc/reference/cwnd-class.md).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Mappage et la gestion des messages](../mfc/message-handling-and-mapping.md)  
  
-   [Fonctions membres couramment substituées](../mfc/commonly-overridden-member-functions.md)  
  
-   [Fonctions membres couramment ajoutées](../mfc/commonly-added-member-functions.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Boîtes de dialogue](../mfc/dialog-boxes.md)   
 [Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)

