---
description: 'En savoir plus sur : Comment WinInet simplifie la création d’applications clientes Internet'
title: Comment WinInet facilite la création d'applications clientes Internet
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
ms.openlocfilehash: efee0b201a165fab8aaf838eedb2ba83b9a5b946
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330130"
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>Comment WinInet facilite la création d'applications clientes Internet

Les extensions Internet Win32, ou WinInet, permettent d’accéder aux protocoles Internet courants, y compris Gopher, FTP et HTTP. À l’aide de WinInet, vous pouvez écrire des applications clientes Internet à un niveau plus élevé de programmation, sans avoir à gérer WinSock, TCP/IP ou les détails de protocoles Internet spécifiques. WinInet fournit un ensemble cohérent de fonctions pour les trois protocoles, avec une interface API Win32 familière. Cette cohérence minimise les modifications de code que vous devez apporter si le protocole sous-jacent change (par exemple, de FTP à HTTP).

Visual C++ offre deux façons d’utiliser WinInet. Vous pouvez appeler les fonctions Internet Win32 directement (consultez la documentation OLE dans le SDK Windows pour plus d’informations) ou vous pouvez utiliser WinInet par le biais des [classes WinInet MFC](mfc-classes-for-creating-internet-client-applications.md).

**Vous pouvez utiliser WinInet pour :**

- Téléchargez des pages HTML.

   HTTP est un protocole utilisé pour transférer des pages HTML d’un serveur vers un navigateur client.

- Envoyer des demandes FTP pour télécharger des fichiers ou récupérer des listes de répertoires.

   Une requête classique est une ouverture de session anonyme pour télécharger un fichier.

- Utilisez le système de menu de Gopher pour accéder aux ressources sur Internet.

   Les éléments de menu peuvent être de plusieurs types, y compris d’autres menus, une base de données indexée que vous pouvez rechercher, un groupe de discussion ou un fichier.

Pour les trois protocoles, vous établissez une connexion, effectuez des demandes au serveur et fermez la connexion.

**Les classes WinInet MFC facilitent les opérations suivantes :**

- Lisez des informations à partir de serveurs HTTP, FTP et Gopher aussi facilement que pour lire des fichiers à partir d’un disque dur.

- Utilisez les protocoles HTTP, FTP et Gopher sans avoir à programmer directement vers WinSock ou TCP/IP.

   Les développeurs qui utilisent les fonctions Internet Win32 n’ont pas besoin d’être familiarisés avec TCP/IP ou Windows Sockets. Vous pouvez toujours programmer au niveau du socket, en utilisant directement les protocoles WinSock et TCP/IP, mais il est encore plus facile d’utiliser les classes WinInet MFC pour accéder aux protocoles HTTP, FTP et Gopher sur Internet. Pour de nombreuses opérations courantes, les développeurs n’ont pas besoin de connaître les détails du protocole particulier qu’ils utilisent.

De nombreuses opérations qui peuvent être effectuées par votre ordinateur en tant que client sur d’autres ordinateurs sur Internet peuvent prendre beaucoup de temps. La vitesse de ces opérations est généralement limitée par la vitesse de votre connexion réseau, mais elles peuvent également être affectées par un autre trafic réseau et la complexité de l’opération. La connexion à un serveur FTP distant, par exemple, nécessite que votre ordinateur recherche d’abord le nom de ce serveur pour trouver son adresse. Votre application tentera ensuite de se connecter au serveur à cette adresse. Une fois la connexion ouverte, votre ordinateur et le serveur distant initieront une conversation avec le protocole de transfert de fichiers avant que vous ne puissiez réellement utiliser la connexion pour récupérer des fichiers.

## <a name="see-also"></a>Voir aussi

[Extensions Internet Win32 (WinInet)](win32-internet-extensions-wininet.md)<br/>
[Comment MFC facilite la création d’applications clientes Internet](how-mfc-makes-it-easier-to-create-internet-client-applications.md)
