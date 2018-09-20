---
title: Création d’un contrôle Rebar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea9ab73bf054b07b24beee8a222cc0a138b9513d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395256"
---
# <a name="creating-a-rebar-control"></a>Création d'un contrôle rebar

[CReBarCtrl](../mfc/reference/crebarctrl-class.md) objets doivent être créés avant que l’objet parent est visible. Cela réduit les risques de problèmes de peinture.

Par exemple, contrôles rebar (utilisés dans les objets de fenêtre frame) sont couramment utilisés comme fenêtres parentes pour les contrôles de barre d’outils. Par conséquent, le parent du contrôle rebar est l’objet de fenêtre frame. Étant donné que l’objet de fenêtre frame est le parent, le `OnCreate` la fonction membre (du parent) est un excellent moyen pour créer le contrôle rebar.

Pour utiliser un `CReBarCtrl` de l’objet, vous serez en général, procédez comme suit :

### <a name="to-use-a-crebarctrl-object"></a>Pour utiliser un objet CReBarCtrl

1. Construire la [CReBarCtrl](../mfc/reference/crebarctrl-class.md) objet.

1. Appelez [créer](../mfc/reference/crebarctrl-class.md#create) pour créer le contrôle commun rebar de Windows et l’attacher à la `CReBarCtrl` objet et en spécifiant éventuellement les styles.

1. Charger une image bitmap, avec un appel à [CBitmap::LoadBitmap](../mfc/reference/cbitmap-class.md#loadbitmap), pour être utilisée comme arrière-plan de l’objet de contrôle rebar.

1. Créer et initialiser des objets de fenêtre enfant (barres d’outils, les contrôles de boîte de dialogue et ainsi de suite) qui seront contenus par l’objet de contrôle rebar.

1. Initialiser un **REBARBANDINFO** structure avec les informations nécessaires pour la bande sur le point d’être inséré.

1. Appelez [InsertBand](../mfc/reference/crebarctrl-class.md#insertband) pour insérer des fenêtres enfants existantes (comme `m_wndReToolBar`) dans le nouveau contrôle rebar. Pour plus d’informations sur l’insertion de bandes dans un contrôle rebar existant, consultez [contrôles Rebar et bandes](../mfc/rebar-controls-and-bands.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

