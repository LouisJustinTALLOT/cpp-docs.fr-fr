---
title: Écriture d’une Application de Client Internet à l’aide de Classes WinInet MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC]
- WinInet classes [MFC], programming
- Internet client applications [MFC], writing
- Internet applications [MFC], WinInet
- Internet applications [MFC], client applications
- MFC, Internet applications
ms.assetid: a2c4a40c-a94e-4b3e-9dbf-f8a8dc8e5428
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00ace36eef483d8385d718e14e1fc4c5f4e9ea1e
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956471"
---
# <a name="writing-an-internet-client-application-using-mfc-wininet-classes"></a>Écriture d'une application cliente Internet en utilisant des classes WinInet MFC
La base de chaque application cliente Internet est la session Internet. MFC implémente les sessions Internet en tant qu’objets de classe [CInternetSession](../mfc/reference/cinternetsession-class.md). En utilisant cette classe, vous pouvez créer une connexion Internet ou plusieurs sessions simultanées.  
  
 Pour communiquer avec un serveur, vous devez un [CInternetConnection](../mfc/reference/cinternetconnection-class.md) objet, ainsi qu’une `CInternetSession`. Vous pouvez créer un `CInternetConnection` à l’aide de [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection), [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection), ou [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection). Chacun de ces appels est spécifique au type de protocole. Ces appels n'ouvrent pas un fichier sur le serveur pour la lecture ou l'écriture. Si vous avez l'intention de lire ou d'écrire des données, vous devez ouvrir le fichier en tant qu'étape distincte.  
  
 Pour la plupart des sessions Internet, le `CInternetSession` objet fonctionne de pair avec un [CInternetFile](../mfc/reference/cinternetfile-class.md) objet :  
  
-   Pour une session Internet, vous devez créer une instance de [CInternetSession](../mfc/reference/cinternetsession-class.md).  
  
-   Si votre session Internet lit ou écrit des données, vous devez créer une instance de `CInternetFile` (ou ses sous-classes, [CHttpFile](../mfc/reference/chttpfile-class.md) ou [CGopherFile](../mfc/reference/cgopherfile-class.md)). Pour lire les données le plus simple consiste à appeler [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl). Cette fonction analyse une URL (Universal Resource Locator) fournie par vous, ouvre une connexion au serveur spécifié par l'URL et retourne un objet `CInternetFile` en lecture seule. `CInternetSession::OpenURL` n'est pas spécifique à un type de protocole — le même appel fonctionne pour les protocoles FTP, HTTP ou l'URL Gopher. `CInternetSession::OpenURL` fonctionne même avec les fichiers locaux (retourne un objet `CStdioFile` au lieu d'un objet `CInternetFile`).  
  
-   Si votre session Internet ne lit la pas ou n'écrit pas les données, mais effectue d'autres tâches, telles que la suppression d'un fichier dans un répertoire FTP, vous pouvez ne pas avoir à créer une instance de `CInternetFile`.  
  
 Il existe deux manières de créer un objet `CInternetFile` :  
  
-   Si vous utilisez `CInternetSession::OpenURL` pour établir la connexion au serveur, l'appel à `OpenURL` retourne `CStdioFile`.  
  
-   Si utiliser `CInternetSession::GetFtpConnection`, `GetGopherConnection`, ou `GetHttpConnection` pour établir la connexion au serveur, vous devez appeler `CFtpConnection::OpenFile`, `CGopherConnection::OpenFile`, ou `CHttpConnection::OpenRequest`, respectivement, pour retourner un `CInternetFile`, `CGopherFile`, ou `CHttpFile`, respectivement.  
  
 Les étapes de l’implémentation d’une application cliente Internet varient selon que vous créez un client Internet générique basé sur `OpenURL` ou un client spécifique au protocole à l’aide d’un de le `GetConnection` fonctions.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Comment écrire une application cliente Internet qui fonctionne génériquement avec FTP, HTTP et gopher](../mfc/steps-in-a-typical-internet-client-application.md)  
  
-   [Comment écrire une application cliente FTP qui ouvre un fichier](../mfc/steps-in-a-typical-ftp-client-application.md)  
  
-   [Comment écrire une application de client FTP qui n’ouvre pas un fichier mais effectue une opération d’annuaire, telles que la suppression d’un fichier](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)  
  
-   [Comment écrire une application cliente gopher](../mfc/steps-in-a-typical-gopher-client-application.md)  
  
-   [Comment écrire une application cliente HTTP](../mfc/steps-in-a-typical-http-client-application.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Classes MFC pour la création d’Applications clientes Internet](../mfc/mfc-classes-for-creating-internet-client-applications.md)   
 [Composants requis pour les classes clientes Internet](../mfc/prerequisites-for-internet-client-classes.md)
