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
ms.openlocfilehash: 9730e7baf9589c4b05a60703c619aae2e941bdec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372756"
---
# <a name="sdi-and-mdi"></a>SDI et MDI

MFC facilite le travail avec les applications interfaces mono documents (SDI) et interface multi-documents (MDI).

Les applications SDI ne permettent qu’une seule fenêtre de cadre de document ouverte à la fois. Les applications MDI permettent d’ouvrir plusieurs fenêtres d’images de documents dans le même cas d’application. Une application MDI dispose d’une fenêtre dans laquelle plusieurs fenêtres d’enfants MDI, qui sont des fenêtres de cadre elles-mêmes, peuvent être ouvertes, chacune contenant un document séparé. Dans certaines applications, les fenêtres de l’enfant peuvent être de différents types, tels que les fenêtres de carte et les fenêtres de feuille de calcul. Dans ce cas, la barre de menu peut changer que les fenêtres d’enfant MDI de différents types sont activés.

> [!NOTE]
> Sous Windows 95 et plus tard, les applications sont généralement SDI parce que le système d’exploitation a adopté une vue "centrée sur le document".

Pour plus d’informations, voir [Documents, Vues et Cadre](../mfc/documents-views-and-the-framework.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des classes pour l’écriture d’applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
