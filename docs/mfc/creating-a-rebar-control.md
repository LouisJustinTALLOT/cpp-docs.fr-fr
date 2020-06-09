---
title: Création d'un contrôle rebar
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
ms.openlocfilehash: 6828fa3b47eaa1e29579b09611d85cd68702c332
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617126"
---
# <a name="creating-a-rebar-control"></a>Création d'un contrôle rebar

Les objets [CReBarCtrl](reference/crebarctrl-class.md) doivent être créés avant que l’objet parent soit visible. Cela réduit les possibilités de peinture des problèmes.

Par exemple, les contrôles rebar (utilisés dans les objets de fenêtre frame) sont couramment utilisés comme fenêtres parentes pour les contrôles ToolBar. Par conséquent, le parent du contrôle rebar est l’objet de fenêtre frame. Étant donné que l’objet de fenêtre frame est le parent, la `OnCreate` fonction membre (du parent) est un excellent emplacement pour créer le contrôle rebar.

Pour utiliser un `CReBarCtrl` objet, vous devez généralement suivre les étapes suivantes :

### <a name="to-use-a-crebarctrl-object"></a>Pour utiliser un objet CReBarCtrl

1. Construisez l’objet [CReBarCtrl](reference/crebarctrl-class.md) .

1. Appelez [Create](reference/crebarctrl-class.md#create) pour créer le contrôle commun Rebar Windows et l’attacher à l' `CReBarCtrl` objet, en spécifiant les styles souhaités.

1. Chargez une bitmap, avec un appel à [CBitmap :: LoadBitmap](reference/cbitmap-class.md#loadbitmap), à utiliser comme arrière-plan de l’objet de contrôle rebar.

1. Créez et initialisez les objets de fenêtre enfants (barres d’outils, contrôles de boîte de dialogue, etc.) qui seront contenus par l’objet de contrôle rebar.

1. Initialisez une structure **REBARBANDINFO** avec les informations nécessaires pour que la bande soit insérée.

1. Appelez [InsertBand](reference/crebarctrl-class.md#insertband) pour insérer les fenêtres enfants existantes (telles que `m_wndReToolBar` ) dans le nouveau contrôle rebar. Pour plus d’informations sur l’insertion de bandes dans un contrôle rebar existant, consultez [contrôles Rebar et bandes](rebar-controls-and-bands.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CReBarCtrl](using-crebarctrl.md)<br/>
[Commandes](controls-mfc.md)
