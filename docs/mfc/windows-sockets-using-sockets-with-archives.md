---
description: 'En savoir plus sur : Windows Sockets : utilisation de sockets avec des Archives'
title: 'Windows Sockets : utilisation de sockets avec des archives'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
ms.openlocfilehash: bd5f239a0fdcee4bf6c6141994c4ca5002bdc6b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331343"
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows Sockets : utilisation de sockets avec des archives

Cet article décrit le [modèle de programmation CSocket](#_core_the_csocket_programming_model). La classe [CSocket](../mfc/reference/csocket-class.md) fournit la prise en charge des sockets à un niveau d’abstraction supérieur à celui de la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md). `CSocket` utilise une version du protocole de sérialisation MFC pour passer des données vers et à partir d’un objet Socket via un objet [CARCHIVE](../mfc/reference/carchive-class.md) MFC. `CSocket` fournit un blocage (lors de la gestion du traitement en arrière-plan des messages Windows) et vous donne accès à `CArchive`, qui gère de nombreux aspects de la communication que vous devriez faire en utilisant l'API brute ou la classe `CAsyncSocket`.

> [!TIP]
> Vous pouvez utiliser la classe `CSocket` seule, en tant que version plus pratique de `CAsyncSocket`, mais le modèle de programmation le plus simple consiste à utiliser `CSocket` avec un objet `CArchive`.

Pour plus d’informations sur le fonctionnement de l’implémentation des sockets avec les archives, consultez [Windows Sockets : fonctionnement des sockets avec les archives](../mfc/windows-sockets-how-sockets-with-archives-work.md). Pour obtenir un exemple de code, consultez [Windows Sockets : séquence des opérations](../mfc/windows-sockets-sequence-of-operations.md) et [Windows Sockets : exemple de sockets utilisant des archives](../mfc/windows-sockets-example-of-sockets-using-archives.md). Pour plus d’informations sur certaines des fonctionnalités que vous pouvez obtenir en dérivant vos propres classes des classes de sockets, consultez [Windows Sockets : dérivation à partir des classes de sockets](../mfc/windows-sockets-deriving-from-socket-classes.md).

> [!NOTE]
> Si vous écrivez un programme client MFC pour communiquer avec des serveurs (non-MFC) établis, n'envoyez pas les objets C++ à l'archive. Sauf si le serveur est une application MFC qui comprend les types d'objets que vous souhaitez envoyer, il ne peut pas recevoir ni désérialiser vos objets. Pour obtenir des informations sur le sujet de la communication avec les applications non-MFC, consultez également l’article [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md).

## <a name="the-csocket-programming-model"></a><a name="_core_the_csocket_programming_model"></a> Le modèle de programmation CSocket

L'utilisation d'un objet `CSocket` implique la création et l'association de plusieurs objets de classe MFC. Dans la procédure générale ci-dessous, chaque action est effectuée par le socket de serveur et le socket client, sauf à l'étape 3, dans laquelle chaque type de socket requiert une action différente.

> [!TIP]
> Au moment de l'exécution, l'application serveur démarre généralement en premier pour être prête et "à l'écoute" lorsque l'application cliente recherche une connexion. Si le serveur n'est pas prêt lorsque le client tente de se connecter, vous aurez généralement besoin que l'application utilisateur tente de se connecter de nouveau ultérieurement.

#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>Pour installer la communication entre un socket de serveur et un socket client

1. Construit un objet [CSocket](../mfc/reference/csocket-class.md) .

1. Utilisez l’objet pour créer le handle de **Socket** sous-jacent.

   Pour un `CSocket` objet client, vous devez normalement utiliser les paramètres par défaut à [créer](../mfc/reference/casyncsocket-class.md#create), sauf si vous avez besoin d’un socket datagramme. Pour un `CSocket` objet serveur, vous devez spécifier un port dans l' `Create` appel.

    > [!NOTE]
    >  `CArchive` ne fonctionne pas avec les sockets datagramme. Si vous souhaitez utiliser `CSocket` pour un socket datagramme, vous devez utiliser la classe comme vous utiliseriez `CAsyncSocket`, c'est à dire, sans archive. Les datagrammes sont peu fiables (aucune garantie d'arrivée et peuvent être répétés, ou hors de la séquence), ils ne sont pas compatibles avec la sérialisation par le biais d'une archive. Vous vous attendez à ce qu'une opération de sérialisation se termine de manière fiable et dans l'ordre. Si vous essayez d'utiliser `CSocket` avec un objet `CArchive` pour un datagramme, une assertion MFC échoue.

1. Si le socket est un client, appelez [CAsyncSocket :: Connect](../mfc/reference/casyncsocket-class.md#connect) pour connecter l’objet socket à un socket serveur.

     -ou-

   Si le socket est un serveur, appelez [CAsyncSocket :: Listen](../mfc/reference/casyncsocket-class.md#listen) pour commencer à écouter les tentatives de connexion à partir d’un client. Lors de la réception d’une demande de connexion, acceptez-la en appelant [CAsyncSocket :: Accept](../mfc/reference/casyncsocket-class.md#accept).

    > [!NOTE]
    >  La `Accept` fonction membre accepte une référence à un nouvel objet vide `CSocket` comme paramètre. Vous devez construire cet objet avant d’appeler `Accept` . Si cet objet socket est hors de portée, la connexion se ferme. N’appelez pas `Create` pour ce nouvel objet Socket.

1. Créez un objet [CSocketFile](../mfc/reference/csocketfile-class.md) , en lui associant l' `CSocket` objet.

1. Créez un objet [CArchive](../mfc/reference/carchive-class.md) pour charger (recevoir) ou stocker (envoyer) des données. L'archive est associée à l'objet `CSocketFile`.

   N'oubliez pas que `CArchive` ne fonctionne pas avec les sockets datagramme.

1. Utilisez l'objet `CArchive` pour passer des données de test entre les sockets client et serveur.

   Gardez à l'esprit qu'un objet donné `CArchive` déplace les données dans une seule direction : pour charger (recevoir) ou enregistrer (émettre). Dans certains cas, vous utiliserez deux objets `CArchive` : un pour envoyer des données, l'autre pour recevoir les accusés de réception.

   Après avoir accepté une connexion et la configuration de l’archive, vous pouvez effectuer des tâches telles que la validation des mots de passe.

1. Détruisez archive, le fichier de sockets et les objets socket.

    > [!NOTE]
    >  La classe `CArchive` fournit la fonction membre `IsBufferEmpty` spécifiquement pour une utilisation avec la classe `CSocket`. Si la mémoire tampon contient plusieurs messages de données, par exemple, vous devez exécuter la boucle jusqu'à ce qu'ils aient tous été lus et que le tampon ait été vidé. Sinon, la notification suivante selon laquelle il y a des données à recevoir peut être retardée indéfiniment. Utilisez `IsBufferEmpty` pour vérifier que vous récupérez toutes les données.

L’article [Windows Sockets : la séquence d’opérations](../mfc/windows-sockets-sequence-of-operations.md) illustre les deux côtés de ce processus avec un exemple de code.

Pour plus d'informations, consultez les pages suivantes :

- [Windows Sockets : Sockets de flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagrammes](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket :: Create](../mfc/reference/csocket-class.md#create)
