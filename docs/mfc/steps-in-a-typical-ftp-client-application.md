---
title: Les étapes dans une Application cliente FTP classique | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC], FTP table
- FTP (File Transfer Protocol)
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fe5a55afda9e77db6e8baddd68c09f4250071bb
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951199"
---
# <a name="steps-in-a-typical-ftp-client-application"></a>Étapes dans une application cliente FTP classique
Une application cliente de type FTP crée un [CInternetSession](../mfc/reference/cinternetsession-class.md) et un [CFtpConnection](../mfc/reference/cftpconnection-class.md) objet. Notez que ces classes WinInet MFC ne contrôlent pas réellement les paramètres de type proxy ; IIS effectue.  
  
 En outre, consultez les articles de la Base de connaissances :  
  
-   Comment faire : Utiliser FTP avec un Proxy CERN utilisant une API WinInet (ID d’Article : Q166961)  
  
-   EXEMPLE : FTP avec mot de passe CERN protégé Proxy (ID d’Article : Q216214)  
  
-   Manager ne parvient pas à afficher les Services Proxy installé des Services Internet (ID d’Article : Q216802)  
  
 Le tableau suivant montre les étapes que vous pouvez effectuer dans une application cliente de type FTP.  
  
|Votre objectif|Actions que vous effectuez|Effects (Effets)|  
|---------------|----------------------|-------------|  
|Ouvrir une session FTP.|Créer un [CInternetSession](../mfc/reference/cinternetsession-class.md) objet.|Initialise WinInet et se connecte au serveur.|  
|Se connecter à un serveur FTP.|Utilisez [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Retourne un [CFtpConnection](../mfc/reference/cftpconnection-class.md) objet.|  
|Remplacez par un nouveau répertoire FTP sur le serveur.|Utilisez [CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Change le répertoire que vous êtes connecté sur le serveur.|  
|Rechercher le premier fichier dans le répertoire FTP.|Utilisez [CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Recherche le premier fichier. Si aucun fichier n’est trouvé, retourne FALSE.|  
|Recherchez le fichier suivant dans le répertoire FTP.|Utilisez [CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Recherche le fichier suivant. Retourne FALSE si le fichier est introuvable.|  
|Ouvrez le fichier trouvé par `FindFile` ou `FindNextFile` pour lire ou écrire.|Utilisez [CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile), en utilisant le nom de fichier retourné par [FindFile](../mfc/reference/cftpfilefind-class.md#findfile) ou [FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Ouvre le fichier sur le serveur pour lire ou écrire. Retourne un [CInternetFile](../mfc/reference/cinternetfile-class.md) objet.|  
|Lire ou écrire dans le fichier.|Utilisez [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read) ou [CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write).|Lit ou écrit le nombre spécifié d’octets, à l’aide d’un tampon que vous fournissez.|  
|Gestion des exceptions.|Utilisez le [CInternetException](../mfc/reference/cinternetexception-class.md) classe.|Gère tous les types d’exceptions Internet courants.|  
|Terminer la session FTP.|Supprimer le [CInternetSession](../mfc/reference/cinternetsession-class.md) objet.|Nettoie automatiquement les connexions et les descripteurs de fichiers ouverts.|  
  
## <a name="see-also"></a>Voir aussi  
 [Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Conditions préalables pour les Classes clientes Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Écriture d’une application cliente Internet en utilisant des classes WinInet MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
