---
description: 'En savoir plus sur : Windows Sockets : séquence d’opérations'
title: 'Windows Sockets : ordre des opérations'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], operations
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- sockets [MFC], operations
- stream sockets [MFC]
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
ms.openlocfilehash: 89870de642abcc8e0584c2c5dc93860eda9785e8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263372"
---
# <a name="windows-sockets-sequence-of-operations"></a>Windows Sockets : ordre des opérations

Cet article illustre, côte à côte, la séquence d’opérations d’un socket de serveur et d’un socket client. Étant donné que les sockets utilisent des `CArchive` objets, ils sont nécessairement des [sockets de flux](../mfc/windows-sockets-stream-sockets.md).

## <a name="sequence-of-operations-for-a-stream-socket-communication"></a>Séquence d’opérations pour une communication de socket de flux

Jusqu’au moment de la construction d’un `CSocketFile` objet, la séquence suivante est exacte (avec quelques différences de paramètres) pour `CAsyncSocket` et `CSocket` . À partir de ce point, la séquence est strictement réservée à `CSocket` . Le tableau suivant illustre la séquence des opérations de configuration de la communication entre un client et un serveur.

### <a name="setting-up-communication-between-a-server-and-a-client"></a>Configuration de la communication entre un serveur et un client

|Serveur|Client|
|------------|------------|
|`// construct a socket`<br /><br /> `CSocket sockSrvr;`|`// construct a socket`<br /><br /> `CSocket sockClient;`|
|`// create the SOCKET`<br /><br /> `sockSrvr.Create(nPort);`1,2|`// create the SOCKET`<br /><br /> `sockClient.Create( );`2|
|`// start listening`<br /><br /> `sockSrvr.Listen( );`||
||`// seek a connection`<br /><br /> `sockClient.Connect(strAddr, nPort);`3,4|
|`// construct a new, empty socket`<br /><br /> `CSocket sockRecv;`<br /><br /> `// accept connection`<br /><br /> `sockSrvr.Accept( sockRecv );` 5,5||
|`// construct file object`<br /><br /> `CSocketFile file(&sockRecv);`|`// construct file object`<br /><br /> `CSocketFile file(&sockClient);`|
|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> -ou-<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> -ou-les deux-|`// construct an archive`<br /><br /> `CArchive arIn(&file, CArchive::load);`<br /><br /> -ou-<br /><br /> `CArchive arOut(&file, CArchive::store);`<br /><br /> -ou-les deux-|
|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> -ou-<br /><br /> `arOut << dwValue;`6|`// use the archive to pass data:`<br /><br /> `arIn >> dwValue;`<br /><br /> -ou-<br /><br /> `arOut << dwValue;`6|

1. Où *NPort* est un numéro de port. Pour plus d’informations sur les ports [, consultez Windows Sockets : ports et adresses de socket](../mfc/windows-sockets-ports-and-socket-addresses.md) .

2. Le serveur doit toujours spécifier un port afin que les clients puissent se connecter. L' `Create` appel spécifie parfois une adresse. Côté client, utilisez les paramètres par défaut, qui demandent à MFC d’utiliser n’importe quel port disponible.

3. Où *NPort* est un numéro de port et *strAddr* est une adresse d’ordinateur ou une adresse IP (Internet Protocol).

4. Les adresses d’ordinateur peuvent prendre plusieurs formes : « ftp.microsoft.com », « microsoft.com ». Les adresses IP utilisent la forme « 127.54.67.32 ». La `Connect` fonction vérifie si l’adresse est un nombre en pointillés (bien qu’elle ne vérifie pas que le nombre est un ordinateur valide sur le réseau). Si ce n’est pas le cas, `Connect` suppose un nom d’ordinateur de l’un des autres formulaires.

5. Lorsque vous appelez `Accept` côté serveur, vous transmettez une référence à un nouvel objet Socket. Vous devez d’abord construire cet objet, mais ne l’appelez pas `Create` . Gardez à l’esprit que si cet objet Socket est hors de portée, la connexion se ferme. MFC connecte le nouvel objet à un handle de **Socket** . Vous pouvez construire le socket sur la pile, comme indiqué, ou sur le tas.

6. L’archive et le fichier de socket sont fermés lorsqu’ils sont hors de portée. Le destructeur de l’objet Socket appelle également la fonction membre [Close](../mfc/reference/casyncsocket-class.md#close) pour l’objet Socket lorsque l’objet est hors de portée ou est supprimé.

## <a name="additional-notes-about-the-sequence"></a>Remarques supplémentaires sur la séquence

La séquence d’appels indiquée dans le tableau précédent concerne un socket de flux. Les sockets de datagrammes, qui sont sans connexion, ne nécessitent pas les appels [CAsyncSocket :: Connect](../mfc/reference/casyncsocket-class.md#connect), [Listen](../mfc/reference/casyncsocket-class.md#listen)et [Accept](../mfc/reference/casyncsocket-class.md#accept) (même si vous pouvez éventuellement utiliser `Connect` ). Au lieu de cela, si vous utilisez `CAsyncSocket` la classe, les sockets datagrammes utilisent les `CAsyncSocket::SendTo` `ReceiveFrom` fonctions membres et. (Si vous utilisez `Connect` avec un socket datagramme, vous utilisez `Send` et `Receive` .) Étant donné que `CArchive` ne fonctionne pas avec les datagrammes, n’utilisez pas `CSocket` avec une archive si le socket est un datagramme.

[CSocketFile](../mfc/reference/csocketfile-class.md) ne prend pas en charge toutes les fonctionnalités de. les `CFile` `CFile` membres tels que `Seek` , qui n’ont aucun sens pour la communication entre les sockets, ne sont pas disponibles. Pour cette raison, certaines fonctions MFC par défaut ne `Serialize` sont pas compatibles avec `CSocketFile` . C’est particulièrement vrai pour la `CEditView` classe. Vous ne devez pas essayer de sérialiser des `CEditView` données via un `CArchive` objet attaché à un `CSocketFile` objet à l’aide de `CEditView::SerializeRaw` ; Utilisez à la `CEditView::Serialize` place (non documenté). La fonction [SerializeRaw](../mfc/reference/ceditview-class.md#serializeraw) s’attend à ce que l’objet fichier ait des fonctions, telles que `Seek` , qui `CSocketFile` ne prend pas en charge.

Pour plus d'informations, consultez les pages suivantes :

- [Windows Sockets : utilisation de sockets avec des Archives](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets : ports et adresses de socket](../mfc/windows-sockets-ports-and-socket-addresses.md)

- [Windows Sockets : Sockets de flux](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets : sockets datagrammes](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket (classe)](../mfc/reference/csocket-class.md)<br/>
[CAsyncSocket::Create](../mfc/reference/casyncsocket-class.md#create)<br/>
[CAsyncSocket :: Close](../mfc/reference/casyncsocket-class.md#close)
