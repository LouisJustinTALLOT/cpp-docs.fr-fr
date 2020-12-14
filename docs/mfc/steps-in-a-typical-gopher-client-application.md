---
description: En savoir plus sur les étapes d’une application cliente Gopher classique
title: Étapes dans une application cliente Gopher classique
ms.date: 11/04/2016
helpviewer_keywords:
- WinInet classes [MFC], gopher
- Internet applications [MFC], gopher client applications
- Gopher client applications [MFC]
- Internet client applications [MFC], gopher table
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
ms.openlocfilehash: 23940457acf52009b6d334deec129324a53a7583
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216624"
---
# <a name="steps-in-a-typical-gopher-client-application"></a>Étapes dans une application cliente Gopher classique

Le tableau suivant présente les étapes que vous pouvez effectuer dans une application cliente Gopher classique.

|Votre objectif|Actions que vous effectuez|Effects (Effets)|
|---------------|----------------------|-------------|
|Commencez une session Gopher.|Créez un objet [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Initialise WinInet et se connecte au serveur.|
|Connectez-vous à un serveur Gopher.|Utilisez [CInternetSession :: GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection).|Retourne un objet [CGopherConnection](../mfc/reference/cgopherconnection-class.md) .|
|Recherchez la première ressource dans le Gopher.|Utilisez [CGopherFileFind :: FindFile](../mfc/reference/cgopherfilefind-class.md#findfile).|Recherche le premier fichier. Retourne la valeur FALSe si aucun fichier n’est trouvé.|
|Recherchez la ressource suivante dans le Gopher.|Utilisez [CGopherFileFind :: FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile).|Recherche le fichier suivant. Retourne la valeur FALSe si le fichier est introuvable.|
|Ouvrez le fichier trouvé par `FindFile` ou `FindNextFile` pour la lecture.|Obtenir un localisateur Gopher à l’aide de [CGopherFileFind :: GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Utilisez [CGopherConnection :: OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Ouvre le fichier spécifié par le localisateur. `OpenFile` retourne un objet [CGopherFile](../mfc/reference/cgopherfile-class.md) .|
|Ouvrez un fichier à l’aide d’un localisateur Gopher que vous fournissez.|Créez un localisateur Gopher à l’aide de [CGopherConnection :: CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator). Utilisez [CGopherConnection :: OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Ouvre le fichier spécifié par le localisateur. `OpenFile` retourne un objet [CGopherFile](../mfc/reference/cgopherfile-class.md) .|
|Lire à partir du fichier.|Utilisez [CGopherFile](../mfc/reference/cgopherfile-class.md).|Lit le nombre d’octets spécifié, à l’aide d’une mémoire tampon que vous fournissez.|
|Traitez les exceptions.|Utilisez la classe [CInternetException](../mfc/reference/cinternetexception-class.md) .|Gère tous les types d’exceptions Internet courants.|
|Mettez fin à la session Gopher.|Supprime l’objet [CInternetSession](../mfc/reference/cinternetsession-class.md) .|Nettoie automatiquement les descripteurs de fichiers ouverts et les connexions.|

## <a name="see-also"></a>Voir aussi

[Extensions Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Conditions préalables pour les classes clientes Internet](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Écriture d’une application cliente Internet à l’aide de classes WinInet MFC](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
