---
title: 'Windows Sockets : dérivation à partir des classes de sockets'
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from socket classes
- Windows Sockets [MFC], deriving from socket classes
- sockets [MFC], deriving from socket classes
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
ms.openlocfilehash: d860aacef164155f87db33355211b1a8e598c91b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648810"
---
# <a name="windows-sockets-deriving-from-socket-classes"></a>Windows Sockets : dérivation à partir des classes de sockets

Cet article décrit certaines des fonctionnalités que vous pouvez acquérir en dérivant votre propre classe à partir d’une des classes socket.

Vous pouvez dériver vos propres classes de socket soit [CAsyncSocket](../mfc/reference/casyncsocket-class.md) ou [CSocket](../mfc/reference/csocket-class.md) pour ajouter vos propres fonctionnalités. En particulier, ces classes fournissent un nombre de fonctions membres virtuelles que vous pouvez substituer. Ces fonctions incluent [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive), [OnSend](../mfc/reference/casyncsocket-class.md#onsend), [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept), [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect), et [OnClose](../mfc/reference/casyncsocket-class.md#onclose). Vous pouvez remplacer les fonctions dans votre classe dérivée de socket pour tirer parti des notifications que lorsque des événements de réseau se produisent. L’infrastructure appelle ces fonctions de rappel de notification pour être averti des événements de sockets importants, tels que la réception de données que vous pouvez commencer la lecture. Pour plus d’informations sur les fonctions de notification, consultez [Windows Sockets : Notifications de Socket](../mfc/windows-sockets-socket-notifications.md).

En outre, la classe `CSocket` fournit le [OnMessagePending](../mfc/reference/csocket-class.md#onmessagepending) fonction membre (une avancée substituable). MFC appelle cette fonction, tandis que le socket est pompage des messages basés sur Windows. Vous pouvez remplacer `OnMessagePending` pour rechercher des messages spécifiques à partir de Windows et y répondre.

La version par défaut de `OnMessagePending` fourni dans la classe `CSocket` examine la file d’attente de messages WM_PAINT en attendant un appel de blocage. Il répartit les messages afin d’améliorer la qualité d’affichage. Outre son utilité, cela illustre une façon de remplacer la fonction vous-même. Autre exemple, envisagez d’utiliser `OnMessagePending` pour la tâche suivante. Supposons que vous affichez une boîte de dialogue non modale en attendant une transaction de réseau terminer. La boîte de dialogue contient un bouton Annuler que l’utilisateur peut utiliser pour annuler les opérations de blocage est trop longue. Votre `OnMessagePending` remplacement peut pomper les messages relatifs à cette boîte de dialogue non modale.

Dans votre `OnMessagePending` remplacer, retourner **TRUE** ou le retour d’un appel à la version de la classe de base de `OnMessagePending`. Appeler la version de la classe de base si elle effectue le travail que vous voulez.

Pour plus d'informations, voir :

- [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : blocage](../mfc/windows-sockets-blocking.md)

- [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets : conversion de chaînes](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)

