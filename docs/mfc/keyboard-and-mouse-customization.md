---
title: Personnalisation du clavier et de la souris
ms.date: 11/19/2018
helpviewer_keywords:
- customizations [MFC], keyboard and mouse (MFC Extensions)
- keyboard and mouse customizations (MFC Extensions)
ms.assetid: 1f789f1b-5f2e-4b11-b974-e3e2a2e49d82
ms.openlocfilehash: 262555b060f226a86438a2189eda44d83c55d5a2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621498"
---
# <a name="keyboard-and-mouse-customization"></a>Personnalisation du clavier et de la souris

MFC permet à l'utilisateur de l'application de personnaliser la façon dont il gère le clavier et l'entrée de la souris. L'utilisateur peut personnaliser l'entrée clavier en attribuant des raccourcis clavier aux commandes. L'utilisateur peut également personnaliser l'entrée de la souris en sélectionnant la commande qui doit être exécutée lorsque l'utilisateur double-clique dans des fenêtres spécifiques de l'application. Cette rubrique explique comment personnaliser les entrées pour votre application.

Dans la boîte de dialogue **personnalisation** , l’utilisateur peut modifier les contrôles personnalisés de la souris et du clavier. Pour afficher cette boîte de dialogue, l’utilisateur pointe sur **personnaliser** dans le menu **affichage** , puis il clique sur **barres d’outils et ancrage**. Dans la boîte de dialogue, l’utilisateur clique sur l’onglet **clavier** ou la **souris** .

## <a name="keyboard-customization"></a>Personnalisation du clavier

L’illustration suivante montre l’onglet **clavier** de la boîte de dialogue **personnalisation** .

![Onglet Clavier de la boîte de dialogue Personnalisation](../mfc/media/mfcnextkeyboardtab.png "Onglet Clavier de la boîte de dialogue Personnalisation") <br/>
Onglet Personnalisation du clavier

L'utilisateur interagit avec l'onglet Clavier pour affecter un ou plusieurs raccourcis clavier à une commande. Les commandes disponibles sont répertoriées sur le côté gauche de l’onglet. L’utilisateur peut sélectionner n’importe quelle commande disponible dans le menu. Seules les commandes de menu peuvent être associées à un raccourci clavier. Une fois que l’utilisateur a entré un nouveau raccourci, le bouton **affecter** devient activé. Lorsque l'utilisateur clique sur ce bouton, l'application associe la commande sélectionnée à ce raccourci.

Tous les raccourcis clavier actuellement assignés sont répertoriés dans la zone de liste de la colonne de droite. L'utilisateur peut également sélectionner des raccourcis et les supprimer, ou réinitialiser tous les mappages de l'application.

