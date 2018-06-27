---
title: 'Windows Sockets : Utilisation de la classe CAsyncSocket | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CAsyncSocket
dev_langs:
- C++
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc461a0a2325f768711f6d7529949ee24a1b4a25
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954882"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets : utilisation de la classe CAsyncSocket
Cet article explique comment utiliser la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md). N’oubliez pas que cette classe encapsule l’API Windows Sockets à un niveau très bas. `CAsyncSocket` est utilisé par les programmeurs qui connaissez approfondie des communications réseau mais que vous souhaitez bénéficier des rappels de notification des événements réseau. Selon cette hypothèse, cet article fournit uniquement les instructions de base. Vous devez probablement envisager d’utiliser `CAsyncSocket` si vous souhaitez simplifier la gérer plusieurs protocoles réseau dans une application MFC Windows Sockets, mais ne souhaitez pas sacrifier la souplesse. Vous pouvez également penser que vous pouvez obtenir une meilleure efficacité par programmation les communications plus directement vous-même qu’Impossible à l’aide de l’autre modèle plus général de la classe `CSocket`.  
  
 `CAsyncSocket` est documenté dans le *référence MFC*. Visual C++ fournit également la spécification Windows Sockets située dans le Kit de développement logiciel Windows. Les détails sont laissées à vous. Visual C++ ne fournit pas d’un exemple d’application pour `CAsyncSocket`.  
  
 Si vous ne sont pas très bien informé sur les communications réseau et que vous souhaitez une solution simple, utilisez la classe [CSocket](../mfc/reference/csocket-class.md) avec un `CArchive` objet. Consultez [Windows Sockets : utilisation de Sockets avec des Archives](../mfc/windows-sockets-using-sockets-with-archives.md) pour plus d’informations.  
  
 Cet article couvre les sujets suivants :  
  
-   Création et utilisation d’un `CAsyncSocket` objet.  
  
-   [Vos responsabilités avec CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).  
  
##  <a name="_core_creating_and_using_a_casyncsocket_object"></a> Création et utilisation d’un objet CAsyncSocket  
  
#### <a name="to-use-casyncsocket"></a>Pour utiliser CAsyncSocket  
  
1.  Construire un [CAsyncSocket](../mfc/reference/casyncsocket-class.md) de l’objet et utiliser l’objet pour créer sous-jacent **SOCKET** gérer.  
  
     La création d’un socket suit le modèle MFC de construction en deux étapes.  
  
     Exemple :  
  
     [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]  
  
     - ou -  
  
     [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]  
  
     Le premier constructeur ci-dessus crée un `CAsyncSocket` objet sur la pile. Le deuxième constructeur crée un `CAsyncSocket` sur le tas. La première [créer](../mfc/reference/casyncsocket-class.md#create) appel ci-dessus utilise les paramètres par défaut pour créer un socket de flux de données. La seconde `Create` appel crée un socket datagramme avec un port spécifié et une adresse. (Vous pouvez utiliser `Create` version ou l’autre méthode de construction.)  
  
     Les paramètres `Create` sont :  
  
    -   Un « port » : un entier court.  
  
         Pour un socket de serveur, vous devez spécifier un port. Pour un socket client, vous acceptez généralement la valeur par défaut pour ce paramètre, ce qui permet de sélectionner un port de Windows Sockets.  
  
    -   Type de socket : **SOCK_STREAM** (la valeur par défaut) ou **SOCK_DGRAM**.  
  
    -   Un socket « address », tel que « FTP.Microsoft.com » ou « 128.56.22.8 ».  
  
         Il s’agit de votre adresse IP (Internet Protocol) sur le réseau. Vous serez probablement toujours reposent sur la valeur par défaut pour ce paramètre.  
  
     Les termes « port » et « adresse de socket » est expliqué dans [Windows Sockets : Ports et adresses de Socket](../mfc/windows-sockets-ports-and-socket-addresses.md).  
  
2.  Si le socket est un client, connecter l’objet socket à un serveur socket, à l’aide de [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect).  
  
     - ou -  
  
     Si le socket est un serveur, définissez le socket de commencer à écouter (avec [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen)) pour les tentatives de connexion à partir d’un client. Lorsqu’il reçoit une demande de connexion, acceptez-la avec [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).  
  
     Après avoir accepté une connexion, vous pouvez effectuer des tâches telles que la validation des mots de passe.  
  
    > [!NOTE]
    >  Le `Accept` fonction membre prend une référence à un vide `CSocket` objet comme paramètre. Vous devez créer cet objet avant d’appeler `Accept`. Si cet objet socket est hors de portée, la connexion se ferme. N’appelez pas `Create` pour ce nouvel objet socket. Pour obtenir un exemple, consultez l’article [Windows Sockets : séquence des opérations](../mfc/windows-sockets-sequence-of-operations.md).  
  
3.  Mener à bien les communications avec d’autres sockets en appelant le `CAsyncSocket` fonctions membres de l’objet qui encapsulent les fonctions API Windows Sockets.  
  
     Consultez la spécification Windows Sockets et la classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md) dans les *référence MFC*.  
  
4.  Détruire le `CAsyncSocket` objet.  
  
     Si vous avez créé l’objet socket sur la pile, son destructeur est appelé lorsque la fonction contenante est hors de portée. Si vous avez créé l’objet socket sur le tas, à l’aide la **nouveau** (opérateur), vous êtes responsable de l’utilisation du **supprimer** opérateur pour détruire l’objet.  
  
     Le destructeur appelle l’objet [fermer](../mfc/reference/casyncsocket-class.md#close) fonction membre avant de détruire l’objet.  
  
 Pour obtenir un exemple de cette séquence dans le code (en fait, pour un `CSocket` objet), consultez [Windows Sockets : séquence des opérations](../mfc/windows-sockets-sequence-of-operations.md).  
  
##  <a name="_core_your_responsibilities_with_casyncsocket"></a> Vos responsabilités avec CAsyncSocket  
 Lorsque vous créez un objet de classe [CAsyncSocket](../mfc/reference/casyncsocket-class.md), l’objet encapsule un Windows **SOCKET** gérer et fournit des opérations sur ce descripteur. Lorsque vous utilisez `CAsyncSocket`, vous devez résoudre tous les problèmes que vous pouvez rencontrer en utilisant directement l’API. Exemple :  
  
-   Scénarios de « Blocage ».  
  
-   Différences de classement d’octets entre l’envoi et la réception des ordinateurs.  
  
-   Conversion de caractères Unicode et définie des chaînes (MBCS).  
  
 Pour les définitions de ces termes et les informations supplémentaires, consultez [Windows Sockets : blocage](../mfc/windows-sockets-blocking.md), [Windows Sockets : classement des octets](../mfc/windows-sockets-byte-ordering.md), [Windows Sockets : conversion de chaînes](../mfc/windows-sockets-converting-strings.md) .  
  
 Malgré ces problèmes, classe `CAsycnSocket` peut-être le bon choix pour vous si votre application nécessite la souplesse et le contrôle. Si non, vous pouvez utiliser la classe `CSocket` à la place. `CSocket` masque de nombreux détails : informatique pompes de messages pendant les appels de blocage de Windows et vous donne accès à `CArchive`, qui gère les différences de classement d’octets et les conversions de chaînes.  
  
 Pour plus d'informations, voir :  
  
-   [Windows Sockets : arrière-plan](../mfc/windows-sockets-background.md)  
  
-   [Windows Sockets : sockets flux](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets : sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)

