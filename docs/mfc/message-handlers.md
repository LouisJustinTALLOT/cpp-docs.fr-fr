---
title: Gestionnaires de messages | Microsoft Docs
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
ms.openlocfilehash: 22dde243bb6d8e8a283e670804d4b8b6cad9082c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46406748"
---
# <a name="message-handlers"></a>Gestionnaires de messages

Dans les MFC, un dédié *gestionnaire* fonction traite chaque message séparément. Les fonctions de gestionnaire de messages sont des fonctions de membre d’une classe. Cette documentation utilise les termes du contrat *fonction membre de gestionnaire de messages*, *fonction gestionnaire de messages*, *Gestionnaire de messages*, et *gestionnaire*indifféremment. Certains types de gestionnaires de messages sont également appelées « gestionnaires de commandes ».

Écriture de gestionnaires de messages représente une proportion importante de votre travail dans l’écriture d’une application framework. Cette série d’articles décrit comment fonctionne le mécanisme de traitement des messages.

Ce que fait le gestionnaire pour un message qu’il n’est tout ce que vous voulez faire en réponse à ce message. Vous pouvez créer les gestionnaires à l’aide de la fenêtre Propriétés de la classe et renseignez ensuite le code du gestionnaire à l’aide de l’éditeur de code source.

Vous pouvez utiliser toutes les fonctionnalités de Microsoft Visual C++ et MFC pour écrire des gestionnaires. Pour obtenir la liste de toutes les classes, consultez [vue d’ensemble de la bibliothèque de classes](../mfc/class-library-overview.md) dans le *référence MFC*.

## <a name="see-also"></a>Voir aussi

[Messages et commandes dans le Framework](../mfc/messages-and-commands-in-the-framework.md)

