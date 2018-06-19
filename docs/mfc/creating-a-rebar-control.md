---
title: Création d’un contrôle Rebar | Documents Microsoft
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
ms.openlocfilehash: 1deb33adc104775cf9b76daf75d4ee08b6475f0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342305"
---
# <a name="creating-a-rebar-control"></a>Création d'un contrôle rebar
[CReBarCtrl](../mfc/reference/crebarctrl-class.md) objets doivent être créés avant que l’objet parent est visible. Cela réduit les possibilités de problèmes de peinture.  
  
 Par exemple, rebar (contrôles) (utilisés dans les objets de fenêtre frame) sont couramment utilisés comme fenêtres parentes pour les contrôles de barre d’outils. Par conséquent, le parent du contrôle rebar est l’objet de fenêtre frame. Étant donné que l’objet de fenêtre frame est le parent, le `OnCreate` la fonction membre (du parent) est un excellent moyen pour créer le contrôle rebar.  
  
 Pour utiliser un `CReBarCtrl` de l’objet, en général, suivez ces étapes :  
  
### <a name="to-use-a-crebarctrl-object"></a>Pour utiliser un objet CReBarCtrl  
  
1.  Construire la [CReBarCtrl](../mfc/reference/crebarctrl-class.md) objet.  
  
2.  Appelez [créer](../mfc/reference/crebarctrl-class.md#create) pour créer le contrôle commun rebar de Windows et l’attacher à la `CReBarCtrl` objet, en spécifiant les styles souhaités.  
  
3.  Charger une image bitmap, avec un appel à [CBitmap::LoadBitmap](../mfc/reference/cbitmap-class.md#loadbitmap), pour être utilisé comme arrière-plan de l’objet de contrôle rebar.  
  
4.  Créer et initialiser tous les objets de fenêtre enfant (barres d’outils, les contrôles de boîte de dialogue, etc.) qui seront contenus par l’objet de contrôle rebar.  
  
5.  Initialiser un **REBARBANDINFO** structure avec les informations nécessaires pour la bande sur le point d’être inséré.  
  
6.  Appelez [InsertBand](../mfc/reference/crebarctrl-class.md#insertband) pour insérer les fenêtres enfants existantes (telles que `m_wndReToolBar`) dans le nouveau contrôle rebar. Pour plus d’informations sur l’insertion de bandes dans un contrôle rebar existant, consultez [les contrôles Rebar et bandes](../mfc/rebar-controls-and-bands.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

