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
ms.openlocfilehash: 0c4f83ccd9bf431f7eb910f77409199da2b1325f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476100"
---
# <a name="windows-sockets-in-mfc"></a>Windows Sockets dans MFC

> [!NOTE]
>  MFC prend en charge Windows Sockets 1, mais ne prend pas en charge [Windows Sockets 2](/windows/desktop/WinSock/windows-sockets-start-page-2). Windows Sockets 2 tout d’abord expédié avec Windows 98 et la version fournie avec Windows 2000.

MFC propose deux modèles pour l’écriture de programmes de communication réseau avec Windows Sockets, mises en œuvre dans les deux classes MFC. Cet article décrit ces modèles et prise en charge des sockets MFC plus de détails. Un « socket » est un point de terminaison de communication : un objet via lequel votre application communique avec d’autres applications Windows Sockets sur un réseau.

Pour plus d’informations sur les Sockets Windows, y compris une explication du concept de socket, consultez [Windows Sockets : arrière-plan](../mfc/windows-sockets-background.md).

##  <a name="_core_sockets_programming_models"></a> Modèles de programmation de sockets

Les Sockets de Windows MFC deux modèles de programmation sont pris en charge par les classes suivantes :

- `CAsyncSocket`

   Cette classe encapsule l’API de Sockets Windows. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) est destiné aux programmeurs qui connaissez la programmation réseau et la flexibilité de programmation directement à l’API des sockets, mais également la commodité de fonctions de rappel pour la notification des événements réseau. Packaging sockets sous forme d’orientée objet pour une utilisation en C++, l’abstraction supplémentaire uniquement que fournit cette classe convertit certains messages Windows liés aux sockets en rappels. Pour plus d’informations, consultez [Windows Sockets : Notifications de Socket](../mfc/windows-sockets-socket-notifications.md).

- `CSocket`

   Cette classe, dérivée de `CAsyncSocket`, fournit un niveau d’abstraction plus élevé pour travailler avec des sockets via une MFC [CArchive](../mfc/reference/carchive-class.md) objet. Utilisation d’un socket avec une archive considérablement ressemble à l’aide du protocole de sérialisation du MFC fichier. Cela rend plus facile à utiliser que la `CAsyncSocket` modèle. [CSocket](../mfc/reference/csocket-class.md) hérite de nombreuses fonctions membres à partir de `CAsyncSocket` qui encapsulent les API de Sockets Windows ; vous devrez utiliser certaines de ces fonctions et de comprendre la programmation générale de sockets. Mais `CSocket` gère de nombreux aspects de la communication que vous devriez effectuer vous-même à l’aide de l’API brute ou classe `CAsyncSocket`. Plus important encore, `CSocket` fournit un blocage (avec traitement en arrière-plan des messages de Windows), qui est indispensable au fonctionnement synchrone de `CArchive`.

Création et utilisation `CSocket` et `CAsyncSocket` objets est décrit dans [Windows Sockets : utilisation de Sockets avec des Archives](../mfc/windows-sockets-using-sockets-with-archives.md) et [Windows Sockets : à l’aide de classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).

##  <a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a> Windows Sockets DLL

Les systèmes d’exploitation Microsoft Windows fournissent les bibliothèques de liens dynamiques (DLL) de Windows Sockets. Visual C++ fournit les fichiers d’en-tête approprié et de bibliothèques et de la spécification Windows Sockets.

Pour plus d’informations sur les Sockets Windows, consultez :

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

