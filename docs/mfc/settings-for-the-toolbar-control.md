---
title: Paramètres du contrôle de barre d’outils | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- toolbar controls [MFC], about toolbar controls
- CToolBarCtrl class [MFC], settings
ms.assetid: 025ba920-b3ee-4d82-9367-e652cd7875b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81631ba25f898e3740b82c0fab9d5af5da930117
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373351"
---
# <a name="settings-for-the-toolbar-control"></a>Paramètres du contrôle ToolBar

Les boutons sur une barre d’outils peuvent afficher une image bitmap, une chaîne ou les deux. Par défaut, la taille de l’image est définie aux dimensions de 16 par 15 pixels. Tous les boutons sont la même largeur, par défaut 24 par 22 pixels. Hauteur de la barre d’outils est déterminée par la hauteur des boutons et la largeur de la barre d’outils est identique à la largeur de la zone cliente d’une fenêtre parente, également par défaut.

Une barre d’outils peut avoir des fonctionnalités de personnalisation intégrées, y compris une boîte de dialogue de personnalisation définie par le système, qui permettent à l’utilisateur à insérer, supprimer ou réorganiser les boutons de barre d’outils. Une application détermine si les fonctionnalités de personnalisation sont disponibles à l’utilisateur et qu’il contrôle l’étendue à laquelle l’utilisateur peut personnaliser la barre d’outils. Pour plus d’informations sur la personnalisation de la barre d’outils, consultez la classe [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) dans le *référence MFC*.

## <a name="see-also"></a>Voir aussi

[Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

