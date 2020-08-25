---
title: AFX (messages)
ms.date: 11/04/2016
f1_keywords:
- SB_LINELEFT
- SB_THUMBTRACK
- AFX_TOOLTIP_TYPE_EDIT
- AFX_WM_ON_HSCROLL
- SB_PAGERIGHT
- AFX_WM_RESETPROMPT
- AFX_WM_CHANGE_RIBBON_CATEGORY
- AFX_TOOLTIP_TYPE_MINIFRAME
- AFX_WM_CUSTOMIZETOOLBAR
- AFX_WM_CHANGE_ACTIVE_TAB
- AFX_WM_ACCGETOBJECT
- AFX_WM_TOOLBARMENU
- AFX_TOOLTIP_TYPE_DOCKBAR
- AFX_WM_CUSTOMIZEHELP
- AFX_WM_ON_GET_TAB_TOOLTIP
- AFX_WM_ON_RIBBON_CUSTOMIZE
- AFX_WM_ON_DRAGCOMPLETE
- AFX_WM_RESETTOOLBAR
- AFX_WM_ON_MOVETOTABGROUP
- AFX_WM_CHECKEMPTYMINIFRAME
- AFX_WM_GETDOCUMENTCOLORS
- SB_RIGHT
- AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU
- AFX_WM_ACCGETSTATE
- SB_PAGELEFT
- SB_ENDSCROLL
- AFX_WM_ON_CANCELTABMOVE
- AFX_TOOLTIP_TYPE_TAB
- AFX_WM_WINDOW_HELP
- AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM
- AFX_WM_SHOWREGULARMENU
- AFX_TOOLTIP_TYPE_TOOLBAR
- AFX_WM_CHANGE_CURRENT_FOLDER
- AFX_WM_UPDATETOOLTIPS
- AFX_WM_ON_MOVE_TAB
- AFX_WM_CHANGING_ACTIVE_TAB
- AFX_WM_RESETMENU
- AFX_WM_GETDRAGBOUNDS
- AFX_WM_RESETCONTEXTMENU
- AFX_TOOLTIP_TYPE_BUTTON
- AFX_WM_ON_CLOSEPOPUPWINDOW
- AFX_TOOLTIP_TYPE_TOOLBOX
- AFX_WM_CHANGEVISUALMANAGER
- SB_LINERIGHT
- AFX_WM_ON_RENAME_TAB
- AFX_TOOLTIP_TYPE_DEFAULT
- AFX_WM_ON_TABGROUPMOUSEMOVE
- SB_LEFT
- AFX_WM_DELETETOOLBAR
- AFX_WM_PROPERTY_CHANGED
- AFX_TOOLTIP_TYPE_ALL
- AFX_WM_ACCHITTEST
- AFX_WM_ON_AFTER_SHELL_COMMAND
- AFX_WM_ON_PRESS_CLOSE_BUTTON
- AFX_WM_RESETKEYBOARD
- AFX_WM_ON_MOVETABCOMPLETE
- AFX_WM_CREATETOOLBAR
- SB_THUMBPOSITION
- AFX_WM_POSTSETPREVIEWFRAME
helpviewer_keywords:
- AFX messages [MFC]
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
ms.openlocfilehash: 409760eff6ba6b31413c11fb45ea91a6d07b9485
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832397"
---
# <a name="afx-messages"></a>AFX (messages)

Ces messages sont utilisés dans MFC.

## <a name="messages"></a>Messages

Le tableau suivant répertorie les messages qui sont utilisés dans la bibliothèque MFC :

