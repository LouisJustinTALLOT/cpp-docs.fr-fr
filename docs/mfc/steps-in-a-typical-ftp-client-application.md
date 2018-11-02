---
title: Étapes dans une application cliente FTP classique
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], FTP table
- FTP (File Transfer Protocol)
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
ms.openlocfilehash: ef772438558e5d587962242fdd7f1230cc2b2f25
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560184"
---
# <a name="steps-in-a-typical-ftp-client-application"></a>Étapes dans une application cliente FTP classique

Crée une application de client FTP typique un [CInternetSession](../mfc/reference/cinternetsession-class.md) et un [CFtpConnection](../mfc/reference/cftpconnection-class.md) objet. Notez que ces classes WinInet MFC ne contrôlent pas réellement les paramètres de type proxy ; IIS se charge.

Le tableau suivant montre les étapes que vous pouvez effectuer dans une application de client FTP typique.

|Votre objectif|Actions que vous effectuez|Effects (Effets)|
|---------------|----------------------|-------------|
|Ouvrir une session FTP.|Créer un [CInternetSession](../mfc/reference/cinternetsession-class.md) objet.|Initialise WinInet et se connecte au serveur.|
|Se connecter à un serveur FTP.|Utilisez [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Retourne un [CFtpConnection](../mfc/reference/cftpconnection-class.md) objet.|
|Remplacez par un nouveau répertoire FTP sur le serveur.|Utilisez [CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Change le répertoire que vous êtes actuellement connecté à sur le serveur.|
|Rechercher le premier fichier dans le répertoire FTP.|Utilisez [CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Recherche le premier fichier. Retourne FALSE si aucun fichier n’est trouvé.|
|Recherchez le fichier suivant dans le répertoire FTP.|Utilisez [CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Recherche le fichier suivant. Retourne FALSE si le fichier est introuvable.|
|Ouvrez le fichier trouvé par `FindFile` ou `FindNextFile` pour lire ou écrire.|Utilisez [CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile), en utilisant le nom de fichier retourné par [FindFile](../mfc/reference/cftpfilefind-class.md#findfile) ou [FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Ouvre le fichier sur le serveur pour lire ou écrire. Retourne un [CInternetFile](../mfc/reference/cinternetfile-class.md) objet.|
|Lire ou écrire dans le fichier.|Utilisez [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read) ou [CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write).|Lit ou écrit le nombre spécifié d’octets, à l’aide d’une mémoire tampon que vous fournissez.|
|Gestion des exceptions.|Utilisez le [CInternetException](../mfc/reference/cinternetexception-class.md) classe.|Gère tous les types d’exception Internet courants.|
|Fin de la session FTP.|Supprimer le [CInternetSession](../mfc/reference/cinternetsession-class.md) objet.|Nettoie automatiquement les connexions et descripteurs de fichiers ouverts.|

## <a name="see-also"></a>Voir aussi

[Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Composants requis pour les classes clientes Internet](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Écriture d’une application cliente Internet en utilisant des classes WinInet MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
