---
title: Les étapes dans une Application cliente Gopher classique | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WinInet classes [MFC], gopher
- Internet applications [MFC], gopher client applications
- Gopher client applications [MFC]
- Internet client applications [MFC], gopher table
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c547d5b2a0bc9755fdf968fc1c42643e96e6fa6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392409"
---
# <a name="steps-in-a-typical-gopher-client-application"></a>Étapes dans une application cliente Gopher classique

Le tableau suivant montre les étapes que vous pouvez effectuer dans une application cliente gopher classique.

|Votre objectif|Actions que vous effectuez|Effects (Effets)|
|---------------|----------------------|-------------|
|Ouvrir une session gopher.|Créer un [CInternetSession](../mfc/reference/cinternetsession-class.md) objet.|Initialise WinInet et se connecte au serveur.|
|Se connecter à un serveur gopher.|Utilisez [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection).|Retourne un [objet CGopherConnection](../mfc/reference/cgopherconnection-class.md) objet.|
|Rechercher la première ressource dans le gopher.|Utilisez [CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile).|Recherche le premier fichier. Retourne FALSE si aucun fichier n’est trouvé.|
|Rechercher la ressource suivante dans le gopher.|Utilisez [CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile).|Recherche le fichier suivant. Retourne FALSE si le fichier est introuvable.|
|Ouvrez le fichier trouvé par `FindFile` ou `FindNextFile` pour la lecture.|Obtenir un localisateur gopher à l’aide de [CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Utilisez [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Ouvre le fichier spécifié par le localisateur. `OpenFile` Retourne un [CGopherFile](../mfc/reference/cgopherfile-class.md) objet.|
|Ouvrez un fichier à l’aide d’un localisateur gopher que vous fournissez.|Créer un localisateur gopher à l’aide de [CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator). Utilisez [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Ouvre le fichier spécifié par le localisateur. `OpenFile` Retourne un [CGopherFile](../mfc/reference/cgopherfile-class.md) objet.|
|Lire à partir du fichier.|Utilisez [CGopherFile](../mfc/reference/cgopherfile-class.md).|Lit le nombre spécifié d’octets, à l’aide d’une mémoire tampon que vous fournissez.|
|Gestion des exceptions.|Utilisez le [CInternetException](../mfc/reference/cinternetexception-class.md) classe.|Gère tous les types d’exception Internet courants.|
|Terminer la session gopher.|Supprimer le [CInternetSession](../mfc/reference/cinternetsession-class.md) objet.|Nettoie automatiquement les connexions et descripteurs de fichiers ouverts.|

## <a name="see-also"></a>Voir aussi

[Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Composants requis pour les classes clientes Internet](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Écriture d’une application cliente Internet en utilisant des classes WinInet MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