|Message|Description|dans *wParam*|*lParam* (tous les paramètres sont [in] sauf indication contraire).|Valeur renvoyée|
|-|-|-|-|-|
|AFX_WM_ACCGETOBJECT|Non utilisé.|Non utilisé.|Non applicable.|Non applicable.|
|AFX_WM_ACCGETSTATE|Utilisé pour la prise en charge de l’accessibilité. Envoie ce message à `CMFCPopupMenu` ou `CMFCRibbonPanelMenu` pour récupérer l’état de l’élément actuel.|Index de l’élément, qui peut être un bouton de menu ou un séparateur.|Non utilisé.|État de l’élément. Elle a la valeur-1 si l’index n’est pas valide, 0 si le bouton de menu n’a pas d’attributs spéciaux. Dans le cas contraire, il s’agit d’une combinaison des indicateurs suivants :<br /><br /> TBBS_DISABLED : l’élément est désactivé<br /><br /> TBBS_CHECKED : l’élément est activé<br /><br /> TBBS_BUTTON : l’élément est un bouton de bouton standard<br /><br /> TBBS_PRESSED : le bouton est enfoncé<br /><br /> TBBS_INDETERMINATE : état non défini<br /><br /> TBBS_SEPARATOR-plutôt qu’un bouton de menu, cet élément constitue une séparation entre les autres éléments de menu|
|AFX_WM_CHANGE_ACTIVE_TAB|L’infrastructure envoie ce message au contrôle de barre de contrôle redimensionnable. Traite ce message pour recevoir des notifications d' `CMFCTabCtrl` objets lorsqu’un utilisateur modifie un onglet actif.|Index d’un onglet.|Non utilisé.|Différente.|
|AFX_WM_CHANGE_CURRENT_FOLDER|L’infrastructure envoie ce message au parent de `CMFCShellListCtrl` lorsque l’utilisateur a modifié le dossier actif.|Non utilisé.|Non utilisé.|Non utilisé.|
|AFX_WM_CHANGEVISUALMANAGER|L’infrastructure envoie ce message à toutes les fenêtres Frame lorsque l’utilisateur modifie le gestionnaire visuel actuel. En réponse à ce message, une fenêtre frame recalcule sa région et ajuste les autres paramètres en fonction des besoins. Vous pouvez traiter le message d’AFX_WM_CHANGEVISUALMANAGER dans votre application si vous devez être informé de cet événement. Vous devez appeler le gestionnaire de classe de base ( `OnChangeVisualManager` ) pour vous assurer que le traitement interne de l’infrastructure de cet événement a lieu.|Non utilisé.|Non utilisé.|Non utilisé.|
|AFX_WM_CHANGING_ACTIVE_TAB|Envoyé au parent de l' `CMFCTabCtrl` objet.  Traiter ce message si vous souhaitez recevoir des notifications d' `CMFCTabCtrl` objets lorsqu’un utilisateur réinitialise un onglet.|Index de l’onglet en cours d’activation.|Non utilisé.|Différente.|
|AFX_WM_CHECKEMPTYMINIFRAME|Uniquement réservé à un usage interne.|Non applicable.|Non applicable.|Non applicable.|
|AFX_WM_CREATETOOLBAR|Envoyé à partir de `CMFCToolBarsListPropertyPage` lorsqu’un utilisateur crée une nouvelle barre d’outils pendant le processus de personnalisation. Vous pouvez traiter ce message pour instancier un objet personnalisé dérivé de CMFCToolBar. Si vous gérez ce message et créez votre propre barre d’outils, omettez l’appel au gestionnaire par défaut.|Non utilisé.|Pointeur vers une chaîne qui contient le nom de la barre d’outils.|Pointeur vers la barre d’outils nouvellement créée. La valeur NULL indique que la création de la barre d’outils a été annulée.|
|AFX_WM_CUSTOMIZEHELP|Envoyé à la fenêtre frame principale à partir de la feuille de propriétés de personnalisation `CMFCToolbarCustomize Dialog` lorsque l’utilisateur appuie sur le bouton **aide** ou sur la touche F1.|Spécifie la page active de la feuille de propriétés de personnalisation.|Pointeur vers un objet `CMFCToolbarCustomize Dialog`.|Zéro.|
|AFX_WM_CUSTOMIZETOOLBAR|Le `CMFCToolbarCustomize Dialog` envoie ce message pour notifier au frame parent que l’utilisateur crée une nouvelle barre d’outils.|TRUE lorsque la personnalisation est démarrée, FALSe lorsque la personnalisation est terminée.|Non utilisé.|Zéro.|
|AFX_WM_DELETETOOLBAR|Envoyé à la fenêtre frame principale lorsque l’utilisateur est sur le paragraphe de supprimer une barre d’outils en mode de personnalisation.<br /><br /> Traiter ce message pour exécuter des actions supplémentaires quand un utilisateur supprime une barre d’outils en mode de personnalisation. Vous devez également appeler le gestionnaire par défaut ( `OnToolbarDelete` ), qui supprime la barre d’outils. Le gestionnaire par défaut retourne une valeur qui indique s’il est possible de supprimer la barre d’outils.|Non utilisé.|Pointeur vers un `CMFCToolBar` objet à supprimer.|Différent de zéro si une barre d’outils ne peut pas être supprimée ; Sinon, 0.|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton` envoie ce message à la fenêtre frame principale pour récupérer les couleurs du document.|Non utilisé.|[in, out] Pointeur vers un `CList<COLORREF, COLORREF>` objet.|Zéro.|
|AFX_WM_GETDRAGBOUNDS|Uniquement réservé à un usage interne.|Non applicable.|Non applicable.|Non applicable.|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|Envoyé à la fenêtre frame principale quand un utilisateur met en surbrillance un élément de la liste du ruban.|Index de l’élément mis en surbrillance|Pointeur vers `CMFCBaseRibbonElement`|Non utilisé.|
|AFX_WM_ON_AFTER_SHELL_COMMAND|Envoyé à un parent de `CMFCShellListCtrl` ou `CMFCShellTreeCtrl` contrôles lorsqu’un utilisateur termine l’exécution d’une commande d’interpréteur de commandes.|ID de la commande exécutée par l’utilisateur|Non utilisé.|Si l’application traite ce message, elle doit retourner la valeur zéro.|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|L’infrastructure envoie ce message au parent du ruban avant d’afficher le menu contextuel. Vous pouvez traiter ce message et modifier les menus contextuels à tout moment.|Non utilisé.|Pointeur vers `CMFCBaseRibbonElement`|Non utilisé.|
|AFX_WM_ON_CANCELTABMOVE|Uniquement réservé à un usage interne.|Non applicable.|Non applicable.||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|L’infrastructure envoie ce message au frame principal lorsque l’utilisateur modifie la catégorie de contrôle du ruban active.|Non utilisé.|Pointeur vers le `CMFCRibbonBar` dont la catégorie a changé.|Non utilisé.|
|AFX_WM_ON_CLOSEPOPUPWINDOW|L’infrastructure envoie ce message pour informer le propriétaire de `CMFCDesktopAlertWnd` la fermeture de la fenêtre.|Non utilisé.|Pointeur vers un `CMFCDesktopAlertWnd` objet.|Non utilisé.|
|AFX_WM_ON_DRAGCOMPLETE|Uniquement réservé à un usage interne.|Non applicable.|Non applicable.|Non applicable.|
|AFX_WM_ON_GET_TAB_TOOLTIP|Envoyé à la fenêtre frame principale quand une fenêtre d’onglets est sur le paragraphe pour afficher une info-bulle pour un onglet, si les info-bulles personnalisées sont activées.|Non utilisé.|Pointeur vers une `CMFCTabToolTipInfo` structure.|Non utilisé.|
|AFX_WM_ON_HSCROLL|Envoyé au contrôle de barre de contrôle redimensionnable. Traite ce message pour recevoir des notifications d' `CMFCTabCtrl` objets lorsqu’un événement de défilement se produit dans la barre de défilement horizontale du widget avec onglets.|Le mot de poids faible spécifie une valeur de barre de défilement qui indique la requête de défilement de l’utilisateur.  Pour plus d'informations, consultez la table plus loin dans cette rubrique.|Non utilisé.|Différente.|
|AFX_WM_ON_MOVE_TAB|Envoyé au parent d’une fenêtre à onglets lorsqu’un utilisateur fait glisser un onglet vers une nouvelle position.|Index de base zéro de l’onglet dans sa position d’origine.|à Index de base zéro de l’onglet à sa nouvelle position.|Zéro.|
|AFX_WM_ON_MOVETABCOMPLETE|Uniquement réservé à un usage interne.|Non applicable.|Non applicable.|Non applicable.|
|AFX_WM_ON_MOVETOTABGROUP|Envoyé à la fenêtre frame principale quand un utilisateur déplace une fenêtre enfant MDI d’un groupe à onglets à un autre.|Handle vers la fenêtre à onglets ( `CMFCTabCtrl` ) à partir duquel la fenêtre enfant MDI a été supprimée.|à Handle vers la fenêtre à onglets ( `CMFCTabCtrl` ) à laquelle la fenêtre enfant MDI a été insérée.|Ignoré.|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|Envoyé à un parent de `CDockablePane` lorsque l’utilisateur clique sur le bouton **Fermer** dans la légende de la barre de contrôle.|Non utilisé.|Pointeur vers un volet Ancrable sur lequel l’utilisateur a cliqué sur le bouton **Fermer** .|TRUE si un volet ne peut pas être fermé ; Sinon, FALSe.|
|AFX_WM_ON_RENAME_TAB|Envoyé au parent de la fenêtre à onglets après que l’utilisateur a renommé un onglet modifiable.|Index de base zéro de l’onglet renommé.|à Pointeur vers une chaîne qui contient le nouveau nom de l’onglet.|Différent de zéro si l’application traite ce message ; l’infrastructure supprime l’appel à `CMFCBaseTabCtrl::SetTabLabel` .  Si la valeur zéro est retournée, `CMFCBaseTabCtrl::SetTabLabel` est appelée par le Framework.|
|AFX_WM_ON_RIBBON_CUSTOMIZE|Envoyé au frame parent lorsque l’utilisateur commence la personnalisation. Traiter ce message si vous souhaitez afficher votre propre boîte de dialogue de personnalisation.|Non utilisé.|Pointeur vers le contrôle de ruban à personnaliser.|Différent de zéro si l’application traite ce message et affiche sa propre boîte de dialogue de personnalisation. Si l’application retourne la valeur zéro, l’infrastructure affiche la boîte de dialogue Personnalisation intégrée.|
|AFX_WM_ON_TABGROUPMOUSEMOVE|Uniquement réservé à un usage interne.|Non applicable.|Non applicable.|Non applicable.|
|AFX_WM_POSTSETPREVIEWFRAME|Envoyé pour notifier le frame principal que l’utilisateur a modifié le mode aperçu avant impression|TRUE indique que le mode aperçu avant impression est défini. FALSe indique que le mode aperçu avant impression est désactivé.|Non utilisé.|Non utilisé.|
|AFX_WM_PROPERTY_CHANGED|Envoyé au propriétaire du contrôle de grille de propriétés ( `CMFCPropertyGridCtrl` ) lorsque l’utilisateur modifie la valeur de la propriété sélectionnée.|ID de contrôle de la liste de propriétés.|Pointeur vers la propriété ( `CMFCPropertyGridProperty` ) qui a changé.|Non utilisé.|
|AFX_WM_RESETCONTEXTMENU|Envoyé à la fenêtre frame principale lorsque l’utilisateur réinitialise le menu contextuel pendant la personnalisation.|ID de ressource du menu contextuel.|Pointeur vers le menu contextuel actuel, `CMFCPopupMenu` .|Non utilisé.|
|AFX_WM_RESETKEYBOARD|L’infrastructure envoie ce message à la fenêtre frame principale lorsque l’utilisateur réinitialise tous les accélérateurs clavier pendant la personnalisation.|Non utilisé.|Non utilisé.|Non utilisé.|
|AFX_WM_RESETMENU|L’infrastructure envoie ce message au propriétaire du menu (une fenêtre frame) lorsque l’utilisateur réinitialise un menu Frame d’application pendant la personnalisation.|ID de ressource de menu.|Non utilisé.|Non utilisé.|
|AFX_WM_RESETPROMPT|L’infrastructure envoie ce message lorsque l’utilisateur réinitialise une barre d’outils à partir de la boîte de dialogue Personnaliser de la barre d’outils. Le gestionnaire par défaut affiche une boîte de message qui demande si l’utilisateur souhaite réinitialiser la barre d’outils.|Non utilisé.|Non utilisé.|Non utilisé.|
|AFX_WM_RESETTOOLBAR|Un `CMFCToolBar` objet envoie ce message lorsqu’une barre d’outils est restaurée à son état d’origine, c’est-à-dire chargé à partir des ressources. Traite ce message pour réinsérer les boutons de barre d’outils dont les classes sont dérivées de `CMFCToolbarButton` . Pour plus d'informations, consultez `CMFCToolbarComboBoxButton`.|ID de ressource d’une barre d’outils dont l’État a été restauré.|Non utilisé.|Zéro.|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton` l’objet envoie ce message à son propriétaire quand l’utilisateur clique sur un bouton de menu normal. Traiter ce message chaque fois que vous utilisez `CMFCToolbarMenuButton` pour afficher un menu contextuel lorsque l’utilisateur clique sur un bouton.|ID de commande d’un bouton qui envoie le message.|Coordonnées d’écran du curseur. Le mot de poids faible spécifie la coordonnée x. Le mot de poids fort spécifie la coordonnée y.|Non utilisé.|
|AFX_WM_TOOLBARMENU|Envoyé à la fenêtre frame principale lorsque l’utilisateur relâche le bouton droit de la souris alors que le pointeur de la souris se trouve dans la zone cliente ou non cliente d’un volet.|Non utilisé.|Coordonnées d’écran du pointeur de la souris. Le mot de poids faible spécifie la coordonnée x. Le mot de poids fort spécifie la coordonnée y.|Zéro si l’application traite ce message ; Sinon, la valeur est différente de zéro.|
|AFX_WM_UPDATETOOLTIPS|Envoyé à tous les propriétaires d’info-bulle pour indiquer que leurs contrôles ToolTip doivent être recréés.|Type de contrôle qui doit traiter ce message. Consultez le tableau plus loin dans cette rubrique pour obtenir la liste des valeurs possibles.|Non utilisé.|Non utilisé.|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog` envoie ce message au frame parent lorsque l’utilisateur clique sur le bouton **aide** ou qu’il entre en mode aide en cliquant sur le bouton de la légende **d’aide** ou la touche F1.|Non utilisé.|Pointeur vers l’instance de `CMFCWindowsManagerDialog` .|Non utilisé.|

Le tableau suivant indique les valeurs du mot de poids faible du paramètre *lParam* de la méthode AFX_WM_HSCROLL :

|Valeur|Signification|
|-|-|
|SB_ENDSCROLL|L’utilisateur termine le défilement.|
|SB_LEFT|L’utilisateur fait défiler le curseur vers l’angle supérieur gauche.|
|SB_RIGHT|L’utilisateur fait défiler vers le bas à droite.|
|SB_LINELEFT|L’utilisateur fait défiler d’une unité vers la gauche.|
|SB_LINERIGHT|L’utilisateur fait défiler vers la droite d’une unité.|
|SB_PAGELEFT|L’utilisateur fait défiler la largeur de la fenêtre vers la gauche.|
|SB_PAGERIGHT|L’utilisateur fait défiler la largeur de la fenêtre vers la droite.|
|SB_THUMBPOSITION|L’utilisateur a fait glisser la case de défilement (Thumb) et relâché le bouton de la souris. Le mot de poids fort indique la position de la case de défilement à la fin de l’opération glisser.|
|SB_THUMBTRACK|L’utilisateur fait glisser la case de défilement. Le message AFX_WM_ON_HSCROLL est envoyé à plusieurs reprises avec cette valeur jusqu’à ce que l’utilisateur relâche le bouton de la souris. Le mot de poids fort indique la position à laquelle la case de défilement a été déplacée.|

> [!NOTE]
> Le mot de poids fort du paramètre *lParam* spécifie la position actuelle de la case de défilement si le mot de poids faible est SB_THUMBPOSITION ou SB_THUMBTRACK ; dans le cas contraire, ce mot n’est pas utilisé.

Le tableau suivant répertorie les valeurs d’indicateur pour le paramètre *lParam* du message AFX_WM_UPDATETOOLTIPS :

|Indicateur|Valeur|
|-|-|
|AFX_TOOLTIP_TYPE_DEFAULT|0x0001|
|AFX_TOOLTIP_TYPE_TOOLBAR|0x0002|
|AFX_TOOLTIP_TYPE_TAB|0x0004|
|AFX_TOOLTIP_TYPE_MINIFRAME|0x0008|
|AFX_TOOLTIP_TYPE_DOCKBAR|0x0010|
|AFX_TOOLTIP_TYPE_EDIT|0x0020|
|AFX_TOOLTIP_TYPE_BUTTON|0x0040|
|AFX_TOOLTIP_TYPE_TOOLBOX|0x0080|
|AFX_TOOLTIP_TYPE_ALL|0xFFFF|

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
