---
description: 'En savoir plus sur : Windows Sockets : ports et adresses de Sockets'
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
ms.openlocfilehash: 354505796ff60cc8968b2e10a2aac98be2eb4666
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263398"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets : ports et adresses de socket

Cet article explique les termes « port » et « Address » utilisés avec Windows Sockets.

## <a name="port"></a><a name="_core_port"></a> Importer

Un port identifie un processus unique pour lequel un service peut être fourni. Dans le contexte actuel, un port est associé à une application qui prend en charge Windows Sockets. L’idée est d’identifier chaque application Windows Sockets de manière unique, de sorte que plusieurs applications Windows Sockets s’exécutent sur un ordinateur en même temps.

Certains ports sont réservés aux services courants, tels que FTP. Vous devez éviter d’utiliser ces ports, sauf si vous fournissez ce type de service. La spécification Windows Sockets détaille ces ports réservés. Fichier WINSOCK. H les répertorie également.

Pour permettre à la DLL Windows Sockets de sélectionner un port utilisable pour vous, transmettez 0 comme valeur de port. MFC sélectionne une valeur de port supérieure à 1 024 décimale. Vous pouvez récupérer la valeur de port que MFC a sélectionnée en appelant la fonction membre [CAsyncSocket :: GetSockName](../mfc/reference/casyncsocket-class.md#getsockname) .

## <a name="socket-address"></a><a name="_core_socket_address"></a> Adresse du socket

Chaque objet Socket est associé à une adresse IP (Internet Protocol) sur le réseau. En règle générale, l’adresse est un nom de machine, tel que « ftp.microsoft.com », ou un nombre en pointillés, tel que « 128.56.22.8 ».

Lorsque vous cherchez à créer un socket, vous n’avez généralement pas besoin de spécifier votre propre adresse.

> [!NOTE]
> Il est possible que votre ordinateur dispose de plusieurs cartes réseau (ou que votre application puisse être exécutée sur un tel ordinateur), chacune représentant un réseau différent. Si c’est le cas, vous devrez peut-être fournir une adresse pour spécifier la carte réseau que le socket utilisera. Il s’agit d’une utilisation avancée et d’un éventuel problème de portabilité.

Pour plus d'informations, consultez les pages suivantes :

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : utilisation de sockets avec des Archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : fonctionnement des sockets avec les Archives](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets : Sockets de flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagrammes](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)
