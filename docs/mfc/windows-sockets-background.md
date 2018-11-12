---
title: 'Windows Sockets : arrière-plan'
ms.date: 11/04/2016
helpviewer_keywords:
- record-oriented data [MFC]
- e-mail [MFC]
- Internet Protocol Suite
- mail [MFC]
- communications [MFC], domain
- Windows Sockets [MFC], stream sockets
- mail [MFC], programming for
- sockets [MFC], stream sockets
- datagram sockets [MFC]
- SOCKET handle
- data types [MFC], socket
- e-mail [MFC], programming for
- X Window servers
- sequenced data flow
- stream sockets [MFC]
ms.assetid: f60d4ed2-bf23-4a0e-98d2-fee77e8473dd
ms.openlocfilehash: 93342f734d1e475cbae1b7e3025c59e6e6f73284
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468027"
---
# <a name="windows-sockets-background"></a>Windows Sockets : arrière-plan

Cet article explique la nature et l’objectif de Windows Sockets. L’article également :

- [Définit le terme « socket »](#_core_definition_of_a_socket).

- [Décrit le type de données de handle SOCKET](#_core_the_socket_data_type).

- [Décrit les utilisations des sockets](#_core_uses_for_sockets).

La spécification Windows Sockets définit une interface de programmation réseau compatible binaire pour Microsoft Windows. Windows Sockets sont basées sur l’implémentation de sockets UNIX dans Berkeley Software Distribution (BSD, version 4.3) à partir de l’Université de Californie de Berkeley. La spécification inclut des routines de sockets BSD-style et extensions spécifiques à Windows. À l’aide de Windows Sockets permet à votre application de communiquer sur n’importe quel réseau qui est conforme à l’API de Sockets Windows. Sur Win32, Windows Sockets fournissent pour la sécurité des threads.

Nombreux éditeurs de logiciels réseau prennent en charge Windows Sockets sous protocoles réseau, notamment Protocol/Internet Protocol TCP/IP (Transmission Control), Xerox réseau système (XNS), le protocole DECNet Digital Equipment Corporation, Novell Corporation Internet Packet Exchange/Sequenced emballés Exchange (IPX/SPX) et autres. Bien que la spécification Windows Sockets présente définit l’abstraction de sockets pour TCP/IP, n’importe quel protocole réseau peut se conformer Windows Sockets, vous devez fournir sa propre version de la bibliothèque de liens dynamiques (DLL) qui implémente Windows Sockets. Serveurs X Windows, les émulateurs de terminal et les systèmes de messagerie électronique constituent des exemples d’applications commerciales écrites avec Windows Sockets.

> [!NOTE]
>  L’objectif de Windows Sockets est de soustraire le réseau sous-jacent afin que vous n’avez pas à être informé de ce réseau, et donc de votre application peut s’exécuter sur n’importe quel réseau qui prend en charge des sockets. Par conséquent, cette documentation ne traite pas les détails des protocoles de réseau.

Les MFC Microsoft Foundation Class Library () prend en charge la programmation avec l’API de Sockets Windows en fournissant deux classes. Une de ces classes, `CSocket`, fournit un niveau élevé d’abstraction afin de simplifier la programmation de communications réseau.

La spécification Windows Sockets, Windows Sockets : An Open Interface for Network Computing sous Microsoft Windows, désormais à la version 1.1, a été développé comme une norme ouverte mise en réseau par un grand nombre d’individus et de sociétés de la Communauté de TCP/IP et est disponible gratuitement pour une utilisation. Les sockets de programmation actuellement de modèle prend en charge un « domaine de communication », à l’aide de la Suite de protocoles Internet. La spécification est disponible dans le SDK Windows.

> [!TIP]
>  Étant donné que les sockets utilisent la Suite de protocoles Internet, ils sont l’itinéraire par défaut pour les applications qui prennent en charge les communications Internet sur l’autoroute « informations ».

##  <a name="_core_definition_of_a_socket"></a> Définition d’un Socket

Un socket est un point de terminaison de communication : un objet par le biais duquel une application Windows Sockets envoie ou reçoit des paquets de données sur un réseau. Un socket a un type et est associé à un processus en cours d’exécution, et il peut avoir un nom. Actuellement, les sockets échangent en général des données uniquement avec d’autres sockets dans le même « domaine de communication, » qui utilise la Suite de protocoles Internet.

Les deux types de sockets sont bidirectionnel ; ils sont des flux de données qui peuvent être communiqués simultanément dans les deux sens (duplex intégral).

Deux types de socket sont disponibles :

- Sockets de Stream

   Stream de sockets fournissent pour un flux de données sans limites d’enregistrement : un flux d’octets. Flux sont garantis pour être remis et être séquencée et non-duplication correctement.

- Sockets datagramme

   Datagramme des flux de données de prise en charge orientée sur un enregistrement de sockets qui ne sont pas garanti pour être remis et ne peuvent pas être séquencée comme envoyé ni non dupliqué.

« Ordonnancé » signifie que les paquets sont remis dans l’ordre d’envoi. « Non dupliqué » signifie que vous obtenez un paquet particulier une seule fois.

> [!NOTE]
>  Sous certains protocoles réseau, tels que XNS, les flux de données peut être orientés enregistrement, en tant que flux d’enregistrements au lieu du flux d’octets. Toutefois, sous le protocole TCP/IP plus courant, les flux sont des flux d’octets. Windows Sockets fournit un niveau d’abstraction indépendant du protocole sous-jacent.

Pour plus d’informations sur ces types et le type de socket à utiliser dans les situations, consultez [Windows Sockets : Sockets de Stream](../mfc/windows-sockets-stream-sockets.md) et [Windows Sockets : Sockets datagramme](../mfc/windows-sockets-datagram-sockets.md).

##  <a name="_core_the_socket_data_type"></a> Le Type de données SOCKET

Chaque objet socket MFC encapsule un handle vers un objet Windows Sockets. Le type de données de ce handle est **SOCKET**. Un **SOCKET** handle est analogue à la `HWND` pour une fenêtre. Les classes de sockets MFC fournissent des opérations sur le descripteur encapsulé.

Le **SOCKET** type de données est décrite en détail dans le SDK Windows. Consultez « Type de données de Socket et valeurs d’erreur » sous Windows Sockets.

##  <a name="_core_uses_for_sockets"></a> Utilisations des Sockets

Sockets sont très utiles dans au moins trois contextes de communication :

- Modèles de client/serveur.

- Scénarios de peer-to-peer, telles que les applications de messagerie.

- Effectue des appels de procédure distante (RPC) en demandant à l’application réceptrice d’interpréter un message comme un appel de fonction.

> [!TIP]
>  La solution idéale pour l’utilisation de sockets MFC est lorsque vous écrivez les deux extrémités de la communication : à l’aide de MFC aux deux extrémités. Pour plus d’informations sur ce sujet, notamment comment gérer le cas lorsque vous communiquez avec les applications non-MFC, consultez [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md).

Pour plus d’informations, consultez la spécification de Windows Sockets : **ntohs**, **ntohl**, **htons**, **htonl**. En outre, consultez les rubriques suivantes :

- [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : exemple de sockets utilisant des archives](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)

