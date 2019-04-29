---
title: Gestionnaires de messages
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
ms.openlocfilehash: 0d3ed6239b638a0e161cd7e3580f4fe6e1b4a7e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383754"
---
# <a name="message-handlers"></a>Gestionnaires de messages

Dans les MFC, un dédié *gestionnaire* fonction traite chaque message séparément. Les fonctions de gestionnaire de messages sont des fonctions de membre d’une classe. Cette documentation utilise les termes du contrat *fonction membre de gestionnaire de messages*, *fonction gestionnaire de messages*, *Gestionnaire de messages*, et *gestionnaire*indifféremment. Certains types de gestionnaires de messages sont également appelées « gestionnaires de commandes ».

Écriture de gestionnaires de messages représente une proportion importante de votre travail dans l’écriture d’une application framework. Cette série d’articles décrit comment fonctionne le mécanisme de traitement des messages.

Ce que fait le gestionnaire pour un message qu’il n’est tout ce que vous voulez faire en réponse à ce message. Vous pouvez créer les gestionnaires à l’aide de la fenêtre Propriétés de la classe et renseignez ensuite le code du gestionnaire à l’aide de l’éditeur de code source.

Vous pouvez utiliser toutes les fonctionnalités de Microsoft Visual C++ et MFC pour écrire des gestionnaires. Pour obtenir la liste de toutes les classes, consultez [vue d’ensemble de la bibliothèque de classes](../mfc/class-library-overview.md) dans le *référence MFC*.

## <a name="see-also"></a>Voir aussi

[Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)
