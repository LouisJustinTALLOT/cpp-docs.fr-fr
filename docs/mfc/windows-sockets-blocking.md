---
description: 'En savoir plus sur : Windows Sockets : blocage'
title: 'Windows Sockets : Blocage'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], blocking mode
- Windows Sockets [MFC], Windows platforms
- Windows Sockets [MFC], blocking mode
- sockets [MFC], behavior on different Windows platforms
- blocking mode sockets
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
ms.openlocfilehash: 21d1a2fb635f3d45e639c950a7ad1748dc3dda74
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197450"
---
# <a name="windows-sockets-blocking"></a>Windows Sockets : Blocage

Cet article et deux autres articles similaires décrivent plusieurs problèmes de programmation Windows Sockets. Cet article traite du blocage. Les autres problèmes sont abordés dans les articles suivants : [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md) et [Windows Sockets : conversion de chaînes](../mfc/windows-sockets-converting-strings.md).

Si vous utilisez ou dérivez de la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md), vous devrez gérer ces problèmes vous-même. Si vous utilisez ou dérivez de la classe [CSocket](../mfc/reference/csocket-class.md), MFC les gère pour vous.

## <a name="blocking"></a>Blocage

Un socket peut être "en mode bloquant" ou "en mode non bloquant". Les fonctions de sockets en mode blocage (ou synchrone) ne retournent pas de résultats tant qu’elles ne terminent pas leur action. On parle de blocage car le socket dont la fonction a été appelée ne peut rien faire, il est bloqué jusqu'à ce que l'appel soit renvoyé. Un appel à la `Receive` fonction membre, par exemple, peut prendre un temps arbitrairement long pour s’exécuter pendant qu’il attend que l’application émettrice envoie (c’est le cas si vous utilisez `CSocket` ou utilisez `CAsyncSocket` with Blocking). Si un `CAsyncSocket` objet est en mode non bloquant (fonctionnement asynchrone), l’appel est retourné immédiatement et le code d’erreur actuel, récupérable avec la fonction membre [GetLastError](../mfc/reference/casyncsocket-class.md#getlasterror) , est **WSAEWOULDBLOCK**, ce qui indique que l’appel aurait été bloqué, car il n’a pas été retourné immédiatement en raison du mode. ( `CSocket` ne retourne jamais **WSAEWOULDBLOCK**. La classe gère le blocage pour vous.)

Le comportement des sockets est différent dans les systèmes d'exploitation 32 bits et 64 bits (tels que Windows 95 ou Windows 98) et dans les systèmes d'exploitation 16 bits (comme Windows 3.1). Contrairement aux systèmes d'exploitation 16 bits, les systèmes d'exploitation 32 bits et 64 bits utilisent les travaux multitâches préemptifs et fournissent le multithreading. Sous les systèmes d'exploitation 32 bits et 64 bits, vous pouvez mettre les sockets dans des threads de travail distincts. Un socket dans un thread peut se bloquer sans interférer avec d'autres activités dans votre application et sans passer du temps à calculer lors du blocage. Pour plus d’informations sur la programmation multithread, consultez l’article sur les [multithreads](../parallel/multithreading-support-for-older-code-visual-cpp.md).

> [!NOTE]
> Dans les applications multithread, utilisez la nature bloquante de `CSocket` pour simplifier la création du programme sans affecter la réactivité de l'interface utilisateur. Lorsque vous gérez des interventions de l'utilisateur dans le thread principal et le traitement de `CSocket` dans d'autres threads, vous pouvez séparer ces opérations logiques. Dans une application qui n’est pas multithread, ces deux opérations doivent être associées et gérées comme un seul thread, qui correspond généralement à `CAsyncSocket` de sorte que vous puissiez traiter les requêtes de communication à la demande, ou en remplaçant `CSocket::OnMessagePending` pour gérer les actions utilisateur pendant la longue activité synchrone.

Le reste de cette discussion est destinée à des programmeurs ciblant les systèmes d'exploitation 16 bits :

Normalement, si vous utilisez `CAsyncSocket`, vous devez éviter d'utiliser les opérations bloquantes et préférer le mode asynchrone à la place. Dans les opérations asynchrones, à partir du moment où vous recevez un code d’erreur **WSAEWOULDBLOCK** après l’appel `Receive` de, par exemple, vous attendez que votre `OnReceive` fonction membre soit appelée pour vous avertir que vous pouvez lire à nouveau. Les appels asynchrones sont effectués en rappelant la fonction de notification de rappel appropriée de votre socket, telle que [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive).

Sous windows, les appels bloquants sont considérés comme une mauvaise pratique. Par défaut, [CAsyncSocket](../mfc/reference/casyncsocket-class.md) prend en charge les appels asynchrones, et vous devez gérer vous-même le blocage à l’aide de notifications de rappel. La classe [CSocket](../mfc/reference/csocket-class.md), en revanche, est synchrone. Cette méthode pompe les messages Windows et gère le blocage pour vous.

Pour plus d'informations sur les blocages, consultez la spécification Windows Sockets. Pour plus d’informations sur les fonctions « on », consultez [Windows Sockets : notifications de socket](../mfc/windows-sockets-socket-notifications.md) et [Windows Sockets : dérivation à partir des classes de socket](../mfc/windows-sockets-deriving-from-socket-classes.md).

Pour plus d'informations, consultez les pages suivantes :

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : utilisation de sockets avec des Archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : Présentation](../mfc/windows-sockets-background.md)

- [Windows Sockets : Sockets de flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagrammes](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket :: OnSend](../mfc/reference/casyncsocket-class.md#onsend)
