---
title: Dérivée des tables des messages | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handling [MFC], derived message handlers
- messages, routing
- message maps [MFC], derived
- derived message maps
ms.assetid: 21829556-6e64-40c3-8279-fed85d99de77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e780d411e62d1347d8286f86b45df864b0fcdb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342964"
---
# <a name="derived-message-maps"></a>Tables des messages dérivées
Au cours de la gestion des messages, un message de la classe de la vérification de la carte n’est pas la fin de l’article de table des messages. Que se passe-t-il si classe `CMyView` (dérivée de `CView`) ne comporte aucune entrée correspondante pour un message  
  
 N’oubliez pas que `CView`, la classe de base de `CMyView`, est dérivée à son tour de `CWnd`. Par conséquent, `CMyView` *est* un `CView` et *est* un `CWnd`. Chacune de ces classes possède sa propre table des messages. L’illustration « Hiérarchie d’une vue » ci-dessous montre la relation hiérarchique entre les classes, mais gardez à l’esprit qu’un `CMyView` objet est un objet unique qui possède les caractéristiques des trois classes.  
  
 ![Hiérarchie d’une vue](../mfc/media/vc38621.gif "vc38621")  
Hiérarchie d’une vue  
  
 Par conséquent, si un message ne peut pas être mis en correspondance dans la classe `CMyView`de table des messages, l’infrastructure recherche également la table des messages de la classe de base immédiate. Le `BEGIN_MESSAGE_MAP` macro au début de la table des messages spécifie deux noms de classe comme arguments :  
  
 [!code-cpp[NVC_MFCMessageHandling#2](../mfc/codesnippet/cpp/derived-message-maps_1.cpp)]  
  
 Le premier argument désigne la classe à laquelle appartient la table des messages. Le deuxième argument fournit une connexion avec la classe de base immédiate — `CView` ici, pour que le framework peut rechercher sa table des messages de trop.  
  
 Les gestionnaires de messages fournis dans une classe de base sont ainsi hérités par la classe dérivée. Cela est très similaire aux fonctions membres virtuelles normales sans avoir à effectuer toutes les fonctions membres de gestionnaire virtuel.  
  
 Si aucun gestionnaire n’est trouvé dans un des mappages de message de la classe de base, par défaut de traitement du message est effectuée. Si le message est une commande, le framework achemine vers la cible de la commande suivante. S’il s’agit d’un message Windows standard, le message est passé à la procédure de fenêtre par défaut appropriée.  
  
 Pour accélérer la correspondance de la table des messages, le framework met en cache les correspondances récentes sur la probabilité qu’il sera le même message à nouveau. Une conséquence de cela est que la structure traite les messages non gérés très efficace. Tables des messages sont également plus faible que les implémentations qui utilisent des fonctions virtuelles.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment le Framework effectue des recherches dans les tables des messages](../mfc/how-the-framework-searches-message-maps.md)

