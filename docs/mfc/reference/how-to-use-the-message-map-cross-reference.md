---
description: 'En savoir plus sur : Comment : utiliser la référence croisée Message-Map'
title: 'Comment : utiliser la référence croisée de la table des messages'
ms.date: 11/04/2016
helpviewer_keywords:
- windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
ms.openlocfilehash: 4bbc140db59a7df4abd42fdcf68b47273ec3e846
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219653"
---
# <a name="how-to-use-the-message-map-cross-reference"></a>Comment : utiliser la référence croisée de la table des messages

Dans entrées nommées \<memberFxn> , écrivez votre propre fonction membre pour une classe [CWnd](../../mfc/reference/cwnd-class.md) dérivée. Donnez à votre fonction le nom de votre choix. D’autres fonctions, telles que `OnActivate` , sont des fonctions membres de classe `CWnd` . Si elles sont appelées, elles passent le message à la `DefWindowProc` fonction Windows. Pour traiter les messages de notification Windows, remplacez la `CWnd` fonction correspondante dans votre classe dérivée. Votre fonction doit appeler la fonction substituée dans votre classe de base pour permettre à la classe de base et à Windows de répondre au message.

Dans tous les cas, placez le prototype de fonction dans l' `CWnd` en-tête de classe dérivé de et codez l’entrée de la table des messages comme indiqué.

Les termes suivants sont utilisés :

|Terme|Définition|
|----------|----------------|
|id|ID d’élément de menu défini par l’utilisateur (messages WM_COMMAND) ou ID de contrôle (messages de notification de fenêtre enfant).|
|« message » et « wNotifyCode »|ID de message Windows tels qu’ils sont définis dans WINDOWS. H.|
|nMessageVariable|Nom d’une variable qui contient la valeur de retour de la `RegisterWindowMessage` fonction Windows.|

## <a name="see-also"></a>Voir aussi

[Tables des messages](../../mfc/reference/message-maps-mfc.md)
