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
ms.openlocfilehash: 25805187f88c5423ea41cd7cbe346e44e7d7d36a
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907463"
---
# <a name="message-handlers"></a>Gestionnaires de messages

Dans MFC, une fonction de *Gestionnaire* dédiée traite chaque message distinct. Les fonctions de gestionnaire de messages sont des fonctions membres d’une classe. Cette documentation utilise les termes *fonction membre du gestionnaire*de messages, *fonction du gestionnaire de*messages, *Gestionnaire de messages*et *Gestionnaire* de manière interchangeable. Certains types de gestionnaires de messages sont également appelés « gestionnaires de commandes ».

L’écriture de gestionnaires de messages tient compte d’une grande partie de votre travail lors de l’écriture d’une application de Framework. Cette famille d’articles décrit le fonctionnement du mécanisme de traitement des messages.

Ce que fait le gestionnaire d’un message, c’est ce que vous souhaitez faire en réponse à ce message. Vous pouvez créer les gestionnaires à l’aide de l' [Assistant classe](reference/mfc-class-wizard.md) de la classe, puis remplir le code du gestionnaire à l’aide de l’éditeur de code source.

Vous pouvez utiliser toutes les fonctionnalités de Microsoft Visual C++ et MFC pour écrire vos gestionnaires. Pour obtenir la liste de toutes les classes, consultez [vue d’ensemble](../mfc/class-library-overview.md) de la bibliothèque de classes dans la *référence MFC*.

## <a name="see-also"></a>Voir aussi

[Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)
