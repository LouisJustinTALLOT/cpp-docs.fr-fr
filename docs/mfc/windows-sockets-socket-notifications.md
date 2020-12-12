---
description: 'En savoir plus sur : Windows Sockets : notifications de socket'
title: 'Windows Sockets : notifications de socket'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
ms.openlocfilehash: 856e954050753545a7ff64d3e111c648dc0284d7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207655"
---
# <a name="windows-sockets-socket-notifications"></a>Windows Sockets : notifications de socket

Cet article décrit les fonctions de notification dans les classes de Socket. Ces fonctions membres sont des fonctions de rappel que l’infrastructure appelle pour notifier votre objet socket d’événements importants. Les fonctions de notification sont les suivantes :

- [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive): avertit ce Socket qu’il y a des données dans la mémoire tampon à récupérer en appelant [Receive](../mfc/reference/casyncsocket-class.md#receive).

- [OnSend](../mfc/reference/casyncsocket-class.md#onsend): avertit ce Socket qu’il peut maintenant envoyer des données en appelant [Send](../mfc/reference/casyncsocket-class.md#send).

- [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept): avertit ce socket d’écoute qu’il peut accepter les demandes de connexion en attente en appelant [Accept](../mfc/reference/casyncsocket-class.md#accept).

- [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect): avertit ce socket de connexion que sa tentative de connexion est terminée : peut-être avec succès ou peut-être en raison d’une erreur.

- [OnClose](../mfc/reference/casyncsocket-class.md#onclose): avertit ce socket que le socket auquel il est connecté est fermé.

    > [!NOTE]
    >  Une fonction de notification supplémentaire est [OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata). Cette notification indique au socket récepteur que le socket d’envoi a des données « hors bande » à envoyer. Les données hors bande sont un canal logiquement indépendant associé à chaque paire de sockets de flux connectés. Le canal hors bande est généralement utilisé pour envoyer des données « urgentes ». MFC prend en charge les données hors bande. Les utilisateurs expérimentés qui travaillent avec la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md) peuvent avoir besoin d’utiliser le canal hors bande, mais les utilisateurs de la classe [CSocket](../mfc/reference/csocket-class.md) ne sont pas déconseillés de l’utiliser. Le moyen le plus simple consiste à créer un deuxième Socket pour transmettre ces données. Pour plus d’informations sur les données hors bande, consultez la spécification Windows Sockets, disponible dans le SDK Windows.

Si vous dérivez de `CAsyncSocket` la classe, vous devez remplacer les fonctions de notification pour les événements réseau qui présentent un intérêt pour votre application. Si vous dérivez une classe de la classe, vous pouvez choisir de `CSocket` remplacer les fonctions de notification intéressantes. Vous pouvez également vous `CSocket` en servir, auquel cas les fonctions de notification ne font rien par défaut.

Ces fonctions sont des fonctions de rappel remplaçables. `CAsyncSocket` et `CSocket` convertir les messages en notifications, mais vous devez implémenter le mode de réponse des fonctions de notification si vous souhaitez les utiliser. Les fonctions de notification sont appelées au moment où votre socket est averti d’un événement d’intérêt, tel que la présence de données à lire.

MFC appelle les fonctions de notification pour vous permettre de personnaliser le comportement de votre socket au moment où il est notifié. Par exemple, vous pouvez appeler `Receive` à partir de votre `OnReceive` fonction de notification, autrement dit, pour être informé qu’il y a des données à lire, vous appelez `Receive` pour le lire. Cette approche n’est pas nécessaire, mais il s’agit d’un scénario valide. Vous pouvez également utiliser votre fonction de notification pour suivre la progression, imprimer des messages de **trace** , etc.

Vous pouvez tirer parti de ces notifications en substituant les fonctions de notification dans une classe de socket dérivée et en fournissant une implémentation.

Pendant une opération telle que la réception ou l’envoi de données, un `CSocket` objet devient synchrone. Pendant l’état synchrone, toutes les notifications destinées à d’autres sockets sont mises en file d’attente pendant que le socket actuel attend la notification qu’il souhaite. (Par exemple, lors d’un `Receive` appel, le socket souhaite qu’une notification soit lue.) Une fois que le socket a terminé son opération synchrone et redevient asynchrone, les autres Sockets peuvent commencer à recevoir les notifications mises en file d’attente.

> [!NOTE]
> Dans `CSocket` , la `OnConnect` fonction de notification n’est jamais appelée. Pour les connexions, vous appelez `Connect` , qui retournera lorsque la connexion sera terminée (avec succès ou par erreur). La façon dont les notifications de connexion sont gérées est un détail d’implémentation MFC.

Pour plus d’informations sur chaque fonction de notification, consultez la fonction sous `CAsyncSocket` la classe dans la *référence MFC*. Pour obtenir le code source et des informations sur les exemples MFC, consultez [MFC Samples](../overview/visual-cpp-samples.md#mfc-samples).

Pour plus d'informations, consultez les pages suivantes :

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : dérivation à partir des classes de Sockets](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets : fonctionnement des sockets avec les Archives](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets : Blocage](../mfc/windows-sockets-blocking.md)

- [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets : conversion de chaînes](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)
