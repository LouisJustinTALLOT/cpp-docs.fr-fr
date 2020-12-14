---
description: 'En savoir plus sur : relation entre un objet fenêtre C++ et un HWND'
title: Relation entre un objet fenêtre C++ et un HWND
ms.date: 11/19/2018
f1_keywords:
- HWND
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
ms.openlocfilehash: bdcf52d2890265b854e3eef7854b489b47eda6a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218093"
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>Relation entre un objet fenêtre C++ et un HWND

L' *objet* Window est un objet de la `CWnd` classe C++ (ou d’une classe dérivée) que votre programme crée directement. Il s’agit d’une réponse aux appels du constructeur et du destructeur de votre programme. La *fenêtre* Windows, en revanche, est un handle opaque d’une structure de données Windows interne qui correspond à une fenêtre et consomme des ressources système lorsqu’elle est présente. Une fenêtre Windows est identifiée par un « handle de fenêtre » ( `HWND` ) et est créée après que l' `CWnd` objet a été créé par un appel à la `Create` fonction membre de la classe `CWnd` . La fenêtre peut être détruite soit par un appel de programme, soit par l’action d’un utilisateur. Le handle de fenêtre est stocké dans la variable membre *m_hWnd* de l’objet fenêtre. L’illustration suivante montre la relation entre l’objet fenêtre C++ et la fenêtre Windows. La création de fenêtres est décrite dans [création de fenêtres](../mfc/creating-windows.md). La destruction de fenêtres est décrite dans [destruction d’objets de fenêtre](../mfc/destroying-window-objects.md).

![Objet de fenêtre CWnd et fenêtre résultante](../mfc/media/vc37fj1.gif "Objet de fenêtre CWnd et fenêtre résultante") <br/>
Objet Window et fenêtre Windows

## <a name="see-also"></a>Voir aussi

[Objets de fenêtre](../mfc/window-objects.md)
