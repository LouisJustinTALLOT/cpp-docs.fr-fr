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
ms.openlocfilehash: 1f31bc2e3c6af9c4b899167ba99c152a231a929d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665840"
---
# <a name="mapping-messages"></a>Mappage des messages

Chaque classe framework peut recevoir des messages ou des commandes possède sa propre « mappage de message ». L’infrastructure utilise les tables des messages pour connecter des messages et des commandes à leurs fonctions gestionnaires. Toute classe dérivée de la classe `CCmdTarget` peut avoir une table des messages. Autres articles expliquent les tables des messages en détail et décrivent comment les utiliser.

Malgré la nom « table des messages, » message maps gèrent les messages et les commandes, tous les trois catégories de messages figurant dans [catégories de messages](../mfc/message-categories.md).

## <a name="see-also"></a>Voir aussi

[Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)

