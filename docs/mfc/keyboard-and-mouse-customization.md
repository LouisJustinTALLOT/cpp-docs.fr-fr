---
title: Personnalisation du clavier et souris | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- customizations [MFC], keyboard and mouse (MFC Extensions)
- keyboard and mouse customizations (MFC Extensions)
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45b073ff2a9565c9106111299ba5b1b9d5a47351
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351661"
---
# <a name="keyboard-and-mouse-customization"></a>Personnalisation du clavier et de la souris
MFC permet à l'utilisateur de l'application de personnaliser la façon dont il gère le clavier et l'entrée de la souris. L'utilisateur peut personnaliser l'entrée clavier en attribuant des raccourcis clavier aux commandes. L'utilisateur peut également personnaliser l'entrée de la souris en sélectionnant la commande qui doit être exécutée lorsque l'utilisateur double-clique dans des fenêtres spécifiques de l'application. Cette rubrique explique comment personnaliser les entrées pour votre application.  
  
 Dans le **personnalisation** boîte de dialogue, l’utilisateur peut modifier les contrôles personnalisés pour la souris et du clavier. Pour afficher cette boîte de dialogue, l’utilisateur pointe vers **personnaliser** sur la **vue** menu, puis clique sur **barres d’outils et fenêtres d’ancrage**. Dans la boîte de dialogue, l’utilisateur peut cliquer sur le **clavier** onglet ou la **souris** onglet.  
  
## <a name="keyboard-customization"></a>Personnalisation du clavier  
 L’illustration suivante montre le **clavier** onglet de la **personnalisation** boîte de dialogue.  
  
 ![Onglet clavier de la boîte de dialogue Personnaliser](../mfc/media/mfcnextkeyboardtab.png "mfcnextkeyboardtab")  
