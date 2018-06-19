---
title: Contextes de périphérique | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OnPrepareDC method [MFC]
- windows [MFC], and device context
- drawing [MFC], device context
- CClientDC class [MFC], and GetDC method [MFC]
- drawing [MFC], in mouse and device contexts
- CDC class [MFC], objects
- device contexts [MFC]
- client areas
- CMetaFileDC class [MFC], and OnPrepareDC method [MFC]
- GDI objects [MFC], device contexts
- graphic objects [MFC], device contexts
- frame windows [MFC], device contexts
- metafiles and device contexts
- EndPaint method [MFC]
- printers [MFC], device contexts
- mouse [MFC], drawing and device contexts
- BeginPaint method, CPaintDC
- CPaintDC class [MFC], device context for painting
- windows [MFC], drawing directly into
- client areas, and device context
- device contexts [MFC], CDC class [MFC]
- user interface [MFC], device contexts
- device-independent drawing
- GetDC method and CClientDC class [MFC]
- CClientDC class [MFC], and ReleaseDC method [MFC]
- ReleaseDC method [MFC]
- device contexts [MFC], about device contexts
- drawing [MFC], directly into windows
- painting and device context
ms.assetid: d0cd51f1-f778-4c7e-bf50-d738d10433c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45a2f99001d45de71ca3ea8a525152d53d67ee64
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348568"
---
# <a name="device-contexts"></a>Contextes de périphérique
Un contexte de périphérique est une structure de données Windows contenant des informations sur les attributs de dessin d’un périphérique tel qu’un écran ou une imprimante. Tous les appels de dessin sont effectués via un objet de contexte de périphérique, qui encapsule les API Windows pour dessiner des lignes, formes et du texte. Contextes de périphérique permettent un dessin indépendant du périphérique dans Windows. Contextes de périphérique peuvent être utilisés pour dessiner à l’écran, l’imprimante ou un métafichier.  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md) objets encapsulent l’idiome commun de Windows, en appelant le `BeginPaint` (fonction), dans le contexte de périphérique de dessin, puis appeler la `EndPaint` (fonction). Le `CPaintDC` appels de constructeurs `BeginPaint` pour vous et le destructeur appelle `EndPaint`. Le processus simplifié consiste à créer le [CDC](../mfc/reference/cdc-class.md) de l’objet, dessiner, puis détruisez le `CDC` objet. Dans le framework, de même, ce processus est automatique. En particulier, votre `OnDraw` fonction reçoit un `CPaintDC` déjà préparé (via `OnPrepareDC`), et vous dessinez simplement dans celui-ci. Il est détruit par l’infrastructure et le contexte de périphérique sous-jacent est à Windows au retour de l’appel à votre `OnDraw` (fonction).  
  
 [CClientDC](../mfc/reference/cclientdc-class.md) objets encapsulent l’utilisation d’un contexte de périphérique qui représente uniquement la zone cliente d’une fenêtre. Le `CClientDC` constructeur appelle la `GetDC` (fonction) et le destructeur appelle la `ReleaseDC` (fonction). [CWindowDC](../mfc/reference/cwindowdc-class.md) objets encapsulent un contexte de périphérique qui représente la fenêtre entière, y compris son cadre.  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md) objets encapsulent le dessin dans un métafichier Windows. Contrairement à la `CPaintDC` passé à `OnDraw`, vous devez appeler dans ce cas [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) vous-même.  
  
## <a name="mouse-drawing"></a>Dessin de la souris  
 La plupart de dessin dans un programme d’infrastructure et par conséquent, la plupart du travail contexte de périphérique — est effectuée dans la vue `OnDraw` fonction membre. Toutefois, vous pouvez toujours utiliser des objets de contexte de périphérique à d’autres fins. Par exemple, pour fournir des commentaires de suivi des mouvements de la souris dans une vue, vous devez dessiner directement dans la vue sans attendre `OnDraw` à appeler.  
  
 Dans ce cas, vous pouvez utiliser un [CClientDC](../mfc/reference/cclientdc-class.md) objet de contexte de périphérique à dessiner directement dans la vue.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Contextes de périphérique (définition)](http://msdn.microsoft.com/library/windows/desktop/dd183553)  
  
-   [Dessin dans une vue](../mfc/drawing-in-a-view.md)  
  
-   [Interprétation de l’entrée utilisateur via une vue](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [Lignes et des courbes](http://msdn.microsoft.com/library/windows/desktop/dd145028)  
  
-   [Formes pleines](http://msdn.microsoft.com/library/windows/desktop/dd162714)  
  
-   [Polices et texte](http://msdn.microsoft.com/library/windows/desktop/dd144819)  
  
-   [Couleurs](http://msdn.microsoft.com/library/windows/desktop/dd183450)  
  
-   [Transformations et des espaces de coordonnées](http://msdn.microsoft.com/library/windows/desktop/dd183475)  
  
## <a name="see-also"></a>Voir aussi  
 [Objets fenêtre](../mfc/window-objects.md)

