---
title: Mappage des messages
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], about message maps
- mappings [MFC], commands
- commands [MFC], mapping
- command mapping [MFC]
- message handling [MFC], connecting to handler functions
- commands [MFC], connecting to handler functions
- mappings [MFC], messages
- messages [MFC], mapping
ms.assetid: 996f0652-0698-4b8c-b893-cdaa836d9d0f
ms.openlocfilehash: 16d6d7725d82bed6c9bfc02e408b68dcf7ffe5e4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625493"
---
# <a name="mapping-messages"></a>Mappage des messages

Chaque classe d’infrastructure qui peut recevoir des messages ou des commandes a sa propre « table des messages ». L’infrastructure utilise des tables de messages pour connecter des messages et des commandes à leurs fonctions gestionnaires. Toute classe dérivée de `CCmdTarget` la classe peut avoir une table des messages. D’autres articles décrivent en détail les tables des messages et expliquent comment les utiliser.

Malgré le nom « table des messages », les tables des messages gèrent les messages et les commandes, les trois catégories de messages figurant dans les [catégories de message](message-categories.md).

## <a name="see-also"></a>Voir aussi

[Messages et commandes dans le Framework](messages-and-commands-in-the-framework.md)
