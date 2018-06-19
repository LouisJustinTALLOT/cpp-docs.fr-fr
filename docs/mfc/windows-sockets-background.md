---
title: 'Windows Sockets : Arrière-plan | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fda86bbbeb49bcb253348ed02abef4fb8d4cff9c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384935"
---
# <a name="windows-sockets-background"></a>Windows Sockets : arrière-plan
Cet article explique la nature et la finalité de Windows Sockets. L’article également :  
  
-   [Définit le terme « support »](#_core_definition_of_a_socket).  
  
-   [Décrit le type de données de handle SOCKET](#_core_the_socket_data_type).  
  
-   [Décrit les utilisations des sockets](#_core_uses_for_sockets).  
  
 La spécification Windows Sockets définit une interface de programmation compatible binaire réseau pour Microsoft Windows. Windows Sockets sont basées sur l’implémentation UNIX sockets Berkeley Software Distribution (BSD, version 4.3) à partir de l’University of California, Berkeley. La spécification inclut à la fois des routines de sockets BSD-style et des extensions spécifiques à Windows. À l’aide de Windows Sockets permet à votre application de communiquer sur n’importe quel réseau qui est conforme à l’API Windows Sockets. Sur Win32, Windows Sockets assure la sécurité des threads.  
  
 Nombreux éditeurs de logiciels réseau prennent en charge Windows Sockets sous les protocoles réseau, notamment Protocol/Internet Protocol TCP/IP (Transmission Control), Xerox réseau système (XNS), le protocole DECNet Digital Equipment Corporation, Novell Corporation Internet Packet Exchange/Sequenced Packed Exchange (IPX/SPX) et autres. Bien que la spécification Windows Sockets actuelle définit l’abstraction des sockets pour TCP/IP, n’importe quel protocole réseau peut respecter Windows Sockets, vous devez fournir sa propre version de la bibliothèque de liens dynamiques (DLL) qui implémente Windows Sockets. Serveurs X Windows, les émulateurs de terminal et les systèmes de messagerie électronique sont des exemples d’applications commerciales écrites avec Windows Sockets.  
  
> [!NOTE]
>  Windows Sockets vise à abstraire le réseau sous-jacent afin que vous n’avez pas à être bien informé sur ce réseau et par conséquent, votre application peut s’exécuter sur n’importe quel réseau qui prend en charge des sockets. Par conséquent, cette documentation ne traite pas les détails des protocoles réseau.  
  
 Les MFC Microsoft Foundation Class Library () prend en charge la programmation avec l’API Windows Sockets en fournissant deux classes. Une de ces classes, `CSocket`, fournit un niveau élevé d’abstraction pour simplifier la programmation de communications réseau.  
  
 La spécification Windows Sockets, Windows Sockets : An Open Interface réseau informatique sous Microsoft Windows, désormais à la version 1.1, une norme ouverte de réseau a été développé par un grand groupe d’individus et de sociétés de la Communauté TCP/IP et est disponible gratuitement pour les utiliser. Les sockets actuellement de programmation modèle prend en charge un « domaine de communication », à l’aide de la Suite de protocoles Internet. La spécification est disponible dans le SDK Windows.  
  
> [!TIP]
>  Comme les sockets utilisent la Suite de protocoles Internet, ils sont l’itinéraire par défaut pour les applications qui prennent en charge les communications Internet sur le bus « informations ».  
  
##  <a name="_core_definition_of_a_socket"></a> Définition d’un Socket  
 Un socket est un point de terminaison de communication : un objet via lequel une application Windows Sockets envoie ou reçoit des paquets de données sur un réseau. Un socket a un type et est associé à un processus en cours d’exécution, et il peut avoir un nom. Actuellement, les sockets échangent en général des données uniquement avec d’autres sockets dans le même « domaine de communication, » qui utilise le protocole Internet (Suite).  
  
 Les deux types de sockets sont bidirectionnels ; ils sont des flux de données pouvant être communiqué simultanément dans les deux sens (duplex intégral).  
  
 Deux types de socket sont disponibles :  
  
-   Sockets flux  
  
     Flux de sockets fournissent pour un flux de données sans limites d’enregistrement : un flux d’octets. Flux de données est garanties à livrer et séquencée et non-duplication correctement.  
  
-   Sockets datagramme  
  
     Datagramme sockets prise en charge orientée sur un enregistrement de flux de données n’est pas garanti pour être remis et ne peut pas être séquencé comme envoyé ni non dupliqué.  
  
 « Séquencé » signifie que les paquets sont remis dans l’ordre d’envoi. « Reliés » signifie que vous obtenez un paquet particulier qu’une seule fois.  
  
> [!NOTE]
>  Dans certains protocoles réseau, tels que XNS, les flux peuvent être orientés enregistrement, en tant que flux d’enregistrements au lieu du flux d’octets. Toutefois, sous le protocole TCP/IP plus courant, les flux sont des flux d’octets. Windows Sockets fournit un niveau d’abstraction indépendant du protocole sous-jacent.  
  
 Pour plus d’informations sur ces types et le type de socket à utiliser dans les situations, consultez [Windows Sockets : Sockets flux](../mfc/windows-sockets-stream-sockets.md) et [Windows Sockets : Sockets datagramme](../mfc/windows-sockets-datagram-sockets.md).  
  
##  <a name="_core_the_socket_data_type"></a> Le Type de données SOCKET  
 Chaque objet socket MFC encapsule un handle vers un objet Windows Sockets. Le type de données de ce descripteur est **SOCKET**. A **SOCKET** handle est analogue à la `HWND` pour une fenêtre. Classes de sockets MFC fournissent des opérations sur le descripteur encapsulé.  
  
 Le **SOCKET** type de données est décrite en détail dans le Kit de développement logiciel Windows. Consultez « Type de données Socket et valeurs d’erreur » sous Windows Sockets.  
  
##  <a name="_core_uses_for_sockets"></a> Utilisations des Sockets  
 Sockets sont très utiles dans au moins trois contextes de communication :  
  
-   Modèles de client/serveur.  
  
-   Scénarios de pair à pair, tels que les applications de messagerie.  
  
-   Effectue des appels de procédure distante (RPC) en demandant à l’application réceptrice interpréter un message comme un appel de fonction.  
  
> [!TIP]
>  Le cas idéal pour utiliser des sockets MFC est lorsque vous écrivez les deux extrémités de la communication : utilisation de MFC aux deux extrémités. Pour plus d’informations sur cette rubrique, y compris comment gérer le cas lorsque vous communiquez avec les applications non-MFC, consultez [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md).  
  
 Pour plus d’informations, consultez la spécification Windows Sockets : **ntohs**, **ntohl**, **htons**, **htonl**. En outre, consultez les rubriques suivantes :  
  
-   [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets : exemple de sockets utilisant des archives](../mfc/windows-sockets-example-of-sockets-using-archives.md)  
  
-   [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)

