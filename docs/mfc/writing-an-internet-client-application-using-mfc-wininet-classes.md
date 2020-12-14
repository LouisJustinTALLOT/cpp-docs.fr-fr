---
description: 'En savoir plus sur : écriture d’une application cliente Internet à l’aide de classes WinInet MFC'
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
ms.openlocfilehash: 61cfe3e9892f2bde6d233728b7b95ca0edd16ee8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189130"
---
# <a name="writing-an-internet-client-application-using-mfc-wininet-classes"></a>Écriture d'une application cliente Internet en utilisant des classes WinInet MFC

La base de chaque application cliente Internet est la session Internet. MFC implémente les sessions Internet en tant qu’objets de la classe [CInternetSession](../mfc/reference/cinternetsession-class.md). En utilisant cette classe, vous pouvez créer une connexion Internet ou plusieurs sessions simultanées.

Pour communiquer avec un serveur, vous avez besoin d’un objet [CInternetConnection,](../mfc/reference/cinternetconnection-class.md) , ainsi que d’un objet `CInternetSession` . Vous pouvez créer un `CInternetConnection` à l’aide de [CInternetSession :: GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection), [CInternetSession :: GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection)ou [CInternetSession :: GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection). Chacun de ces appels est spécifique au type de protocole. Ces appels n'ouvrent pas un fichier sur le serveur pour la lecture ou l'écriture. Si vous avez l'intention de lire ou d'écrire des données, vous devez ouvrir le fichier en tant qu'étape distincte.

Pour la plupart des sessions Internet, l’objet fonctionne à la main `CInternetSession` avec un objet [CInternetFile](../mfc/reference/cinternetfile-class.md) :

- Pour une session Internet, vous devez créer une instance de [CInternetSession](../mfc/reference/cinternetsession-class.md).

- Si votre session Internet lit ou écrit des données, vous devez créer une instance de `CInternetFile` (ou ses sous-classes, [CHttpFile](../mfc/reference/chttpfile-class.md) ou [CGopherFile](../mfc/reference/cgopherfile-class.md)). Le moyen le plus simple de lire des données est d’appeler [CInternetSession :: OpenURL](../mfc/reference/cinternetsession-class.md#openurl). Cette fonction analyse une URL (Universal Resource Locator) fournie par vous, ouvre une connexion au serveur spécifié par l'URL et retourne un objet `CInternetFile` en lecture seule. `CInternetSession::OpenURL` n'est pas spécifique à un type de protocole — le même appel fonctionne pour les protocoles FTP, HTTP ou l'URL Gopher. `CInternetSession::OpenURL` fonctionne même avec les fichiers locaux (retourne un objet `CStdioFile` au lieu d'un objet `CInternetFile`).

- Si votre session Internet ne lit la pas ou n’écrit pas les données, mais effectue d’autres tâches, telles que la suppression d’un fichier dans un répertoire FTP, vous pouvez ne pas avoir à créer une instance de `CInternetFile`.

Il existe deux manières de créer un objet `CInternetFile` :

- Si vous utilisez `CInternetSession::OpenURL` pour établir la connexion au serveur, l'appel à `OpenURL` retourne `CStdioFile`.

- Si `CInternetSession::GetFtpConnection` vous utilisez, `GetGopherConnection` ou `GetHttpConnection` pour établir votre connexion au serveur, vous devez appeler `CFtpConnection::OpenFile` , `CGopherConnection::OpenFile` ou `CHttpConnection::OpenRequest` , respectivement, pour retourner `CInternetFile` respectivement, `CGopherFile` ou `CHttpFile` .

Les étapes de l’implémentation d’une application cliente Internet varient selon que vous créez un client Internet générique basé sur `OpenURL` ou un client spécifique au protocole à l’aide de l’une des `GetConnection` fonctions.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Comment faire écrire une application cliente Internet qui fonctionne de façon générique avec FTP, HTTP et Gopher](../mfc/steps-in-a-typical-internet-client-application.md)

- [Comment faire écrire une application cliente FTP qui ouvre un fichier](../mfc/steps-in-a-typical-ftp-client-application.md)

- [Comment faire écrire une application cliente FTP qui n’ouvre pas de fichier, mais effectue une opération de répertoire, telle que la suppression d’un fichier](../mfc/steps-in-a-typical-ftp-client-application-to-delete-a-file.md)

- [Comment faire écrire une application cliente Gopher](../mfc/steps-in-a-typical-gopher-client-application.md)

- [Comment faire écrire une application cliente HTTP](../mfc/steps-in-a-typical-http-client-application.md)

## <a name="see-also"></a>Voir aussi

[Extensions Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Classes MFC pour la création d’applications clientes Internet](../mfc/mfc-classes-for-creating-internet-client-applications.md)<br/>
[Conditions préalables pour les classes clientes Internet](../mfc/prerequisites-for-internet-client-classes.md)
