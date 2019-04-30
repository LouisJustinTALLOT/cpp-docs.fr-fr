---
title: Coupure des mots dans les contrôles RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
ms.openlocfilehash: e71643350ced5b8ecff7c8ac7829741cc3e8493b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399536"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Coupure des mots dans les contrôles RichEdit

Un contrôle rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) appelle une fonction appelée « procédure word saut » pour trouver des sauts entre les mots et déterminer où il peut rompre les lignes. Le contrôle utilise ces informations lors des opérations de retour et lors du traitement des combinaisons de touches CTRL + gauche et CTRL + flèche droite. Une application peut envoyer des messages à un contrôle RichEdit pour remplacer la procédure de césure de mots par défaut, pour récupérer des informations de césure de mots et pour déterminer quelle ligne un caractère donné tombe.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
