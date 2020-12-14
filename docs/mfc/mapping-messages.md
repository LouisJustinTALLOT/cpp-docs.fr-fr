---
description: 'En savoir plus sur : mappage des messages'
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
ms.openlocfilehash: 34d100a7ae527acc9f5520474e75b486b2f6276c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280792"
---
# <a name="mapping-messages"></a>Mappage des messages

Chaque classe d’infrastructure qui peut recevoir des messages ou des commandes a sa propre « table des messages ». L’infrastructure utilise des tables de messages pour connecter des messages et des commandes à leurs fonctions gestionnaires. Toute classe dérivée de `CCmdTarget` la classe peut avoir une table des messages. D’autres articles décrivent en détail les tables des messages et expliquent comment les utiliser.

Malgré le nom « table des messages », les tables des messages gèrent les messages et les commandes, les trois catégories de messages figurant dans les [catégories de message](message-categories.md).

## <a name="see-also"></a>Voir aussi

[Messages et commandes dans le Framework](messages-and-commands-in-the-framework.md)
