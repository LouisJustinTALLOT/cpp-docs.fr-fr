---
title: 'Windows Sockets : Sockets datagramme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sockets [MFC], datagram
- Windows Sockets [MFC], bi-directional data flow
- datagram sockets [MFC]
- Windows Sockets [MFC], datagram
- sockets [MFC], bi-directional data flow
ms.assetid: bec16a1c-74c0-4ff9-8c18-c2d87897d264
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a63caa786ce5198fb902b8d48101507fb2b4113
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444214"
---
# <a name="windows-sockets-datagram-sockets"></a>Windows Sockets : sockets datagramme

Cet article décrit les sockets datagramme, un des deux types de Windows Socket disponibles. (L’autre type est le [socket flux](../mfc/windows-sockets-stream-sockets.md).)

Sockets datagramme prend en charge un flux de données bidirectionnel qui n’est pas garanti pour être séquencée ni non dupliqué. Datagrammes également ne sont pas forcément fiables ; ils peuvent n’arrivent pas. Les données du datagramme peuvent arriver en désordre et éventuellement en double, mais les limites d’enregistrement dans les données sont conservées tant que les enregistrements sont plus petites que la limite de taille interne du destinataire. Vous êtes responsable de la gestion de séquencement et la fiabilité. (Fiabilité a tendance à être correctement sur les réseaux locaux [LAN] mais moins étendu etc. réseaux [WAN], tel qu’Internet).

Les datagrammes sont « sans connexion », autrement dit, aucune connexion explicite n’est établie ; vous envoyez un message de datagramme à un socket spécifié et que vous pouvez recevoir des messages à partir d’un socket spécifié.

Un exemple d’un socket datagramme est une application qui conserve les horloges système sur le réseau synchronisé. Cet exemple illustre une fonctionnalité supplémentaire de sockets datagramme au moins certains paramètres : diffuser des messages à un grand nombre d’adresses réseau.

Sockets datagramme sont plus performants que les sockets de flux de données orienté par enregistrement. Pour plus d’informations sur les sockets datagramme, consultez la spécification Windows Sockets, disponible dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Windows Sockets dans MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[Windows Sockets : arrière-plan](../mfc/windows-sockets-background.md)

