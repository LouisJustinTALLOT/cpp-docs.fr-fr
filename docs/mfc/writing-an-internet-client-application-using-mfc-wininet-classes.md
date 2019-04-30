---
title: Écriture d'une application cliente Internet en utilisant des classes WinInet MFC
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC]
- WinInet classes [MFC], programming
- Internet client applications [MFC], writing
- Internet applications [MFC], WinInet
- Internet applications [MFC], client applications
- MFC, Internet applications
ms.assetid: a2c4a40c-a94e-4b3e-9dbf-f8a8dc8e5428
ms.openlocfilehash: 6e32210217321e4eb59d7d3e666a4f5494eb3642
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399471"
---
# <a name="writing-an-internet-client-application-using-mfc-wininet-classes"></a>Écriture d'une application cliente Internet en utilisant des classes WinInet MFC

La base de chaque application cliente Internet est la session Internet. MFC implémente les sessions Internet en tant qu’objets de classe [CInternetSession](../mfc/reference/cinternetsession-class.md). En utilisant cette classe, vous pouvez créer une connexion Internet ou plusieurs sessions simultanées.

Pour communiquer avec un serveur, vous devez un [CInternetConnection](../mfc/reference/cinternetconnection-class.md) objet ainsi qu’un `CInternetSession`. Vous pouvez créer un `CInternetConnection` à l’aide de [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection), [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection), ou [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection). Chacun de ces appels est spécifique au type de protocole. Ces appels n'ouvrent pas un fichier sur le serveur pour la lecture ou l'écriture. Si vous avez l'intention de lire ou d'écrire des données, vous devez ouvrir le fichier en tant qu'étape distincte.

Pour la plupart des sessions Internet, le `CInternetSession` objet fonctionne de pair avec un [CInternetFile](../mfc/reference/cinternetfile-class.md) objet :

- Pour une session Internet, vous devez créer une instance de [CInternetSession](../mfc/reference/cinternetsession-class.md).

- Si votre session Internet lit ou écrit des données, vous devez créer une instance de `CInternetFile` (ou ses sous-classes, [CHttpFile](../mfc/reference/chttpfile-class.md) ou [CGopherFile](../mfc/reference/cgopherfile-class.md)). Le moyen le plus simple pour lire des données consiste à appeler [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl). Cette fonction analyse une URL (Universal Resource Locator) fournie par vous, ouvre une connexion au serveur spécifié par l'URL et retourne un objet `CInternetFile` en lecture seule. `CInternetSession::OpenURL` n'est pas spécifique à un type de protocole — le même appel fonctionne pour les protocoles FTP, HTTP ou l'URL Gopher. `CInternetSession::OpenURL` fonctionne même avec les fichiers locaux (retourne un objet `CStdioFile` au lieu d'un objet `CInternetFile`).

- Si votre session Internet ne lit la pas ou n’écrit pas les données, mais effectue d’autres tâches, telles que la suppression d’un fichier dans un répertoire FTP, vous pouvez ne pas avoir à créer une instance de `CInternetFile`.

Il existe deux manières de créer un objet `CInternetFile` :

- Si vous utilisez `CInternetSession::OpenURL` pour établir la connexion au serveur, l'appel à `OpenURL` retourne `CStdioFile`.

- Si utiliser `CInternetSession::GetFtpConnection`, `GetGopherConnection`, ou `GetHttpConnection` pour établir votre connexion au serveur, vous devez appeler `CFtpConnection::OpenFile`, `CGopherConnection::OpenFile`, ou `CHttpConnection::OpenRequest`, respectivement, pour retourner un `CInternetFile`, `CGopherFile`, ou `CHttpFile`, respectivement.

Les étapes de l’implémentation d’une application cliente Internet varient selon que vous créez un client Internet générique basé sur `OpenURL` ou un client spécifique au protocole à l’aide d’une de la `GetConnection` fonctions.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Comment écrire une application cliente Internet qui fonctionne génériquement avec FTP, HTTP et gopher](../mfc/steps-in-a-typical-internet-client-application.md)

- [Comment écrire une application cliente FTP qui ouvre un fichier](../mfc/steps-in-a-typical-ftp-client-application.md)

- [Comment écrire une application de client FTP qui n’ouvre pas un fichier mais effectue une opération d’annuaire, telles que la suppression d’un fichier](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)

- [Comment écrire une application cliente gopher](../mfc/steps-in-a-typical-gopher-client-application.md)

- [Comment écrire une application cliente HTTP](../mfc/steps-in-a-typical-http-client-application.md)

## <a name="see-also"></a>Voir aussi

[Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Classes MFC pour la création d’applications clientes Internet](../mfc/mfc-classes-for-creating-internet-client-applications.md)<br/>
[Composants requis pour les classes clientes Internet](../mfc/prerequisites-for-internet-client-classes.md)
