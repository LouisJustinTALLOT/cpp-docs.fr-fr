---
title: Mappage des Messages | Documents Microsoft
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
ms.openlocfilehash: f521145599a3d734a22dd3b2707ad4dd16df8e80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345984"
---
# <a name="mapping-messages"></a>Mappage des messages
Chaque classe de framework qui peut recevoir des messages ou des commandes possède sa propre « table des messages ». L’infrastructure utilise les tables des messages pour connecter des messages et commandes aux fonctions gestionnaires. Toute classe dérivée de la classe `CCmdTarget` peut avoir une table des messages. Autres articles expliquent les tables des messages en détail et décrivent comment les utiliser.  
  
 En dépit du nom « table des messages, » message maps gèrent deux messages et les commandes, les trois catégories de messages répertoriées dans [catégories de messages](../mfc/message-categories.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)

