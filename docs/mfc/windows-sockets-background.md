---
description: 'En savoir plus sur : Windows Sockets : arrière-plan'
title: 'Windows Sockets : Présentation'
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
ms.openlocfilehash: 9ac373f5f81dfe3914664d14122a7a6bd46cda40
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214466"
---
# <a name="windows-sockets-background"></a>Windows Sockets : Présentation

Cet article explique la nature et l’objectif de Windows Sockets. L’article présente également les éléments suivants :

- [Définit le terme « Socket »](#_core_definition_of_a_socket).

- [Décrit le type de données du handle de socket](#_core_the_socket_data_type).

- [Décrit les utilisations de pour les sockets](#_core_uses_for_sockets).

La spécification Windows Sockets définit une interface de programmation réseau compatible binaire pour Microsoft Windows. Les sockets Windows sont basés sur l’implémentation des sockets UNIX dans Berkeley Software Distribution (BSD, version 4,3) de l’Université de Californie, à Berkeley. La spécification comprend des routines de sockets de type BSD et des extensions spécifiques à Windows. L’utilisation de Windows Sockets permet à votre application de communiquer sur tout réseau conforme à l’API Windows Sockets. Sur Win32, Windows Sockets assure la sécurité des threads.

De nombreux fournisseurs de logiciels réseau prennent en charge Windows Sockets sous les protocoles réseau, notamment le protocole TCP/IP (Transmission Control Protocol/Internet Protocol), le système de réseau Xerox (XNS), le protocole DECnet de Digital Equipment Corporation, l’échange de paquets Internet/les échanges de paquets en séquences (IPX/SPX) de Novell Corporation et d’autres. Bien que la spécification Windows Sockets présente la définition de l’abstraction des sockets pour TCP/IP, tout protocole réseau peut se conformer aux sockets Windows en fournissant sa propre version de la bibliothèque de liens dynamiques (DLL) qui implémente Windows Sockets. Des exemples d’applications commerciales écrites avec Windows Sockets incluent les serveurs X Windows, les émulateurs de terminaux et les systèmes de messagerie électronique.

> [!NOTE]
> L’objectif de Windows Sockets est de soustraire le réseau sous-jacent, de sorte que vous n’avez pas à être informé de ce réseau et que votre application puisse s’exécuter sur n’importe quel réseau qui prend en charge les sockets. Par conséquent, cette documentation n’aborde pas les détails des protocoles réseau.

Le bibliothèque MFC (Microsoft Foundation Class) (MFC) prend en charge la programmation avec l’API Windows Sockets en fournissant deux classes. L’une de ces classes, `CSocket` , fournit un niveau élevé d’abstraction pour simplifier la programmation des communications réseau.

La spécification Windows Sockets (Windows Sockets) : une interface ouverte pour l’informatique en réseau sous Microsoft Windows, désormais disponible à la version 1,1, a été développée en tant que norme de mise en réseau ouverte par un grand groupe de personnes et d’entreprises dans la communauté TCP/IP et est disponible gratuitement. Le modèle de programmation Sockets prend actuellement en charge un « domaine de communication », à l’aide de la suite de protocoles Internet. La spécification est disponible dans le SDK Windows.

> [!TIP]
> Étant donné que les sockets utilisent la suite de protocoles Internet, il s’agit de l’itinéraire préféré pour les applications qui prennent en charge les communications Internet sur l' « autoroute des informations ».

## <a name="definition-of-a-socket"></a><a name="_core_definition_of_a_socket"></a> Définition d’un socket

Un socket est un point de terminaison de communication : un objet par le biais duquel une application Windows Sockets envoie ou reçoit des paquets de données sur un réseau. Un socket a un type et est associé à un processus en cours d’exécution, et il peut avoir un nom. Actuellement, les sockets échangent généralement des données uniquement avec d’autres Sockets dans le même « domaine de communication », qui utilise la suite de protocoles Internet.

Les deux types de sockets sont bidirectionnels ; Il s’agit de flux de données qui peuvent être communiqués dans les deux sens simultanément (Full-duplex).

Deux types de sockets sont disponibles :

- Sockets de flux

   Les sockets de flux fournissent un flux de données sans limites d’enregistrement : un flux d’octets. Les flux sont assurés d’être remis et sont correctement séquencés et non dupliqués.

- Sockets datagramme

   Les sockets de datagrammes prennent en charge un workflow de données orienté enregistrement qui n’est pas forcément remis et qui ne peut pas être séquencé comme envoyé ou non dupliqué.

« Séquencé » signifie que les paquets sont remis dans l’ordre envoyé. « Unduplicated » signifie que vous ne recevez un paquet particulier qu’une seule fois.

> [!NOTE]
> Sous certains protocoles réseau, tels que XNS, les flux peuvent être orientés enregistrement, sous la forme de flux d’enregistrements plutôt que de flux d’octets. Toutefois, sous le protocole TCP/IP plus courant, les flux sont des flux d’octets. Windows Sockets fournit un niveau d’abstraction indépendant du protocole sous-jacent.

Pour plus d’informations sur ces types et sur le type de socket à utiliser dans les situations, consultez [Windows Sockets : Sockets de flux](../mfc/windows-sockets-stream-sockets.md) et [Windows Sockets : Sockets de datagrammes](../mfc/windows-sockets-datagram-sockets.md).

## <a name="the-socket-data-type"></a><a name="_core_the_socket_data_type"></a> Type de données SOCKET

Chaque objet Socket MFC encapsule un handle vers un objet Windows Sockets. Le type de données de ce descripteur est **Socket**. Un handle de **Socket** est analogue à `HWND` pour une fenêtre. Les classes de socket MFC fournissent des opérations sur le handle encapsulé.

Le type de données **Socket** est décrit en détail dans la SDK Windows. Consultez « type de données de socket et valeurs d’erreur » sous Windows Sockets.

## <a name="uses-for-sockets"></a><a name="_core_uses_for_sockets"></a> Utilisations pour les sockets

Les sockets sont très utiles dans au moins trois contextes de communication :

- Modèles client/serveur.

- Les scénarios d’égal à égal, tels que les applications de messagerie.

- En effectuant des appels de procédure distante (RPC) en demandant à l’application réceptrice d’interpréter un message comme un appel de fonction.

> [!TIP]
> Le cas idéal pour l’utilisation des sockets MFC est lorsque vous écrivez les deux extrémités de la communication : à l’aide de MFC aux deux extrémités. Pour plus d’informations sur cette rubrique, notamment sur la façon de gérer le cas lorsque vous communiquez avec des applications non-MFC, consultez [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md).

Pour plus d’informations, consultez Spécification Windows Sockets : **ntohs**, **ntohl**, **htons**, **htonl**. Consultez également les rubriques suivantes :

- [Windows Sockets : utilisation de sockets avec des Archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : exemple de sockets utilisant des Archives](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)