Si vous souhaitez prendre en charge cette personnalisation dans votre application, vous devez créer un objet [CKeyboardManager](reference/ckeyboardmanager-class.md) . Pour créer un `CKeyboardManager` objet, appelez la fonction [CWinAppEx :: InitKeyboardManager](reference/cwinappex-class.md#initkeyboardmanager). Cette méthode crée et initialise un gestionnaire de clavier. Si vous créez un gestionnaire de clavier manuellement, vous devez toujours appeler `CWinAppEx::InitKeyboardManager` pour l'initialisation.

Si vous utilisez l'Assistant pour créer votre application, il initialisera le gestionnaire de clavier. Une fois que votre application a initialisé le gestionnaire de clavier, l’infrastructure ajoute un onglet **clavier** à la boîte de dialogue **personnalisation** .

## <a name="mouse-customization"></a>Personnalisation de la souris

L’illustration suivante montre l’onglet **souris** de la boîte de dialogue **personnalisation** .

![Onglet Souris de la boîte de dialogue Personnalisation](../mfc/media/mfcnextmousetab.png "Onglet Souris de la boîte de dialogue Personnalisation") <br/>
Onglet de personnalisation de la souris

L'utilisateur interagit avec cet onglet pour assigner une commande de menu à l'action de double-clic de la souris. L'utilisateur sélectionne une vue sur le côté gauche de la fenêtre, puis utilise les contrôles à droite pour associer une commande à l'action de double-clic. Une fois que l’utilisateur a cliqué sur **Fermer**, l’application exécute la commande associée chaque fois que l’utilisateur double-clique n’importe où dans la vue.

Par défaut, la personnalisation de la souris n'est pas activée lorsque vous créez une application à l'aide de l'Assistant.

#### <a name="to-enable-mouse-customization"></a>Pour activer la personnalisation de la souris

1. Initialisez un objet [CMouseManager](reference/cmousemanager-class.md) en appelant [CWinAppEx :: InitMouseManager](reference/cwinappex-class.md#initmousemanager).

1. Obtenez un pointeur vers le gestionnaire de la souris à l’aide de [CWinAppEx :: GetMouseManager](reference/cwinappex-class.md#getmousemanager).

1. Ajoutez des affichages au gestionnaire de souris à l’aide de la méthode [CMouseManager :: AddView](reference/cmousemanager-class.md#addview) . Effectuez cette opération pour chaque vue que vous souhaitez ajouter au gestionnaire de souris.

Une fois que votre application a initialisé le gestionnaire de la souris, l’infrastructure ajoute l’onglet **souris** à la boîte de dialogue **personnaliser** . Si vous n'ajoutez pas de vue, l'accès à l'onglet génère une exception non gérée. Une fois que vous avez créé une liste de vues, l’onglet de la **souris** est disponible pour l’utilisateur.

Lorsque vous ajoutez une nouvelle vue au gestionnaire de souris, vous lui attribuez un ID unique Si vous souhaitez prendre en charge la personnalisation de la souris pour une fenêtre, vous devez traiter le message WM_LBUTTONDBLCLICK et appeler la fonction [CWinAppEx :: OnViewDoubleClick](reference/cwinappex-class.md#onviewdoubleclick) . Lorsque vous appelez cette fonction, l'un des paramètres est l'ID de cette fenêtre. Il est de la responsabilité des programmeurs de conserver les numéros d'identification et les objets associés.

## <a name="security-concerns"></a>Problèmes de sécurité

Comme décrit dans [Outils définis par l’utilisateur](user-defined-tools.md), l’utilisateur peut associer un ID d’outil défini par l’utilisateur à l’événement de double-clic. Lorsque l'utilisateur double-clique sur une vue, l'application recherche un outil utilisateur qui correspond à l'ID associé. Si l'application trouve un outil correspondant, il exécute l'outil. Si l'application ne trouve pas d'outil correspondant, il envoie un message WM_COMMAND avec l'ID de la vue sur laquelle a eu lieu le double-clic.

Les paramètres personnalisés sont stockés dans le Registre. En modifiant le Registre, un pirate peut remplacer un ID de l'outil utilisateur valide au moyen d'une commande aléatoire. Lorsque l'utilisateur double-clique sur une vue, la vue traite la commande que la personne malveillante a attaquée. Cela peut entraîner un comportement inattendu et potentiellement dangereux.

En outre, ce type d'attaque peut contourner les mesures de protection de l'interface utilisateur. Par exemple, supposons que la fonction d'impression d'une application est désactivée. Autrement dit, dans son interface utilisateur, le menu et le bouton **Imprimer** ne sont pas disponibles. Normalement, l'application ne permet pas d'imprimer des documents. Mais si un intrus a modifié le Registre, un utilisateur peut alors envoyer la commande d'impression simplement en double-cliquant sur la vue, en ignorant les éléments de l'interface utilisateur qui ne sont pas disponibles.

Pour vous protéger contre ce type d'attaque, ajoutez du code à votre gestionnaire de commandes d'application pour vérifier qu'une commande est valide avant son exécution. Pour éviter qu'une commande soit envoyée à l'application, ne dépendez pas de l'interface utilisateur.

## <a name="see-also"></a>Voir aussi

[Personnalisation pour MFC](customization-for-mfc.md)<br/>
[CKeyboardManager, classe](reference/ckeyboardmanager-class.md)<br/>
[CMouseManager, classe](reference/cmousemanager-class.md)<br/>
[Implications en matière de sécurité de la personnalisation](security-implications-of-customization.md)
