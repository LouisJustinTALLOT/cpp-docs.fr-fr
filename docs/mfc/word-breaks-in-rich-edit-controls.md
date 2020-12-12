---
description: 'En savoir plus sur : césures de mots dans les contrôles RichEdit'
title: Coupure des mots dans les contrôles RichEdit
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
ms.openlocfilehash: 662a6b8441c4a9041a539acdabcab74f12d52782
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172711"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Coupure des mots dans les contrôles RichEdit

Un contrôle Rich Edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) appelle une fonction appelée « procédure d’arrêt de mot » pour rechercher des sauts entre les mots et déterminer où elle peut couper les lignes. Le contrôle utilise ces informations lors de l’exécution d’opérations de retour automatique à la ligne et lors du traitement des combinaisons de touches CTRL + gauche et CTRL + droite. Une application peut envoyer des messages à un contrôle Rich Edit pour remplacer la procédure de césure par défaut, pour récupérer des informations de césure de mots et pour déterminer la ligne sur laquelle se trouve un caractère donné.

## <a name="see-also"></a>Voir aussi

[Utilisation de CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
