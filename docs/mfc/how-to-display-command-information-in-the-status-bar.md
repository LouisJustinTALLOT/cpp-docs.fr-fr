---
title: "Comment : afficher les informations sur les commandes dans la barre d'état"
ms.date: 11/04/2016
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
ms.openlocfilehash: 6da45edf611d70920340d8f9a9c2fd8de5cc0307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654101"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>Comment : afficher les informations sur les commandes dans la barre d'état

Lorsque vous exécutez l’Assistant Application pour créer le squelette de votre application, vous pouvez prendre en charge une barre d’outils et une barre d’état. Qu’une seule option dans l’Assistant Application prend en charge les deux. Quand une barre d’état est présente, l’application fournit automatiquement des commentaires utiles lorsque l’utilisateur positionne le pointeur sur les éléments dans les menus. L’application affiche automatiquement une chaîne d’invite dans la barre d’état lorsque l’élément de menu est mis en surbrillance. Par exemple, lorsque l’utilisateur déplace le pointeur sur le **couper** commande sur le **modifier** menu, la barre d’état peut afficher « Coupe la sélection et le place dans le Presse-papiers » dans la zone de message de la barre d’état. L’invite aide l’utilisateur à comprendre l’objectif de l’élément de menu. Cela fonctionne également lorsque l’utilisateur clique sur un bouton de barre d’outils.

Vous pouvez ajouter à l’aide de cette barre d’état en définissant des chaînes d’invite pour les éléments de menu que vous ajoutez au programme. Pour ce faire, fournissez les chaînes d’invite lorsque vous modifiez les propriétés de l’élément de menu dans l’éditeur de menus. Les chaînes que vous définissez sont stockés dans le fichier de ressources d’application ; ils ont les mêmes ID que les commandes qu’elles expliquent.

Par défaut, l’Assistant Application ajoute **AFX_IDS_IDLEMESSAGE**, l’ID d’un message « Prêt » standard, qui s’affiche lorsque le programme est en attente pour les nouveaux messages. Si vous spécifiez l’option aide contextuelle dans l’Assistant Application, le message est modifié à « De l’aide, appuyez sur F1. »

## <a name="see-also"></a>Voir aussi

[Gestion et mappage des messages](../mfc/message-handling-and-mapping.md)

