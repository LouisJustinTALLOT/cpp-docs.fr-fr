---
description: 'En savoir plus sur : la manière dont MFC facilite la création d’applications clientes Internet'
title: Comment MFC facilite la création d'applications clientes Internet
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], MFC
- Internet applications [MFC], MFC
- MFC, Internet applications
ms.assetid: 94437b3f-f15c-437d-b5fd-264a2efec9ab
ms.openlocfilehash: 7cc201c67cf4964e5bd561cd173186bc57feb89b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343600"
---
# <a name="how-mfc-makes-it-easier-to-create-internet-client-applications"></a>Comment MFC facilite la création d'applications clientes Internet

Les Microsoft Foundation Classes encapsulent les fonctions de l’extension Internet Win32 (WinInet) de manière à fournir un contexte familier aux programmeurs MFC. MFC fournit trois classes de fichiers Internet ([CInternetFile](reference/cinternetfile-class.md), [CHttpFile](reference/chttpfile-class.md)et [CGopherFile](reference/cgopherfile-class.md)) dérivées de la classe [CStdioFile](reference/cstdiofile-class.md) . Non seulement ces classes permettent d’extraire et de manipuler des données Internet familières aux programmeurs qui ont utilisé `CStdioFile` pour les fichiers locaux, mais avec ces classes, vous pouvez gérer des fichiers locaux et des fichiers Internet de manière cohérente et transparente.

Les classes WinInet MFC fournissent les mêmes fonctionnalités que `CStdioFile` pour les données transférées sur Internet. Ces classes font abstraction des protocoles Internet pour HTTP, FTP et Gopher dans une interface de programmation d’applications de haut niveau, ce qui fournit un chemin simple et rapide pour rendre les applications sensibles à Internet. Par exemple, la connexion à un serveur FTP requiert toujours plusieurs étapes à un niveau bas, mais en tant que développeur MFC, vous devez effectuer un seul appel à `CInternetSession::GetFTPConnection` pour créer cette connexion.

En outre, les classes WinInet MFC présentent les avantages suivants :

- E/s mises en mémoire tampon

- Handles de type sécurisé pour vos données

- Paramètres par défaut pour de nombreuses fonctions

- Gestion des exceptions pour les erreurs Internet courantes

- Nettoyage automatique des handles et des connexions ouverts

## <a name="see-also"></a>Voir aussi

[Extensions Internet Win32 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[Comment WinInet facilite la création d’applications clientes Internet](how-wininet-makes-it-easier-to-create-internet-client-applications.md)
