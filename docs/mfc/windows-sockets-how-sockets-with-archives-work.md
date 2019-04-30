---
title: 'Windows Sockets : Fonctionnement des Sockets avec des Archives'
ms.date: 11/19/2018
helpviewer_keywords:
- Windows Sockets [MFC], synchronous
- sockets [MFC], synchronous operation
- sockets [MFC], with archives
- synchronous state socket
- Windows Sockets [MFC], with archives
- two-state socket object
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
ms.openlocfilehash: 3af94bc881276238f1a8d2dbeeee4dca1f173a4b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389443"
---
# <a name="windows-sockets-how-sockets-with-archives-work"></a>Windows Sockets : Fonctionnement des Sockets avec des Archives

Cet article explique comment un [CSocket](../mfc/reference/csocket-class.md) objet, un [CSocketFile](../mfc/reference/csocketfile-class.md) objet et un [CArchive](../mfc/reference/carchive-class.md) objet sont combinées afin de simplifier l’envoi et réception de données via un Windows Socket.

L’article [Windows Sockets : Exemple de Sockets utilisant des Archives](../mfc/windows-sockets-example-of-sockets-using-archives.md) présente le `PacketSerialize` (fonction). L’objet de l’archive dans le `PacketSerialize` exemple fonctionne comme un objet archive transmis à une MFC [Serialize](../mfc/reference/cobject-class.md#serialize) (fonction). La principale différence est que pour les sockets, l’archive n'est pas attachée à une norme [CFile](../mfc/reference/cfile-class.md) objet (généralement associé à un fichier de disque), mais un `CSocketFile` objet. Au lieu de la connexion à un fichier de disque, le `CSocketFile` objet se connecte à un `CSocket` objet.

Un `CArchive` objet gère une mémoire tampon. Lorsque la mémoire tampon d’une archive (envoi) de stockage est plein, associé à un `CFile` contenu du tampon d’objet écrit. Le vidage de la mémoire tampon d’une archive attachée à un socket est équivalent à l’envoi d’un message. Lorsque la mémoire tampon d’une archive de chargement (réception) est plein, le `CFile` objet arrête la lecture jusqu'à ce que la mémoire tampon est à nouveau disponible.

Classe `CSocketFile` dérive `CFile`, mais il ne prend pas en charge [CFile](../mfc/reference/cfile-class.md) des fonctions de membre, telles que les fonctions de positionnement (`Seek`, `GetLength`, `SetLength`, et ainsi de suite), le verrouillage de fonctions () `LockRange`, `UnlockRange`), ou le `GetPosition` (fonction). Tous les le [CSocketFile](../mfc/reference/csocketfile-class.md) objet doit faire est d’écrire ou lire des séquences d’octets vers ou depuis associé `CSocket` objet. Car un fichier n’est pas impliqué, opérations telles que `Seek` et `GetPosition` n’ont aucun sens. `CSocketFile` est dérivé de `CFile`, donc elle hériterait normalement toutes ces fonctions de membre. Pour éviter cela, la non prise en charge `CFile` fonctions membres sont remplacées dans `CSocketFile` pour lever une [exception CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md).

Le `CSocketFile` objet appelle les fonctions de membres son `CSocket` objet pour envoyer ou recevoir des données.

La figure suivante montre les relations entre ces objets des deux côtés de la communication.

![CArchive, CSocketFile et CSocket](../mfc/media/vc38ia1.gif "CArchive, CSocketFile et CSocket") <br/>
CArchive, CSocketFile et CSocket

L’objectif de cette complexité apparente consiste à vous protègent contre la nécessité de gérer les détails du socket vous-même. Vous créez le socket, le fichier et l’archive et ensuite commencez à envoyer ou recevoir des données en les insérant dans l’archive ou en l’extrayant à partir de l’archive. [CArchive](../mfc/reference/carchive-class.md), [CSocketFile](../mfc/reference/csocketfile-class.md), et [CSocket](../mfc/reference/csocket-class.md) gérer les détails en arrière-plan.

Un `CSocket` objet est en fait un objet de deux états : parfois asynchrone (état habituel), tantôt synchrone. Dans son état asynchrone, un socket peut recevoir des notifications asynchrones à partir de l’infrastructure. Toutefois, pendant une opération de réception ou envoi de données, le socket devient synchrone. Cela signifie que le socket reçoit pas aller au-delà des notifications asynchrones jusqu'à ce que l’opération synchrone est terminée. Car il remet les modes, par exemple, faire quelque chose comme ce qui suit :

[!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/cpp/windows-sockets-how-sockets-with-archives-work_1.cpp)]

Si `CSocket` n’étaient pas implémentées en tant qu’objet deux États, il est parfois possible de recevoir des notifications supplémentaires pour le même type d’événement pendant que vous ont été traite une notification précédente. Par exemple, vous pouvez obtenir un `OnReceive` notification lors du traitement un `OnReceive`. Dans le fragment de code ci-dessus, extraction `str` à partir de l’archive peut entraîner la récursivité. En basculant les États, `CSocket` empêche la récurrence tout en empêchant des notifications supplémentaires. La règle générale n’est aucune notification au sein de notifications.

> [!NOTE]
> Un `CSocketFile` peut également être utilisé comme un fichier (limité) sans un `CArchive` objet. Par défaut, le `CSocketFile` du constructeur *bArchiveCompatible* paramètre est **TRUE**. Spécifie que l’objet de fichier doit être utilisé avec une archive. Pour utiliser l’objet fichier sans archive, passez **FALSE** dans le *bArchiveCompatible* paramètre.

En mode « compatible archive », un `CSocketFile` objet offre de meilleures performances et réduit le risque d’un « blocage ». Un blocage se produit lorsque les sockets émettrices et réceptrices sont en attente sur eux ou en attente pour une ressource commune. Cette situation peut se produire si le `CArchive` objet travaillé avec le `CSocketFile` comme il le fait avec un `CFile` objet. Avec `CFile`, l’archive peut supposer que s’il reçoit le moins d’octets qu’il est demandé, la fin du fichier a été atteinte. Avec `CSocketFile`, toutefois, données en fonction de message ; la mémoire tampon peut contenir plusieurs messages, jusqu'à réception de moins que le nombre d’octets demandés n’implique pas la fin du fichier. L’application ne bloque pas, dans ce cas, comme cela pourrait être avec `CFile`, et il peut continuer à lire des messages à partir de la mémoire tampon jusqu'à ce que la mémoire tampon est vide. Le [IsBufferEmpty](../mfc/reference/carchive-class.md#isbufferempty) fonctionner dans `CArchive` est utile pour surveiller l’état de la mémoire tampon de l’archive dans ce cas.

Pour plus d’informations, consultez [Windows Sockets : Utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CObject::Serialize](../mfc/reference/cobject-class.md#serialize)
