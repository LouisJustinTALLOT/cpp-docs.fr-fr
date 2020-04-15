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
ms.openlocfilehash: d3fc32d9da54d9cf8c79e9e5de45b81c2ef64a6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371970"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets : utilisation de la classe CAsyncSocket

Cet article explique comment utiliser la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md). Sachez que cette classe résume l’API Windows Sockets à un niveau très bas. `CAsyncSocket`est utilisé par les programmeurs qui connaissent les communications réseau en détail, mais qui veulent la commodité des rappels pour la notification des événements réseau. Sur la base de cette hypothèse, cet article ne fournit que des instructions de base. Vous devriez probablement `CAsyncSocket` envisager d’utiliser si vous voulez la facilité de Windows Sockets de traiter avec plusieurs protocoles réseau dans une application MFC, mais ne veulent pas sacrifier la flexibilité. Vous pourriez également sentir que vous pouvez obtenir une meilleure efficacité en programmant `CSocket`les communications plus directement vous-même que vous pourriez en utilisant le modèle alternatif plus général de classe .

`CAsyncSocket`est documenté dans la *référence MFC*. Visual CMD fournit également les spécifications Windows Sockets, situées dans le SDK Windows. Les détails vous sont laissés. Visual CMD ne fournit pas `CAsyncSocket`d’exemple pour .

Si vous n’êtes pas très bien informé sur les communications réseau `CArchive` et que vous voulez une solution simple, utilisez la classe [CSocket](../mfc/reference/csocket-class.md) avec un objet. Voir [Windows Sockets: Using Sockets with Archives](../mfc/windows-sockets-using-sockets-with-archives.md) pour plus d’informations.

Cet article couvre les points suivants :

- Création et `CAsyncSocket` utilisation d’un objet.

- [Vos responsabilités avec CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).

## <a name="creating-and-using-a-casyncsocket-object"></a><a name="_core_creating_and_using_a_casyncsocket_object"></a>Création et utilisation d’un objet CAsyncSocket

#### <a name="to-use-casyncsocket"></a>Pour utiliser CAsyncSocket

1. Construisez un objet [CAsyncSocket](../mfc/reference/casyncsocket-class.md) et utilisez l’objet pour créer la poignée **SOCKET** sous-jacente.

   La création d’une prise suit le modèle MFC de la construction en deux étapes.

   Par exemple :

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     -ou-

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   Le premier constructeur ci-dessus crée un `CAsyncSocket` objet sur la pile. Le deuxième constructeur `CAsyncSocket` crée un sur le tas. Le premier appel [Créer](../mfc/reference/casyncsocket-class.md#create) ci-dessus utilise les paramètres par défaut pour créer une prise de flux. Le `Create` deuxième appel crée une prise de datagram avec un port et une adresse spécifiés. (Vous pouvez `Create` utiliser l’une ou l’autre version avec l’une ou l’autre méthode de construction.)

   Les paramètres `Create` à être:

   - Un "port": un peu d’ensurger.

      Pour une prise de serveur, vous devez spécifier un port. Pour une prise client, vous acceptez généralement la valeur par défaut de ce paramètre, qui permet aux prises Windows de sélectionner un port.

   - Type de prise : **SOCK_STREAM** (par défaut) ou **SOCK_DGRAM**.

   - Une prise "adresse", comme "ftp.microsoft.com" ou "128.56.22.8".

      Il s’agit de votre adresse De protocole Internet (IP) sur le réseau. Vous comptez probablement toujours sur la valeur par défaut pour ce paramètre.

   Les termes «port» et «adresse de prise» sont expliqués dans [Windows Sockets: Ports et Socket Addresses](../mfc/windows-sockets-ports-and-socket-addresses.md).

1. Si la prise est un client, connectez l’objet de prise à une prise de serveur, en utilisant [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect).

     -ou-

   Si la prise est un serveur, définissez la prise pour commencer à écouter (avec [CAsyncSocket::Ecouter](../mfc/reference/casyncsocket-class.md#listen)) pour les tentatives de connexion d’un client. Lors de la réception d’une demande de connexion, l’accepter avec [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).

   Après avoir accepté une connexion, vous pouvez effectuer des tâches telles que la validation des mots de passe.

    > [!NOTE]
    >  La `Accept` fonction membre fait référence à `CSocket` un nouvel objet vide comme paramètre. Vous devez construire cet `Accept`objet avant d’appeler . Si cet objet socket est hors de portée, la connexion se ferme. N’appelez `Create` pas pour ce nouvel objet de prise. Par exemple, voir l’article [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md).

1. Effectuez des communications avec d’autres prises en appelant les fonctions membres de l’objet `CAsyncSocket` qui encapsulent les fonctions d’API Windows Sockets.

   Voir les spécifications Windows Sockets et la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md) dans la *référence MFC*.

1. Détruisez `CAsyncSocket` l’objet.

   Si vous avez créé l’objet de prise sur la pile, son destructeur est appelé lorsque la fonction contenante sort de portée. Si vous avez créé l’objet de prise sur le tas, en utilisant le **nouvel** opérateur, vous êtes responsable de l’utilisation de l’opérateur **de suppression** pour détruire l’objet.

   Le destructeur appelle la fonction de membre [Close](../mfc/reference/casyncsocket-class.md#close) de l’objet avant de détruire l’objet.

Pour un exemple de cette séquence `CSocket` dans le code (en fait pour un objet), voir [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md).

## <a name="your-responsibilities-with-casyncsocket"></a><a name="_core_your_responsibilities_with_casyncsocket"></a>Vos responsabilités avec CAsyncSocket

Lorsque vous créez un objet de classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md), l’objet encapsule une poignée Windows **SOCKET** et fournit des opérations sur cette poignée. Lorsque vous `CAsyncSocket`utilisez, vous devez faire face à tous les problèmes auxquels vous pourriez faire face si vous utilisez l’API directement. Par exemple :

- Scénarios de "blocage".

- Byte commander des différences entre les machines d’envoi et de réception.

- Conversion entre les cordes Unicode et multioctets (MBCS).

Pour les définitions de ces termes et des informations supplémentaires, voir [Windows Sockets: Blocking](../mfc/windows-sockets-blocking.md), [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md), [Windows Sockets: Converting Strings](../mfc/windows-sockets-converting-strings.md).

Malgré ces problèmes, la classe `CAsycnSocket` peut être le bon choix pour vous si votre application nécessite toute la flexibilité et le contrôle que vous pouvez obtenir. Si ce n’est `CSocket` pas le cas, vous devriez envisager d’utiliser la classe à la place. `CSocket`cache beaucoup de détails à vous: il pompe les messages Windows `CArchive`lors du blocage des appels et vous donne accès à , qui gère les différences de commande byte et la conversion des chaînes pour vous.

Pour plus d'informations, consultez les pages suivantes :

- [Windows Sockets : arrière-plan](../mfc/windows-sockets-background.md)

- [Windows Sockets : sockets flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)
