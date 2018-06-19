---
title: Utilisation de CAnimateCtrl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CAnimateCtrl
dev_langs:
- C++
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5685d6aed00cd57f4329b3865f96fa75226d7cf6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381616"
---
# <a name="using-canimatectrl"></a>Utilisation de CAnimateCtrl
Un contrôle animation, représenté par la classe [CAnimateCtrl](../mfc/reference/canimatectrl-class.md), est une fenêtre qui affiche une image au format de la vidéo entrelacée AVI (Audio), le format audio/vidéo Windows standard. Un clip AVI est une série d’images bitmap, comme un film.  
  
 Étant donné que votre thread continue de s’exécuter pendant que le clip AVI s’affiche, une utilisation courante d’un contrôle animation consiste à indiquer l’activité du système pendant une longue opération. Par exemple, la boîte de dialogue Rechercher de Windows affiche une loupe qui se déplace en tant que le système recherche un fichier.  
  
 Contrôles animation peuvent lire uniquement des clips AVI simples et ils ne prennent pas en charge son. (Pour obtenir une liste complète des limitations, consultez [CAnimateCtrl](../mfc/reference/canimatectrl-class.md).) Étant donné que les fonctionnalités d’un contrôle animation sont très limitées et sujets à modification, vous devez utiliser une alternative tels que le contrôle MCIWnd si vous avez besoin d’un contrôle pour fournir des fonctions d’enregistrement et/ou de lecture multimédia. Pour plus d’informations sur le contrôle MCIWnd, consultez la documentation multimédia.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Utilisation d’un contrôle Animation](../mfc/using-an-animation-control.md)  
  
-   [Notifications envoyées par les contrôles d’animation](../mfc/notifications-sent-by-animation-controls.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles](../mfc/controls-mfc.md)

