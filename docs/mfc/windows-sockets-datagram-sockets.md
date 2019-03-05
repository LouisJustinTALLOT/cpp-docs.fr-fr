---
title: 'Windows Sockets : Sockets datagramme'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
ms.openlocfilehash: 14d33ece66d902b5705e573e9863ea78fff9737f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266792"
---
# <a name="windows-sockets-datagram-sockets"></a>Windows Sockets : Sockets datagramme

Cet article décrit les sockets datagramme, un des deux types de Windows Socket disponibles. (L’autre type est le [socket flux](../mfc/windows-sockets-stream-sockets.md).)

Sockets datagramme prend en charge un flux de données bidirectionnel qui n’est pas garanti pour être séquencée ni non dupliqué. Datagrammes également ne sont pas forcément fiables ; ils peuvent n’arrivent pas. Les données du datagramme peuvent arriver en désordre et éventuellement en double, mais les limites d’enregistrement dans les données sont conservées tant que les enregistrements sont plus petites que la limite de taille interne du destinataire. Vous êtes responsable de la gestion de séquencement et la fiabilité. (Fiabilité a tendance à être correctement sur les réseaux locaux [LAN] mais moins étendu etc. réseaux [WAN], tel qu’Internet).

Les datagrammes sont « sans connexion », autrement dit, aucune connexion explicite n’est établie ; vous envoyez un message de datagramme à un socket spécifié et que vous pouvez recevoir des messages à partir d’un socket spécifié.

Un exemple d’un socket datagramme est une application qui conserve les horloges système sur le réseau synchronisé. Cet exemple illustre une fonctionnalité supplémentaire de sockets datagramme au moins certains paramètres : diffuser des messages à un grand nombre d’adresses réseau.

Sockets datagramme sont plus performants que les sockets de flux de données orienté par enregistrement. Pour plus d’informations sur les sockets datagramme, consultez la spécification Windows Sockets, disponible dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows Sockets : En arrière-plan](../mfc/windows-sockets-background.md)
