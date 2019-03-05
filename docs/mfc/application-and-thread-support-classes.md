---
title: Classes de prise en charge des applications et des threads
ms.date: 11/04/2016
f1_keywords:
- vc.classes.support
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
ms.openlocfilehash: 667725a60fb0c907a9c2d017674f9d097d1f4946
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262036"
---
# <a name="application-and-thread-support-classes"></a>Classes de prise en charge des applications et des threads

Chaque application possède un seul et unique objet application ; Cet objet coordonne les autres objets dans le programme en cours d’exécution et est dérivé de `CWinApp`.

La bibliothèque Microsoft Foundation classes (MFC) prend en charge plusieurs threads d’exécution dans une application. Toutes les applications doivent avoir au moins un thread ; le thread utilisé par votre `CWinApp` objet est ce thread principal.

`CWinThread` Encapsule une partie des fonctionnalités de thread du système d’exploitation. Pour rendre l’utilisation de plusieurs threads, MFC fournit également synchronisation classes d’objets pour fournir une interface C++ pour les objets de synchronisation Win32.

## <a name="application-and-thread-classes"></a>Application Classes et des threads

[CWinApp](../mfc/reference/cwinapp-class.md)<br/>
Encapsule le code pour initialiser, exécuter et arrêter l’application. Vous dérivera votre objet d’application à partir de cette classe.

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
La classe de base pour tous les threads. Utiliser directement, ou dériver une classe de `CWinThread` si votre thread exécute des fonctions de l’interface utilisateur. `CWinApp` est dérivé de `CWinThread`.

## <a name="synchronization-object-classes"></a>Classes d’objet de synchronisation

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
Classe de base des classes d’objet de synchronisation.

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
Une classe de synchronisation qui permet à un seul thread dans un processus unique pour accéder à un objet.

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
Une classe de synchronisation qui permet à un et un nombre maximal spécifié d’un accès simultané à un objet.

[CMutex](../mfc/reference/cmutex-class.md)<br/>
Une classe de synchronisation qui permet à un seul thread au sein de n’importe quel nombre de processus pour accéder à un objet.

[CEvent](../mfc/reference/cevent-class.md)<br/>
Une classe de synchronisation qui indique à une application lorsqu’un événement s’est produite.

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
Utilisé dans les fonctions membres de classes thread-safe pour verrouiller sur un objet de synchronisation.

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
Utilisé dans les fonctions membres de classes thread-safe pour verrouiller un ou plusieurs objets de synchronisation à partir d’un tableau d’objets de synchronisation.

## <a name="related-classes"></a>Classes connexes

[CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)<br/>
Analyse de la ligne de commande avec laquelle votre programme a été démarré.

[CWaitCursor](../mfc/reference/cwaitcursor-class.md)<br/>
Place un curseur d’attente sur l’écran. Utilisé pendant les opérations de longue durée.

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
Gère le stockage persistant de l’ancrage des données d’état pour les barres de contrôles.

[CRecentFileList](../mfc/reference/crecentfilelist-class.md)<br/>
Gère le plus récemment (MRU) liste des fichiers utilisés.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)
