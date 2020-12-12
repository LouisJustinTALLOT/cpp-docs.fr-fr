---
description: 'En savoir plus sur : Windows Sockets : fonctionnement des sockets avec les Archives'
title: 'Windows Sockets : fonctionnement des sockets avec des archives'
ms.date: 11/19/2018
helpviewer_keywords:
- Windows Sockets [MFC], synchronous
- sockets [MFC], synchronous operation
- sockets [MFC], with archives
- synchronous state socket
- Windows Sockets [MFC], with archives
- two-state socket object
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
ms.openlocfilehash: 19b24a9942b7405304c9037091266b4535bffbc3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263541"
---
# <a name="windows-sockets-how-sockets-with-archives-work"></a>Windows Sockets : fonctionnement des sockets avec des archives

Cet article explique comment un objet [CSocket](../mfc/reference/csocket-class.md) , un objet [CSocketFile](../mfc/reference/csocketfile-class.md) et un objet [CArchive](../mfc/reference/carchive-class.md) sont combinés pour simplifier l’envoi et la réception de données via un socket Windows.

L’article [Windows Sockets : exemple de sockets utilisant des archives](../mfc/windows-sockets-example-of-sockets-using-archives.md) présente la `PacketSerialize` fonction. L’objet archive de l' `PacketSerialize` exemple fonctionne très bien comme un objet archive passé à une fonction [Serialize](../mfc/reference/cobject-class.md#serialize) MFC. La principale différence est que pour les sockets, l’archive est attachée à un objet [CFile](../mfc/reference/cfile-class.md) standard (généralement associé à un fichier disque), mais à un `CSocketFile` objet. Au lieu de se connecter à un fichier sur disque, l' `CSocketFile` objet se connecte à un `CSocket` objet.

Un `CArchive` objet gère une mémoire tampon. Lorsque la mémoire tampon d’une archive de stockage (envoi) est pleine, un `CFile` objet associé écrit le contenu de la mémoire tampon. Le vidage de la mémoire tampon d’une archive attachée à un socket équivaut à l’envoi d’un message. Lorsque la mémoire tampon d’une archive de chargement (réception) est pleine, l' `CFile` objet cesse de lire jusqu’à ce que la mémoire tampon soit à nouveau disponible.

`CSocketFile`La classe dérive de `CFile` , mais elle ne prend pas en charge les fonctions membres [CFile](../mfc/reference/cfile-class.md) telles que les fonctions de positionnement ( `Seek` , `GetLength` , `SetLength` , etc.), les fonctions de verrouillage ( `LockRange` , `UnlockRange` ) ou la `GetPosition` fonction. Tout l’objet [CSocketFile](../mfc/reference/csocketfile-class.md) doit effectuer des séquences d’octets en écriture ou en lecture de l' `CSocket` objet associé. Étant donné qu’un fichier n’est pas impliqué, les opérations telles que et ne sont pas `Seek` `GetPosition` pertinentes. `CSocketFile` est dérivé de `CFile` , donc il hériterait normalement de toutes ces fonctions membres. Pour éviter cela, les fonctions membres non prises en charge `CFile` sont substituées dans `CSocketFile` pour lever une [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md).

L' `CSocketFile` objet appelle des fonctions membres de son `CSocket` objet pour envoyer ou recevoir des données.

L’illustration suivante montre les relations entre ces objets des deux côtés de la communication.

![CArchive, CSocketFile et CSocket](../mfc/media/vc38ia1.gif "CArchive, CSocketFile et CSocket") <br/>
CArchive, CSocketFile et CSocket

L’objectif de cette complexité apparente est de vous protéger contre la nécessité de gérer vous-même les détails du Socket. Vous créez le socket, le fichier et l’archive, puis commencez à envoyer ou à recevoir des données en les insérant dans l’archive ou en les extrayant de l’archive. [CArchive](../mfc/reference/carchive-class.md), [CSocketFile](../mfc/reference/csocketfile-class.md)et [CSocket](../mfc/reference/csocket-class.md) gèrent les détails en arrière-plan.

Un `CSocket` objet est en fait un objet à deux États : parfois asynchrone (État habituel) et parfois synchrone. Dans son état asynchrone, un socket peut recevoir des notifications asynchrones de l’infrastructure. Toutefois, lors d’une opération telle que la réception ou l’envoi de données, le socket devient synchrone. Cela signifie que le socket ne reçoit pas de notifications asynchrones supplémentaires tant que l’opération synchrone n’est pas terminée. Comme il change de mode, vous pouvez, par exemple, effectuer une opération semblable à la suivante :

[!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/cpp/windows-sockets-how-sockets-with-archives-work_1.cpp)]

Si `CSocket` n’a pas été implémenté en tant qu’objet à deux États, il peut être possible de recevoir des notifications supplémentaires pour le même type d’événement lors du traitement d’une notification précédente. Par exemple, vous pouvez recevoir une `OnReceive` notification lors du traitement d’un `OnReceive` . Dans le fragment de code ci-dessus, l’extraction `str` de l’archive peut entraîner une récurrence. En basculant les États, `CSocket` empêche la récursivité en empêchant des notifications supplémentaires. La règle générale n’est pas une notification dans les notifications.

> [!NOTE]
> Un `CSocketFile` peut également être utilisé en tant que fichier (limité) sans `CArchive` objet. Par défaut, le `CSocketFile` paramètre *bArchiveCompatible* du constructeur a la **valeur true**. Cela spécifie que l’objet fichier est destiné à être utilisé avec une archive. Pour utiliser l’objet fichier sans Archive, transmettez **false** dans le paramètre *bArchiveCompatible* .

Dans son mode « compatible Archive », un `CSocketFile` objet offre de meilleures performances et réduit le risque d’un blocage. Un blocage se produit lorsque les sockets d’envoi et de réception sont attendus l’un l’autre, ou attendent une ressource commune. Cette situation peut se produire si l' `CArchive` objet fonctionnait de la `CSocketFile` même manière qu’avec un `CFile` objet. Avec `CFile` , l’archive peut supposer que si elle reçoit moins d’octets que le nombre demandé, la fin du fichier a été atteinte. `CSocketFile`Toutefois, avec, les données sont basées sur des messages ; la mémoire tampon peut contenir plusieurs messages. par conséquent, la réception d’un nombre inférieur au nombre d’octets demandés n’implique pas la fin du fichier. L’application ne se bloque pas dans ce cas comme avec `CFile` , et elle peut continuer à lire les messages à partir de la mémoire tampon jusqu’à ce que la mémoire tampon soit vide. Dans ce cas, la fonction [IsBufferEmpty](../mfc/reference/carchive-class.md#isbufferempty) dans `CArchive` est utile pour surveiller l’état de la mémoire tampon de l’archive.

Pour plus d’informations, consultez [Windows Sockets : utilisation de sockets avec des archives](../mfc/windows-sockets-using-sockets-with-archives.md)

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CObject :: Serialize](../mfc/reference/cobject-class.md#serialize)
