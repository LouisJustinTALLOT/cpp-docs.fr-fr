---
description: 'En savoir plus sur : styles de Frame-Window (C++)'
title: Styles de fenêtre frame (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
ms.openlocfilehash: 5d7b0effe4b7cea17eb0b5bd8208563ba552ba99
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180341"
---
# <a name="frame-window-styles-c"></a>Styles de fenêtre frame (C++)

Les fenêtres Frame que vous obtenez avec l’infrastructure sont adaptées à la plupart des programmes, mais vous pouvez bénéficier d’une plus grande flexibilité en utilisant les fonctions avancées [PreCreateWindow](reference/cwnd-class.md#precreatewindow) et la fonction globale MFC [AfxRegisterWndClass](reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow` est une fonction membre de `CWnd` .

Si vous appliquez les styles de **WS_HSCROLL** et de **WS_VSCROLL** à la fenêtre frame principale, ils sont appliqués à la fenêtre **MdiClient** afin que les utilisateurs puissent faire défiler la zone **MdiClient** .

Si le bit de style de la fenêtre **FWS_ADDTOTITLE** est défini (par défaut), la vue indique à la fenêtre frame le titre à afficher dans la barre de titre de la fenêtre en fonction du nom du document de la vue.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Gestion des fenêtres enfants MDI (MdiClient)](managing-mdi-child-windows.md), fenêtre dans un frame MDI qui contient les fenêtres enfants MDI

- [Modification des styles d'une fenêtre créée par MFC](changing-the-styles-of-a-window-created-by-mfc.md)

- [Styles de fenêtre](reference/styles-used-by-mfc.md#window-styles)

## <a name="see-also"></a>Voir aussi

[Fenêtres Frame](frame-windows.md)
