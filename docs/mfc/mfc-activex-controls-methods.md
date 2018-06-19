---
title: 'Contrôles ActiveX MFC : Méthodes | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b09de5382117b4444eb1bfd90bc0f9d447e537e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348307"
---
# <a name="mfc-activex-controls-methods"></a>Contrôles ActiveX MFC : méthodes
Un contrôle ActiveX déclenche des événements pour la communication entre lui-même et son conteneur. Un conteneur peut également communiquer avec un contrôle au moyen de méthodes et propriétés. Méthodes sont également appelées fonctions.  
  
 Propriétés et méthodes fournissent une interface exportée pour une utilisation par d’autres applications, telles que les conteneurs de contrôles ActiveX et les clients Automation. Pour plus d’informations sur les propriétés du contrôle ActiveX, consultez l’article [contrôles ActiveX MFC : propriétés](../mfc/mfc-activex-controls-properties.md).  
  
 Méthodes sont similaires dans l’utilisation et leur finalité aux fonctions membres d’une classe C++. Il existe deux types de méthodes à votre contrôle peut implémenter : stock et personnalisés. Semblables aux événements stock, les méthodes stock sont celles qui [COleControl](../mfc/reference/colecontrol-class.md) fournit une implémentation. Pour plus d’informations sur les méthodes stock, consultez l’article [contrôles ActiveX MFC : ajout de méthodes Stock](../mfc/mfc-activex-controls-adding-stock-methods.md). Méthodes personnalisées, définies par le développeur, permettent une personnalisation supplémentaire du contrôle. Pour plus d’informations, consultez l’article [contrôles ActiveX MFC : ajout de méthodes personnalisées](../mfc/mfc-activex-controls-adding-custom-methods.md).  
  
 Les MFC Microsoft Foundation Class Library () implémente un mécanisme qui permet à votre contrôle prendre en charge les méthodes stock et personnalisées. La première partie est la classe `COleControl`. Dérivée de `CWnd`, `COleControl` fonctions membres prennent en charge les méthodes stock qui sont communes à tous les contrôles ActiveX. La deuxième partie de ce mécanisme est la table de dispatch. Une table de dispatch est similaire à une table des messages ; Toutefois, au lieu d’une fonction de mappage à un ID de message Windows, une table de dispatch mappe des fonctions membres virtuelles à des ID IDispatch.  
  
 Pour un contrôle à prendre en charge différentes méthodes correctement, sa classe doit déclarer une table de dispatch. Cela est accompli par la ligne suivante du code situé dans l’en-tête de classe de contrôle (. H) fichier :  
  
 [!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/cpp/mfc-activex-controls-methods_1.h)]  
  
 L’objectif principal de la table de dispatch est d’établir la relation entre les noms des méthodes utilisées par un appelant externe (par exemple, le conteneur) et les fonctions membres de la classe du contrôle qui implémentent les méthodes. Une fois que la table de dispatch a été déclarée, il doit être défini dans l’implémentation du contrôle (. (CPP) du contrôle. Les lignes de code suivantes définissent la table de dispatch :  
  
 [!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]  
  
 Si vous avez utilisé le [Assistant contrôle ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md) pour créer le projet, ces lignes ont été ajoutées automatiquement. Si l’Assistant contrôle ActiveX MFC n’a pas été utilisé, vous devez ajouter manuellement ces lignes.  
  
 Les articles suivants décrivent les méthodes en détail :  
  
-   [Contrôles ActiveX MFC : ajout de méthodes stock](../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [Contrôles ActiveX MFC : ajout de méthodes personnalisées](../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [Contrôles ActiveX MFC : retour de codes d’erreur à partir d’une méthode](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

