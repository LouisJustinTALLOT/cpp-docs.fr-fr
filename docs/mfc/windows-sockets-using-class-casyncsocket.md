---
title: 'Windows Sockets : utilisation de la classe CAsyncSocket'
ms.date: 11/04/2016
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
ms.openlocfilehash: 3977308776c4ec6fed844038c4453ad03d065f98
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445941"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets : utilisation de la classe CAsyncSocket

Cet article explique comment utiliser la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md). N’oubliez pas que cette classe encapsule l’API Windows Sockets à un niveau très bas. `CAsyncSocket` est utilisé par les programmeurs qui connaissent les communications réseau en détail, mais qui veulent la commodité des rappels pour la notification des événements réseau. Sur la base de cette hypothèse, cet article fournit uniquement des instructions de base. Vous devez probablement envisager d’utiliser `CAsyncSocket` si vous souhaitez que Windows Sockets soit plus facile à gérer avec plusieurs protocoles réseau dans une application MFC, mais ne souhaite pas sacrifier la flexibilité. Vous vous sentirez peut-être également à obtenir une meilleure efficacité en programmant les communications plus directement que vous ne pouviez utiliser le modèle d’alternative plus général de la classe `CSocket`.

`CAsyncSocket` est documenté dans la *référence MFC*. Visual C++ fournit également la spécification Windows Sockets, située dans le SDK Windows. Les détails sont conservés. Visual C++ ne fournit pas d’exemple d’application pour `CAsyncSocket`.

Si vous n’êtes pas très compétent en ce qui concerne les communications réseau et que vous souhaitez une solution simple, utilisez la classe [CSocket](../mfc/reference/csocket-class.md) avec un objet `CArchive`. Pour plus d’informations, consultez [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md) .

Cet article couvre les points suivants :

- Création et utilisation d’un objet `CAsyncSocket`.

- [Vos responsabilités avec CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).

##  <a name="_core_creating_and_using_a_casyncsocket_object"></a>Création et utilisation d’un objet CAsyncSocket

#### <a name="to-use-casyncsocket"></a>Pour utiliser CAsyncSocket

1. Construisez un objet [CAsyncSocket](../mfc/reference/casyncsocket-class.md) et utilisez l’objet pour créer le handle de **Socket** sous-jacent.

   La création d’un socket suit le modèle MFC de construction en deux étapes.

   Par exemple :

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     -ou-

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   Le premier constructeur ci-dessus crée un objet `CAsyncSocket` sur la pile. Le deuxième constructeur crée un `CAsyncSocket` sur le tas. Le premier appel de [Create](../mfc/reference/casyncsocket-class.md#create) ci-dessus utilise les paramètres par défaut pour créer un socket de flux. Le deuxième `Create` appel crée un socket de datagramme avec un port et une adresse spécifiés. (Vous pouvez utiliser l’une ou l’autre `Create` version avec l’une ou l’autre méthode de construction.)

   Les paramètres à `Create` sont :

   - « Port » : un entier bref.

      Pour un socket serveur, vous devez spécifier un port. Pour un socket client, vous acceptez généralement la valeur par défaut pour ce paramètre, ce qui permet à Windows Sockets de sélectionner un port.

   - Type de socket : **SOCK_STREAM** (valeur par défaut) ou **SOCK_DGRAM**.

   - Une « adresse » de socket, telle que « ftp.microsoft.com » ou « 128.56.22.8 ».

      Il s’agit de votre adresse IP (Internet Protocol) sur le réseau. Vous reposerez probablement toujours sur la valeur par défaut de ce paramètre.

   Les termes « port » et « adresse de socket » sont expliqués dans [Windows Sockets : ports et adresses de socket](../mfc/windows-sockets-ports-and-socket-addresses.md).

1. Si le socket est un client, connectez l’objet socket à un socket serveur à l’aide de [CAsyncSocket :: Connect](../mfc/reference/casyncsocket-class.md#connect).

     -ou-

   Si le socket est un serveur, définissez le socket sur commencer l’écoute (avec [CAsyncSocket :: Listen](../mfc/reference/casyncsocket-class.md#listen)) pour les tentatives de connexion à partir d’un client. Lors de la réception d’une demande de connexion, acceptez-la avec [CAsyncSocket :: Accept](../mfc/reference/casyncsocket-class.md#accept).

   Après avoir accepté une connexion, vous pouvez effectuer des tâches telles que la validation des mots de passe.

    > [!NOTE]
    >  La fonction membre `Accept` accepte une référence à un nouvel objet `CSocket` vide comme paramètre. Vous devez construire cet objet avant d’appeler `Accept`. Si cet objet socket est hors de portée, la connexion se ferme. N’appelez pas `Create` pour ce nouvel objet Socket. Pour obtenir un exemple, consultez l’article [Windows Sockets : séquence des opérations](../mfc/windows-sockets-sequence-of-operations.md).

1. Effectuez des communications avec d’autres Sockets en appelant les fonctions membres de l’objet `CAsyncSocket` qui encapsulent les fonctions de l’API Windows Sockets.

   Consultez la spécification Windows Sockets et la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md) dans la *référence MFC*.

1. Détruisez l’objet `CAsyncSocket`.

   Si vous avez créé l’objet socket sur la pile, son destructeur est appelé lorsque la fonction conteneur est hors de portée. Si vous avez créé l’objet socket sur le tas, à l’aide de l’opérateur **New** , vous êtes responsable de l’utilisation de l’opérateur **Delete** pour détruire l’objet.

   Le destructeur appelle la fonction membre [Close](../mfc/reference/casyncsocket-class.md#close) de l’objet avant de détruire l’objet.

Pour obtenir un exemple de cette séquence dans le code (en fait pour un objet `CSocket`), consultez [Windows Sockets : séquence des opérations](../mfc/windows-sockets-sequence-of-operations.md).

##  <a name="_core_your_responsibilities_with_casyncsocket"></a>Vos responsabilités avec CAsyncSocket

Lorsque vous créez un objet de classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md), l’objet encapsule un handle Windows **Socket** et fournit des opérations sur ce handle. Lorsque vous utilisez `CAsyncSocket`, vous devez gérer tous les problèmes que vous pouvez rencontrer si vous utilisez l’API directement. Par exemple :

- Scénarios de « blocage ».

- Différences d’ordre d’octet entre les ordinateurs d’envoi et de réception.

- Conversion entre les chaînes Unicode et MBCS (Multibyte Character Set).

Pour obtenir les définitions de ces termes et des informations supplémentaires, consultez [Windows Sockets : blocage](../mfc/windows-sockets-blocking.md), [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md), [Windows Sockets : conversion de chaînes](../mfc/windows-sockets-converting-strings.md).

Malgré ces problèmes, la classe `CAsycnSocket` peut être le bon choix pour vous si votre application a besoin de toute la flexibilité et du contrôle que vous pouvez obtenir. Si ce n’est pas le cas, vous devez envisager d’utiliser la classe `CSocket` à la place. `CSocket` masque un grand nombre de détails : il pompe les messages Windows pendant les appels de blocage et vous donne accès à `CArchive`, qui gère les différences d’ordre d’octet et la conversion de chaînes pour vous.

Pour plus d'informations, consultez les pages suivantes :

- [Windows Sockets : arrière-plan](../mfc/windows-sockets-background.md)

- [Windows Sockets : sockets flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)
