---
title: "Méthodes de création d’une barre d’outils | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d93f8e43c933e9c8054e798c11754cc48bf54a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="methods-of-creating-a-toolbar"></a>Méthodes de création d'une barre d'outils
MFC fournit deux classes pour créer des barres d’outils : [CToolBar](../mfc/reference/ctoolbar-class.md) et [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) (qui encapsule le API de contrôle commun de Windows). `CToolBar`fournit toutes les fonctionnalités du contrôle commun de barre d’outils, et il traite la plupart des paramètres des contrôles communs requis et des structures pour vous. Toutefois, votre fichier exécutable obtenu sera plus grand que celui créé à l’aide de `CToolBarCtrl`.  
  
 `CToolBarCtrl`généralement les résultats dans un fichier exécutable plus petit et que vous pouvez utiliser `CToolBarCtrl` si vous ne souhaitez pas intégrer la barre d’outils dans l’architecture MFC. Si vous envisagez d’utiliser `CToolBarCtrl` et intégrer la barre d’outils dans l’architecture MFC, vous devez prendre soin de communiquer les manipulations du contrôle de barre d’outils à MFC. Cette communication n’est pas difficile ; Toutefois, il s’agit d’un travail supplémentaire qui n’est pas nécessaire lorsque vous utilisez `CToolBar`.  
  
 Visual C++ propose deux méthodes pour tirer parti du contrôle commun de barre d’outils.  
  
-   Créer la barre d’outils à l’aide de `CToolBar`, puis appelez [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl) pour accéder à la `CToolBarCtrl` fonctions membres.  
  
-   Créer la barre d’outils à l’aide de [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)du constructeur.  
  
 Ces deux méthodes vous donnera accès aux fonctions membres du contrôle de barre d’outils. Lorsque vous appelez `CToolBar::GetToolBarCtrl`, il retourne une référence à un `CToolBarCtrl` afin de pouvoir utiliser l’ensemble des fonctions membres de l’objet. Consultez [CToolBar](../mfc/reference/ctoolbar-class.md) pour plus d’informations sur la construction et la création d’une barre d’outils à l’aide de `CToolBar`.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

