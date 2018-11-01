---
title: 'Windows Sockets : utilisation de la classe CAsyncSocket'
ms.date: 11/04/2016
f1_keywords:
- CAsyncSocket
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
ms.openlocfilehash: abce497f49347719af08e71a75afa12cb99507f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459291"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets : utilisation de la classe CAsyncSocket

Cet article explique comment utiliser la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md). N’oubliez pas que cette classe encapsule l’API de Sockets Windows à un niveau très bas. `CAsyncSocket` doit être utilisé par les programmeurs qui connaissent les communications réseau en détail mais souhaitez bénéficier des rappels pour la notification des événements réseau. Selon cette hypothèse, cet article fournit uniquement les instructions de base. Vous devez probablement envisager d’utiliser `CAsyncSocket` si vous souhaitez simplifier la gestion de plusieurs protocoles réseau dans une application MFC Windows Sockets, mais ne souhaitez pas sacrifier la souplesse. Vous pouvez également penser que vous pouvez obtenir une meilleure efficacité par programmation les communications plus directement vous-même à vous impossible à l’aide de l’autre modèle plus général de la classe `CSocket`.

`CAsyncSocket` est documenté dans le *référence MFC*. Visual C++ fournit également la spécification Windows Sockets, située dans le SDK Windows. Les détails sont laissées à vous. Visual C++ ne fournit pas d’un exemple d’application pour `CAsyncSocket`.

Si vous ne sont pas très bien informé sur les communications réseau et que vous souhaitez une solution simple, utilisez la classe [CSocket](../mfc/reference/csocket-class.md) avec un `CArchive` objet. Consultez [Windows Sockets : utilisation de Sockets avec des Archives](../mfc/windows-sockets-using-sockets-with-archives.md) pour plus d’informations.

Cet article couvre les sujets suivants :

- Création et utilisation d’un `CAsyncSocket` objet.

- [Vos responsabilités avec CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).

##  <a name="_core_creating_and_using_a_casyncsocket_object"></a> Création et utilisation d’un objet CAsyncSocket

#### <a name="to-use-casyncsocket"></a>Pour utiliser CAsyncSocket

1. Construire un [CAsyncSocket](../mfc/reference/casyncsocket-class.md) et que vous utilisez l’objet à créer sous-jacent **SOCKET** gérer.

   La création d’un socket suit le modèle MFC de construction en deux étapes.

   Exemple :

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     - ou -

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   Le premier constructeur ci-dessus crée un `CAsyncSocket` objet sur la pile. Le deuxième constructeur crée un `CAsyncSocket` sur le tas. La première [créer](../mfc/reference/casyncsocket-class.md#create) appel ci-dessus utilise les paramètres par défaut pour créer un socket de flux de données. La seconde `Create` appel crée un socket datagramme avec un port spécifié et une adresse. (Vous pouvez utiliser `Create` version avec chaque méthode de construction.)

   Les paramètres à `Create` sont :

   - Un « port » : un entier court.

         For a server socket, you must specify a port. For a client socket, you typically accept the default value for this parameter, which lets Windows Sockets select a port.

   - Un type de socket : **SOCK_STREAM** (la valeur par défaut) ou **SOCK_DGRAM**.

   - Un socket « address », tel que « FTP.Microsoft.com » ou « 128.56.22.8 ».

         This is your Internet Protocol (IP) address on the network. You will probably always rely on the default value for this parameter.

   Les termes « port » et « adresse de socket » est expliqué dans [Windows Sockets : Ports et adresses de Socket](../mfc/windows-sockets-ports-and-socket-addresses.md).

1. Si le socket est un client, connecter l’objet socket à un serveur socket, à l’aide de [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect).

     - ou -

   Si le socket est un serveur, définissez le socket pour commencer à écouter (avec [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen)) tentatives de connexion à partir d’un client. Lorsqu’il reçoit une demande de connexion, acceptez-la avec [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).

   Après avoir accepté une connexion, vous pouvez effectuer des tâches telles que la validation des mots de passe.

    > [!NOTE]
    >  Le `Accept` fonction membre prend une référence à un vide `CSocket` objet comme paramètre. Vous devez créer cet objet avant d’appeler `Accept`. Si cet objet socket est hors de portée, la connexion se ferme. N’appelez pas `Create` pour ce nouvel objet socket. Pour obtenir un exemple, consultez l’article [Windows Sockets : séquence des opérations](../mfc/windows-sockets-sequence-of-operations.md).

1. Exécutez vos communications avec d’autres sockets en appelant le `CAsyncSocket` fonctions membres de l’objet qui encapsulent les fonctions d’API de Sockets Windows.

   Consultez la spécification Windows Sockets et la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md) dans le *référence MFC*.

1. Détruire le `CAsyncSocket` objet.

   Si vous avez créé l’objet socket sur la pile, son destructeur est appelé lorsque la fonction contenante va hors de portée. Si vous avez créé l’objet socket sur le tas, à l’aide la **nouveau** opérateur, il vous incombe à l’aide de la **supprimer** opérateur pour détruire l’objet.

   Le destructeur appelle l’objet [fermer](../mfc/reference/casyncsocket-class.md#close) fonction membre avant de détruire l’objet.

Pour obtenir un exemple de cette séquence dans le code (en fait, pour un `CSocket` objet), consultez [Windows Sockets : séquence des opérations](../mfc/windows-sockets-sequence-of-operations.md).

##  <a name="_core_your_responsibilities_with_casyncsocket"></a> Vos responsabilités avec CAsyncSocket

Lorsque vous créez un objet de classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md), l’objet encapsule un Windows **SOCKET** gérer et fournit des opérations sur ce descripteur. Lorsque vous utilisez `CAsyncSocket`, vous devez résoudre tous les problèmes que vous pouvez rencontrer si vous utilisez l’API directement. Exemple :

- Scénarios de « Blocage ».

- Différences d’ordre octet entre l’envoi et la réception des machines.

- Conversion entre des caractères Unicode et définie des chaînes (MBCS).

Pour les définitions de ces termes et les informations supplémentaires, consultez [Windows Sockets : blocage](../mfc/windows-sockets-blocking.md), [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md), [Windows Sockets : conversion de chaînes](../mfc/windows-sockets-converting-strings.md) .

Malgré ces problèmes, classe `CAsycnSocket` est peut-être le bon choix pour vous si votre application nécessite la souplesse et le contrôle, vous pouvez obtenir. Si pas, vous devez envisager d’utiliser la classe `CSocket` à la place. `CSocket` masque de nombreux détails part : informatique pompes de messages pendant les appels de blocage de Windows et vous donne accès à `CArchive`, qui gère les différences de classement d’octets et de conversion de chaînes pour vous.

Pour plus d'informations, voir :

- [Windows Sockets : arrière-plan](../mfc/windows-sockets-background.md)

- [Windows Sockets : sockets flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)

