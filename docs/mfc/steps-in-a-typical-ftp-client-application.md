---
description: En savoir plus sur les étapes d’une application cliente FTP classique
title: Étapes dans une application cliente FTP classique
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], FTP table
- FTP (File Transfer Protocol)
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
ms.openlocfilehash: caac613adf3ad886c4b36ae567a3b8c5c928ee10
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216637"
---
# <a name="steps-in-a-typical-ftp-client-application"></a>Étapes dans une application cliente FTP classique

Une application cliente FTP classique crée un [CInternetSession](../mfc/reference/cinternetsession-class.md) et un objet [CFtpConnection](../mfc/reference/cftpconnection-class.md) . Notez que ces classes WinInet MFC ne contrôlent pas réellement les paramètres de type de proxy ; IIS.

Le tableau suivant présente les étapes que vous pouvez effectuer dans une application cliente FTP classique.

|Votre objectif|Actions que vous effectuez|Effects (Effets)|
|---------------|----------------------|-------------|
|Commencez une session FTP.|Créez un objet [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Initialise WinInet et se connecte au serveur.|
|Établit une connexion à un serveur FTP.|Utilisez [CInternetSession :: GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Retourne un objet [CFtpConnection](../mfc/reference/cftpconnection-class.md) .|
|Accédez à un nouveau répertoire FTP sur le serveur.|Utilisez [CFtpConnection :: SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Modifie le répertoire auquel vous êtes actuellement connecté sur le serveur.|
|Recherchez le premier fichier dans le répertoire FTP.|Utilisez [CFtpFileFind :: FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Recherche le premier fichier. Retourne la valeur FALSe si aucun fichier n’est trouvé.|
|Recherchez le fichier suivant dans le répertoire FTP.|Utilisez [CFtpFileFind :: FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Recherche le fichier suivant. Retourne la valeur FALSe si le fichier est introuvable.|
|Ouvrez le fichier trouvé par `FindFile` ou `FindNextFile` pour la lecture ou l’écriture.|Utilisez [CFtpConnection :: OpenFile](../mfc/reference/cftpconnection-class.md#openfile), en utilisant le nom de fichier retourné par [FindFile](../mfc/reference/cftpfilefind-class.md#findfile) ou [FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Ouvre le fichier sur le serveur pour la lecture ou l’écriture. Retourne un objet [CInternetFile](../mfc/reference/cinternetfile-class.md) .|
|Lire ou écrire dans le fichier.|Utilisez [CInternetFile :: Read](../mfc/reference/cinternetfile-class.md#read) ou [CInternetFile :: Write](../mfc/reference/cinternetfile-class.md#write).|Lit ou écrit le nombre d’octets spécifié, à l’aide d’une mémoire tampon que vous fournissez.|
|Traitez les exceptions.|Utilisez la classe [CInternetException](../mfc/reference/cinternetexception-class.md) .|Gère tous les types d’exceptions Internet courants.|
|Mettez fin à la session FTP.|Supprime l’objet [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Nettoie automatiquement les descripteurs de fichiers ouverts et les connexions.|

## <a name="see-also"></a>Voir aussi

[Extensions Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Conditions préalables pour les classes clientes Internet](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Écriture d’une application cliente Internet à l’aide de classes WinInet MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
