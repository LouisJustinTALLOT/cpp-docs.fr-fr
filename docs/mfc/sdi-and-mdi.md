---
title: SDI et MDI
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
ms.openlocfilehash: 725249e5a71e8ee097c641e5972e3cc8bb0e3e33
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308528"
---
# <a name="sdi-and-mdi"></a>SDI et MDI

MFC rend plus facile travailler avec l’interface monodocument (SDI) et applications d’interface multidocument (MDI).

Les applications SDI ne permettent qu’une seule fenêtre frame de document ouvert à la fois. Les applications MDI permettent document plusieurs fenêtres frame être ouvert dans la même instance d’une application. Une application MDI possède une fenêtre dans quel MDI plusieurs fenêtres enfants, qui sont elles-mêmes des fenêtres frame, peuvent être ouvertes, chacune contenant un document distinct. Dans certaines applications, les fenêtres enfants peuvent être de différents types, tels que les fenêtres de graphique et feuille de calcul. Dans ce cas, la barre de menus peut modifier comme fenêtres enfants MDI de types différents sont activés.

> [!NOTE]
>  Sous Windows 95 et versions ultérieures, les applications sont généralement SDI, car le système d’exploitation a adopté une vue « centré sur le document ».

Pour plus d’informations, consultez [Documents, vues et l’infrastructure](../mfc/documents-views-and-the-framework.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des classes pour l’écriture d’applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
