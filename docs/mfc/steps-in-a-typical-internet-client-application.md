---
description: En savoir plus sur les étapes d’une application cliente Internet classique
title: Étapes dans une application cliente Internet classique
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], general table
- WinInet classes [MFC], programming
- Internet applications [MFC], client applications
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
ms.openlocfilehash: 9660687136361efb0256ecdd1fd19b577c46ab26
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216546"
---
# <a name="steps-in-a-typical-internet-client-application"></a>Étapes dans une application cliente Internet classique

Le tableau suivant présente les étapes que vous pouvez effectuer dans une application cliente Internet classique.

|Votre objectif|Actions que vous effectuez|Effects (Effets)|
|---------------|----------------------|-------------|
|Commencez une session Internet.|Créez un objet [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Initialise WinInet et se connecte au serveur.|
|Définissez une option de requête Internet (limite de délai d’attente ou nombre de nouvelles tentatives, par exemple).|Utilisez [CInternetSession :: SetOption](../mfc/reference/cinternetsession-class.md#setoption).|Retourne FALSe si l’opération a échoué.|
|Établissez une fonction de rappel pour surveiller l’état de la session.|Utilisez [CInternetSession :: EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback).|Établit un rappel à [CInternetSession :: OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback). Substituez `OnStatusCallback` pour créer votre propre routine de rappel.|
|Connectez-vous à un serveur Internet, un serveur intranet ou un fichier local.|Utilisez [CInternetSession :: OpenURL](../mfc/reference/cinternetsession-class.md#openurl).|Analyse l’URL et ouvre une connexion au serveur spécifié. Retourne un [CStdioFile](../mfc/reference/cstdiofile-class.md) (si vous transmettez `OpenURL` un nom de fichier local). Il s’agit de l’objet par le biais duquel vous accédez aux données récupérées à partir du serveur ou du fichier.|
|Lire à partir du fichier.|Utilisez [CInternetFile :: Read](../mfc/reference/cinternetfile-class.md#read).|Lit le nombre d’octets spécifié à l’aide d’une mémoire tampon que vous fournissez.|
|Traitez les exceptions.|Utilisez la classe [CInternetException](../mfc/reference/cinternetexception-class.md) .|Gère tous les types d’exceptions Internet courants.|
|Mettez fin à la session Internet.|Supprime l’objet [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Nettoie automatiquement les descripteurs de fichiers ouverts et les connexions.|

## <a name="see-also"></a>Voir aussi

[Extensions Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Conditions préalables pour les classes clientes Internet](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Écriture d’une application cliente Internet à l’aide de classes WinInet MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
