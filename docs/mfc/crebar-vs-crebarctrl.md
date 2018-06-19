---
title: CReBar et. CReBarCtrl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CReBar
- CReBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6d0b8df40676cc64c97a6bdef013321c404899f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344972"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar et. CReBarCtrl
MFC propose deux classes pour créer des rebars : [CReBar](../mfc/reference/crebar-class.md) et [CReBarCtrl](../mfc/reference/crebarctrl-class.md) (qui encapsule le API de contrôle commun de Windows). **CReBar** fournit toutes les fonctionnalités du contrôle commun rebar, et il gère la plupart des paramètres des contrôles communs requis et des structures pour vous.  
  
 `CReBarCtrl` est une classe wrapper pour le contrôle rebar Win32 et par conséquent, peut être plus facile à implémenter si vous ne souhaitez pas intégrer le rebar dans l’architecture MFC. Si vous envisagez d’utiliser `CReBarCtrl` et intégrer le rebar dans l’architecture MFC, vous devez prendre soin de communiquer les manipulations du contrôle rebar à MFC. Cette communication n’est pas difficile ; Toutefois, il s’agit d’un travail supplémentaire qui n’est pas nécessaire lorsque vous utilisez **CReBar**.  
  
 Visual C++ propose deux méthodes pour tirer parti du contrôle commun rebar.  
  
-   Créez le rebar à l’aide **CReBar**, puis appelez [CReBar::GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl) à accéder à la `CReBarCtrl` fonctions membres.  
  
    > [!NOTE]
    >  `CReBar::GetReBarCtrl` est une fonction membre inline qui effectue un cast de le **cela** pointeur de l’objet rebar. Cela signifie que, au moment de l’exécution, l’appel de fonction n’a aucune surcharge.  
  
-   Créez le rebar en utilisant [CReBarCtrl](../mfc/reference/crebarctrl-class.md)du constructeur.  
  
 Ces deux méthodes vous donnera accès aux fonctions membres du contrôle rebar. Lorsque vous appelez `CReBar::GetReBarCtrl`, il retourne une référence à un `CReBarCtrl` afin de pouvoir utiliser l’ensemble des fonctions membres de l’objet. Consultez [CReBar](../mfc/reference/crebar-class.md) pour plus d’informations sur la construction et la création d’un rebar à l’aide de **CReBar**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

