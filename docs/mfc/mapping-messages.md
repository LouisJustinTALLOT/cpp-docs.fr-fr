---
title: Mappage des Messages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7324da5eaff15d240cabbaede2c2982021361257
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410976"
---
# <a name="mapping-messages"></a>Mappage des messages

Chaque classe framework peut recevoir des messages ou des commandes possède sa propre « mappage de message ». L’infrastructure utilise les tables des messages pour connecter des messages et des commandes à leurs fonctions gestionnaires. Toute classe dérivée de la classe `CCmdTarget` peut avoir une table des messages. Autres articles expliquent les tables des messages en détail et décrivent comment les utiliser.

Malgré la nom « table des messages, » message maps gèrent les messages et les commandes, tous les trois catégories de messages figurant dans [catégories de messages](../mfc/message-categories.md).

## <a name="see-also"></a>Voir aussi

[Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)

