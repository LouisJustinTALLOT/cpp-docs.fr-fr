---
description: 'En savoir plus sur : routage des commandes'
title: routage des commandes
ms.date: 09/06/2019
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- handlers [MFC]
- handlers, command [MFC]
- command routing
ms.assetid: 9393a956-bdd4-47c5-9013-dbd680433f93
ms.openlocfilehash: 4004f74413f236599c5cdd14f6593bc5d2bd26b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283444"
---
# <a name="command-routing"></a>routage des commandes

La responsabilité de l’utilisation des commandes se limite à l’établissement de connexions de table des messages entre les commandes et leurs fonctions gestionnaires, une tâche pour laquelle vous utilisez l' [Assistant classe MFC](reference/mfc-class-wizard.md). Vous devez également écrire le code pour les gestionnaires de commandes.

Les messages de fenêtres sont généralement envoyés dans la fenêtre frame principale, mais les messages de commande sont ensuite routés vers d’autres objets. L’infrastructure achemine les commandes par le biais d’une séquence standard d’objets cibles de commande, dont l’un est censé avoir un responsable pour la commande. Chaque objet cible de commande consulte sa table des messages pour voir si elle peut traiter le message entrant.

Différentes classes de cibles de commande vérifient leurs propres tables des messages à différents moments. En règle générale, une classe achemine la commande vers certains autres objets pour leur donner la première occasion de la commande. Si aucun de ces objets ne gère la commande, la classe d’origine vérifie sa propre tables des messages. Ensuite, si elle ne peut pas fournir de gestionnaire elle-même, elle peut acheminer la commande vers d’autres cibles de commande. Le tableau [Itinéraire de commande standard](#_core_standard_command_route) ci-dessous montre comment chacune des classes structure cette séquence. L’ordre général dans lequel une cible de commande achemine une commande est le suivant :

1. Vers son objet cible de commande enfant actuellement actif.

1. Vers elle-même.

1. Vers d’autres cibles de commande.

Quel est le coût de ce mécanisme de routage par rapport à ce que fait votre gestionnaire en réponse à une commande, le coût du routage est faible. N’oubliez pas que l’infrastructure génère des commandes uniquement quand l’utilisateur interagit avec un objet d’interface utilisateur.

### <a name="standard-command-route"></a><a name="_core_standard_command_route"></a> Itinéraire de commande standard

|Quand un objet de ce type reçoit une commande. . .|Il se donne à lui-même et à d’autres objets cibles de commande une occasion de gérer la commande dans cet ordre :|
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
|Fenêtre frame MDI  (`CMDIFrameWnd`)|1. actif `CMDIChildWnd`<br />2. cette fenêtre frame<br />3. application ( `CWinApp` objet)|
|Fenêtre frame de document  (`CFrameWnd`, `CMDIChildWnd`)|1. affichage actif<br />2. cette fenêtre frame<br />3. application ( `CWinApp` objet)|
|Affichage|1. cette vue<br />2. document attaché à la vue|
|Document|1. ce document<br />2. modèle de document attaché au document|
|Boîte de dialogue|1. cette boîte de dialogue<br />2. fenêtre propriétaire de la boîte de dialogue<br />3. application ( `CWinApp` objet)|

Quand les entrées numérotées dans la deuxième colonne du tableau précédent indiquent d’autres objets, tel qu’un document, consultez l’article correspondant dans la première colonne. Par exemple, quand vous lisez dans la deuxième colonne que la vue transfère une commande à son document, consultez l’entrée « Document » dans la première colonne pour suivre le routage.

## <a name="see-also"></a>Voir aussi

[Comment le Framework appelle un gestionnaire](how-the-framework-calls-a-handler.md)
