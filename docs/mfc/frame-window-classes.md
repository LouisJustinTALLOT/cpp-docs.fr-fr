---
title: Classes de fenêtre frame | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame window classes [MFC], about frame window classes
- frame window classes [MFC]
- windows [MFC], MDI
- document frame windows [MFC], classes
- single document interface (SDI), frame windows
- window classes [MFC], frame
- MFC, frame windows
- MDI [MFC], frame windows
- classes [MFC], window
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ac60fb8d1b12708c7e64a91beb224ca436e5005
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404525"
---
# <a name="frame-window-classes"></a>Classes de fenêtre frame

Chaque application a une « fenêtre frame principale », une fenêtre du bureau qui a généralement le nom de l’application dans sa légende. Chaque document provient généralement d’une « fenêtre frame de document ». Une fenêtre frame de document contient au moins une vue, qui présente les données du document.

## <a name="frame-windows-in-sdi-and-mdi-applications"></a>Windows frame dans les Applications SDI et MDI

Pour une application SDI, il existe une fenêtre frame dérivée à partir de la classe [CFrameWnd](../mfc/reference/cframewnd-class.md). Cette fenêtre est la fenêtre frame principale et la fenêtre frame de document. Pour une application MDI, la fenêtre frame principale est dérivée à partir de la classe [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), et les fenêtres frame de document, qui sont des fenêtres enfants MDI, sont dérivées de la classe [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).

## <a name="use-the-frame-window-class-or-derive-from-it"></a>Utilisez la classe de fenêtre Frame, ou dériver à partir de celui-ci

Ces classes fournissent la plupart des fonctionnalités de fenêtre frame que vous avez besoin pour vos applications. Dans des circonstances normales, le comportement par défaut et leur apparence répondra à vos besoins. Si vous avez besoin des fonctionnalités supplémentaires, dérivez à partir de ces classes.

### <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Classes de fenêtre frame créées par l’Assistant Application](../mfc/frame-window-classes-created-by-the-application-wizard.md)

- [Styles de fenêtre frame](../mfc/frame-window-styles-cpp.md)

- [Modification des styles d’une fenêtre créée par MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>Voir aussi

[Fenêtres frame](../mfc/frame-windows.md)

