---
title: Les étapes dans une Application cliente HTTP classique | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTTP client applications [MFC]
- client applications [MFC], HTTP
- Internet applications [MFC], HTTP client applications
- applications [MFC], HTTP client
- Internet client applications [MFC], HTTP table
- WinInet classes [MFC], HTTP
ms.assetid: f86552e8-8acd-4b23-bdc5-0c3a247ebd74
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c25402662296a9ebf2f15fe902dcefabb9d47073
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380956"
---
# <a name="steps-in-a-typical-http-client-application"></a>Étapes dans une application cliente HTTP classique
Le tableau suivant montre les étapes que vous pouvez effectuer dans une application cliente de type HTTP :  
  
|Votre objectif|Actions que vous effectuez|Effects (Effets)|  
|---------------|----------------------|-------------|  
|Ouvrir une session HTTP.|Créer un [CInternetSession](../mfc/reference/cinternetsession-class.md) objet.|Initialise WinInet et se connecte au serveur.|  
|Se connecter à un serveur HTTP.|Utilisez [CInternetSession::GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection).|Retourne un [objet CHttpConnection](../mfc/reference/chttpconnection-class.md) objet.|  
|Ouvrez une requête HTTP.|Utilisez [CHttpConnection::OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest).|Retourne un [CHttpFile](../mfc/reference/chttpfile-class.md) objet.|  
|Envoie une requête HTTP.|Utilisez [CHttpFile::AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders) et [CHttpFile::SendRequest](../mfc/reference/chttpfile-class.md#sendrequest).|Recherche le fichier. Retourne FALSE si le fichier est introuvable.|  
|Lire à partir du fichier.|Utilisez [CHttpFile](../mfc/reference/chttpfile-class.md).|Lit le nombre spécifié d’octets à l’aide d’un tampon que vous fournissez.|  
|Gestion des exceptions.|Utilisez le [CInternetException](../mfc/reference/cinternetexception-class.md) classe.|Gère tous les types d’exceptions Internet courants.|  
|Terminer la session HTTP.|Supprimer le [CInternetSession](../mfc/reference/cinternetsession-class.md) objet.|Nettoie automatiquement les connexions et les descripteurs de fichiers ouverts.|  
  
## <a name="see-also"></a>Voir aussi  
 [Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Conditions préalables pour les Classes clientes Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Écriture d’une application cliente Internet en utilisant des classes WinInet MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
