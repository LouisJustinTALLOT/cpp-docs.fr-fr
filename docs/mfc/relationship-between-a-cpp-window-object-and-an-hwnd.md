---
title: Relation entre un objet fenêtre C++ et HWND | Documents Microsoft
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
ms.openlocfilehash: 3864de8b3133fd2284b3ce57b75b30d8f41c26a7
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928526"
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>Relation entre un objet fenêtre C++ et un HWND
La fenêtre *objet* est un objet de C++ `CWnd` classe (ou une classe dérivée) que votre programme crée directement. Il va et vient en réponse aux appels de constructeur et le destructeur de votre programme. Les fenêtres *fenêtre*, quant à lui, est un handle opaque vers une structure de données interne Windows qui correspond à une fenêtre et consomme des ressources système lorsqu’il est présent. Une fenêtre Windows est identifiée par un « handle de fenêtre » (`HWND`) et est créé après le `CWnd` objet est créé par un appel à la `Create` fonction membre de classe `CWnd`. La fenêtre peut être détruite par un appel de programme ou par l’action d’un utilisateur. Le handle de fenêtre est stocké dans l’objet de fenêtre *m_hWnd* variable membre. L’illustration suivante montre la relation entre l’objet fenêtre C++ et la fenêtre Windows. Création de fenêtres est décrite dans [création de fenêtres](../mfc/creating-windows.md). Détruire des fenêtres sont décrite dans [destruction d’objets](../mfc/destroying-window-objects.md).  
  
 ![CWnd objet fenêtre et fenêtre résultante](../mfc/media/vc37fj1.gif "vc37fj1")  
Objet fenêtre et fenêtre Windows  
  
## <a name="see-also"></a>Voir aussi  
 [Objets fenêtre](../mfc/window-objects.md)

