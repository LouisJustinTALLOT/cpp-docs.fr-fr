---
title: 'Windows Sockets : blocage'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], blocking mode
- Windows Sockets [MFC], Windows platforms
- Windows Sockets [MFC], blocking mode
- sockets [MFC], behavior on different Windows platforms
- blocking mode sockets
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
ms.openlocfilehash: 7b41f034e08570e418bf24d9d720795eafc37932
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610572"
---
# <a name="windows-sockets-blocking"></a>Windows Sockets : blocage

Cet article et deux autres articles similaires décrivent plusieurs problèmes de programmation Windows Sockets. Cet article traite du blocage. Les autres problèmes sont décrits dans les articles : [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md) et [Windows Sockets : conversion de chaînes](../mfc/windows-sockets-converting-strings.md).

Si vous utilisez ou dériver de la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md), vous devez gérer ces problèmes vous-même. Si vous utilisez ou dériver de la classe [CSocket](../mfc/reference/csocket-class.md), MFC les gèrera.

## <a name="blocking"></a>Blocage

Un socket peut être "en mode bloquant" ou "en mode non bloquant". Les fonctions de sockets en mode blocage (ou synchrone) ne retournent pas de résultats tant qu'elles ne terminent pas leur action. On parle de blocage car le socket dont la fonction a été appelée ne peut rien faire, il est bloqué jusqu'à ce que l'appel soit renvoyé. Un appel à la `Receive` fonction membre, par exemple, peut prendre beaucoup de temps à effectuer, car il attend que l’application émettrice peut envoyer (il s’agit si vous utilisez `CSocket`, ou à l’aide de `CAsyncSocket` avec le blocage). Si un `CAsyncSocket` objet est en mode non bloquant (mode asynchrone), l’appel retourne immédiatement et le code d’erreur actuel, récupérable avec la [GetLastError](../mfc/reference/casyncsocket-class.md#getlasterror) la fonction membre **WSAEWOULDBLOCK**, indiquant que l’appel aurait bloqué l’ai ne pas renvoyé immédiatement en raison du mode. (`CSocket` ne retourne jamais **WSAEWOULDBLOCK**. La classe gère le blocage pour vous.)

Le comportement des sockets est différent dans les systèmes d'exploitation 32 bits et 64 bits (tels que Windows 95 ou Windows 98) et dans les systèmes d'exploitation 16 bits (comme Windows 3.1). Contrairement aux systèmes d'exploitation 16 bits, les systèmes d'exploitation 32 bits et 64 bits utilisent les travaux multitâches préemptifs et fournissent le multithreading. Sous les systèmes d'exploitation 32 bits et 64 bits, vous pouvez mettre les sockets dans des threads de travail distincts. Un socket dans un thread peut se bloquer sans interférer avec d'autres activités dans votre application et sans passer du temps à calculer lors du blocage. Pour plus d’informations sur la programmation multithread, consultez l’article [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

> [!NOTE]
>  Dans les applications multithread, utilisez la nature bloquante de `CSocket` pour simplifier la création du programme sans affecter la réactivité de l'interface utilisateur. Lorsque vous gérez des interventions de l'utilisateur dans le thread principal et le traitement de `CSocket` dans d'autres threads, vous pouvez séparer ces opérations logiques. Dans une application qui n'est pas multithread, ces deux opérations doivent être associées et gérées comme un seul thread, qui correspond généralement à `CAsyncSocket` de sorte que vous puissiez traiter les requêtes de communication à la demande, ou en remplaçant `CSocket::OnMessagePending` pour gérer les actions utilisateur pendant la longue activité synchrone.

Le reste de cette discussion est destinée à des programmeurs ciblant les systèmes d'exploitation 16 bits :

Normalement, si vous utilisez `CAsyncSocket`, vous devez éviter d'utiliser les opérations bloquantes et préférer le mode asynchrone à la place. Dans les opérations asynchrones, à partir du point auquel vous recevez un **WSAEWOULDBLOCK** code d’erreur après avoir appelé `Receive`, par exemple, vous attendez que votre `OnReceive` fonction membre est appelée pour vous informer que vous pouvez lire à nouveau. Appels asynchrones sont effectués en appelant telles que la fonction de notification de rappel appropriées de votre socket, [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive).

Sous windows, les appels bloquants sont considérés comme une mauvaise pratique. Par défaut, [CAsyncSocket](../mfc/reference/casyncsocket-class.md) prend en charge les appels asynchrones et vous devez gérer les blocages vous-même à l’aide de notifications de rappel. Classe [CSocket](../mfc/reference/csocket-class.md), quant à elle, est synchrone. Cette méthode pompe les messages Windows et gère le blocage pour vous.

Pour plus d'informations sur les blocages, consultez la spécification Windows Sockets. Pour plus d’informations sur les fonctions « On », consultez [Windows Sockets : Notifications de Socket](../mfc/windows-sockets-socket-notifications.md) et [Windows Sockets : dérivation à partir de Classes de sockets](../mfc/windows-sockets-deriving-from-socket-classes.md).

Pour plus d'informations, voir :

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : arrière-plan](../mfc/windows-sockets-background.md)

- [Windows Sockets : sockets flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket::OnSend](../mfc/reference/casyncsocket-class.md#onsend)

