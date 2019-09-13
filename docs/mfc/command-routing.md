---
title: routage des commandes
ms.date: 09/06/2019
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- handlers [MFC]
- handlers, command [MFC]
- command routing
ms.assetid: 9393a956-bdd4-47c5-9013-dbd680433f93
ms.openlocfilehash: 8d1e1e59c56439c01655a1416df645ccc6922411
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907623"
---
# <a name="command-routing"></a>routage des commandes

La responsabilité de l’utilisation des commandes se limite à l’établissement de connexions de table des messages entre les commandes et leurs fonctions gestionnaires, une tâche pour laquelle vous utilisez l' [Assistant classe MFC](reference/mfc-class-wizard.md). Vous devez également écrire le code pour les gestionnaires de commandes.

Les messages de fenêtres sont généralement envoyés dans la fenêtre frame principale, mais les messages de commande sont ensuite routés vers d’autres objets. L’infrastructure achemine les commandes par le biais d’une séquence standard d’objets cibles de commande, dont l’un est censé avoir un responsable pour la commande. Chaque objet cible de commande consulte sa table des messages pour voir si elle peut traiter le message entrant.

Différentes classes de cibles de commande vérifient leurs propres tables des messages à différents moments. En règle générale, une classe achemine la commande vers certains autres objets pour leur donner la première occasion de la commande. Si aucun de ces objets ne gère la commande, la classe d’origine vérifie sa propre tables des messages. Ensuite, si elle ne peut pas fournir de gestionnaire elle-même, elle peut acheminer la commande vers d’autres cibles de commande. Le tableau [Itinéraire de commande standard](#_core_standard_command_route) ci-dessous montre comment chacune des classes structure cette séquence. L’ordre général dans lequel une cible de commande achemine une commande est le suivant :

1. Vers son objet cible de commande enfant actuellement actif.

1. Vers elle-même.

1. Vers d’autres cibles de commande.

Quel est le coût de ce mécanisme de routage par rapport à ce que fait votre gestionnaire en réponse à une commande, le coût du routage est faible. N’oubliez pas que l’infrastructure génère des commandes uniquement quand l’utilisateur interagit avec un objet d’interface utilisateur.

### <a name="_core_standard_command_route"></a> Itinéraire de commande standard

|Quand un objet de ce type reçoit une commande. . .|Il se donne à lui-même et à d’autres objets cibles de commande une occasion de gérer la commande dans cet ordre :|
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
|Fenêtre frame MDI  (`CMDIFrameWnd`)|1.  `CMDIChildWnd` actif<br />2.  Cette fenêtre frame<br />3.  Application (objet `CWinApp`)|
|Fenêtre frame de document  (`CFrameWnd`, `CMDIChildWnd`)|1.  Vue active<br />2.  Cette fenêtre frame<br />3.  Application (objet `CWinApp`)|
|Vue|1.  Cette vue<br />2.  Document associé à la vue|
|Document|1.  Ce document<br />2.  Modèle de document associé au document|
|Boîte de dialogue|1.  Cette boîte de dialogue<br />2.  Fenêtre propriétaire de la boîte de dialogue<br />3.  Application (objet `CWinApp`)|

Quand les entrées numérotées dans la deuxième colonne du tableau précédent indiquent d’autres objets, tel qu’un document, consultez l’article correspondant dans la première colonne. Par exemple, quand vous lisez dans la deuxième colonne que la vue transfère une commande à son document, consultez l’entrée « Document » dans la première colonne pour suivre le routage.

## <a name="see-also"></a>Voir aussi

[Méthode d’appel d’un gestionnaire par le Framework](../mfc/how-the-framework-calls-a-handler.md)
