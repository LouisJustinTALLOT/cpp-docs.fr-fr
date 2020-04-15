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
ms.openlocfilehash: 9579d4bb8768b0227453af401d6fdc8a8bd482b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376015"
---
# <a name="idle-loop-processing"></a>Traitement des boucles inactives

De nombreuses applications effectuent le traitement lent "en arrière-plan". Parfois, les facteurs de performance exigent l'utilisation du multithreading pour un tel travail. Les fils impliquent des frais généraux de développement supplémentaires, de sorte qu’ils ne sont pas recommandés pour des tâches simples comme le travail de temps d’inactivité que MFC fait dans la fonction [OnIdle.](../mfc/reference/cwinthread-class.md#onidle) Cet article se concentre sur le traitement des temps d'inactivité. Pour plus d’informations sur la multithreading, voir [Sujets multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Certains types de traitement en arrière-plan sont correctement effectués pendant les intervalles où l'utilisateur n'interagit pas avec l'application. Dans une application développée pour le système d'exploitation Microsoft Windows, une application peut effectuer un traitement en période d'inactivité en divisant un processus long en de nombreux petits fragments. Après le traitement de chaque fragment, l’application donne un contrôle d’exécution à Windows à l’aide d’une boucle [PeekMessage.](/windows/win32/api/winuser/nf-winuser-peekmessagew)

Cet article décrit les deux modes de traitement des temps d'inactivité pouvant être exécutés dans votre application :

- Utilisation **de PeekMessage** dans la boucle de message principale de MFC.

- Intégration d’une autre boucle **PeekMessage** ailleurs dans l’application.

## <a name="peekmessage-in-the-mfc-message-loop"></a><a name="_core_peekmessage_in_the_mfc_message_loop"></a>PeekMessage dans la boucle de message MFC

Dans une application développée avec MFC, `CWinThread` la boucle de message principale de la classe contient une boucle de message qui appelle [l’API PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) Win32. Cette boucle appelle également la fonction membre `OnIdle` de `CWinThread` entre les messages. Une application peut traiter les messages dans cette durée d'inactivité en remplaçant la fonction `OnIdle`.

> [!NOTE]
> `Run`, `OnIdle`et certaines autres fonctions de `CWinThread` membre sont `CWinApp`maintenant des membres de la classe plutôt que de la classe . `CWinApp` est dérivé de `CWinThread`.

Pour plus d’informations sur l’exécution du traitement au ralenti, voir [OnIdle](../mfc/reference/cwinthread-class.md#onidle) dans la *référence MFC*.

## <a name="peekmessage-elsewhere-in-your-application"></a><a name="_core_peekmessage_elsewhere_in_your_application"></a>PeekMessage Ailleurs dans votre demande

Une autre méthode de traiter les temps d'inactivité dans une application implique l'incorporation d'une boucle de messages dans une de vos fonctions. Cette boucle de message est très similaire à la boucle de message principal de MFC, trouvée dans [CWinThread::Run](../mfc/reference/cwinthread-class.md#run). Cela signifie que cette boucle dans une application développée avec MFC doit exécuter plusieurs des fonctions identiques à la boucle de messages principale. Le fragment de code suivant montre comment écrire une boucle de messages compatible avec MFC :

[!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]

Ce code, incorporé dans une fonction, tourne en boucle tant que du temps d'inactivité est à traiter. Dans cette boucle, une boucle `PeekMessage`imbriquée appelle à plusieurs reprises . Comme cet appel retourne une valeur différente de zéro, la boucle appelle `CWinThread::PumpMessage` pour effectuer la conversion et la distribution des messages normaux. Bien que `PumpMessage` soit non documenté, vous pouvez examiner son code source dans le fichier ThrdCore.Cpp du répertoire \atlmfc\src\mfc du programme d'installation de Visual C++.

Une fois que la boucle interne se termine, la boucle externe effectue le traitement des temps d'inactivité avec un ou plusieurs appels à `OnIdle`. Le premier appel est destiné aux objectifs de MFC. Vous pouvez effectuer des appels supplémentaires à `OnIdle` pour effectuer votre propre travail en arrière-plan.

Pour plus d’informations sur l’exécution du traitement au ralenti, voir [OnIdle](../mfc/reference/cwinthread-class.md#onidle) dans la référence de bibliothèque MFC.

## <a name="see-also"></a>Voir aussi

[Rubriques MFC générales](../mfc/general-mfc-topics.md)
