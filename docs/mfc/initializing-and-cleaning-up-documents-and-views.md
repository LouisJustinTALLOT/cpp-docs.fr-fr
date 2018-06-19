---
title: Initialisation et nettoyage des Documents et vues | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializing documents [MFC]
- views [MFC], cleaning up
- documents [MFC], initializing
- documents [MFC], cleaning up
- views [MFC], initializing
- initializing objects [MFC], document objects
- document objects [MFC], life cycle of
- initializing views [MFC]
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f59dcfbdac4a2d5da732c5e7f8cfc78083bf843
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346361"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>Initialisation et nettoyage des documents et vues
Utilisez les instructions suivantes pour initialiser et nettoyer vos documents et les vues :  
  
-   L’infrastructure MFC initialise les documents et vues ; vous initialisez toutes les données que vous leur ajoutez.  
  
-   L’infrastructure procède au nettoyage des documents et vues fermer ; Vous devez libérer toute mémoire allouée dans le tas à partir de dans les fonctions membres de ces documents et vues.  
  
> [!NOTE]
>  Rappelez-vous que l’initialisation de l’application entière est préférable de la substitution de la [InitInstance](../mfc/reference/cwinapp-class.md#initinstance) fonction membre de classe `CWinApp`, et le nettoyage de l’application entière est préférable de la substitution de la `CWinApp`fonction membre [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance).  
  
 Cycle de vie d’un document (et sa fenêtre frame et vue ou vues) dans un formulaire MDI application est la suivante :  
  
1.  Lors de la création dynamique, le document est appelé.  
  
2.  Pour de chaque nouveau document, le document [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) ou [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) est appelée.  
  
3.  L’utilisateur interagit avec le document tout au long de sa durée de vie. Cela se produit généralement lorsque l’utilisateur travaille sur des données du document dans la vue, sélectionner et modifier les données. La vue passe les modifications au document pour le stockage et la mise à jour d’autres vues. Pendant ce temps, le document et la vue peuvent gérer des commandes.  
  
4.  Le framework appelle [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) pour supprimer les données spécifiques à un document.  
  
5.  Le destructeur du document est appelé.  
  
 Dans une application SDI, l’étape 1 est effectuée une seule fois, lorsque la création du document. Puis les étapes 2 à 4 sont exécutées plusieurs fois chaque fois qu'un nouveau document est ouvert. Le nouveau document réutilise l’objet document existant. Enfin, l’étape 5 est effectuée lorsque l’application se termine.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Initialisation des documents et vues](../mfc/initializing-documents-and-views.md)  
  
-   [Nettoyage des documents et vues](../mfc/cleaning-up-documents-and-views.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture document/vue](../mfc/document-view-architecture.md)

