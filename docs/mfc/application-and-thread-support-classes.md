---
description: 'En savoir plus sur : classes de prise en charge des applications et des threads'
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
ms.openlocfilehash: 89ab6e324a777c272dcbcfabc746c03cb6731589
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176741"
---
# <a name="application-and-thread-support-classes"></a>Classes de prise en charge des applications et des threads

Chaque application a un seul et unique objet d’application ; cet objet coordonne les autres objets du programme en cours d’exécution et est dérivé de `CWinApp` .

La bibliothèque MFC (Microsoft Foundation Class) prend en charge plusieurs threads d’exécution au sein d’une application. Toutes les applications doivent avoir au moins un thread. le thread utilisé par votre `CWinApp` objet est ce thread principal.

`CWinThread` encapsule une partie des fonctionnalités de thread du système d’exploitation. Pour faciliter l’utilisation de plusieurs threads, MFC fournit également des classes d’objet de synchronisation pour fournir une interface C++ aux objets de synchronisation Win32.

## <a name="application-and-thread-classes"></a>Classes d’application et de thread

[CWinApp](reference/cwinapp-class.md)<br/>
Encapsule le code pour initialiser, exécuter et terminer l’application. Vous allez dériver votre objet d’application de cette classe.

[CWinThread](reference/cwinthread-class.md)<br/>
Classe de base pour tous les threads. Utilisez directement ou dérivez une classe de `CWinThread` si votre thread exécute des fonctions d’interface utilisateur. `CWinApp` est dérivé de `CWinThread`.

## <a name="synchronization-object-classes"></a>Classes d’objets de synchronisation

[CSyncObject](reference/csyncobject-class.md)<br/>
Classe de base des classes d’objets de synchronisation.

[CCriticalSection](reference/ccriticalsection-class.md)<br/>
Classe de synchronisation qui autorise un seul thread dans un processus unique à accéder à un objet.

[CSemaphore](reference/csemaphore-class.md)<br/>
Classe de synchronisation qui autorise entre un et un nombre maximal spécifié d’accès simultanés à un objet.

[CMutex](reference/cmutex-class.md)<br/>
Classe de synchronisation qui permet à un seul thread dans un nombre quelconque de processus d’accéder à un objet.

[CEvent](reference/cevent-class.md)<br/>
Classe de synchronisation qui notifie une application quand un événement s’est produit.

[CSingleLock](reference/csinglelock-class.md)<br/>
Utilisé dans les fonctions membres des classes thread-safe pour verrouiller un objet de synchronisation.

[CMultiLock](reference/cmultilock-class.md)<br/>
Utilisé dans les fonctions membres des classes thread-safe pour verrouiller un ou plusieurs objets de synchronisation à partir d’un tableau d’objets de synchronisation.

## <a name="related-classes"></a>Classes connexes

[CCommandLineInfo](reference/ccommandlineinfo-class.md)<br/>
Analyse la ligne de commande avec laquelle votre programme a été démarré.

[CWaitCursor](reference/cwaitcursor-class.md)<br/>
Place un curseur d’attente sur l’écran. Utilisé pendant les opérations de longue durée.

[CDockState](reference/cdockstate-class.md)<br/>
Gère le stockage persistant des données d’état d’ancrage pour les barres de contrôles.

[CRecentFileList](reference/crecentfilelist-class.md)<br/>
Conserve la liste des derniers fichiers utilisés (MRU).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](class-library-overview.md)
