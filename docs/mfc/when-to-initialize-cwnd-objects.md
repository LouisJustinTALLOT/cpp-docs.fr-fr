---
title: Quand initialiser les objets CWnd
ms.date: 11/04/2016
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
ms.openlocfilehash: c75745547846fbf6c7e01ecf473d4d6f366bd264
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548549"
---
# <a name="when-to-initialize-cwnd-objects"></a>Quand initialiser les objets CWnd

Vous ne pouvez pas créer vos propres enfants windows ou appeler toutes les fonctions API de Windows dans le constructeur d’un `CWnd`-objet dérivé. Il s’agit, car le `HWND` pour le `CWnd` objet n’a pas encore été créé. L’initialisation de Windows plus spécifiques, telles que l’ajout de fenêtres enfants, doit être effectuée dans un [OnCreate](../mfc/reference/cwnd-class.md#oncreate) Gestionnaire de messages.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Création de fenêtres frame de document](../mfc/creating-document-frame-windows.md)

- [Création d’un document/vue](../mfc/document-view-creation.md)

## <a name="see-also"></a>Voir aussi

[Utilisation de fenêtres frame](../mfc/using-frame-windows.md)

