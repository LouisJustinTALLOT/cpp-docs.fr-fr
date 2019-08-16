---
title: Traitement des boucles inactives
ms.date: 11/04/2016
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
ms.openlocfilehash: 72491c057f3bf7c531bb5515b07f1e9d0acf35d5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508410"
---
# <a name="idle-loop-processing"></a>Traitement des boucles inactives

De nombreuses applications effectuent le traitement lent "en arrière-plan". Parfois, les facteurs de performance exigent l'utilisation du multithreading pour un tel travail. Les threads impliquent une surcharge de développement supplémentaire, ils ne sont donc pas recommandés pour des tâches simples telles que le travail de temps d’inactivité que MFC effectue dans la fonction [OnIdle](../mfc/reference/cwinthread-class.md#onidle) . Cet article se concentre sur le traitement des temps d'inactivité. Pour plus d’informations sur le multithreading, consultez [rubriques](../parallel/multithreading-support-for-older-code-visual-cpp.md)sur le multithreading.

Certains types de traitement en arrière-plan sont correctement effectués pendant les intervalles où l'utilisateur n'interagit pas avec l'application. Dans une application développée pour le système d'exploitation Microsoft Windows, une application peut effectuer un traitement en période d'inactivité en divisant un processus long en de nombreux petits fragments. Après le traitement de chaque fragment, l’application produit le contrôle d’exécution à Windows à l’aide d’une boucle [PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) .

Cet article décrit les deux modes de traitement des temps d'inactivité pouvant être exécutés dans votre application :

- Utilisation de **PeekMessage** dans la boucle de messages principale de MFC.

- Incorporation d’une autre boucle **PeekMessage** ailleurs dans l’application.

##  <a name="_core_peekmessage_in_the_mfc_message_loop"></a>PeekMessage dans la boucle de messages MFC

Dans une application développée avec MFC, la boucle de message principale de `CWinThread` la classe contient une boucle de messages qui appelle l’API Win32 [PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) . Cette boucle appelle également la fonction membre `OnIdle` de `CWinThread` entre les messages. Une application peut traiter les messages dans cette durée d'inactivité en remplaçant la fonction `OnIdle`.

> [!NOTE]
>  `Run`, `OnIdle`, et certaines autres fonctions membres sont désormais membres de la `CWinThread` classe plutôt que de `CWinApp`la classe. `CWinApp` est dérivé de `CWinThread`.

Pour plus d’informations sur l’exécution du traitement inactif, consultez [OnIdle](../mfc/reference/cwinthread-class.md#onidle) dans la *référence MFC*.

##  <a name="_core_peekmessage_elsewhere_in_your_application"></a>PeekMessage ailleurs dans votre application

Une autre méthode de traiter les temps d'inactivité dans une application implique l'incorporation d'une boucle de messages dans une de vos fonctions. Cette boucle de messages est très similaire à la boucle de messages principale de MFC, qui se trouve dans [CWinThread:: Run](../mfc/reference/cwinthread-class.md#run). Cela signifie que cette boucle dans une application développée avec MFC doit exécuter plusieurs des fonctions identiques à la boucle de messages principale. Le fragment de code suivant montre comment écrire une boucle de messages compatible avec MFC :

[!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]

Ce code, incorporé dans une fonction, tourne en boucle tant que du temps d'inactivité est à traiter. Dans cette boucle, une boucle imbriquée appelle `PeekMessage`à plusieurs reprises. Comme cet appel retourne une valeur différente de zéro, la boucle appelle `CWinThread::PumpMessage` pour effectuer la conversion et la distribution des messages normaux. Bien que `PumpMessage` soit non documenté, vous pouvez examiner son code source dans le fichier ThrdCore.Cpp du répertoire \atlmfc\src\mfc du programme d'installation de Visual C++.

Une fois que la boucle interne se termine, la boucle externe effectue le traitement des temps d'inactivité avec un ou plusieurs appels à `OnIdle`. Le premier appel est destiné aux objectifs de MFC. Vous pouvez effectuer des appels supplémentaires à `OnIdle` pour effectuer votre propre travail en arrière-plan.

Pour plus d’informations sur l’exécution du traitement inactif, consultez [OnIdle](../mfc/reference/cwinthread-class.md#onidle) dans la référence de la bibliothèque MFC.

## <a name="see-also"></a>Voir aussi

[Rubriques MFC générales](../mfc/general-mfc-topics.md)
