---
title: 'Windows Sockets : Ordre des opérations | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], operations
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- sockets [MFC], operations
- stream sockets [MFC]
ms.assetid: 43ce76f5-aad3-4247-b8a6-16cc7d012796
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93fe2221e25951a53340d5da97f7d5c48ce477cf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385256"
---
# <a name="windows-sockets-sequence-of-operations"></a>Windows Sockets : ordre des opérations
Cet article explique côte à côte, l’ordre des opérations pour un socket serveur et un socket client. Comme les sockets utilisent `CArchive` des objets, ils sont nécessairement [sockets de flux](../mfc/windows-sockets-stream-sockets.md).  
  
## <a name="sequence-of-operations-for-a-stream-socket-communication"></a>Ordre des opérations pour une Communication par Socket flux  
 Jusqu’au moment de la construction d’un `CSocketFile` de l’objet, la séquence suivante est précise (avec quelques différences de paramètres) pour les deux `CAsyncSocket` et `CSocket`. À ce stade, la séquence est strictement pour `CSocket`. Le tableau suivant illustre la séquence d’opérations pour établir la communication entre un client et un serveur.  
  
### <a name="setting-up-communication-between-a-server-and-a-client"></a>Établissement de la Communication entre un serveur et un Client  
  
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
  
 1. Où `nPort` est un numéro de port. Consultez [Windows Sockets : Ports et adresses de Socket](../mfc/windows-sockets-ports-and-socket-addresses.md) pour plus d’informations sur les ports.  
  
 2. Le serveur doit toujours spécifier un port afin que les clients peuvent se connecter. Le **créer** appel spécifie également une adresse. Du côté client, utilisez les paramètres par défaut, qui demandent à MFC d’utiliser tout port disponible.  
  
 3. Où `nPort` est un numéro de port et *strAddr* est une adresse d’ordinateur ou une adresse IP (Internet Protocol).  
  
 4. Les adresses d’ordinateurs peuvent prendre plusieurs formes : « FTP.Microsoft.com », « microsoft.com ». Adresses IP utilisent la forme « nombre de pointillés » « 127.54.67.32 ». Le **Connect** fonction vérifie si l’adresse est un nombre en pointillé (bien qu’il ne vérifie pas le nombre est un ordinateur valide sur le réseau). Si ce n’est pas le cas, **Connect** suppose un nom d’ordinateur de l’un des autres formes.  
  
 5. Lorsque vous appelez **accepter** côté serveur, vous passez une référence à un nouvel objet socket. Vous devez créer cet objet tout d’abord, mais n’appelez pas **créer** pour celle-ci. Gardez à l’esprit que si cet objet socket est hors de portée, la connexion se ferme. MFC connecte le nouvel objet à un **SOCKET** gérer. Vous pouvez construire le socket sur la pile, comme illustré, ou sur le tas.  
  
 6. L’archive et le fichier de socket sont fermés lorsqu’ils sont hors de portée. Destructeur de l’objet socket appelle également la [fermer](../mfc/reference/casyncsocket-class.md#close) fonction membre pour l’objet socket lorsque l’objet est hors de portée ou est supprimé.  
  
## <a name="additional-notes-about-the-sequence"></a>Remarques supplémentaires sur la séquence  
 La séquence des appels indiquée dans le tableau précédent est pour un socket de flux de données. Sockets datagramme, qui sont sans connexion, ne requièrent pas la [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect), [écouter](../mfc/reference/casyncsocket-class.md#listen), et [accepter](../mfc/reference/casyncsocket-class.md#accept) appels (bien que vous pouvez éventuellement utiliser **Connecter**). Au lieu de cela, si vous utilisez la classe `CAsyncSocket`, les sockets datagramme utilisent le `CAsyncSocket::SendTo` et `ReceiveFrom` fonctions membres. (Si vous utilisez **Connect** avec un socket datagramme, vous utilisez **envoyer** et **réception**.) Étant donné que `CArchive` ne fonctionne pas avec les datagrammes, n’utilisez pas `CSocket` avec une archive si le socket est un datagramme.  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md) ne prend pas en charge toutes les `CFile`de fonctionnalités ; `CFile` membres tels que `Seek`, laquelle aucun sens pour une communication par socket, ne sont pas disponibles. Pour cette raison, certains par défaut MFC `Serialize` fonctions ne sont pas compatibles avec `CSocketFile`. Cela est particulièrement vrai pour les `CEditView` classe. Vous ne devez pas essayer de sérialiser `CEditView` données via un `CArchive` objet attaché à un `CSocketFile` à l’aide de l’objet `CEditView::SerializeRaw`; utilisez **plutôt CEditView::Serialize** à la place (non documenté). Le [fonction SerializeRaw](../mfc/reference/ceditview-class.md#serializeraw) fonction attend l’objet fichier ont des fonctions, telles que `Seek`, qui `CSocketFile` ne prend pas en charge.  
  
 Pour plus d'informations, voir :  
  
-   [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
-   [Windows Sockets : utilisation de la classe CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)  
  
-   [Windows Sockets : ports et adresses de socket](../mfc/windows-sockets-ports-and-socket-addresses.md)  
  
-   [Windows Sockets : sockets flux](../mfc/windows-sockets-stream-sockets.md)  
  
-   [Windows Sockets : sockets datagramme](../mfc/windows-sockets-datagram-sockets.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)   
 [CSocket (classe)](../mfc/reference/csocket-class.md)   
 [CAsyncSocket::Create](../mfc/reference/casyncsocket-class.md#create)   
 [CAsyncSocket::Close](../mfc/reference/casyncsocket-class.md#close)

