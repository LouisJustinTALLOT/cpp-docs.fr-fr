---
description: En savoir plus sur les objets de fenêtre
title: Objets fenêtres
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], window
- Windows window [MFC]
- MFC, windows
- frame windows [MFC], C++ window objects
- window objects [MFC]
- windows [MFC], C++ window objects
- window messages [MFC]
- HWND
- messages [MFC], Windows
- Visual C++, window objects [MFC]
- HWND, window objects [MFC]
ms.assetid: 28b33ce2-af05-4617-9d03-1cb9a02be687
ms.openlocfilehash: 5a7755dfecc8205279785a6452b04c3f8dc429d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214492"
---
# <a name="window-objects"></a>Objets fenêtres

MFC fournit la classe [CWnd](../mfc/reference/cwnd-class.md) pour encapsuler le `HWND` handle d’une fenêtre. L'objet `CWnd` est un objet Windows C++, distinct de `HWND` qui représente une fenêtre Windows mais qui le contient. Utilisez `CWnd` pour dériver vos classes de la fenêtre enfant, ou utilisez l'une des nombreuses classes MFC dérivées de `CWnd`. La classe `CWnd` est la classe de base pour toutes les fenêtres, en particulier les fenêtres frame, les boîtes de dialogue, les fenêtres enfants, les contrôles et les barres de contrôle, telles que les barres d'outils. Une bonne compréhension de [la relation entre un objet fenêtre C++ et un HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md) est essentielle pour une programmation efficace avec MFC.

MFC fournit certaines fonctionnalités et gestion de fenêtres par défaut, mais vous pouvez dériver votre propre classe à partir de `CWnd` et utiliser ses fonctions membre pour personnaliser les fonctionnalités fournies. Vous pouvez créer des fenêtres enfants en créant un `CWnd` objet et en appelant sa fonction membre [Create](../mfc/reference/cwnd-class.md#create) , puis personnaliser les fenêtres enfants à l’aide de `CWnd` fonctions membres. Vous pouvez incorporer des objets dérivés de [CView](../mfc/reference/cview-class.md), tels que des vues de formulaire ou des arborescences, dans une fenêtre frame. Vous pouvez prendre en charge plusieurs vues de vos documents par le biais de volets Splitter, fournis par la classe [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).

Chaque objet dérivé de la classe `CWnd` contient une table de messages, dans laquelle vous pouvez mapper des messages Windows ou des ID de commande à vos propres gestionnaires.

La documentation générale sur la programmation pour Windows constitue une bonne ressource pour apprendre à utiliser les fonctions membres de `CWnd`, qui encapsulent les API `HWND`.

## <a name="functions-for-operating-on-a-cwnd"></a>Fonctions pour une exécution CWnd

`CWnd` et ses [classes de fenêtre dérivées](../mfc/derived-window-classes.md) fournissent des constructeurs, des destructeurs et des fonctions membres pour initialiser l’objet, créer les structures Windows sous-jacentes et accéder au encapsulé `HWND` . `CWnd` fournit également des fonctions membres qui encapsulent les API Windows pour envoyer des messages, accéder à l'état de la fenêtre, convertir des coordonnées, mettre à jour, défiler, accéder au Presse-papiers, et bien d'autres tâches. La plupart des API de gestion de fenêtre Windows qui prennent un argument `HWND` sont encapsulées en fonctions membres de `CWnd`. Les noms des fonctions et leurs paramètres sont conservés dans la fonction membre de `CWnd`. Pour plus d’informations sur les API Windows encapsulées par `CWnd` , consultez la classe [CWnd](../mfc/reference/cwnd-class.md).

## <a name="cwnd-and-windows-messages"></a>Messages Windows et CWnd

L’un des principaux objectifs de `CWnd` est de fournir une interface pour gérer les messages Windows, tels que WM_PAINT ou WM_MOUSEMOVE. La plupart des fonctions membres de `CWnd` sont des gestionnaires pour les messages standard, ceux qui commencent par l’identificateur **afx_msg** et le préfixe « on », tels que `OnPaint` et `OnMouseMove` . La [gestion des messages et le mappage](../mfc/message-handling-and-mapping.md) couvrent en détail les messages et la gestion des messages. Les informations s'appliquent identiquement aux fenêtres de le framework et celles que vous créez vous-même à des fins spéciales.

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Relation entre un objet de fenêtre C++ et un HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)

- [Classes de fenêtre dérivées](../mfc/derived-window-classes.md)

- [Création de fenêtres](../mfc/creating-windows.md)

- [Destruction d’objets fenêtres](../mfc/destroying-window-objects.md)

- [Détachement d’un CWnd de son HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [Utilisation d'objets de fenêtre](../mfc/working-with-window-objects.md)

- [Contextes de périphérique](../mfc/device-contexts.md): objets qui rendent l’appareil de dessin Windows indépendant

- [Objets graphiques](../mfc/graphic-objects.md): stylets, pinceaux, polices, images bitmap, palettes, régions

## <a name="see-also"></a>Voir aussi

[Windows](../mfc/windows.md)
