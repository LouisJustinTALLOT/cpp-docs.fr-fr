---
title: 'Windows Sockets : Notifications de Socket | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90dfddb72ba3362f0e6595ee4f34ea2145bb85ec
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375266"
---
# <a name="windows-sockets-socket-notifications"></a>Windows Sockets : notifications de socket

Cet article décrit les fonctions de notification dans les classes de Sockets. Ces fonctions membres sont des fonctions de rappel que l’infrastructure appelle pour avertir votre objet socket d’événements importants. Les fonctions de notification sont :

- [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive): signale au socket qu’il y a des données dans la mémoire tampon pour pouvoir les récupérer en appelant [réception](../mfc/reference/casyncsocket-class.md#receive).

- [OnSend](../mfc/reference/casyncsocket-class.md#onsend): signale au socket qu’il peut maintenant envoyer des données en appelant [envoyer](../mfc/reference/casyncsocket-class.md#send).

- [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept): avertit le socket d’écoute qu’il peut accepter les demandes de connexion en attente en appelant [Accept](../mfc/reference/casyncsocket-class.md#accept).

- [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect): avertit le socket de connexion que sa tentative de connexion terminé : réussi ou erreur.

- [OnClose](../mfc/reference/casyncsocket-class.md#onclose): signale au socket qui le socket, il est connecté à s’est fermée.

    > [!NOTE]
    >  Une fonction de notification supplémentaire est [OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata). Cette notification indique le socket de réception que le socket émetteur est « out-of-band » des données à envoyer. Données hors bande sont un canal de logiquement indépendant associé à chaque paire de sockets de flux de données connectée. Le canal hors-bande est généralement utilisé pour envoyer des données « urgentes ». MFC prend en charge les données hors bande. Avancée des utilisateurs travaillant avec la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md) devrez peut-être utiliser le canal d’out-of-band, mais les utilisateurs de classe [CSocket](../mfc/reference/csocket-class.md) est déconseillé de l’utiliser. Le plus simple consiste à créer un deuxième socket pour transmettre ces données. Pour plus d’informations sur les données hors bande, consultez la spécification Windows Sockets, disponible dans le SDK Windows.

Si vous dérivez de la classe `CAsyncSocket`, vous devez substituer les fonctions de notification pour les événements présentant un intérêt pour votre application de réseau. Si vous dérivez une classe à partir de la classe `CSocket`, c’est votre choix s’il faut remplacer les fonctions de notification qui vous intéresse. Vous pouvez également utiliser `CSocket` lui-même, auquel cas la notification fonctionne par défaut à ne rien faire.

Ces fonctions sont des fonctions de rappel substituable. `CAsyncSocket` et `CSocket` convertir des messages pour envoyer des notifications, mais vous devez implémenter la notification fonctionne répondre si vous souhaitez les utiliser. Les fonctions de notification sont appelées au moment où que votre socket reçoit une notification d’un événement d’intérêt, telles que la présence de données à lire.

MFC appelle les fonctions de notification pour vous permettre de personnaliser le comportement de votre socket au moment où qu'il est notifié. Par exemple, vous pouvez appeler `Receive` à partir de votre `OnReceive` fonction de notification, autrement dit, elle est averti qu’il existe des données à lire, que vous appelez `Receive` pour le lire. Cette approche n’est pas nécessaire, mais il s’agit d’un scénario valide. Comme alternative, vous pouvez utiliser votre fonction de notification pour suivre la progression, d’impression **TRACE** messages et ainsi de suite.

Vous pouvez tirer parti de ces notifications en remplaçant les fonctions de notification dans une classe dérivée de socket et en fournissant une implémentation.

Pendant une opération de réception ou envoi de données, un `CSocket` objet devient synchrone. Au cours de l’état synchrone, toutes les notifications destinées aux autres sockets sont en file d’attente pendant que le socket en cours attend une notification qu’il veut. (Par exemple, pendant un `Receive` appel, le socket attend une notification à lire.) Une fois le socket a terminé son opération synchrone et asynchrone redevient, autres sockets peuvent commencer à recevoir les notifications en file d’attente.

> [!NOTE]
>  Dans `CSocket`, le `OnConnect` fonction de notification n’est jamais appelée. Pour les connexions, vous appelez `Connect`, qui retournera l’issue de la connexion (avec succès ou erreur). Gestion des notifications de connexion est un détail d’implémentation MFC.

Pour plus d’informations sur chaque fonction de notification, consultez la fonction sous classe `CAsyncSocket` dans le *référence MFC*. Pour le code source et des informations sur les exemples MFC, consultez [exemples MFC](../visual-cpp-samples.md).

Pour plus d'informations, voir :

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : dérivation à partir des classes de sockets](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets : fonctionnement des sockets avec des archives](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets : blocage](../mfc/windows-sockets-blocking.md)

- [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets : conversion de chaînes](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)

