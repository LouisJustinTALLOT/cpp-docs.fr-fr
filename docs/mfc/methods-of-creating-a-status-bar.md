---
title: Méthodes de création d’une barre d’état | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0428bfc906ba6e8a1ecc7bd7c198327e8c31505
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346927"
---
# <a name="methods-of-creating-a-status-bar"></a>Méthodes de création d'une barre d'état
MFC fournit deux classes pour créer des barres d’état : [CStatusBar](../mfc/reference/cstatusbar-class.md) et [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) (qui encapsule le API de contrôle commun de Windows). `CStatusBar` fournit toutes les fonctionnalités de la barre d’état contrôle commun, il interagit avec les menus et barres d’outils automatiquement, et il traite la plupart des paramètres des contrôles communs requis et des structures pour vous. Toutefois, votre fichier exécutable obtenu sera plus grand que celui créé à l’aide de `CStatusBarCtrl`.  
  
 `CStatusBarCtrl` généralement les résultats dans un fichier exécutable plus petit et que vous pouvez utiliser `CStatusBarCtrl` si vous ne souhaitez pas intégrer la barre d’état dans l’architecture MFC. Si vous envisagez d’utiliser `CStatusBarCtrl` et intégrer la barre d’état dans l’architecture MFC, vous devez prendre soin de communiquer les manipulations à MFC du contrôle de la barre d’état. Cette communication n’est pas difficile ; Toutefois, il s’agit d’un travail supplémentaire qui n’est pas nécessaire lorsque vous utilisez `CStatusBar`.  
  
 Visual C++ offre deux moyens pour tirer parti du contrôle commun de barre de statut.  
  
-   Créer l’état de la barre à l’aide de `CStatusBar`, puis appelez [CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl) pour accéder à la `CStatusBarCtrl` fonctions membres.  
  
-   Créer l’état de la barre à l’aide de [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)du constructeur.  
  
 Ces deux méthodes vous donnera accès aux fonctions membres du contrôle de barre d’état. Lorsque vous appelez `CStatusBar::GetStatusBarCtrl`, il retourne une référence à un `CStatusBarCtrl` afin de pouvoir utiliser l’ensemble des fonctions membres de l’objet. Consultez [CStatusBar](../mfc/reference/cstatusbar-class.md) pour plus d’informations sur la construction et la création de la barre à l’aide d’un état `CStatusBar`.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

