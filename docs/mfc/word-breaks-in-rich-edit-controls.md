---
title: Coupure des mots dans les contrôles RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
ms.openlocfilehash: efe4a0a2c06c14d913d43c51d1f0100f27c6a537
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632594"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Coupure des mots dans les contrôles RichEdit

Un contrôle rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) appelle une fonction appelée « procédure word saut » pour trouver des sauts entre les mots et déterminer où il peut rompre les lignes. Le contrôle utilise ces informations lors des opérations de retour et lors du traitement des combinaisons de touches CTRL + gauche et CTRL + flèche droite. Une application peut envoyer des messages à un contrôle RichEdit pour remplacer la procédure de césure de mots par défaut, pour récupérer des informations de césure de mots et pour déterminer quelle ligne un caractère donné tombe.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

