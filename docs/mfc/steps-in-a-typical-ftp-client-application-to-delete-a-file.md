---
title: "Les étapes dans une Application cliente FTP classique pour supprimer un fichier | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC], FTP delete
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 2c347a96-c0a4-4827-98fe-668406e552bc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 77fecfb9c11c95d14c8816fe1c3b23046eae98c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="steps-in-a-typical-ftp-client-application-to-delete-a-file"></a>Étapes pour supprimer un fichier dans une application cliente FTP classique
Le tableau suivant décrit les étapes que vous pouvez effectuer dans une application cliente FTP classique qui supprime un fichier.  
  
|Votre objectif|Actions que vous effectuez|Effects (Effets)|  
|---------------|----------------------|-------------|  
|Ouvrir une session FTP.|Créer un [CInternetSession](../mfc/reference/cinternetsession-class.md) objet.|Initialise WinInet et se connecte au serveur.|  
|Se connecter à un serveur FTP.|Utilisez [CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection).|Retourne un [CFtpConnection](../mfc/reference/cftpconnection-class.md) objet.|  
|Vérifiez que vous êtes dans le répertoire correct sur le serveur FTP.|Utilisez [CFtpConnection::GetCurrentDirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory) ou [CFtpConnection::GetCurrentDirectoryAsURL](../mfc/reference/cftpconnection-class.md#getcurrentdirectoryasurl).|Retourne le nom ou l’URL de l’annuaire que vous êtes connecté sur le serveur, en fonction de la fonction membre sélectionné.|  
|Remplacez par un nouveau répertoire FTP sur le serveur.|Utilisez [CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory).|Change le répertoire que vous êtes connecté sur le serveur.|  
|Rechercher le premier fichier dans le répertoire FTP.|Utilisez [CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile).|Recherche le premier fichier. Si aucun fichier n’est trouvé, retourne FALSE.|  
|Recherchez le fichier suivant dans le répertoire FTP.|Utilisez [CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile).|Recherche le fichier suivant. Retourne FALSE si le fichier est introuvable.|  
|Supprimer le fichier trouvé par **FindFile** ou `FindNextFile`.|Utilisez [CFtpConnection::Remove](../mfc/reference/cftpconnection-class.md#remove), en utilisant le nom de fichier retourné par **FindFile** ou `FindNextFile`.|Supprime le fichier sur le serveur pour lire ou écrire.|  
|Gestion des exceptions.|Utilisez le [CInternetException](../mfc/reference/cinternetexception-class.md) classe.|Gère tous les types d’exceptions Internet courants.|  
|Terminer la session FTP.|Supprimer le [CInternetSession](../mfc/reference/cinternetsession-class.md) objet.|Nettoie automatiquement les connexions et les descripteurs de fichiers ouverts.|  
  
## <a name="see-also"></a>Voir aussi  
 [Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Conditions préalables pour les Classes clientes Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Écriture d’une application cliente Internet en utilisant des classes WinInet MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
