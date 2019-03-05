---
title: 'Windows Sockets : Ports et adresses de Socket'
ms.date: 11/04/2016
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
ms.openlocfilehash: c33ec1376c1898272cf80e8d77c5cc273e16f9de
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277772"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets : Ports et adresses de Socket

Cet article explique les termes « port » et « address » en tant qu’utilisé avec Windows Sockets.

##  <a name="_core_port"></a> Port

Un port identifie un processus unique pour lequel un service peut être fourni. Dans ce contexte, un port est associé à une application qui prend en charge de Windows Sockets. L’idée consiste à identifier de manière unique chaque application Windows Sockets afin d’avoir plus d’une application Windows Sockets en cours d’exécution sur un ordinateur en même temps.

Certains ports sont réservés pour les services communs, tels que FTP. Évitez d’utiliser ces ports, sauf si vous fournissez ce type de service. La spécification Windows Sockets détaille ces ports réservés. Le fichier WINSOCK. H les répertorie également.

Pour permettre à la DLL de Sockets Windows de sélectionner un port à utiliser pour vous, passez 0 comme valeur du port. MFC sélectionne une valeur de port supérieure à 1 024 décimal. Vous pouvez récupérer la valeur de port sélectionné de MFC en appelant le [fonction membre CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname) fonction membre.

##  <a name="_core_socket_address"></a> Adresse de socket

Chaque objet socket est associé à une adresse IP (Internet Protocol) sur le réseau. En règle générale, l’adresse est un nom d’ordinateur, telles que « FTP.Microsoft.com », ou un nombre en pointillés, tels que « 128.56.22.8 ».

Lorsque vous cherchez à créer un socket, généralement inutile de spécifier votre propre adresse.

> [!NOTE]
>  Il est possible que votre ordinateur possède plusieurs cartes réseau (ou votre application s’exécute un jour sur un ordinateur de ce type), chacune représentant un autre réseau. Dans ce cas, vous devrez peut-être donner une adresse pour spécifier la carte réseau que le socket doit utiliser. Voici certaine soit une utilisation avancée et un problème de portabilité possible.

Pour plus d'informations, voir :

- [Windows Sockets : À l’aide de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : Utilisation de Sockets avec des Archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : Fonctionnement des Sockets avec des Archives](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets : Sockets de Stream](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : Sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)
