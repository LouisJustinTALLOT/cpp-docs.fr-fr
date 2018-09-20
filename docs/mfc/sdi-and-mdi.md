---
title: SDI et MDI | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8189af7939bfca0fd206fa72892098e373444879
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401444"
---
# <a name="sdi-and-mdi"></a>SDI et MDI

MFC rend plus facile travailler avec l’interface monodocument (SDI) et applications d’interface multidocument (MDI).

Les applications SDI ne permettent qu’une seule fenêtre frame de document ouvert à la fois. Les applications MDI permettent document plusieurs fenêtres frame être ouvert dans la même instance d’une application. Une application MDI possède une fenêtre dans quel MDI plusieurs fenêtres enfants, qui sont elles-mêmes des fenêtres frame, peuvent être ouvertes, chacune contenant un document distinct. Dans certaines applications, les fenêtres enfants peuvent être de différents types, tels que les fenêtres de graphique et feuille de calcul. Dans ce cas, la barre de menus peut modifier comme fenêtres enfants MDI de types différents sont activés.

> [!NOTE]
>  Sous Windows 95 et versions ultérieures, les applications sont généralement SDI, car le système d’exploitation a adopté une vue « centré sur le document ».

Pour plus d’informations, consultez [Documents, vues et l’infrastructure](../mfc/documents-views-and-the-framework.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des classes pour l’écriture d’applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
