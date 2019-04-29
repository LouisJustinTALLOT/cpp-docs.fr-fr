---
title: Comment WinInet facilite la création d'applications clientes Internet
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], vs. WinInet
- WinInet classes [MFC], vs. WinSock
- WinInet classes [MFC], Internet client applications
ms.assetid: dc0f9f47-3184-4e7a-8074-2c63e0359885
ms.openlocfilehash: 6da2ef1595e525bcfd407d67c806aa80cf90f1c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262708"
---
# <a name="how-wininet-makes-it-easier-to-create-internet-client-applications"></a>Comment WinInet facilite la création d'applications clientes Internet

L’extension Internet Win32, ou WinInet, donnent accès à des protocoles Internet courants, notamment gopher, FTP et HTTP. À l’aide de WinInet, vous pouvez écrire des applications de client Internet à un niveau supérieur de la programmation, sans avoir à gérer avec WinSock, TCP/IP ou les détails des protocoles Internet spécifiques. WinInet fournit un ensemble cohérent de fonctions pour les trois protocoles, avec une interface API Win32 familière. Cette cohérence réduit les modifications de code que vous devez faire si le protocole sous-jacent change (par exemple, à partir de FTP sur HTTP).

Visual C++ propose deux méthodes que vous pouvez utiliser WinInet. Vous pouvez appeler directement les fonctions Win32 Internet (consultez la documentation OLE dans le SDK Windows pour plus d’informations) ou vous pouvez utiliser WinInet via le [classes WinInet MFC](../mfc/mfc-classes-for-creating-internet-client-applications.md).

**Vous pouvez utiliser WinInet pour :**

- Télécharger des pages HTML.

   HTTP est un protocole utilisé pour transférer des pages HTML à partir d’un serveur vers un navigateur client.

- Envoyer des demandes FTP pour charger ou télécharger des fichiers ou obtenir les listes de répertoires.

   Une demande standard est une connexion anonyme pour télécharger un fichier.

- Utilisez le système de menus de gopher pour accéder aux ressources sur Internet.

   Éléments de menu peuvent contenir plusieurs types, y compris les autres menus, vous pouvez rechercher une base de données indexée, un groupe de discussion ou un fichier.

Pour les trois protocoles, établir une connexion, effectuer des demandes au serveur et fermer la connexion.

**Les classes WinInet MFC facilitent les :**

- Lire les informations à partir de serveurs HTTP, FTP et gopher aussi facilement que la lecture des fichiers à partir d’un disque dur.

- Utilisez des protocoles HTTP, FTP et gopher sans programmer directement WinSock ou TCP/IP.

   Les développeurs qui utilisent les fonctions Win32 Internet n’avez pas besoin de se familiariser avec TCP/IP ou de Windows Sockets. Vous pouvez toujours programmer au niveau du socket, à l’aide de protocoles WinSock et TCP/IP directement, mais il est encore plus facile à utiliser les classes WinInet MFC pour l’accès HTTP, FTP et les protocoles gopher via Internet. Pour de nombreuses opérations courantes, les développeurs n’ont pas à connaître les détails du protocole particulier qu’ils utilisent.

Nombre d’opérations qui peut être effectuée par votre ordinateur en tant que client à d’autres ordinateurs sur Internet peut prendre un certain temps. La vitesse de ces opérations est généralement limitée par la vitesse de votre connexion réseau, mais ils peuvent également être affectées par tout autre trafic réseau et la complexité de l’opération. Connexion à un serveur FTP distant, par exemple, nécessite que votre ordinateur tout d’abord rechercher le nom de ce serveur pour trouver son adresse. Votre application sera puis essayez de vous connecter au serveur à l’adresse. Une fois que la connexion est ouverte, votre ordinateur et le serveur distant lance une conversation avec le protocole de transfert de fichier avant de pouvoir utiliser réellement la connexion pour récupérer des fichiers.

## <a name="see-also"></a>Voir aussi

[Extension Internet Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Comment MFC facilite la création d’applications clientes Internet](../mfc/how-mfc-makes-it-easier-to-create-internet-client-applications.md)
