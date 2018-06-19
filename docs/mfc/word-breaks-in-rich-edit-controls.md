---
title: Coupure des mots dans les contrôles RichEdit | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 373a30ed4a327cff99cb3cfce873707314608b57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382958"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Coupure des mots dans les contrôles RichEdit
Un contrôle RichEdit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) appelle une fonction appelée « procédure word saut » pour trouver des coupures entre les mots et déterminer où il peut passer des lignes. Le contrôle utilise ces informations lorsque vous effectuez des opérations de retour et lors du traitement des combinaisons de touches CTRL + gauche et CTRL + droite. Une application peut envoyer des messages à un contrôle RichEdit pour remplacer la procédure à la césure par défaut, pour récupérer les informations de césure de mots et de déterminer quelle ligne un caractère donné tombe.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

