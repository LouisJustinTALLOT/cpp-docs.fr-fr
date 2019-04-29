---
title: 'Windows Sockets : Ordre des opérations'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], operations
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- sockets [MFC], operations
- stream sockets [MFC]
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
ms.openlocfilehash: 0f9fd339fdbdfee9381ea693568f40473c2397e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296512"
---
# <a name="windows-sockets-sequence-of-operations"></a>Windows Sockets : Ordre des opérations

Cet article illustre côte à côte, la séquence des opérations pour un socket de serveur et un socket client. Étant donné que les sockets utilisent `CArchive` objets, elles sont nécessairement [sockets de flux](../mfc/windows-sockets-stream-sockets.md).

## <a name="sequence-of-operations-for-a-stream-socket-communication"></a>Ordre des opérations pour une Communication par Socket Stream

Jusqu’au moment de la construction d’un `CSocketFile` de l’objet, la séquence suivante est précise (avec quelques différences de paramètres) pour les deux `CAsyncSocket` et `CSocket`. À ce stade, la séquence est strictement pour `CSocket`. Le tableau suivant illustre la séquence des opérations pour établir la communication entre un client et un serveur.

### <a name="setting-up-communication-between-a-server-and-a-client"></a>Configuration de la Communication entre un serveur et un Client

|Serveur|Client|
|------------|------------|
|`// construct a socket`<br /><br /> `CSocket sockSrvr;`|`// construct a socket`<br /><br /> `CSocket sockClient;`|
|`// create the SOCKET`<br /><br /> `sockSrvr.Create(nPort);`1,2|`// create the SOCKET`<br /><br /> `sockClient.Create( );`2|
|`// start listening`<br /><br /> `sockSrvr.Listen( );`||
||`// seek a connection`<br /><br /> `sockClient.Connect(strAddr, nPort);`3,4|
|`// construct a new, empty socket`<br /><br /> `CSocket sockRecv;`<br /><br /> `// accept connection`<br /><br /> `sockSrvr.Accept( sockRecv );` 5||
|`// construct file object`<br /><br /> `CSocketFile file(&sockRecv);`|`// construct file object`<br /><br /> `CSocketFile file(&sockClient);`|
|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> - ou -<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> - ou les deux :|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> - ou -<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> - ou les deux :|
|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> - ou -<br /><br /> `arOut << dwValue;`6|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> - ou -<br /><br /> `arOut << dwValue;`6|

1. Où *%nPort* est un numéro de port. Consultez [Windows Sockets : Ports et adresses de Socket](../mfc/windows-sockets-ports-and-socket-addresses.md) pour plus d’informations sur les ports.

2. Le serveur doit toujours spécifier un port afin que les clients peuvent se connecter. Le `Create` appel spécifie également une adresse. Du côté client, utilisez les paramètres par défaut, qui demandent à MFC d’utiliser n’importe quel port disponible.

3. Où *%nPort* est un numéro de port et *strAddr* est une adresse d’ordinateur ou une adresse IP (Internet Protocol).

4. Adresses de la machine peuvent prendre plusieurs formes : « FTP.Microsoft.com », « microsoft.com ». Adresses IP utilisent le formulaire « nombre de pointillés » « 127.54.67.32 ». Le `Connect` fonction vérifie si l’adresse est un nombre en pointillés (bien qu’il ne vérifie pas que le nombre est un ordinateur valide sur le réseau). Si ce n’est pas le cas, `Connect` suppose un nom de l’ordinateur d’un des autres formes.

5. Lorsque vous appelez `Accept` côté serveur, vous passez une référence à un nouvel objet socket. Vous devez créer cet objet tout d’abord, mais que vous n’appelez pas `Create` pour celui-ci. N’oubliez pas que si cet objet socket est hors de portée, la connexion se ferme. MFC connecte le nouvel objet à un **SOCKET** gérer. Vous pouvez construire le socket sur la pile, comme illustré, ou sur le tas.

6. L’archive et le fichier de socket sont fermés lorsqu’ils sont hors de portée. Destructeur de l’objet socket appelle également la [fermer](../mfc/reference/casyncsocket-class.md#close) fonction membre pour l’objet socket lorsque l’objet est hors de portée ou est supprimé.

## <a name="additional-notes-about-the-sequence"></a>Remarques supplémentaires sur la séquence

La séquence d’appels indiqués dans le tableau précédent concerne un socket de flux de données. Les sockets datagramme, qui sont sans connexion, ne nécessitent pas la [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect), [écouter](../mfc/reference/casyncsocket-class.md#listen), et [Accept](../mfc/reference/casyncsocket-class.md#accept) appels (bien que vous pouvez éventuellement utiliser `Connect`). Au lieu de cela, si vous utilisez la classe `CAsyncSocket`, utilisez des sockets datagramme le `CAsyncSocket::SendTo` et `ReceiveFrom` fonctions membres. (Si vous utilisez `Connect` avec un socket datagramme, vous utilisez `Send` et `Receive`.) Étant donné que `CArchive` ne fonctionne pas avec des datagrammes, n’utilisez pas `CSocket` avec une archive si le socket est un datagramme.

[CSocketFile](../mfc/reference/csocketfile-class.md) ne prend pas en charge toutes les `CFile`de fonctionnalités ; `CFile` membres comme `Seek`, laquelle aucun sens pour une communication par socket, ne sont pas disponibles. Pour cette raison, certains par défaut MFC `Serialize` fonctions ne sont pas compatibles avec `CSocketFile`. Cela est particulièrement vrai pour le `CEditView` classe. Vous ne devez pas essayer de sérialiser `CEditView` données via un `CArchive` objet attaché à un `CSocketFile` à l’aide de l’objet `CEditView::SerializeRaw`; utilisez `CEditView::Serialize` à la place (non documentée). Le [fonction SerializeRaw](../mfc/reference/ceditview-class.md#serializeraw) fonction attend l’objet de fichier d’avoir des fonctions, telle que `Seek`, qui `CSocketFile` ne prend pas en charge.

Pour plus d'informations, voir :

- [Windows Sockets : Utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : Utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : Ports et adresses de socket](../mfc/windows-sockets-ports-and-socket-addresses.md)

- [Windows Sockets : Sockets flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : Sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket, classe](../mfc/reference/csocket-class.md)<br/>
[CAsyncSocket::Create](../mfc/reference/casyncsocket-class.md#create)<br/>
[CAsyncSocket::Close](../mfc/reference/casyncsocket-class.md#close)
