---
title: Windows Sockets dans MFC
ms.date: 11/04/2016
helpviewer_keywords:
- WINSOCK.DLL
- sockets [MFC], programming models
- MFC, Windows Sockets
- Windows Sockets [MFC], MFC support
- Windows Sockets [MFC], programming models
- WSOCK32.DLL
- sockets [MFC], MFC
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
ms.openlocfilehash: 8e5562b028d3d9b7cba4b47716b63fd1392c514f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371097"
---
# <a name="windows-sockets-in-mfc"></a>Windows Sockets dans MFC

> [!NOTE]
> MFC prend en charge Windows Sockets 1 mais ne prend pas en charge [Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2). Windows Sockets 2 d’abord expédié avec Windows 98 et est la version incluse avec Windows 2000.

MFC fournit deux modèles pour l’écriture de programmes de communications réseau avec Windows Sockets, incarnés dans deux classes MFC. Cet article décrit ces modèles et détaille davantage le soutien des prises MFC. Une « prise » est un critère de communication : un objet par lequel votre application communique avec d’autres applications Windows Sockets sur un réseau.

Pour plus d’informations sur Windows Sockets, y compris une explication du concept de prise, voir [Windows Sockets: Background](../mfc/windows-sockets-background.md).

## <a name="sockets-programming-models"></a><a name="_core_sockets_programming_models"></a>Modèles de programmation Sockets

Les deux modèles de programmation MFC Windows Sockets sont pris en charge par les classes suivantes :

- `CAsyncSocket`

   Cette classe résume l’API Windows Sockets. [CAsyncSocket s’adresse](../mfc/reference/casyncsocket-class.md) aux programmeurs qui connaissent la programmation du réseau et qui veulent la flexibilité de la programmation directement aux prises API, mais qui veulent aussi la commodité des fonctions de rappel pour la notification des événements réseau. Outre les prises d’emballage sous forme orientée objet pour être utilisées dans le C, la seule abstraction supplémentaire que cette classe fournit est de convertir certains messages Windows liés aux prises en rappels. Pour plus d’informations, voir [Windows Sockets: Socket Notifications](../mfc/windows-sockets-socket-notifications.md).

- `CSocket`

   Cette classe, `CAsyncSocket`dérivée de , fournit une abstraction de niveau supérieur pour travailler avec des prises à travers un objet [MFC CArchive.](../mfc/reference/carchive-class.md) L’utilisation d’une prise avec une archive ressemble beaucoup à l’utilisation du protocole de sérialisation des fichiers de MFC. Cela le rend plus `CAsyncSocket` facile à utiliser que le modèle. [CSocket](../mfc/reference/csocket-class.md) hérite de nombreuses `CAsyncSocket` fonctions de membres à partir de cet API Encapsulate Windows Sockets; vous devrez utiliser certaines de ces fonctions et comprendre la programmation de prises en général. Mais `CSocket` gère de nombreux aspects de la communication que vous auriez `CAsyncSocket`à faire vous-même en utilisant soit l’API brute ou la classe . Plus important `CSocket` encore, fournit le blocage (avec le traitement de fond `CArchive`des messages Windows), qui est essentiel au fonctionnement synchrone de .

La création `CSocket` `CAsyncSocket` et l’utilisation et l’utilisation d’objets sont décrites dans [Windows Sockets: Using Sockets with Archives](../mfc/windows-sockets-using-sockets-with-archives.md) and Windows [Sockets: Using Class CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).

## <a name="windows-sockets-dlls"></a><a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a>Windows Sockets DLL

Les systèmes d’exploitation Microsoft Windows fournissent les bibliothèques à liaison dynamique Windows Sockets (DLL). Visual CMD fournit les fichiers et bibliothèques d’en-tête appropriés et les spécifications Windows Sockets.

Pour plus d’informations sur Windows Sockets, voir :

- [Windows Sockets : sockets flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)

- [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : ordre des opérations](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows Sockets : exemple de sockets utilisant des archives](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets : fonctionnement des sockets avec des archives](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : dérivation à partir des classes de sockets](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets : notifications de socket](../mfc/windows-sockets-socket-notifications.md)

- [Windows Sockets : blocage](../mfc/windows-sockets-blocking.md)

- [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets : conversion de chaînes](../mfc/windows-sockets-converting-strings.md)

- [Windows Sockets : ports et adresses de socket](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets](../mfc/windows-sockets.md)
