---
title: 'Windows Sockets : Fonctionnement des Sockets avec des Archives | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Sockets [MFC], synchronous
- sockets [MFC], synchronous operation
- sockets [MFC], with archives
- synchronous state socket
- Windows Sockets [MFC], with archives
- two-state socket object
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c4f581acb0af27f44c88d59597e52b057991ee4
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954277"
---
# <a name="windows-sockets-how-sockets-with-archives-work"></a>Windows Sockets : fonctionnement des sockets avec des archives
Cet article explique comment un [CSocket](../mfc/reference/csocket-class.md) objet, un [CSocketFile](../mfc/reference/csocketfile-class.md) objet et un [CArchive](../mfc/reference/carchive-class.md) objet sont combinées afin de simplifier l’envoi et de recevoir des données via un Windows Socket.  
  
 L’article [Windows Sockets : exemple de Sockets utilisant des Archives](../mfc/windows-sockets-example-of-sockets-using-archives.md) présente la `PacketSerialize` (fonction). L’objet de l’archive dans le `PacketSerialize` exemple fonctionne comme un objet archive transmis à une MFC [Serialize](../mfc/reference/cobject-class.md#serialize) (fonction). La principale différence est que pour les sockets, l’archive n'est pas attachée à une norme [CFile](../mfc/reference/cfile-class.md) objet (en général associé à un fichier de disque), mais un `CSocketFile` objet. Au lieu de se connecter à un fichier de disque, le `CSocketFile` objet se connecte à un `CSocket` objet.  
  
 A `CArchive` objet gère une mémoire tampon. Lorsque la mémoire tampon d’une archive (envoi) de stockage est plein, associé à un `CFile` contenu du tampon d’objet écrit. Le vidage de la mémoire tampon d’une archive attachée à un socket est équivalent à l’envoi d’un message. Lorsque la mémoire tampon d’une archive de chargement (réception) est plein, le `CFile` objet s’arrête de lire jusqu'à ce que la mémoire tampon est à nouveau disponible.  
  
 Classe `CSocketFile` dérive `CFile`, mais il ne prend pas en charge [CFile](../mfc/reference/cfile-class.md) fonctions membres telles que les fonctions de positionnement (`Seek`, `GetLength`, `SetLength`, et ainsi de suite), le verrouillage de fonctions () `LockRange`, `UnlockRange`), ou le `GetPosition` (fonction). Tous les le [CSocketFile](../mfc/reference/csocketfile-class.md) objet doit faire est d’écrire ou lire des séquences d’octets à partir d’associé ou `CSocket` objet. Car un fichier n’est pas impliqué, opérations telles que `Seek` et `GetPosition` aucun sens. `CSocketFile` est dérivé de `CFile`, de sorte qu’il serait normalement héritent toutes ces fonctions membres. Pour éviter cela, la non prise en charge `CFile` fonctions membres sont remplacées dans `CSocketFile` pour lever une [exception CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md).  
  
 Le `CSocketFile` objet appelle les fonctions de membres son `CSocket` objet pour envoyer ou recevoir des données.  
  
 L’illustration suivante montre les relations entre les objets des deux côtés de la communication.  
  
 ![CArchive, CSocketFile et CSocket](../mfc/media/vc38ia1.gif "vc38ia1")  
CArchive, CSocketFile et CSocket  
  
 L’objectif de cette complexité apparente est de vous protéger de la nécessité de gérer les détails du socket vous-même. Vous créez le socket, le fichier et l’archive et ensuite commencez à envoyer ou recevoir des données en les insérant dans l’archive ou en l’extrayant à partir de l’archive. [CArchive](../mfc/reference/carchive-class.md), [CSocketFile](../mfc/reference/csocketfile-class.md), et [CSocket](../mfc/reference/csocket-class.md) gérer les détails en arrière-plan.  
  
 A `CSocket` objet est en fait un objet de deux états : parfois asynchrone (état habituel), tantôt synchrone. Dans son état asynchrone, un socket peut recevoir des notifications asynchrones de l’infrastructure. Toutefois, pendant une opération de réception ou envoi de données, le socket devient synchrone. Cela signifie que le socket reçoit des notifications asynchrones plues aucune jusqu'à ce que l’opération synchrone. Car il remet les modes, vous, par exemple, faire quelque chose comme suit :  
  
 [!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/cpp/windows-sockets-how-sockets-with-archives-work_1.cpp)]  
  
 Si `CSocket` n’étaient pas implémentées en tant qu’objet deux États, il est possible de recevoir des notifications supplémentaires pour le même type d’événement pendant que vous ont été traite une notification précédente. Par exemple, vous pouvez obtenir un `OnReceive` notification lors du traitement un `OnReceive`. Dans le fragment de code ci-dessus, extraction `str` à partir de l’archive peut entraîner une récurrence. En changeant d’état, `CSocket` empêche la récurrence tout en empêchant les notifications supplémentaires. La règle générale n’est aucune notification dans les notifications.  
  
> [!NOTE]
>  A `CSocketFile` peut également être utilisé comme un fichier (limité) sans un `CArchive` objet. Par défaut, le `CSocketFile` du constructeur *bArchiveCompatible* paramètre est **TRUE**. Spécifie que l’objet de fichier doit être utilisé avec une archive. Pour utiliser l’objet fichier sans archive, passez **FALSE** dans les *bArchiveCompatible* paramètre.  
  
 En mode « compatible archive », un `CSocketFile` objet offre de meilleures performances et réduit le risque de « blocage ». Un blocage se produit lorsque les sockets de transmission et de réception sont en attente sur l’autre, ou en attente d’une ressource commune. Cette situation peut se produire si le `CArchive` objet travaillé avec la `CSocketFile` comme il le fait avec un `CFile` objet. Avec `CFile`, l’archive peut supposer que s’il reçoit le nombre d’octets qu’il a demandée, la fin du fichier a été atteinte. Avec `CSocketFile`, toutefois, données message en fonction ; la mémoire tampon peut contenir plusieurs messages, donc recevoir moins que le nombre d’octets demandés n’implique pas la fin du fichier. L’application ne bloque pas, dans ce cas, ce qui est possible avec `CFile`, et poursuivre la lecture de messages à partir de la mémoire tampon jusqu'à ce que la mémoire tampon est vide. Le [IsBufferEmpty](../mfc/reference/carchive-class.md#isbufferempty) fonctionner dans `CArchive` est utile pour surveiller l’état du tampon de l’archive dans ce cas.  
  
 Pour plus d’informations, consultez [Windows Sockets : utilisation de Sockets avec des Archives](../mfc/windows-sockets-using-sockets-with-archives.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)   
 [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)

