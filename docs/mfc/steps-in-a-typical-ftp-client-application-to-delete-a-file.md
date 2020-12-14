---
description: En savoir plus sur les étapes d’une application cliente FTP classique pour supprimer un fichier
title: Étapes pour supprimer un fichier dans une application cliente FTP classique
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], FTP delete
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 2c347a96-c0a4-4827-98fe-668406e552bc
ms.openlocfilehash: 0de5ba71ac127a44c964571d243997bcb49faaa0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216650"
---
# <a name="steps-in-a-typical-ftp-client-application-to-delete-a-file"></a>Étapes pour supprimer un fichier dans une application cliente FTP classique

Le tableau suivant présente les étapes que vous pouvez effectuer dans une application cliente FTP classique qui supprime un fichier.

|Votre objectif|Actions que vous effectuez|Effects (Effets)|
|---------------|----------------------|-------------|
|Commencez une session FTP.|Créez un objet [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Initialise WinInet et se connecte au serveur.|
|Établit une connexion à un serveur FTP.|Utilisez [CInternetSession :: GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Retourne un objet [CFtpConnection](../mfc/reference/cftpconnection-class.md) .|
|Vérifiez que vous êtes dans le répertoire approprié sur le serveur FTP.|Utilisez [CFtpConnection :: GetCurrentDirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory) ou [CFtpConnection :: GetCurrentDirectoryAsURL](../mfc/reference/cftpconnection-class.md#getcurrentdirectoryasurl).|Retourne le nom ou l’URL du répertoire auquel vous êtes actuellement connecté sur le serveur, en fonction de la fonction membre sélectionnée.|
|Accédez à un nouveau répertoire FTP sur le serveur.|Utilisez [CFtpConnection :: SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Modifie le répertoire auquel vous êtes actuellement connecté sur le serveur.|
|Recherchez le premier fichier dans le répertoire FTP.|Utilisez [CFtpFileFind :: FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Recherche le premier fichier. Retourne la valeur FALSe si aucun fichier n’est trouvé.|
|Recherchez le fichier suivant dans le répertoire FTP.|Utilisez [CFtpFileFind :: FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Recherche le fichier suivant. Retourne la valeur FALSe si le fichier est introuvable.|
|Supprimez le fichier trouvé par `FindFile` ou `FindNextFile` .|Utilisez [CFtpConnection :: Remove](../mfc/reference/cftpconnection-class.md#remove), en utilisant le nom de fichier retourné par `FindFile` ou `FindNextFile` .|Supprime le fichier sur le serveur pour la lecture ou l’écriture.|
|Traitez les exceptions.|Utilisez la classe [CInternetException](../mfc/reference/cinternetexception-class.md) .|Gère tous les types d’exceptions Internet courants.|
|Mettez fin à la session FTP.|Supprime l’objet [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Nettoie automatiquement les descripteurs de fichiers ouverts et les connexions.|

## <a name="see-also"></a>Voir aussi

[Extensions Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Conditions préalables pour les classes clientes Internet](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Écriture d’une application cliente Internet à l’aide de classes WinInet MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
