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
ms.openlocfilehash: 1c4a6dc6740660d1097785578cdac355983cad18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360130"
---
# <a name="windows-sockets-background"></a>Windows Sockets : arrière-plan

Cet article explique la nature et le but de Windows Sockets. L’article aussi:

- [Définit le terme "socket"](#_core_definition_of_a_socket).

- [Décrit le type de données de poignée SOCKET](#_core_the_socket_data_type).

- [Décrit les utilisations pour les prises](#_core_uses_for_sockets).

La spécification Windows Sockets définit une interface de programmation réseau compatible binaire pour Microsoft Windows. Windows Sockets sont basés sur la mise en œuvre des prises UNIX dans la Berkeley Software Distribution (BSD, version 4.3) de l’Université de Californie à Berkeley. La spécification comprend à la fois des routines de prise de style BSD et des extensions spécifiques à Windows. L’utilisation de Windows Sockets permet à votre application de communiquer sur n’importe quel réseau conforme à l’API Windows Sockets. Sur Win32, Windows Sockets assure la sécurité des threads.

De nombreux fournisseurs de logiciels réseau prennent en charge Windows Sockets dans le cadre de protocoles réseau, y compris Le protocole de contrôle de transmission/protocole Internet (TCP/IP), Xerox Network System (XNS), le protocole DECNet de Digital Equipment Corporation, l’Internet Packet Exchange/Sequenced Packed Exchange de Novell Corporation (IPX/SPX) et d’autres. Bien que les spécifications actuelles de Windows Sockets définissent l’abstraction des prises pour TCP/IP, tout protocole réseau peut se conformer aux prises Windows en fournissant sa propre version de la bibliothèque de liaison dynamique (DLL) qui implémente windows Sockets. Des exemples d’applications commerciales écrites avec Windows Sockets comprennent les serveurs X Windows, les émulateurs terminaux et les systèmes de messagerie électronique.

> [!NOTE]
> Le but de Windows Sockets est d’abstraction du réseau sous-jacent afin que vous n’ayez pas à être bien informé sur ce réseau et de sorte que votre application peut s’exécuter sur n’importe quel réseau qui prend en charge les prises. Par conséquent, cette documentation ne traite pas des détails des protocoles réseau.

La Microsoft Foundation Class Library (MFC) prend en charge la programmation avec l’API Windows Sockets en fournissant deux classes. L’une de `CSocket`ces classes, fournit un haut niveau d’abstraction pour simplifier votre programmation de communication réseau.

La spécification Windows Sockets, Windows Sockets: An Open Interface for Network Computing Under Microsoft Windows, maintenant à la version 1.1, a été développée comme norme de réseautage ouverte par un grand groupe de personnes et de sociétés de la communauté TCP/IP et est librement disponible pour une utilisation. Le modèle de programmation de prises prend en charge un « domaine de communication » actuellement, en utilisant la suite de protocole Internet. Les spécifications sont disponibles dans le Windows SDK.

> [!TIP]
> Étant donné que les prises utilisent la suite de protocole Internet, elles sont l’itinéraire privilégié pour les applications qui prennent en charge les communications Internet sur l'« autoroute de l’information ».

## <a name="definition-of-a-socket"></a><a name="_core_definition_of_a_socket"></a>Définition d’une prise

Une prise est un critère de communication — un objet par lequel une application Windows Sockets envoie ou reçoit des paquets de données sur un réseau. Une prise a un type et est associée à un processus d’exécution, et il peut avoir un nom. Actuellement, les prises n’échangent généralement des données qu’avec d’autres prises dans le même « domaine de communication », qui utilise la suite de protocole Internet.

Les deux types de prises sont bidirectionnels; ce sont des flux de données qui peuvent être communiqués dans les deux sens simultanément (plein duplex).

Deux types de prises sont disponibles :

- Sockets de flux

   Les prises de flux fournissent un flux de données sans limites d’enregistrement : un flux d’octets. Les flux sont garantis pour être livrés et correctement séquencés et non dédupqués.

- Sockets datagramme

   Les prises de datagram prennent en charge un flux de données axé sur les dossiers qui n’est pas garanti d’être livré et qui ne peut pas être séquencé comme envoyé ou non.

"Sequenced" signifie que les paquets sont livrés dans l’ordre envoyé. "Unduplicated" signifie que vous obtenez un paquet particulier qu’une seule fois.

> [!NOTE]
> Selon certains protocoles réseau, tels que XNS, les flux peuvent être orientés vers les enregistrements, sous forme de flux d’enregistrements plutôt que de flux d’octets. Toutefois, en vertu du protocole TCP/IP plus courant, les flux sont des flux d’enlise. Windows Sockets fournit un niveau d’abstraction indépendant du protocole sous-jacent.

Pour plus d’informations sur ces types et quel type de prise à utiliser dans quelles situations, voir [Windows Sockets: Stream Sockets](../mfc/windows-sockets-stream-sockets.md) et [Windows Sockets: Datagram Sockets](../mfc/windows-sockets-datagram-sockets.md).

## <a name="the-socket-data-type"></a><a name="_core_the_socket_data_type"></a>Le type de données SOCKET

Chaque objet de prise MFC résume une poignée à un objet Windows Sockets. Le type de données de cette poignée est **SOCKET**. Une poignée **SOCKET** est `HWND` analogue à la pour une fenêtre. Les classes de prises MFC fournissent des opérations sur la poignée encapsulée.

Le type de données **SOCKET** est décrit en détail dans le SDK Windows. Voir "Socket Data Type and Error Values" sous Windows Sockets.

## <a name="uses-for-sockets"></a><a name="_core_uses_for_sockets"></a>Utilisations pour les prises

Les prises sont très utiles dans au moins trois contextes de communication :

- Modèles clients/serveurs.

- Scénarios peer-to-peer, tels que les applications de messagerie.

- Faire des appels de procédure à distance (RPC) en faisant interpréter l’application de réception comme un appel de fonction.

> [!TIP]
> Le cas idéal pour l’utilisation des prises MFC est lorsque vous écrivez les deux extrémités de la communication: en utilisant MFC aux deux extrémités. Pour plus d’informations sur ce sujet, y compris la façon de gérer le cas lorsque vous communiquez avec des applications non-MFC, voir [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md).

Pour plus d’informations, voir Windows Sockets Specification: **ntohs**, **ntohl**, **htons**, **htonl**. Aussi, voir les sujets suivants:

- [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : exemple de sockets utilisant des archives](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)