Onglet Personnalisation du clavier  
  
 L'utilisateur interagit avec l'onglet Clavier pour affecter un ou plusieurs raccourcis clavier à une commande. Les commandes disponibles sont répertoriées sur le côté gauche de l'onglet. L'utilisateur peut choisir n'importe quelle commande disponible dans le menu. Seules les commandes de menu peuvent être associées à un raccourci clavier. Une fois que l’utilisateur entre un nouveau raccourci, le **affecter** bouton est activé. Lorsque l'utilisateur clique sur ce bouton, l'application associe la commande sélectionnée à ce raccourci.  
  
 Tous les raccourcis clavier actuellement assignés sont répertoriés dans la zone de liste de la colonne de droite. L'utilisateur peut également sélectionner des raccourcis et les supprimer, ou réinitialiser tous les mappages de l'application.  
  
 Si vous souhaitez prendre en charge cette personnalisation dans votre application, vous devez créer un [CKeyboardManager](../mfc/reference/ckeyboardmanager-class.md) objet. Pour créer un `CKeyboardManager` d’objet, appelez la fonction [CWinAppEx::InitKeyboardManager](../mfc/reference/cwinappex-class.md#initkeyboardmanager). Cette méthode crée et initialise un gestionnaire de clavier. Si vous créez un gestionnaire de clavier manuellement, vous devez toujours appeler `CWinAppEx::InitKeyboardManager` pour l'initialisation.  
  
 Si vous utilisez l'Assistant pour créer votre application, il initialisera le gestionnaire de clavier. Une fois que votre application initialise le Gestionnaire de clavier, le framework ajoute un **clavier** TAB pour accéder à la **personnalisation** boîte de dialogue.  
  
## <a name="mouse-customization"></a>Personnalisation de la souris  
 L’illustration suivante montre le **souris** onglet de la **personnalisation** boîte de dialogue.  
  
 ![Onglet de la souris dans la boîte de dialogue Personnaliser](../mfc/media/mfcnextmousetab.png "mfcnextmousetab")  
Onglet de personnalisation de la souris  
  
 L'utilisateur interagit avec cet onglet pour assigner une commande de menu à l'action de double-clic de la souris. L'utilisateur sélectionne une vue sur le côté gauche de la fenêtre, puis utilise les contrôles à droite pour associer une commande à l'action de double-clic. Une fois que l’utilisateur clique sur **fermer**, l’application exécute la commande associée à chaque fois que l’utilisateur double-clique sur n’importe où dans la vue.  
  
 Par défaut, la personnalisation de la souris n'est pas activée lorsque vous créez une application à l'aide de l'Assistant.  
  
#### <a name="to-enable-mouse-customization"></a>Pour activer la personnalisation de la souris  
  
1.  Initialiser un [CMouseManager](../mfc/reference/cmousemanager-class.md) objet en appelant [CWinAppEx::InitMouseManager](../mfc/reference/cwinappex-class.md#initmousemanager).  
  
2.  Obtenir un pointeur vers le Gestionnaire de la souris à l’aide de [CWinAppEx::GetMouseManager](../mfc/reference/cwinappex-class.md#getmousemanager).  
  
3.  Ajouter des vues dans le Gestionnaire de la souris à l’aide de la [CMouseManager::AddView](../mfc/reference/cmousemanager-class.md#addview) (méthode). Effectuez cette opération pour chaque vue que vous souhaitez ajouter au gestionnaire de souris.  
  
 Une fois que votre application initialise le Gestionnaire de la souris, le framework ajoute la **souris** TAB pour accéder à la **personnaliser** boîte de dialogue. Si vous n'ajoutez pas de vue, l'accès à l'onglet génère une exception non gérée. Après avoir créé une liste de vues, les **souris** onglet est disponible à l’utilisateur.  
  
 Lorsque vous ajoutez une nouvelle vue au gestionnaire de souris, vous lui attribuez un ID unique Si vous souhaitez prendre en charge la personnalisation de la souris pour une fenêtre, vous devez traiter le `WM_LBUTTONDBLCLICK` message et appeler le [CWinAppEx::OnViewDoubleClick](../mfc/reference/cwinappex-class.md#onviewdoubleclick) (fonction). Lorsque vous appelez cette fonction, l'un des paramètres est l'ID de cette fenêtre. Il est de la responsabilité des programmeurs de conserver les numéros d'identification et les objets associés.  
  
## <a name="security-concerns"></a>Problèmes de sécurité  
 Comme décrit dans [outils définis par l’utilisateur](../mfc/user-defined-tools.md), l’utilisateur peut associer un ID de l’outil défini par l’utilisateur à l’événement de double-clic. Lorsque l'utilisateur double-clique sur une vue, l'application recherche un outil utilisateur qui correspond à l'ID associé. Si l'application trouve un outil correspondant, il exécute l'outil. Si l'application ne trouve pas d'outil correspondant, il envoie un message WM_COMMAND avec l'ID de la vue sur laquelle a eu lieu le double-clic.  
  
 Les paramètres personnalisés sont stockés dans le Registre. En modifiant le Registre, un pirate peut remplacer un ID de l'outil utilisateur valide au moyen d'une commande aléatoire. Lorsque l'utilisateur double-clique sur une vue, la vue traite la commande que la personne malveillante a attaquée. Cela peut entraîner un comportement inattendu et potentiellement dangereux.  
  
 En outre, ce type d'attaque peut contourner les mesures de protection de l'interface utilisateur. Par exemple, supposons que la fonction d'impression d'une application est désactivée. Autrement dit, dans son interface utilisateur, le **impression** menus et des boutons ne sont pas disponibles. Normalement, l'application ne permet pas d'imprimer des documents. Mais si un intrus a modifié le Registre, un utilisateur peut alors envoyer la commande d'impression simplement en double-cliquant sur la vue, en ignorant les éléments de l'interface utilisateur qui ne sont pas disponibles.  
  
 Pour vous protéger contre ce type d'attaque, ajoutez du code à votre gestionnaire de commandes d'application pour vérifier qu'une commande est valide avant son exécution. Pour éviter qu'une commande soit envoyée à l'application, ne dépendez pas de l'interface utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation pour MFC](../mfc/customization-for-mfc.md)   
 [Classe de CKeyboardManager](../mfc/reference/ckeyboardmanager-class.md)   
 [Classe de CMouseManager](../mfc/reference/cmousemanager-class.md)   
 [Implications en matière de sécurité de la personnalisation](../mfc/security-implications-of-customization.md)

