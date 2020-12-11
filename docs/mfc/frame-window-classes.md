---
description: 'En savoir plus sur : classes Frame-Window'
title: Classes de fenêtre frame
ms.date: 11/04/2016
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
ms.openlocfilehash: 888fae71bef2dd2e30e10c645e78ab981a30c6af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154953"
---
# <a name="frame-window-classes"></a>Classes de fenêtre frame

Chaque application possède une « fenêtre frame principale », une fenêtre de bureau qui contient généralement le nom de l’application dans sa légende. Chaque document possède généralement une « fenêtre frame de document ». Une fenêtre frame de document contient au moins une vue, qui présente les données du document.

## <a name="frame-windows-in-sdi-and-mdi-applications"></a>Fenêtres Frame dans les applications SDI et MDI

Pour une application SDI, il existe une fenêtre frame dérivée de la classe [CFrameWnd](reference/cframewnd-class.md). Cette fenêtre est à la fois la fenêtre frame principale et la fenêtre frame de document. Pour une application MDI, la fenêtre frame principale est dérivée de la classe [CMDIFrameWnd](reference/cmdiframewnd-class.md)et les fenêtres frame de document, qui sont des fenêtres enfants MDI, sont dérivées de la classe [CMDIChildWnd](reference/cmdichildwnd-class.md).

## <a name="use-the-frame-window-class-or-derive-from-it"></a>Utilisez la classe Frame-Window ou dérivez-la

Ces classes fournissent la plupart des fonctionnalités de fenêtre frame dont vous avez besoin pour vos applications. Dans des circonstances normales, le comportement et l’apparence par défaut qu’ils fournissent répondent à vos besoins. Si vous avez besoin de fonctionnalités supplémentaires, dérivez de ces classes.

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Classes de fenêtre frame créées par l’Assistant Application](frame-window-classes-created-by-the-application-wizard.md)

- [Styles de fenêtre frame](frame-window-styles-cpp.md)

- [Modification des styles d'une fenêtre créée par MFC](changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>Voir aussi

[Fenêtres Frame](frame-windows.md)
