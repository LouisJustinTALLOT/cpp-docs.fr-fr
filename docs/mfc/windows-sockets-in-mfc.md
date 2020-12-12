---
description: 'En savoir plus sur : Windows Sockets dans MFC'
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
ms.openlocfilehash: 9724613fe20abbd53b8f7de6a57723510d37b7f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263424"
---
# <a name="windows-sockets-in-mfc"></a>Windows Sockets dans MFC

> [!NOTE]
> MFC prend en charge Windows Sockets 1, mais ne prend pas en charge [Windows Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2). Windows Sockets 2 a été fourni avec Windows 98 et est la version fournie avec Windows 2000.

MFC fournit deux modèles pour l’écriture de programmes de communication réseau avec Windows Sockets, incorporés dans deux classes MFC. Cet article décrit ces modèles et fournit des informations supplémentaires sur la prise en charge des sockets MFC. Un « socket » est un point de terminaison de communication : un objet par le biais duquel votre application communique avec d’autres applications Windows Sockets sur un réseau.

Pour plus d’informations sur Windows Sockets, notamment une explication du concept de socket, consultez [Windows Sockets : Background](../mfc/windows-sockets-background.md).

## <a name="sockets-programming-models"></a><a name="_core_sockets_programming_models"></a> Modèles de programmation de Sockets

Les deux modèles de programmation MFC Windows Sockets sont pris en charge par les classes suivantes :

- `CAsyncSocket`

   Cette classe encapsule l’API Windows Sockets. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) est destiné aux programmeurs qui connaissent la programmation réseau et qui souhaitent avoir la possibilité de programmer directement sur l’API Sockets, mais qui veulent également la commodité des fonctions de rappel pour la notification des événements réseau. En dehors de l’empaquetage de sockets dans un formulaire orienté objet pour une utilisation en C++, la seule abstraction supplémentaire que cette classe fournit est la conversion de certains messages Windows liés au socket en rappels. Pour plus d’informations, consultez [Windows Sockets : notifications de sockets](../mfc/windows-sockets-socket-notifications.md).

- `CSocket`

   Cette classe, dérivée de `CAsyncSocket` , fournit une abstraction de niveau supérieur pour l’utilisation des sockets via un objet [CArchive](../mfc/reference/carchive-class.md) MFC. L’utilisation d’un socket avec une archive ressemble beaucoup à l’utilisation du protocole de sérialisation de fichiers MFC. Cela facilite son utilisation par rapport au `CAsyncSocket` modèle. [CSocket](../mfc/reference/csocket-class.md) hérite de nombreuses fonctions membres de `CAsyncSocket` qui encapsulent les API de sockets Windows. vous devez utiliser certaines de ces fonctions et comprendre la programmation de sockets en général. Toutefois, `CSocket` gère de nombreux aspects de la communication que vous auriez à faire vous-même à l’aide de l’API brute ou de la classe `CAsyncSocket` . Plus important encore, `CSocket` fournit un blocage (avec traitement en arrière-plan des messages Windows), qui est essentiel pour le fonctionnement synchrone de `CArchive` .

La création et l’utilisation `CSocket` des `CAsyncSocket` objets et est décrite dans [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md) et [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).

## <a name="windows-sockets-dlls"></a><a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a> Dll Windows Sockets

Les systèmes d’exploitation Microsoft Windows fournissent les bibliothèques de liens dynamiques (DLL) de Windows Sockets. Visual C++ fournit les fichiers d’en-tête et les bibliothèques appropriés, ainsi que la spécification Windows Sockets.

Pour plus d’informations sur Windows Sockets, consultez :

- [Windows Sockets : Sockets de flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagrammes](../mfc/windows-sockets-datagram-sockets.md)

- [Windows Sockets : utilisation de sockets avec des Archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : séquence d’opérations](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows Sockets : exemple de sockets utilisant des Archives](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets : fonctionnement des sockets avec les Archives](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : dérivation à partir des classes de Sockets](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets : notifications de socket](../mfc/windows-sockets-socket-notifications.md)

- [Windows Sockets : Blocage](../mfc/windows-sockets-blocking.md)

- [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets : conversion de chaînes](../mfc/windows-sockets-converting-strings.md)

- [Windows Sockets : ports et adresses de socket](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets](../mfc/windows-sockets.md)
