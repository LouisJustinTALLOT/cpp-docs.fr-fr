---
title: Quand initialiser les objets CWnd | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee10a4632809a224028bfa482f80ed9e8a9334a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382871"
---
# <a name="when-to-initialize-cwnd-objects"></a>Quand initialiser les objets CWnd
Vous ne peut pas créer votre propre enfant windows ou appeler des fonctions API Windows dans le constructeur d’un `CWnd`-objet dérivé. C’est parce que le `HWND` pour la `CWnd` objet n’a pas encore été créé. L’initialisation de Windows plus spécifiques, telles que l’ajout de fenêtres enfants, doit être effectuée dans un [OnCreate](../mfc/reference/cwnd-class.md#oncreate) Gestionnaire de messages.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Création de fenêtres frame de document](../mfc/creating-document-frame-windows.md)  
  
-   [La création de document/vue](../mfc/document-view-creation.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de fenêtres frame](../mfc/using-frame-windows.md)

