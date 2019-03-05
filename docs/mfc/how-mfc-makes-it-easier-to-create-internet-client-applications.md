---
title: Comment MFC facilite la création d'applications clientes Internet
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
- MFC, Internet applications
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
ms.openlocfilehash: ffeed3a844fb86acf1bf8c5181c59529824c27f9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300738"
---
# <a name="how-mfc-makes-it-easier-to-create-internet-client-applications"></a>Comment MFC facilite la création d'applications clientes Internet

Microsoft Foundation Classes encapsulent les fonctions d’Extension Win32 Internet (WinInet) d’une manière qui fournit un contexte familier aux programmeurs MFC. MFC fournit trois classes de fichier Internet ([CInternetFile](../mfc/reference/cinternetfile-class.md), [CHttpFile](../mfc/reference/chttpfile-class.md), et [CGopherFile](../mfc/reference/cgopherfile-class.md)) dérivées de la [CStdioFile](../mfc/reference/cstdiofile-class.md) classe . Non seulement ces classes apporter extraction et la manipulation de données Internet familier aux programmeurs qui ont utilisé `CStdioFile` pour les fichiers locaux, mais avec ces classes vous pouvez gérer les fichiers locaux et les fichiers Internet de manière cohérente et transparente.

Les classes WinInet MFC fournissent les mêmes fonctionnalités que `CStdioFile` pour les données transférées sur Internet. Ces classes abstraites les protocoles Internet pour HTTP, FTP et gopher dans une application de haut niveau interface de programmation, en fournissant un chemin d’accès rapide et simple pour la création d’applications Internet. Par exemple, connexion à un serveur FTP requiert toujours plusieurs étapes de bas niveau, mais qu’un développeur MFC, vous devez uniquement effectuer un appel à `CInternetSession::GetFTPConnection` pour créer cette connexion.

En outre, les classes WinInet MFC offrent les avantages suivants :

- E/s mises en mémoire tampon

- Descripteurs de type sécurisé pour vos données

- Paramètres par défaut pour de nombreuses fonctions

- Gestion des exceptions pour les erreurs liées à Internet

- Nettoyage automatique des connexions et descripteurs ouverts

## <a name="see-also"></a>Voir aussi

[Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Comment WinInet facilite la création d’applications clientes Internet](../mfc/how-wininet-makes-it-easier-to-create-internet-client-applications.md)
