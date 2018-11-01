---
title: 'Comment : utiliser la référence croisée de la table des messages'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.messages
helpviewer_keywords:
- windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
ms.openlocfilehash: 71c46e7c30eab414534012c2fe314999568d2bd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457796"
---
# <a name="how-to-use-the-message-map-cross-reference"></a>Comment : utiliser la référence croisée de la table des messages

Dans les entrées étiquetées \<memberFxn >, écrire votre propre fonction membre pour une dérivée [CWnd](../../mfc/reference/cwnd-class.md) classe. Donnez à votre fonction de n’importe quel nom de que votre choix. Autres fonctions, telles que `OnActivate`, sont des fonctions membres de classe `CWnd`. Si elle est appelée, elles passent le message à la `DefWindowProc` (fonction) Windows. Pour traiter les messages de notification de Windows, remplacer le correspondantes `CWnd` fonction dans votre classe dérivée. Votre fonction doit appeler la fonction substituée dans votre classe de base pour permettre à la classe de base et Windows répondent au message.

Dans tous les cas, placez le prototype de fonction le `CWnd`-en-tête de la classe dérivée et le code de l’entrée de mappage de message comme indiqué.

Les termes suivants sont utilisés :

|Terme|Définition|
|----------|----------------|
|ID|Tout ID d’élément de menu défini par l’utilisateur (messages WM_COMMAND) ou l’ID de contrôle (messages de notification de fenêtre enfant).|
|« message » et « wNotifyCode »|ID de message Windows tel que défini dans WINDOWS. H.|
|nMessageVariable|Nom d’une variable qui contient la valeur de retour à partir de la `RegisterWindowMessage` (fonction) Windows.|

## <a name="see-also"></a>Voir aussi

[Tables des messages](../../mfc/reference/message-maps-mfc.md)

