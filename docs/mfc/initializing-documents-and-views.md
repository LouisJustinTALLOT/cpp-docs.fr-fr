---
title: Initialisation des Documents et vues | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6a6f989b8c6b19c78cf9ad508d18e9592bb9305
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417395"
---
# <a name="initializing-documents-and-views"></a>Initialisation des documents et vues

Les documents sont créés de deux manières différentes, donc votre classe de document doit prendre en charge les deux sens. Tout d’abord, l’utilisateur peut créer un nouveau document vide avec la commande fichier nouveau. Dans ce cas, initialisez le document dans la substitution de la [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) fonction membre de classe [CDocument](../mfc/reference/cdocument-class.md). En second lieu, l’utilisateur peut utiliser la commande Ouvrir dans le menu fichier pour créer un nouveau document dont le contenu est lus à partir d’un fichier. Dans ce cas, initialisez le document dans la substitution de la [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) fonction membre de classe `CDocument`. Si les deux initialisations sont identiques, vous pouvez appeler une fonction membre commune à partir de ces deux substitutions, ou `OnOpenDocument` peut appeler `OnNewDocument` pour initialiser un document propre, puis terminez l’opération d’ouverture.

Affichages sont créés une fois que les documents correspondants sont créés. Le meilleur moment pour initialiser une vue est une fois que l’infrastructure a fini de créer le document, la fenêtre frame et la vue. Vous pouvez initialiser votre vue en substituant le [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) fonction membre de [CView](../mfc/reference/cview-class.md). Si vous devez réinitialiser ou ajuster quoi que ce soit chaque fois que les modifications de document, vous pouvez remplacer [OnUpdate](../mfc/reference/cview-class.md#onupdate).

## <a name="see-also"></a>Voir aussi

[Initialisation et nettoyage des documents et vues](../mfc/initializing-and-cleaning-up-documents-and-views.md)

