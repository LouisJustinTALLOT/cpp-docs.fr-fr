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
ms.openlocfilehash: 87d4f0eb57f9e26dbf73da06b5d7ca6d61d6c174
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359997"
---
# <a name="windows-sockets-blocking"></a>Windows Sockets : blocage

Cet article et deux autres articles similaires décrivent plusieurs problèmes de programmation Windows Sockets. Cet article traite du blocage. Les autres numéros sont abordés dans les articles: [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md) et [Windows Sockets: Converting Strings](../mfc/windows-sockets-converting-strings.md).

Si vous utilisez ou dérivez de la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md), vous aurez besoin de gérer ces questions vous-même. Si vous utilisez ou dérivez de la classe [CSocket,](../mfc/reference/csocket-class.md)MFC les gère pour vous.

## <a name="blocking"></a>Blocage

Un socket peut être "en mode bloquant" ou "en mode non bloquant". Les fonctions de sockets en mode blocage (ou synchrone) ne retournent pas de résultats tant qu’elles ne terminent pas leur action. On parle de blocage car le socket dont la fonction a été appelée ne peut rien faire, il est bloqué jusqu'à ce que l'appel soit renvoyé. Un appel `Receive` à la fonction membre, par exemple, peut prendre un temps arbitrairement long à remplir car `CSocket`il `CAsyncSocket` attend que l’application d’envoi à envoyer (c’est si vous utilisez , ou en utilisant avec le blocage). Si `CAsyncSocket` un objet est en mode non-blocage (fonctionnement asynchrone), l’appel retourne immédiatement et le code d’erreur actuel, récupérable avec la fonction membre [GetLastError,](../mfc/reference/casyncsocket-class.md#getlasterror) est **WSAEWOULDBLOCK**, indiquant que l’appel aurait bloqué s’il n’avait pas retourné immédiatement en raison du mode. (`CSocket` ne retourne jamais **WSAEWOULDBLOCK**. La classe gère le blocage pour vous.)

Le comportement des sockets est différent dans les systèmes d'exploitation 32 bits et 64 bits (tels que Windows 95 ou Windows 98) et dans les systèmes d'exploitation 16 bits (comme Windows 3.1). Contrairement aux systèmes d'exploitation 16 bits, les systèmes d'exploitation 32 bits et 64 bits utilisent les travaux multitâches préemptifs et fournissent le multithreading. Sous les systèmes d'exploitation 32 bits et 64 bits, vous pouvez mettre les sockets dans des threads de travail distincts. Un socket dans un thread peut se bloquer sans interférer avec d'autres activités dans votre application et sans passer du temps à calculer lors du blocage. Pour plus d’informations sur la programmation multithreaded, voir l’article [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

> [!NOTE]
> Dans les applications multithread, utilisez la nature bloquante de `CSocket` pour simplifier la création du programme sans affecter la réactivité de l'interface utilisateur. Lorsque vous gérez des interventions de l'utilisateur dans le thread principal et le traitement de `CSocket` dans d'autres threads, vous pouvez séparer ces opérations logiques. Dans une application qui n’est pas multithread, ces deux opérations doivent être associées et gérées comme un seul thread, qui correspond généralement à `CAsyncSocket` de sorte que vous puissiez traiter les requêtes de communication à la demande, ou en remplaçant `CSocket::OnMessagePending` pour gérer les actions utilisateur pendant la longue activité synchrone.

Le reste de cette discussion est destinée à des programmeurs ciblant les systèmes d'exploitation 16 bits :

Normalement, si vous utilisez `CAsyncSocket`, vous devez éviter d'utiliser les opérations bloquantes et préférer le mode asynchrone à la place. Dans les opérations asynchrones, à partir du moment où vous recevez `Receive`un code d’erreur `OnReceive` **WSAEWOULDBLOCK** après avoir appelé , par exemple, vous attendez jusqu’à ce que votre fonction de membre est appelée pour vous informer que vous pouvez lire à nouveau. Des appels asynchrones sont effectués en annulant la fonction de notification de rappel appropriée de votre prise, comme [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive).

Sous windows, les appels bloquants sont considérés comme une mauvaise pratique. Par défaut, [CAsyncSocket](../mfc/reference/casyncsocket-class.md) prend en charge les appels asynchrones, et vous devez gérer le blocage vous-même à l’aide de notifications de rappel. La classe [CSocket](../mfc/reference/csocket-class.md), d’autre part, est synchrone. Cette méthode pompe les messages Windows et gère le blocage pour vous.

Pour plus d'informations sur les blocages, consultez la spécification Windows Sockets. Pour plus d’informations sur les fonctions "On", voir [Windows Sockets: Socket Notifications](../mfc/windows-sockets-socket-notifications.md) et [Windows Sockets: Deriving from Socket Classes](../mfc/windows-sockets-deriving-from-socket-classes.md).

Pour plus d'informations, consultez les pages suivantes :

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : arrière-plan](../mfc/windows-sockets-background.md)

- [Windows Sockets : sockets flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket::OnSend](../mfc/reference/casyncsocket-class.md#onsend)
