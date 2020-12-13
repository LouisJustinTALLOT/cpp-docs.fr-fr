---
description: 'En savoir plus sur : quand initialiser des objets CWnd'
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
ms.openlocfilehash: 89d40b826507574fddd41364ac6cecc526663519
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142764"
---
# <a name="when-to-initialize-cwnd-objects"></a>Quand initialiser les objets CWnd

Vous ne pouvez pas créer vos propres fenêtres enfants ou appeler des fonctions API Windows dans le constructeur d’un `CWnd` objet dérivé de. Cela est dû au fait que le `HWND` pour l' `CWnd` objet n’a pas encore été créé. La plupart des initialisations spécifiques à Windows, telles que l’ajout de fenêtres enfants, doivent être effectuées dans un gestionnaire de messages [OnCreate](../mfc/reference/cwnd-class.md#oncreate) .

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Création de fenêtres d’image de document](../mfc/creating-document-frame-windows.md)

- [Création de document/vue](../mfc/document-view-creation.md)

## <a name="see-also"></a>Voir aussi

[Utilisation des fenêtres Frame](../mfc/using-frame-windows.md)
