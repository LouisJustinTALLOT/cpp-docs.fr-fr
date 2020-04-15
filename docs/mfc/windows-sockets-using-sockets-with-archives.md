---
title: 'Windows Sockets : utilisation de sockets avec des archives'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
ms.openlocfilehash: 55b4f9a5412c1447fe2b3bde10cb934b91abf008
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359954"
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows Sockets : utilisation de sockets avec des archives

Cet article décrit le modèle de [programmation CSocket](#_core_the_csocket_programming_model). Classe [CSocket](../mfc/reference/csocket-class.md) fournit le soutien de prise à un niveau plus élevé d’abstraction que ne le fait [CAsyncSocket](../mfc/reference/casyncsocket-class.md)classe . `CSocket`utilise une version du protocole de sérialisation MFC pour transmettre des données à un objet de prise à travers un objet [MFC CArchive.](../mfc/reference/carchive-class.md) `CSocket` fournit un blocage (lors de la gestion du traitement en arrière-plan des messages Windows) et vous donne accès à `CArchive`, qui gère de nombreux aspects de la communication que vous devriez faire en utilisant l'API brute ou la classe `CAsyncSocket`.

> [!TIP]
> Vous pouvez utiliser la classe `CSocket` seule, en tant que version plus pratique de `CAsyncSocket`, mais le modèle de programmation le plus simple consiste à utiliser `CSocket` avec un objet `CArchive`.

Pour plus d’informations sur le fonctionnement de la mise en œuvre des prises avec les archives, voir [Windows Sockets: How Sockets with Archives Work](../mfc/windows-sockets-how-sockets-with-archives-work.md). Par exemple, codez [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md) and Windows [Sockets: Exemple de prises utilisant des archives](../mfc/windows-sockets-example-of-sockets-using-archives.md). Pour plus d’informations sur certaines fonctionnalités que vous pouvez gagner en dérivant vos propres classes des classes de prises, voir [Windows Sockets: Deriving from Socket Classes](../mfc/windows-sockets-deriving-from-socket-classes.md).

> [!NOTE]
> Si vous écrivez un programme client MFC pour communiquer avec des serveurs (non-MFC) établis, n'envoyez pas les objets C++ à l'archive. Sauf si le serveur est une application MFC qui comprend les types d'objets que vous souhaitez envoyer, il ne peut pas recevoir ni désérialiser vos objets. Pour les documents connexes sur le sujet de la communication avec les applications non-MFC, voir également l’article [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md).

## <a name="the-csocket-programming-model"></a><a name="_core_the_csocket_programming_model"></a>Le modèle de programmation CSocket

L'utilisation d'un objet `CSocket` implique la création et l'association de plusieurs objets de classe MFC. Dans la procédure générale ci-dessous, chaque action est effectuée par le socket de serveur et le socket client, sauf à l'étape 3, dans laquelle chaque type de socket requiert une action différente.

> [!TIP]
> Au moment de l'exécution, l'application serveur démarre généralement en premier pour être prête et "à l'écoute" lorsque l'application cliente recherche une connexion. Si le serveur n'est pas prêt lorsque le client tente de se connecter, vous aurez généralement besoin que l'application utilisateur tente de se connecter de nouveau ultérieurement.

#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>Pour installer la communication entre un socket de serveur et un socket client

1. Construire un objet [CSocket.](../mfc/reference/csocket-class.md)

1. Utilisez l’objet pour créer la poignée **SOCKET** sous-jacente.

   Pour `CSocket` un objet client, vous devez normalement utiliser les paramètres par défaut pour [créer,](../mfc/reference/casyncsocket-class.md#create)sauf si vous avez besoin d’une prise de datagram. Pour `CSocket` un objet serveur, vous devez `Create` spécifier un port dans l’appel.

    > [!NOTE]
    >  `CArchive` ne fonctionne pas avec les sockets datagramme. Si vous souhaitez utiliser `CSocket` pour un socket datagramme, vous devez utiliser la classe comme vous utiliseriez `CAsyncSocket`, c'est à dire, sans archive. Les datagrammes sont peu fiables (aucune garantie d'arrivée et peuvent être répétés, ou hors de la séquence), ils ne sont pas compatibles avec la sérialisation par le biais d'une archive. Vous vous attendez à ce qu'une opération de sérialisation se termine de manière fiable et dans l'ordre. Si vous essayez d'utiliser `CSocket` avec un objet `CArchive` pour un datagramme, une assertion MFC échoue.

1. Si la prise est un client, appelez [CAsyncSocket: :Connectez-vous](../mfc/reference/casyncsocket-class.md#connect) pour connecter l’objet de prise à une prise de serveur.

     -ou-

   Si la prise est un serveur, appelez [CAsyncSocket: :Écoutez](../mfc/reference/casyncsocket-class.md#listen) pour commencer à écouter pour les tentatives de connexion d’un client. Lors de la réception d’une demande de connexion, l’accepter en appelant [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).

    > [!NOTE]
    >  La `Accept` fonction membre fait référence à `CSocket` un nouvel objet vide comme paramètre. Vous devez construire cet `Accept`objet avant d’appeler . Si cet objet socket est hors de portée, la connexion se ferme. N’appelez `Create` pas pour ce nouvel objet de prise.

1. Créez un objet [CSocketFile,](../mfc/reference/csocketfile-class.md) en associant l’objet `CSocket` avec lui.

1. Créez un objet [CArchive](../mfc/reference/carchive-class.md) pour le chargement (recevoir) ou le stockage (d’envoi) de données. L'archive est associée à l'objet `CSocketFile`.

   N'oubliez pas que `CArchive` ne fonctionne pas avec les sockets datagramme.

1. Utilisez l'objet `CArchive` pour passer des données de test entre les sockets client et serveur.

   Gardez à l'esprit qu'un objet donné `CArchive` déplace les données dans une seule direction : pour charger (recevoir) ou enregistrer (émettre). Dans certains cas, vous utiliserez deux objets `CArchive` : un pour envoyer des données, l'autre pour recevoir les accusés de réception.

   Après avoir accepté une connexion et la configuration de l’archive, vous pouvez effectuer des tâches telles que la validation des mots de passe.

1. Détruisez archive, le fichier de sockets et les objets socket.

    > [!NOTE]
    >  La classe `CArchive` fournit la fonction membre `IsBufferEmpty` spécifiquement pour une utilisation avec la classe `CSocket`. Si la mémoire tampon contient plusieurs messages de données, par exemple, vous devez exécuter la boucle jusqu'à ce qu'ils aient tous été lus et que le tampon ait été vidé. Sinon, la notification suivante selon laquelle il y a des données à recevoir peut être retardée indéfiniment. Utilisez `IsBufferEmpty` pour vérifier que vous récupérez toutes les données.

L’article [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md) illustre les deux côtés de ce processus avec un code d’exemple.

Pour plus d'informations, consultez les pages suivantes :

- [Windows Sockets : sockets flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket::Créer](../mfc/reference/csocket-class.md#create)
