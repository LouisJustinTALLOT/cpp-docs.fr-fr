---
description: 'En savoir plus sur : contextes de périphérique'
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
ms.openlocfilehash: 725387ad3aa3f099c72c82aecd14d89bad7168bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97261591"
---
# <a name="device-contexts"></a>Contextes de périphérique

Un contexte de périphérique est une structure de données Windows contenant des informations sur les attributs de dessin d’un appareil tel qu’un affichage ou une imprimante. Tous les appels de dessin sont effectués à l’aide d’un objet de contexte d’appareil, qui encapsule les API Windows pour dessiner des lignes, des formes et du texte. Les contextes de périphérique permettent un dessin indépendant du périphérique dans Windows. Les contextes de périphérique peuvent être utilisés pour dessiner à l’écran, à l’imprimante ou à un métafichier.

Les objets [CPaintDC](reference/cpaintdc-class.md) encapsulent l’idiome commun de Windows, l’appel de la `BeginPaint` fonction, puis le dessin dans le contexte de périphérique, puis l’appel de la `EndPaint` fonction. Le `CPaintDC` constructeur `BeginPaint` vous appelle pour vous, et le destructeur appelle `EndPaint` . Le processus simplifié consiste à créer l’objet [CDC](reference/cdc-class.md) , à dessiner, puis à détruire l' `CDC` objet. Dans l’infrastructure, une grande partie de ce processus est automatisée. En particulier, votre `OnDraw` fonction reçoit un `CPaintDC` déjà préparé (via) et vous la configurez `OnPrepareDC` simplement. Elle est détruite par l’infrastructure et le contexte de périphérique sous-jacent est distribué à Windows lors du retour de l’appel à votre `OnDraw` fonction.

Les objets [CClientDC](reference/cclientdc-class.md) encapsulent l’utilisation d’un contexte de périphérique qui représente uniquement la zone cliente d’une fenêtre. Le `CClientDC` constructeur appelle la `GetDC` fonction et le destructeur appelle la `ReleaseDC` fonction. Les objets [CWindowDC](reference/cwindowdc-class.md) encapsulent un contexte de périphérique qui représente la fenêtre entière, y compris son frame.

Les objets [CMetaFileDC](reference/cmetafiledc-class.md) encapsulent le dessin dans un métafichier Windows. Contrairement au `CPaintDC` passé à `OnDraw` , vous devez dans ce cas appeler [OnPrepareDC](reference/cview-class.md#onpreparedc) vous-même.

## <a name="mouse-drawing"></a>Dessin de la souris

La plupart des dessins dans un programme d’infrastructure, et par conséquent la plupart du travail de contexte de périphérique, s’effectuent dans la fonction membre de la vue `OnDraw` . Toutefois, vous pouvez toujours utiliser des objets de contexte d’appareil à d’autres fins. Par exemple, pour fournir des commentaires de suivi pour le déplacement de la souris dans une vue, vous devez dessiner directement dans la vue sans attendre que `OnDraw` soit appelé.

Dans ce cas, vous pouvez utiliser un objet de contexte d’appareil [CClientDC](reference/cclientdc-class.md) pour dessiner directement dans la vue.

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Contextes de périphérique (définition)](/windows/win32/gdi/device-contexts)

- [Dessin dans une vue](drawing-in-a-view.md)

- [Interprétation de l’entrée utilisateur via une vue](interpreting-user-input-through-a-view.md)

- [Lignes et courbes](/windows/win32/gdi/lines-and-curves)

- [Formes remplies](/windows/win32/gdi/filled-shapes)

- [Polices et texte](/windows/win32/gdi/fonts-and-text)

- [Couleurs](/windows/win32/gdi/colors)

- [Espaces de coordonnées et transformations](/windows/win32/gdi/coordinate-spaces-and-transformations)

## <a name="see-also"></a>Voir aussi

[Objets de fenêtre](window-objects.md)
