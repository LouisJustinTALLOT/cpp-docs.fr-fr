---
title: Relation entre un objet fenêtre C++ et un HWND | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- HWND
dev_langs:
- C++
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 844f62b110f54ba3e2c8909a78d58c9f2c01dcac
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392812"
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>Relation entre un objet fenêtre C++ et un HWND

La fenêtre *objet* est un objet du C++ `CWnd` classe (ou une classe dérivée) que votre programme crée directement. Il va et vient en réponse aux appels de constructeur et destructeur de votre programme. Le Windows *fenêtre*, quant à eux, est un handle opaque à une structure de données Windows interne qui correspond à une fenêtre et consomme des ressources système lorsqu’il est présent. Une fenêtre Windows est identifiée par un handle de fenêtre « » (`HWND`) et est créé après le `CWnd` objet est créé par un appel à la `Create` fonction membre de classe `CWnd`. La fenêtre peut être détruite par un appel de programme ou par l’action d’un utilisateur. Le handle de fenêtre est stocké dans l’objet de fenêtre *m_hWnd* variable membre. La figure suivante montre la relation entre l’objet fenêtre C++ et la fenêtre de Windows. Création de fenêtres est abordée dans [Windows création](../mfc/creating-windows.md). Détruire des fenêtres est abordée dans [destruction d’objets](../mfc/destroying-window-objects.md).

![CWnd objet fenêtre et fenêtre résultante](../mfc/media/vc37fj1.gif "vc37fj1") objet fenêtre et fenêtre de Windows

## <a name="see-also"></a>Voir aussi

[Objets fenêtre](../mfc/window-objects.md)

