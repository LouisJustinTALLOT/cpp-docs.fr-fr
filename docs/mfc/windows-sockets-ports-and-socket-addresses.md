---
title: 'Windows Sockets : ports et adresses de socket'
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
ms.openlocfilehash: 791bf07c927e80e65e0fda79fae8a50235bc2def
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371043"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets : ports et adresses de socket

Cet article explique les termes "port" et "adresse" tel qu’utilisé avec Windows Sockets.

## <a name="port"></a><a name="_core_port"></a>Port

Un port identifie un processus unique pour lequel un service peut être fourni. Dans le contexte actuel, un port est associé à une application qui prend en charge Windows Sockets. L’idée est d’identifier chaque application Windows Sockets de manière unique afin que vous puissiez avoir plus d’une application Windows Sockets fonctionnant sur une machine en même temps.

Certains ports sont réservés aux services communs, tels que le FTP. Vous devriez éviter d’utiliser ces ports à moins que vous ne fournissiez ce genre de service. Les spécifications Windows Sockets détaillent ces ports réservés. Le fichier WINSOCK. H les énumère également.

Pour laisser les prises Windows DLL sélectionner un port utilisable pour vous, passez 0 comme valeur portuaire. MFC choisit une valeur portuaire supérieure à 1 024 décimales. Vous pouvez récupérer la valeur portuaire que MFC a sélectionnée en appelant le [CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname) fonction membre.

## <a name="socket-address"></a><a name="_core_socket_address"></a>Adresse de prise

Chaque objet de prise est associé à une adresse de protocole Internet (IP) sur le réseau. Typiquement, l’adresse est un nom de machine, tel que "ftp.microsoft.com", ou un numéro pointillé, comme "128.56.22.8".

Lorsque vous cherchez à créer une prise, vous n’avez généralement pas besoin de spécifier votre propre adresse.

> [!NOTE]
> Il est possible que votre machine dispose de plusieurs cartes réseau (ou votre application pourrait un jour fonctionner sur une telle machine), chacune représentant un réseau différent. Si c’est le cas, vous devrez peut-être donner une adresse pour spécifier la carte réseau que la prise utilisera. Il s’agit certainement d’une utilisation avancée et d’un problème de portabilité possible.

Pour plus d'informations, consultez les pages suivantes :

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : fonctionnement des sockets avec des archives](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets : sockets flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)
