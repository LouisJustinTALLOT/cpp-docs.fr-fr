---
description: En savoir plus sur les étapes d’une application cliente HTTP standard
title: Étapes dans une application cliente HTTP classique
ms.date: 11/04/2016
helpviewer_keywords:
- HTTP client applications [MFC]
- client applications [MFC], HTTP
- Internet applications [MFC], HTTP client applications
- applications [MFC], HTTP client
- Internet client applications [MFC], HTTP table
- WinInet classes [MFC], HTTP
ms.assetid: f86552e8-8acd-4b23-bdc5-0c3a247ebd74
ms.openlocfilehash: 0f08ca7629c389df67b579b8c20acceeb16b0cd3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216598"
---
# <a name="steps-in-a-typical-http-client-application"></a>Étapes dans une application cliente HTTP classique

Le tableau suivant présente les étapes que vous pouvez effectuer dans une application cliente HTTP standard :

|Votre objectif|Actions que vous effectuez|Effects (Effets)|
|---------------|----------------------|-------------|
|Commencez une session HTTP.|Créez un objet [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Initialise WinInet et se connecte au serveur.|
|Connectez-vous à un serveur HTTP.|Utilisez [CInternetSession :: GetHttpConnection](../mfc/reference/cinternetsession-class.md#gethttpconnection).|Retourne un objet [CHttpConnection](../mfc/reference/chttpconnection-class.md) .|
|Ouvrez une requête HTTP.|Utilisez [CHttpConnection :: OpenRequest](../mfc/reference/chttpconnection-class.md#openrequest).|Retourne un objet [CHttpFile](../mfc/reference/chttpfile-class.md) .|
|Envoyer une requête HTTP.|Utilisez [CHttpFile :: AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders) et [CHttpFile :: SendRequest](../mfc/reference/chttpfile-class.md#sendrequest).|Recherche le fichier. Retourne la valeur FALSe si le fichier est introuvable.|
|Lire à partir du fichier.|Utilisez [CHttpFile](../mfc/reference/chttpfile-class.md).|Lit le nombre d’octets spécifié à l’aide d’une mémoire tampon que vous fournissez.|
|Traitez les exceptions.|Utilisez la classe [CInternetException](../mfc/reference/cinternetexception-class.md) .|Gère tous les types d’exceptions Internet courants.|
|Mettez fin à la session HTTP.|Supprime l’objet [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Nettoie automatiquement les descripteurs de fichiers ouverts et les connexions.|

## <a name="see-also"></a>Voir aussi

[Extensions Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Conditions préalables pour les classes clientes Internet](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Écriture d’une application cliente Internet à l’aide de classes WinInet MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
