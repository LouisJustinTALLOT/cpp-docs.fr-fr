---
description: 'En savoir plus sur : Windows Sockets : sockets datagrammes'
title: 'Windows Sockets : sockets datagramme'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
ms.openlocfilehash: 8de374d6e96348504d4b1fc126c1607c029cd6c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132975"
---
# <a name="windows-sockets-datagram-sockets"></a>Windows Sockets : sockets datagramme

Cet article décrit les sockets datagrammes, l’un des deux types de sockets Windows disponibles. (L’autre type est le [Socket de flux](../mfc/windows-sockets-stream-sockets.md).)

Les sockets datagrammes prennent en charge un workflow de données bidirectionnel qui n’est pas forcément séquencé ou non dupliqué. Il n’est pas garanti que les datagrammes soient fiables ; ils peuvent échouer. Les données de datagramme peuvent arriver dans le désordre et éventuellement dupliquées, mais les limites d’enregistrement dans les données sont conservées, à condition que les enregistrements soient plus petits que la limite de taille interne du récepteur. Vous êtes responsable de la gestion du séquencement et de la fiabilité. (La fiabilité tend à être correcte sur les réseaux locaux [LAN], mais moins sur les réseaux étendus [WAN], comme Internet.)

Les datagrammes sont « sans connexion », autrement dit, aucune connexion explicite n’est établie. vous envoyez un message de datagramme à un socket spécifié et vous pouvez recevoir des messages à partir d’un socket spécifié.

Un exemple de socket de datagramme est une application qui maintient la synchronisation des horloges système sur le réseau. Cela illustre une capacité supplémentaire des sockets de datagramme dans au moins certains paramètres : diffusion de messages vers un grand nombre d’adresses réseau.

Les sockets datagrammes sont mieux que les sockets de flux pour les données orientées enregistrement. Pour plus d’informations sur les sockets de datagramme, consultez la spécification Windows Sockets, disponible dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows Sockets : Présentation](../mfc/windows-sockets-background.md)
