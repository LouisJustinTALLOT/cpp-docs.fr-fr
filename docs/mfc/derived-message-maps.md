---
title: Tables des messages dérivées
ms.date: 11/19/2018
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
ms.openlocfilehash: 0868b12720cfa338ab7275a358e065506adc11d1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615916"
---
# <a name="derived-message-maps"></a>Tables des messages dérivées

Pendant la gestion des messages, la vérification de la propre table des messages d’une classe n’est pas la fin de l’histoire de la table des messages. Que se passe-t-il si `CMyView` la classe (dérivée de `CView` ) n’a pas d’entrée correspondante pour un message

Gardez à l’esprit que `CView` , la classe de base de `CMyView` , est dérivée à son tour de `CWnd` . C' `CMyView` *est* donc un `CView` et *est* un `CWnd` . Chacune de ces classes possède sa propre table des messages. La figure « une hiérarchie d’affichage » ci-dessous montre la relation hiérarchique des classes, mais gardez à l’esprit qu’un `CMyView` objet est un objet unique qui a les caractéristiques des trois classes.

![Hiérarchie d'un affichage](../mfc/media/vc38621.gif "Hiérarchie d'un affichage") <br/>
Une hiérarchie d’affichage

Par conséquent, si un message ne peut pas être mis en correspondance dans `CMyView` la table des messages de la classe, le Framework recherche également la table des messages de sa classe de base immédiate. La `BEGIN_MESSAGE_MAP` macro au début de la table des messages spécifie deux noms de classe comme arguments :

[!code-cpp[NVC_MFCMessageHandling#2](codesnippet/cpp/derived-message-maps_1.cpp)]

Le premier argument nomme la classe à laquelle appartient la table des messages. Le deuxième argument fournit une connexion avec la classe de base immédiate, ici, de `CView` sorte que l’infrastructure peut également rechercher dans sa table des messages.

Les gestionnaires de messages fournis dans une classe de base sont donc hérités par la classe dérivée. Cela est très similaire aux fonctions membres virtuelles normales, sans qu’il soit nécessaire de faire en sorte que toutes les fonctions membres du gestionnaire soient virtuelles.

Si aucun gestionnaire n’est trouvé dans l’une des tables de messages de la classe de base, le traitement par défaut du message est effectué. Si le message est une commande, le Framework l’achemine vers la cible de la commande suivante. S’il s’agit d’un message Windows standard, le message est transmis à la procédure de fenêtre par défaut appropriée.

Pour accélérer la mise en correspondance de la table des messages, le Framework met en cache les correspondances récentes sur la probabilité qu’il reçoive le même message. L’une des conséquences est que l’infrastructure traite les messages non gérés de manière très efficace. Les tables des messages sont également plus efficaces que les implémentations qui utilisent des fonctions virtuelles.

## <a name="see-also"></a>Voir aussi

[Comment le Framework effectue des recherches dans les tables des messages](how-the-framework-searches-message-maps.md)
