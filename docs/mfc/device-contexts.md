---
title: Contextes de périphérique
ms.date: 11/04/2016
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
ms.openlocfilehash: 105e438a9ed3e8f7de7edc813fec516c0e99700a
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694684"
---
# <a name="device-contexts"></a>Contextes de périphérique

Un contexte de périphérique est une structure de données Windows contenant des informations sur les attributs de dessin d’un appareil tel qu’un écran ou une imprimante. Tous les appels de dessins sont effectués via un objet de contexte de périphérique, qui encapsule les API Windows pour le dessin de lignes, de formes et de texte. Contextes de périphérique permettent un dessin indépendant du périphérique dans Windows. Contextes de périphérique peuvent être utilisés pour dessiner à l’écran, à l’imprimante ou d’un métafichier.

[CPaintDC](../mfc/reference/cpaintdc-class.md) objets encapsulent l’idiome commun de Windows, en appelant le `BeginPaint` (fonction), dessin dans le contexte de périphérique, puis appeler la `EndPaint` (fonction). Le `CPaintDC` constructeur appelle `BeginPaint` pour vous et le destructeur appelle `EndPaint`. Le processus simplifié consiste à créer le [CDC](../mfc/reference/cdc-class.md) de l’objet, dessiner, puis détruisez le `CDC` objet. Dans le framework, une grande partie de la même ce processus est automatisée. En particulier, votre `OnDraw` fonction reçoit un `CPaintDC` déjà préparé (via `OnPrepareDC`), et vous simplement dessinez dans celle-ci. Il est détruit par l’infrastructure et le contexte de périphérique sous-jacent est à Windows au retour de l’appel à votre `OnDraw` (fonction).

[CClientDC](../mfc/reference/cclientdc-class.md) objets encapsulent l’utilisation d’un contexte de périphérique qui représente uniquement la zone cliente d’une fenêtre. Le `CClientDC` constructeur appelle la `GetDC` (fonction) et le destructeur appelle le `ReleaseDC` (fonction). [CWindowDC](../mfc/reference/cwindowdc-class.md) objets encapsulent un contexte de périphérique qui représente la fenêtre entière, y compris son cadre.

[CMetaFileDC](../mfc/reference/cmetafiledc-class.md) objets encapsulent le dessin dans un métafichier Windows. Contrairement à la `CPaintDC` passé à `OnDraw`, vous devez appeler dans ce cas [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) vous-même.

## <a name="mouse-drawing"></a>Dessin de la souris

La plupart des dessin dans un programme de framework et par conséquent, la plupart des travaux de contexte de périphérique — est effectuée dans la vue `OnDraw` fonction membre. Toutefois, vous pouvez toujours utiliser des objets de contexte de périphérique à d’autres fins. Par exemple, pour fournir des commentaires de suivi pour le déplacement de la souris dans une vue, vous devez dessiner directement dans la vue sans attendre `OnDraw` à appeler.

Dans ce cas, vous pouvez utiliser un [CClientDC](../mfc/reference/cclientdc-class.md) objet de contexte de périphérique sur lequel dessiner directement dans la vue.

### <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Contextes de périphérique (définition)](/windows/desktop/gdi/device-contexts)

- [Dessin dans une vue](../mfc/drawing-in-a-view.md)

- [Interprétation de l’entrée utilisateur via une vue](../mfc/interpreting-user-input-through-a-view.md)

- [Lignes et courbes](/windows/desktop/gdi/lines-and-curves)

- [Remplissage de formes](/windows/desktop/gdi/filled-shapes)

- [Polices et texte](/windows/desktop/gdi/fonts-and-text)

- [Couleurs](/windows/desktop/gdi/colors)

- [Transformations et les espaces de coordonnées](/windows/desktop/gdi/coordinate-spaces-and-transformations)

## <a name="see-also"></a>Voir aussi

[Objets fenêtre](../mfc/window-objects.md)

