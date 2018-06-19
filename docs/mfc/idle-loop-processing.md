---
title: Traitement des boucles inactives | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, background processing
- PeekMessage method [MFC], elsewhere than message loop
- PeekMessage method [MFC]
- MFC, messages
- messages [MFC], loops
- OnIdle method [MFC]
- processing [MFC], background
- idle loop processing [MFC]
- idle processing [MFC]
- threading [MFC], alternatives to multithreading
- processing, during idle loop
- processing [MFC]
- background processing [MFC]
ms.assetid: 5c7c46c1-6107-4304-895f-480983bb1e44
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d66983eb915c856ecf52e225b71151359a499b4b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354899"
---
# <a name="idle-loop-processing"></a>Traitement des boucles inactives
De nombreuses applications effectuent le traitement lent "en arrière-plan". Parfois, les facteurs de performance exigent l'utilisation du multithreading pour un tel travail. Threads impliquent une surcharge de développement supplémentaire, ils ne sont donc pas recommandés pour les tâches simples comme le travail de la durée d’inactivité que MFC effectue dans le [OnIdle](../mfc/reference/cwinthread-class.md#onidle) (fonction). Cet article se concentre sur le traitement des temps d'inactivité. Pour plus d’informations sur le multithreading, consultez [rubriques de Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 Certains types de traitement en arrière-plan sont correctement effectués pendant les intervalles où l'utilisateur n'interagit pas avec l'application. Dans une application développée pour le système d'exploitation Microsoft Windows, une application peut effectuer un traitement en période d'inactivité en divisant un processus long en de nombreux petits fragments. Après avoir traité chaque fragment, l’application cède le contrôle de l’exécution à Windows en utilisant un [PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943) boucle.  
  
 Cet article décrit les deux modes de traitement des temps d'inactivité pouvant être exécutés dans votre application :  
  
-   À l’aide de **PeekMessage** dans une boucle de messages principale de MFC.  
  
-   Incorporation d’une autre **PeekMessage** boucle quelque part ailleurs dans l’application.  
  
##  <a name="_core_peekmessage_in_the_mfc_message_loop"></a> PeekMessage dans la boucle de messages MFC  
 Dans une application développée avec MFC, le message principal en boucle dans le `CWinThread` classe contient une boucle de message qui appelle le [PeekMessage](http://msdn.microsoft.com/library/windows/desktop/ms644943) API Win32. Cette boucle appelle également la fonction membre `OnIdle` de `CWinThread` entre les messages. Une application peut traiter les messages dans cette durée d'inactivité en remplaçant la fonction `OnIdle`.  
  
> [!NOTE]
>  **Exécutez**, `OnIdle`, et d’autres fonctions membres sont désormais des membres de classe `CWinThread` au lieu de la classe `CWinApp`. `CWinApp` est dérivé de `CWinThread`.  
  
 Pour plus d’informations sur les performances de traitement inactif, consultez [OnIdle](../mfc/reference/cwinthread-class.md#onidle) dans les *référence MFC*.  
  
##  <a name="_core_peekmessage_elsewhere_in_your_application"></a> PeekMessage ailleurs dans votre Application  
 Une autre méthode de traiter les temps d'inactivité dans une application implique l'incorporation d'une boucle de messages dans une de vos fonctions. Cette boucle de messages est très similaire à la boucle de messages principale de MFC, trouvé dans [CWinThread::Run](../mfc/reference/cwinthread-class.md#run). Cela signifie que cette boucle dans une application développée avec MFC doit exécuter plusieurs des fonctions identiques à la boucle de messages principale. Le fragment de code suivant montre comment écrire une boucle de messages compatible avec MFC :  
  
 [!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]  
  
 Ce code, incorporé dans une fonction, tourne en boucle tant que du temps d'inactivité est à traiter. Dans cette boucle, une boucle imbriquée appelle à plusieurs reprises **PeekMessage**. Comme cet appel retourne une valeur différente de zéro, la boucle appelle `CWinThread::PumpMessage` pour effectuer la conversion et la distribution des messages normaux. Bien que `PumpMessage` soit non documenté, vous pouvez examiner son code source dans le fichier ThrdCore.Cpp du répertoire \atlmfc\src\mfc du programme d'installation de Visual C++.  
  
 Une fois que la boucle interne se termine, la boucle externe effectue le traitement des temps d'inactivité avec un ou plusieurs appels à `OnIdle`. Le premier appel est destiné aux objectifs de MFC. Vous pouvez effectuer des appels supplémentaires à `OnIdle` pour effectuer votre propre travail en arrière-plan.  
  
 Pour plus d’informations sur les performances de traitement inactif, consultez [OnIdle](../mfc/reference/cwinthread-class.md#onidle) dans la référence de la bibliothèque MFC.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques MFC générales](../mfc/general-mfc-topics.md)

