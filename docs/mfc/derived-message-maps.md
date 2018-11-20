---
title: Tables des messages dérivées
ms.date: 11/19/2018
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
ms.openlocfilehash: 2ae536a53a43472a4fb81d30e685fbc3faaa603f
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175599"
---
# <a name="derived-message-maps"></a>Tables des messages dérivées

Au cours de la gestion des messages, la vérification d’un message de la classe map n’est pas la fin de l’histoire de la table des messages. Que se passe-t-il si classe `CMyView` (dérivée de `CView`) ne comporte aucune entrée correspondante pour un message

N’oubliez pas que `CView`, la classe de base de `CMyView`, est dérivé à son tour `CWnd`. Par conséquent `CMyView` *est* un `CView` et *est* un `CWnd`. Chacune de ces classes a sa propre table des messages. La figure « Hiérarchie d’une vue » ci-dessous montre la relation hiérarchique entre les classes, mais gardez à l’esprit qu’un `CMyView` objet est un objet unique qui présente les caractéristiques des trois classes.

![Hiérarchie d’une vue](../mfc/media/vc38621.gif "hiérarchie d’une vue") <br/>
Une hiérarchie d’affichage

Par conséquent, si un message ne peut pas être mis en correspondance dans la classe `CMyView`de table des messages, l’infrastructure recherche également dans la table des messages de sa classe de base immédiate. Le `BEGIN_MESSAGE_MAP` macro au début de la table des messages spécifie deux noms de classe comme arguments :

[!code-cpp[NVC_MFCMessageHandling#2](../mfc/codesnippet/cpp/derived-message-maps_1.cpp)]

Le premier argument nomme la classe à laquelle appartient la table des messages. Le deuxième argument fournit une connexion avec la classe de base immédiate — `CView` ici, pour que l’infrastructure peut rechercher sa table des messages trop.

Les gestionnaires de messages fournis dans une classe de base sont ainsi hérités par la classe dérivée. Cela est très similaire aux fonctions membres virtuelles normales sans avoir à effectuer toutes les fonctions membres de gestionnaire virtuel.

Si aucun gestionnaire n’est trouvé dans un des mappages de message de la classe de base, par défaut de traitement du message est effectuée. Si le message est une commande, le framework achemine vers la cible de commande suivante. Dans le cas d’un message Windows standard, le message est passé à la procédure de fenêtre par défaut approprié.

Pour accélérer la correspondance de la table des messages, le framework met en cache les correspondances récentes sur la probabilité qu’il reçoit à nouveau le même message. Une conséquence de cela est que la structure traite les messages non gérés très efficacement. Tables des messages sont également plus compact que les implémentations qui utilisent des fonctions virtuelles.

## <a name="see-also"></a>Voir aussi

[Comment le Framework effectue des recherches dans les tables des messages](../mfc/how-the-framework-searches-message-maps.md)

