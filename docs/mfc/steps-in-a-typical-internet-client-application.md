---
title: Les étapes dans une Application cliente Internet classique | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Internet client applications [MFC], general table
- WinInet classes [MFC], programming
- Internet applications [MFC], client applications
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1c7a7053b8378ea62dc0291dba1b79b794dd099
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381272"
---
# <a name="steps-in-a-typical-internet-client-application"></a>Étapes dans une application cliente Internet classique
Le tableau suivant montre les étapes que vous pouvez effectuer dans une application cliente de type Internet.  
  
|Votre objectif|Actions que vous effectuez|Effects (Effets)|  
|---------------|----------------------|-------------|  
|Ouvrir une session Internet.|Créer un [CInternetSession](../mfc/reference/cinternetsession-class.md) objet.|Initialise WinInet et se connecte au serveur.|  
|Définir une option de requête Internet (limite de délai d’attente ou nombre de tentatives, par exemple).|Utilisez [CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption).|Retourne FALSE si l’opération a échoué.|  
|Établir une fonction de rappel pour surveiller l’état de la session.|Utilisez [CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback).|Établit un rappel à [CInternetSession::OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback). Substituer `OnStatusCallback` pour créer votre propre routine de rappel.|  
|Se connecter à un serveur Internet, le serveur intranet ou le fichier local.|Utilisez [CInternetSession::OpenURL](../mfc/reference/cinternetsession-class.md#openurl).|Analyse de l’URL et ouvre une connexion au serveur spécifié. Retourne un [CStdioFile](../mfc/reference/cstdiofile-class.md) (si vous passez `OpenURL` un nom de fichier local). Il s’agit de l’objet par le biais duquel vous accéder aux données récupérées du serveur ou du fichier.|  
|Lire à partir du fichier.|Utilisez [CInternetFile::Read](../mfc/reference/cinternetfile-class.md#read).|Lit le nombre spécifié d’octets à l’aide d’un tampon que vous fournissez.|  
|Gestion des exceptions.|Utilisez le [CInternetException](../mfc/reference/cinternetexception-class.md) classe.|Gère tous les types d’exceptions Internet courants.|  
|Terminer une session Internet.|Supprimer le [CInternetSession](../mfc/reference/cinternetsession-class.md) objet.|Nettoie automatiquement les connexions et les descripteurs de fichiers ouverts.|  
  
## <a name="see-also"></a>Voir aussi  
 [Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)   
 [Conditions préalables pour les Classes clientes Internet](../mfc/prerequisites-for-internet-client-classes.md)   
 [Écriture d’une application cliente Internet en utilisant des classes WinInet MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
