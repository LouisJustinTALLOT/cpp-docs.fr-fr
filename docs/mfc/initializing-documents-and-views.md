---
title: Initialisation des documents et vues
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
ms.openlocfilehash: 0cf9faecbb7e0d74c2199a1a829aa68241e1c019
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264090"
---
# <a name="initializing-documents-and-views"></a>Initialisation des documents et vues

Les documents sont créés de deux manières différentes, donc votre classe de document doit prendre en charge les deux sens. Tout d’abord, l’utilisateur peut créer un nouveau document vide avec la commande fichier nouveau. Dans ce cas, initialisez le document dans la substitution de la [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) fonction membre de classe [CDocument](../mfc/reference/cdocument-class.md). En second lieu, l’utilisateur peut utiliser la commande Ouvrir dans le menu fichier pour créer un nouveau document dont le contenu est lus à partir d’un fichier. Dans ce cas, initialisez le document dans la substitution de la [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) fonction membre de classe `CDocument`. Si les deux initialisations sont identiques, vous pouvez appeler une fonction membre commune à partir de ces deux substitutions, ou `OnOpenDocument` peut appeler `OnNewDocument` pour initialiser un document propre, puis terminez l’opération d’ouverture.

Affichages sont créés une fois que les documents correspondants sont créés. Le meilleur moment pour initialiser une vue est une fois que l’infrastructure a fini de créer le document, la fenêtre frame et la vue. Vous pouvez initialiser votre vue en substituant le [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) fonction membre de [CView](../mfc/reference/cview-class.md). Si vous devez réinitialiser ou ajuster quoi que ce soit chaque fois que les modifications de document, vous pouvez remplacer [OnUpdate](../mfc/reference/cview-class.md#onupdate).

## <a name="see-also"></a>Voir aussi

[Initialisation et nettoyage des documents et vues](../mfc/initializing-and-cleaning-up-documents-and-views.md)
