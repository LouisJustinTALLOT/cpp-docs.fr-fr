---
title: Application et Thread prennent en charge les Classes | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.support
dev_langs:
- C++
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9f3877cf85e369756b15d565af1481fd6d258df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341308"
---
# <a name="application-and-thread-support-classes"></a>Classes de prise en charge des applications et des threads
Chaque application possède un seul et unique objet application ; Cet objet coordonne les autres objets dans le programme en cours d’exécution et qu’il est dérivé de `CWinApp`.  
  
 La bibliothèque Microsoft Foundation classes (MFC) prend en charge plusieurs threads d’exécution dans une application. Toutes les applications doivent avoir au moins un thread ; le thread utilisé par votre `CWinApp` objet est ce thread principal.  
  
 `CWinThread` Encapsule une partie des fonctionnalités de thread du système d’exploitation. Pour rendre l’utilisation de plusieurs threads, MFC fournit également synchronisation classes d’objet pour fournir une interface C++ pour les objets de synchronisation Win32.  
  
## <a name="application-and-thread-classes"></a>Application de Classes et des threads  
 [CWinApp](../mfc/reference/cwinapp-class.md)  
 Encapsule le code pour initialiser, exécuter et mettre fin à l’application. Vous dérivera votre objet d’application à partir de cette classe.  
  
 [CWinThread](../mfc/reference/cwinthread-class.md)  
 La classe de base pour tous les threads. Utilisez directement, ou dériver une classe de `CWinThread` si votre thread exécute des fonctions de l’interface utilisateur. `CWinApp` est dérivé de `CWinThread`.  
  
## <a name="synchronization-object-classes"></a>Classes d’objet de synchronisation  
 [CSyncObject](../mfc/reference/csyncobject-class.md)  
 Classe de base des classes d’objet de synchronisation.  
  
 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
 Une classe de synchronisation qui permet à un seul thread dans un processus unique pour accéder à un objet.  
  
 [CSemaphore](../mfc/reference/csemaphore-class.md)  
 Une classe de synchronisation qui permet à un et un nombre maximal spécifié d’un accès simultané à un objet.  
  
 [CMutex](../mfc/reference/cmutex-class.md)  
 Une classe de synchronisation qui permet à un seul thread au sein de n’importe quel nombre de processus pour accéder à un objet.  
  
 [CEvent](../mfc/reference/cevent-class.md)  
 Une classe de synchronisation qui avertit une application quand un événement s’est produit.  
  
 [CSingleLock](../mfc/reference/csinglelock-class.md)  
 Utilisé dans les fonctions membres des classes thread-safe à un verrou sur un objet de synchronisation.  
  
 [CMultiLock](../mfc/reference/cmultilock-class.md)  
 Utilisé dans les fonctions membres des classes thread-safe pour verrouiller un ou plusieurs objets de synchronisation à partir d’un tableau d’objets de synchronisation.  
  
## <a name="related-classes"></a>Classes associées  
 [CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)  
 Analyse de la ligne de commande avec lesquels votre programme a été démarré.  
  
 [CWaitCursor](../mfc/reference/cwaitcursor-class.md)  
 Place un curseur d’attente sur l’écran. Utilisée au cours des opérations de longue durée.  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 Gère le stockage persistant d’ancrage des données d’état pour les barres de contrôles.  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 Gère la liste (MRU) des fichiers utilisés récemment.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

