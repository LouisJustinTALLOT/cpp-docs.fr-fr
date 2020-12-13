---
description: 'En savoir plus sur : Windows Sockets : dérivation à partir des classes de Sockets'
title: 'Windows Sockets : dérivation à partir des classes de sockets'
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [MFC], from socket classes
- Windows Sockets [MFC], deriving from socket classes
- sockets [MFC], deriving from socket classes
ms.assetid: 3a26e67a-e323-433b-9b05-eca018799801
ms.openlocfilehash: ba3526ddde4d254ff044fa09588d7764b16fb719
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132962"
---
# <a name="windows-sockets-deriving-from-socket-classes"></a>Windows Sockets : dérivation à partir des classes de sockets

Cet article décrit quelques-unes des fonctionnalités que vous pouvez obtenir en dérivant votre propre classe de l’une des classes de Socket.

Vous pouvez dériver vos propres classes de socket à l’aide de [CAsyncSocket](../mfc/reference/casyncsocket-class.md) ou de [CSocket](../mfc/reference/csocket-class.md) pour ajouter vos propres fonctionnalités. En particulier, ces classes fournissent un certain nombre de fonctions membres virtuelles que vous pouvez substituer. Ces fonctions incluent [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive), [OnSend](../mfc/reference/casyncsocket-class.md#onsend), [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept), [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect)et [OnClose](../mfc/reference/casyncsocket-class.md#onclose). Vous pouvez remplacer les fonctions dans votre classe de socket dérivée pour tirer parti des notifications qu’ils fournissent lorsque des événements réseau se produisent. L’infrastructure appelle ces fonctions de rappel de notification pour vous avertir des événements de socket importants, tels que la réception de données que vous pouvez commencer à lire. Pour plus d’informations sur les fonctions de notification, consultez [Windows Sockets : notifications de socket](../mfc/windows-sockets-socket-notifications.md).

En outre, `CSocket` la classe fournit la fonction membre [OnMessagePending](../mfc/reference/csocket-class.md#onmessagepending) (élément remplaçable avancé). MFC appelle cette fonction lorsque le socket pompe des messages Windows. Vous pouvez remplacer `OnMessagePending` pour rechercher des messages spécifiques à partir de Windows et y répondre.

La version par défaut de `OnMessagePending` fournie dans `CSocket` la classe examine la file d’attente de messages pour WM_PAINT messages en attendant la fin d’un appel bloquant. Elle distribue des messages de peinture pour améliorer la qualité d’affichage. Hormis ce qui est utile, cela illustre une façon de remplacer la fonction vous-même. Autre exemple, envisagez `OnMessagePending` d’utiliser pour la tâche suivante. Supposons que vous affichez une boîte de dialogue non modale en attendant la fin d’une transaction réseau. La boîte de dialogue contient un bouton Annuler que l’utilisateur peut utiliser pour annuler les transactions bloquantes qui prennent trop de temps. Votre `OnMessagePending` remplacement peut pomper des messages liés à cette boîte de dialogue non modale.

Dans votre `OnMessagePending` substitution, retournez la **valeur true** ou le retour d’un appel à la version de classe de base de `OnMessagePending` . Appelez la version de la classe de base si elle effectue un travail que vous voulez encore faire.

Pour plus d'informations, consultez les pages suivantes :

- [Windows Sockets : utilisation de sockets avec des Archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : Blocage](../mfc/windows-sockets-blocking.md)

- [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets : conversion de chaînes](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)
