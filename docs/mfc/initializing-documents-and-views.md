---
title: Initialisation des Documents et vues | Documents Microsoft
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
ms.openlocfilehash: 43610a08d5a3713cc40de0a2279286735a27d1da
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928180"
---
# <a name="initializing-documents-and-views"></a>Initialisation des documents et vues
Les documents sont créés de deux manières différentes, votre classe de document doit prendre en charge les deux sens. Tout d’abord, l’utilisateur peut créer un nouveau document vide avec la commande fichier nouveau. Dans ce cas, initialisez le document dans la substitution de la [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) fonction membre de classe [CDocument](../mfc/reference/cdocument-class.md). En second lieu, l’utilisateur peut utiliser la commande Ouvrir dans le menu fichier pour créer un nouveau document dont le contenu est lus à partir d’un fichier. Dans ce cas, initialisez le document dans la substitution de la [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) fonction membre de classe `CDocument`. Si les deux initialisations sont identiques, vous pouvez appeler une fonction membre commune à partir des deux remplacements, ou `OnOpenDocument` peut appeler `OnNewDocument` pour initialiser un document propre et puis de terminer l’opération d’ouverture.  
  
 Vues sont créées après la création de leurs documents. Le meilleur moment pour initialiser une vue est une fois que l’infrastructure a fini de créer le document, la fenêtre frame et la vue. Vous pouvez initialiser votre vue en remplaçant le [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) fonction membre de [CView](../mfc/reference/cview-class.md). Si vous devez réinitialiser ou ajuster tout élément chaque fois que les modifications de document, vous pouvez substituer [OnUpdate](../mfc/reference/cview-class.md#onupdate).  
  
## <a name="see-also"></a>Voir aussi  
 [Initialisation et nettoyage des documents et vues](../mfc/initializing-and-cleaning-up-documents-and-views.md)

