---
title: Composants requis pour les classes clientes Internet
ms.date: 11/04/2016
helpviewer_keywords:
- Internet files [MFC], writing to
- Internet [MFC], connections
- FTP (File Transfer Protocol), MFC classes
- Gopher prerequisites [MFC]
- files [MFC], writing to
- classes [MFC], connections
- HTTP [MFC], prerequisites for Internet clients
- connections [MFC], classes for
- Internet client class prerequisites [MFC]
- files [MFC], reading
- URLs [MFC], Internet client applications
- prerequisites, Internet client classes [MFC]
- Gopher client applications [MFC]
ms.assetid: c51d1dfe-260c-4228-8100-e4efd90e9599
ms.openlocfilehash: aaf5756df69728e8ae89fb278bc0671bfc6840b7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619833"
---
# <a name="prerequisites-for-internet-client-classes"></a>Composants requis pour les classes clientes Internet

Certaines actions effectuées par un client Internet (par exemple, la lecture d’un fichier) comportent des actions prérequises (dans ce cas, l’établissement d’une connexion Internet). Les tableaux suivants répertorient les conditions préalables pour certaines actions du client.

### <a name="general-internet-url-ftp-gopher-or-http"></a>URL Internet générale (FTP, Gopher ou HTTP)

|Action|Prérequis|
|------------|------------------|
|Établissez une connexion.|Créez un [CInternetSession](reference/cinternetsession-class.md) pour établir la base d’une application cliente Internet.|
|Ouvrez une URL.|Établissez une connexion. Appelez [CInternetSession :: OpenURL](reference/cinternetsession-class.md#openurl). La `OpenURL` fonction retourne un objet de ressource en lecture seule.|
|Lire les données d’URL.|Ouvrez l’URL. Appelez [CInternetFile :: Read](reference/cinternetfile-class.md#read).|
|Définissez une option Internet.|Établissez une connexion. Appelez [CInternetSession :: SetOption](reference/cinternetsession-class.md#setoption).|
|Définissez une fonction à appeler avec les informations d’État.|Établissez une connexion. Appelez [CInternetSession :: EnableStatusCallback](reference/cinternetsession-class.md#enablestatuscallback). Substituez [CInternetSession :: OnStatusCallback](reference/cinternetsession-class.md#onstatuscallback) pour gérer les appels.|

### <a name="ftp"></a>FTP

|Action|Prérequis|
|------------|------------------|
|Établissez une connexion FTP.|Créez un [CInternetSession](reference/cinternetsession-class.md) en tant que base de cette application cliente Internet. Appelez [CInternetSession :: GetFtpConnection](reference/cinternetsession-class.md#getftpconnection) pour créer un objet [CFtpConnection](reference/cftpconnection-class.md) .|
|Recherchez la première ressource.|Établissez une connexion FTP. Créez un objet [CFtpFileFind](reference/cftpfilefind-class.md) . Appelez [CFtpFileFind :: FindFile](reference/cftpfilefind-class.md#findfile).|
|Énumérer toutes les ressources disponibles.|Recherche le premier fichier. Appelez [CFtpFileFind :: FindNextFile](reference/cftpfilefind-class.md#findnextfile) jusqu’à ce qu’il retourne false.|
|Ouvrez un fichier FTP.|Établissez une connexion FTP. Appelez [CFtpConnection :: OpenFile](reference/cftpconnection-class.md#openfile) pour créer et ouvrir un objet [CInternetFile](reference/cinternetfile-class.md) .|
|Lire un fichier FTP.|Ouvrez un fichier FTP avec accès en lecture. Appelez [CInternetFile :: Read](reference/cinternetfile-class.md#read).|
|Écrire dans un fichier FTP.|Ouvrez un fichier FTP avec un accès en écriture. Appelez [CInternetFile :: Write](reference/cinternetfile-class.md#write).|
|Modifiez le répertoire du client sur le serveur.|Établissez une connexion FTP. Appelez [CFtpConnection :: SetCurrentDirectory](reference/cftpconnection-class.md#setcurrentdirectory).|
|Récupérez le répertoire actuel du client sur le serveur.|Établissez une connexion FTP. Appelez [CFtpConnection :: GetCurrentDirectory](reference/cftpconnection-class.md#getcurrentdirectory).|

### <a name="http"></a>HTTP

|Action|Prérequis|
|------------|------------------|
|Établissez une connexion HTTP.|Créez un [CInternetSession](reference/cinternetsession-class.md) en tant que base de cette application cliente Internet. Appelez [CInternetSession :: GetHttpConnection](reference/cinternetsession-class.md#gethttpconnection) pour créer un objet [CHttpConnection](reference/chttpconnection-class.md) .|
|Ouvrez un fichier HTTP.|Établissez une connexion HTTP. Appelez [CHttpConnection :: OpenRequest](reference/chttpconnection-class.md#openrequest) pour créer un objet [CHttpFile](reference/chttpfile-class.md) . Appelez [CHttpFile :: AddRequestHeaders](reference/chttpfile-class.md#addrequestheaders). Appelez [CHttpFile :: SendRequest](reference/chttpfile-class.md#sendrequest).|
|Lire un fichier HTTP.|Ouvrez un fichier HTTP. Appelez [CInternetFile :: Read](reference/cinternetfile-class.md#read).|
|Obtenir des informations sur une requête HTTP.|Établissez une connexion HTTP. Appelez [CHttpConnection :: OpenRequest](reference/chttpconnection-class.md#openrequest) pour créer un objet [CHttpFile](reference/chttpfile-class.md) . Appelez [CHttpFile :: QueryInfo](reference/chttpfile-class.md#queryinfo).|

### <a name="gopher"></a>Gopher

|Action|Prérequis|
|------------|------------------|
|Établissez une connexion Gopher.|Créez un [CInternetSession](reference/cinternetsession-class.md) en tant que base de cette application cliente Internet. Appelez [CInternetSession :: GetGopherConnection](reference/cinternetsession-class.md#getgopherconnection) pour créer un [CGopherConnection](reference/cgopherconnection-class.md).|
|Recherche le premier fichier dans le répertoire actif.|Établissez une connexion Gopher. Créez un objet [CGopherFileFind](reference/cgopherfilefind-class.md) . Appelez [CGopherConnection :: CreateLocator](reference/cgopherconnection-class.md#createlocator) pour créer un objet [CGopherLocator](reference/cgopherlocator-class.md) . Transmettez le localisateur à [CGopherFileFind :: FindFile](reference/cgopherfilefind-class.md#findfile). Appelez [CGopherFileFind :: GetLocator](reference/cgopherfilefind-class.md#getlocator) pour obtenir le Localisateur d’un fichier si vous en avez besoin ultérieurement.|
|Énumérer tous les fichiers disponibles.|Recherche le premier fichier. Appelez [CGopherFileFind :: FindNextFile](reference/cgopherfilefind-class.md#findnextfile) jusqu’à ce qu’il retourne false.|
|Ouvrez un fichier Gopher.|Établissez une connexion Gopher. Créez un localisateur Gopher avec [CGopherConnection :: CreateLocator](reference/cgopherconnection-class.md#createlocator) ou recherchez un localisateur avec [CGopherFileFind :: GetLocator](reference/cgopherfilefind-class.md#getlocator). Appelez [CGopherConnection :: OpenFile](reference/cgopherconnection-class.md#openfile).|
|Lire un fichier Gopher.|Ouvrez un fichier Gopher. Utilisez [CGopherFile](reference/cgopherfile-class.md).|

## <a name="see-also"></a>Voir aussi

[Extension Internet Win32 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[Classes MFC pour la création d’applications clientes Internet](mfc-classes-for-creating-internet-client-applications.md)<br/>
[Écriture d’une application cliente Internet en utilisant des classes WinInet MFC](writing-an-internet-client-application-using-mfc-wininet-classes.md)
