---
title: Gestionnaires de messages | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be4ccf9ec33e5ddf497193c1942e9f300f8cae57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347628"
---
# <a name="message-handlers"></a>Gestionnaires de messages
Dans les MFC, dédiée *gestionnaire* fonction traite chaque message séparément. Les fonctions de gestionnaire de messages sont des fonctions de membre d’une classe. Cette documentation utilise les termes du contrat *fonction membre de gestionnaire de messages*, *fonction gestionnaire de messages*, *le Gestionnaire de messages*, et *gestionnaire*indifféremment. Certains types de gestionnaires de messages sont également appelés « gestionnaires de commandes ».  
  
 L’écriture de gestionnaires de messages représente une grande partie de votre travail de l’écriture d’une application framework. Cette série d’articles explique comment fonctionne le mécanisme de traitement des messages.  
  
 Ce que fait le gestionnaire pour un message qu’il ne fait tout ce que vous souhaitez faire en réponse à ce message. Vous pouvez créer des gestionnaires à l’aide de la fenêtre Propriétés de la classe et puis entrez le code du gestionnaire à l’aide de l’éditeur de code source.  
  
 Vous pouvez utiliser toutes les fonctionnalités de Microsoft Visual C++ et MFC pour écrire des gestionnaires. Pour obtenir la liste de toutes les classes, consultez [vue d’ensemble de la bibliothèque de classes](../mfc/class-library-overview.md) dans les *référence MFC*.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)

