---
title: 'Windows Sockets : Ports et adresses de Socket | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 42ea9b8a39de8d36ecb621164d98e072a4041211
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383985"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets : ports et adresses de socket
Cet article explique les termes « port » et « address » comme utilisé avec Windows Sockets.  
  
##  <a name="_core_port"></a> port  
 Un port identifie un processus unique pour lequel un service peut être fourni. Dans ce contexte, un port est associé à une application qui prend en charge de Windows Sockets. L’idée est d’identifier de manière unique chaque application Windows Sockets afin d’avoir plus d’une application Windows Sockets en cours d’exécution sur un ordinateur en même temps.  
  
 Certains ports sont réservés pour les services courants, tels que FTP. Évitez d’utiliser ces ports, sauf si vous fournissez ce type de service. La spécification Windows Sockets détaille ces ports réservés. Le fichier WINSOCK. H les répertorie également.  
  
 Pour permettre à la DLL Windows Sockets sélectionner un port à utiliser pour vous, passez 0 comme valeur du port. MFC sélectionne une valeur de port supérieure à 1 024 décimal. Vous pouvez récupérer la valeur de port sélectionnée par MFC en appelant le [fonction membre CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname) fonction membre.  
  
##  <a name="_core_socket_address"></a> Adresse de socket  
 Chaque objet socket est associé à une adresse IP (Internet Protocol) sur le réseau. En règle générale, l’adresse est un nom d’ordinateur, tel que « FTP.Microsoft.com », ou un nombre en pointillés, comme « 128.56.22.8 ».  
  
 Lorsque vous cherchez à créer un socket, vous n’avez généralement pas besoin spécifier votre propre adresse.  
  
> [!NOTE]
>  Il est possible que votre ordinateur possède plusieurs cartes réseau (ou votre application s’exécute un jour sur un ordinateur de ce type), représentant chacune un autre réseau. Dans ce cas, vous devrez donner une adresse pour spécifier la carte réseau utilise le socket. Il s’agit d’une utilisation avancée et d’un problème de portabilité possible certaine.  
  
 Pour plus d'informations, voir :  
  
-   [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets : fonctionnement des sockets avec des archives](../mfc/windows-sockets-how-sockets-with-archives-work.md)  
  
-   [Windows Sockets : sockets flux](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets : sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)

