---
title: AFX, Messages | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- AFX messages [MFC]
ms.assetid: 3d601f3c-af6d-47d3-8553-34f1318fa74f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76396a402f348181fbcd65a2ccb962207216abda
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954658"
---
# <a name="afx-messages"></a>AFX (messages)
Ces messages sont utilisés dans la bibliothèque MFC.  
  
## <a name="messages"></a>Messages  
 Le tableau suivant répertorie les messages qui sont utilisés dans la bibliothèque MFC :  
  
||||||  
|-|-|-|-|-|  
|Message|Description|[in] *wParam*|*lParam* (tous les paramètres sont [in], sauf indication contraire).|Valeur de retour|  
|AFX_WM_ACCGETOBJECT|Non utilisé.|Non utilisé.|Non applicable.|Non applicable.|  
|AFX_WM_ACCGETSTATE|Utilisé pour la prise en charge de l’accessibilité. Envoyer ce message à `CMFCPopupMenu` ou `CMFCRibbonPanelMenu` pour récupérer l’état de l’élément actuel.|Index de l’élément, ce qui peut être un bouton de menu ou un séparateur.|Non utilisé.|L’état de l’élément. Il est -1 si l’index n’est pas valide, 0 si le bouton de menu n’a aucun attribut spécial. Dans le cas contraire, il est une combinaison des indicateurs suivants :<br /><br /> TBBS_DISABLED : l’élément est désactivé<br /><br /> TBBS_CHECKED : l’élément est activé<br /><br /> TBBS_BUTTON : l’élément est un bouton de commande standard<br /><br /> TBBS_PRESSED : bouton est enfoncé.<br /><br /> TBBS_INDETERMINATE : état indéfini<br /><br /> TBBS_SEPARATOR - plutôt qu’un bouton de menu, formulaires de cet élément une séparation entre les autres éléments de menu|  
|AFX_WM_CHANGE_ACTIVE_TAB|Le framework envoie ce message pour le contrôle de barre de contrôle redimensionnable. Traiter ce message pour recevoir des notifications à partir de `CMFCTabCtrl` objets lorsqu’un utilisateur modifie un onglet actif.|L’index d’un onglet.|Non utilisé.|Différent de zéro.|  
|AFX_WM_CHANGE_CURRENT_FOLDER|Le framework envoie ce message au parent de `CMFCShellListCtrl` lorsque l’utilisateur a modifié le dossier actif.|Non utilisé.|Non utilisé.|Non utilisé.|  
|AFX_WM_CHANGEVISUALMANAGER|Le framework envoie ce message à toutes les fenêtres frame lorsque l’utilisateur modifie le gestionnaire en cours de Visual. En réponse à ce message, une fenêtre frame recalcule sa région et ajuste les autres paramètres en fonction des besoins. Si vous avez besoin être averti de cet événement, vous pouvez traiter le message AFX_WM_CHANGEVISUALMANAGER dans votre application. Vous devez appeler le Gestionnaire de classe de base (`OnChangeVisualManager`) pour vous assurer que l’infrastructure interne du traitement de cet événement a lieu.|Non utilisé.|Non utilisé.|Non utilisé.|  
|AFX_WM_CHANGING_ACTIVE_TAB|Envoyé au parent de `CMFCTabCtrl` objet.  Traiter ce message si vous souhaitez recevoir des notifications à partir de `CMFCTabCtrl` objets lorsqu’un utilisateur réinitialise un onglet.|Index de l’onglet est en cours d’activation.|Non utilisé.|Différent de zéro.|  
|AFX_WM_CHECKEMPTYMINIFRAME|Uniquement réservé à un usage interne.|Non applicable.|Non applicable.|Non applicable.|  
|AFX_WM_CREATETOOLBAR|Envoyé à partir de `CMFCToolBarsListPropertyPage` lorsqu’un utilisateur crée une nouvelle barre d’outils pendant le processus de personnalisation. Vous pouvez traiter ce message pour instancier un objet dérivé de CMFCToolBar personnalisé. Si vous gérez ce message et que vous créez votre propre barre d’outils, omettez d’appeler le gestionnaire par défaut.|Non utilisé.|Pointeur vers une chaîne qui contient le nom de la barre d’outils.|Pointeur vers la barre d’outils nouvellement créé. NULL indique que la création de la barre d’outils a été annulée.|  
|AFX_WM_CUSTOMIZEHELP|Envoyé à la fenêtre frame principale à partir de la feuille de propriétés de personnalisation `CMFCToolbarCustomize Dialog` lorsque l’utilisateur appuie sur le **aide** bouton ou la touche F1.|Spécifie la page active de la feuille de propriétés de personnalisation.|Un pointeur vers un `CMFCToolbarCustomize Dialog` objet.|Zéro.|  
|AFX_WM_CUSTOMIZETOOLBAR|Le `CMFCToolbarCustomize Dialog` envoie ce message pour informer le frame parent que l’utilisateur est en train de créer une barre d’outils.|`TRUE` démarrage de la personnalisation, `FALSE` lorsque la personnalisation est terminée.|Non utilisé.|Zéro.|  
|AFX_WM_DELETETOOLBAR|Envoyé à la fenêtre frame principale lorsque l’utilisateur est sur le point de supprimer une barre d’outils dans le mode de personnalisation.<br /><br /> Traiter ce message pour exécuter des actions supplémentaires lorsqu’un utilisateur supprime une barre d’outils dans le mode de personnalisation. Vous devez également appeler le gestionnaire par défaut (`OnToolbarDelete`), ce qui supprime la barre d’outils. Le gestionnaire par défaut retourne une valeur qui indique s’il est possible de supprimer la barre d’outils.|Non utilisé.|Pointeur vers un `CMFCToolBar` objet à supprimer.|Différent de zéro si une barre d’outils ne peut pas être supprimé ; Sinon, 0.|  
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton` envoie ce message à la fenêtre frame principale pour récupérer les couleurs du document.|Non utilisé.|[dans, out] Pointeur vers un `CList<COLORREF, COLORREF>` objet.|Zéro.|  
|AFX_WM_GETDRAGBOUNDS|Uniquement réservé à un usage interne.|Non applicable.|Non applicable.|Non applicable.|  
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|Envoyé à la fenêtre frame principale lorsqu’un utilisateur met en surbrillance un élément de liste du ruban.|Index de l’élément en surbrillance|Un pointeur vers `CMFCBaseRibbonElement`|Non utilisé.|  
|AFX_WM_ON_AFTER_SHELL_COMMAND|Envoyé à un parent de `CMFCShellListCtrl` ou `CMFCShellTreeCtrl` contrôle lorsqu’un utilisateur termine l’exécution d’une invite de commandes.|L’ID de la commande exécuté par l’utilisateur|Non utilisé.|Si l’application traite ce message, elle doit retourner zéro.|  
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|Le framework envoie ce message au parent du ruban avant d’afficher le menu contextuel. Vous pouvez traiter ce message et modifier des menus contextuels à tout moment.|Non utilisé.|Un pointeur vers `CMFCBaseRibbonElement`|Non utilisé.|  
|AFX_WM_ON_CANCELTABMOVE|Uniquement réservé à un usage interne.|Non applicable.|Non applicable.||  
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|Le framework envoie ce message au frame principal lorsque l’utilisateur modifie la catégorie de contrôle de ruban active.|Non utilisé.|Un pointeur vers le `CMFCRibbonBar` dont la catégorie a changé.|Non utilisé.|  
|AFX_WM_ON_CLOSEPOPUPWINDOW|Le framework envoie ce message pour notifier le propriétaire de `CMFCDesktopAlertWnd` que la fenêtre est sur le point d’être fermé.|Non utilisé.|Un pointeur vers `CMFCDesktopAlertWnd` objet.|Non utilisé.|  
|AFX_WM_ON_DRAGCOMPLETE|Uniquement réservé à un usage interne.|Non applicable.|Non applicable.|Non applicable.|  
|AFX_WM_ON_GET_TAB_TOOLTIP|Envoyé à la fenêtre frame principale lorsqu’une fenêtre de l’onglet est sur le point d’afficher une info-bulle d’un onglet, si les info-bulles personnalisées sont activées.|Non utilisé.|Un pointeur vers un `CMFCTabToolTipInfo` structure.|Non utilisé.|  
|AFX_WM_ON_HSCROLL|Envoyé pour le contrôle de barre de contrôle redimensionnable. Traiter ce message pour recevoir des notifications à partir de `CMFCTabCtrl` objets lorsqu’un événement de défilement se produit dans la barre de défilement horizontale du widget à onglets.|Le mot de poids faible spécifie une valeur de barre de défilement qui indique l’utilisateur de faire défiler les demande.  Pour plus d'informations, consultez la table plus loin dans cette rubrique.|Non utilisé.|Différent de zéro.|  
|AFX_WM_ON_MOVE_TAB|Envoyés vers le parent d’une fenêtre à onglets lorsqu’un utilisateur fait glisser un onglet vers une nouvelle position.|Index de base zéro de l’onglet dans sa position d’origine.|[out] Index de base zéro de l’onglet dans son nouvel emplacement.|Zéro.|  
|AFX_WM_ON_MOVETABCOMPLETE|Uniquement réservé à un usage interne.|Non applicable.|Non applicable.|Non applicable.|  
|AFX_WM_ON_MOVETOTABGROUP|Envoyé à la fenêtre frame principale lorsqu’un utilisateur déplace une fenêtre enfant MDI à partir d’un groupe d’onglets à un autre.|Un handle de fenêtre à onglets (`CMFCTabCtrl`) à partir de laquelle la fenêtre MDI enfant a été supprimée.|[out] Un handle de fenêtre à onglets (`CMFCTabCtrl`) à laquelle la fenêtre MDI enfant a été insérée.|Ignoré.|  
|AFX_WM_ON_PRESS_CLOSE_BUTTON|Envoyé à un parent de `CDockablePane` lorsque l’utilisateur clique sur le **fermer** bouton sur la légende de la barre de contrôle.|Non utilisé.|Un pointeur vers un volet ancrable sur lequel l’utilisateur a cliqué sur le **fermer** bouton.|`TRUE` Si un volet ne peut pas être fermé ; Sinon, FALSE.|  
|AFX_WM_ON_RENAME_TAB|Une fois que l’utilisateur a renommé un onglet modifiable, envoyé au parent de la fenêtre à onglets.|Index de base zéro de l’onglet renommé.|[out] Pointeur vers une chaîne qui contient le nouveau nom d’onglet.|Différent de zéro si l’application traite le message ; le framework supprime l’appel à `CMFCBaseTabCtrl::SetTabLabel`.  Si la valeur zéro est renvoyée, `CMFCBaseTabCtrl::SetTabLabel` est appelé par l’infrastructure.|  
|AFX_WM_ON_RIBBON_CUSTOMIZE|Envoyés vers le frame parent lorsque l’utilisateur commence la personnalisation. Traiter ce message si vous souhaitez afficher votre propre boîte de dialogue de personnalisation.|Non utilisé.|Pointeur vers le contrôle de ruban à personnaliser.|Différent de zéro si l’application traite ce message et affiche sa propre boîte de dialogue de personnalisation. Si l’application renvoie zéro, le framework affiche la boîte de dialogue de personnalisation intégrées.|  
|AFX_WM_ON_TABGROUPMOUSEMOVE|Uniquement réservé à un usage interne.|Non applicable.|Non applicable.|Non applicable.|  
|AFX_WM_POSTSETPREVIEWFRAME|Envoyé pour informer le frame principal que l’utilisateur a modifié le mode Aperçu avant impression|`TRUE` Indique que le mode Aperçu avant impression est défini. `FALSE` Indique que le mode Aperçu avant impression est désactivé.|Non utilisé.|Non utilisé.|  
|AFX_WM_PROPERTY_CHANGED|Envoyé au propriétaire de la propriété du contrôle de grille (`CMFCPropertyGridCtrl`) lorsque l’utilisateur modifie la valeur de la propriété sélectionnée.|L’ID de contrôle de la liste de propriétés.|Un pointeur vers la propriété (`CMFCPropertyGridProperty`) qui a changé.|Non utilisé.|  
|AFX_WM_RESETCONTEXTMENU|Envoyé à la fenêtre frame principale lorsque l’utilisateur réinitialise le menu contextuel au cours de personnalisation.|L’ID de ressource du menu contextuel.|Un pointeur vers le menu contextuel en cours, `CMFCPopupMenu`.|Non utilisé.|  
|AFX_WM_RESETKEYBOARD|Le framework envoie ce message à la fenêtre frame principale lorsque l’utilisateur réinitialise tous les accélérateurs clavier au cours de personnalisation.|Non utilisé.|Non utilisé.|Non utilisé.|  
|AFX_WM_RESETMENU|Le framework envoie ce message au propriétaire du menu (une fenêtre frame) lorsque l’utilisateur réinitialise un menu de frame d’application au cours de personnalisation|L’ID de ressource de menu.|Non utilisé.|Non utilisé.|  
|AFX_WM_RESETPROMPT|Le framework envoie ce message lors de la boîte de dialogue de personnalisation de l’utilisateur réinitialise une barre d’outils à partir de la barre d’outils. Le gestionnaire par défaut affiche une boîte de message qui vous demande si l’utilisateur souhaite réinitialiser la barre d’outils.|Non utilisé.|Non utilisé.|Non utilisé.|  
|AFX_WM_RESETTOOLBAR|A `CMFCToolBar` objet envoie ce message lorsqu’une barre d’outils est restaurée à son état d’origine, autrement dit, chargé à partir des ressources. Traiter ce message et réinsérez les boutons de barre d’outils dont les classes sont dérivées de `CMFCToolbarButton`. Pour plus d'informations, consultez `CMFCToolbarComboBoxButton`.|L’ID de ressource d’une barre d’outils dont l’état a été restauré.|Non utilisé.|Zéro.|  
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton` objet envoie ce message à son propriétaire lorsque l’utilisateur clique sur un bouton de menu standard. Traiter ce message chaque fois que vous utilisez `CMFCToolbarMenuButton` pour afficher un menu contextuel lorsque l’utilisateur clique sur un bouton.|L’ID de commande d’un bouton qui envoie le message.|Coordonnées d’écran du curseur. Le mot de poids faible spécifie la coordonnée x. Le mot de poids fort spécifie la coordonnée y.|Non utilisé.|  
|AFX_WM_TOOLBARMENU|Envoyé à la fenêtre frame principale lorsque l’utilisateur relâche le bouton droit de la souris alors que le pointeur de la souris se trouve dans le client ou d’une zone non cliente d’un volet.|Non utilisé.|Coordonnées d’écran du pointeur de la souris. Le mot de poids faible spécifie la coordonnée x. Le mot de poids fort spécifie la coordonnée y.|Zéro si l’application traite le message ; Sinon, différente de zéro.|  
|AFX_WM_UPDATETOOLTIPS|Envoyé à tous les propriétaires de l’info-bulle pour indiquer que les contrôles d’info-bulle doivent être recréées.|Le type de contrôle qui doit traiter ce message. Consultez le tableau plus loin dans cette rubrique pour obtenir la liste des valeurs possibles.|Non utilisé.|Non utilisé.|  
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog` envoie ce message pour le frame parent lorsque l’utilisateur clique sur le **aide** bouton ou insère le mode d’aide en cliquant sur le **aide** bouton de légende ou la touche F1.|Non utilisé.|Un pointeur vers l’instance de `CMFCWindowsManagerDialog`.|Non utilisé.|  
  
 Le tableau suivant montre les valeurs pour le mot de poids faible de la *lParam* paramètre de la méthode AFX_WM_HSCROLL :  
  
|||  
|-|-|  
|Value|Signification|  
|SB_ENDSCROLL|L’utilisateur termine le défilement.|  
|SB_LEFT|L’utilisateur fait défiler à l’angle supérieur gauche.|  
|SB_RIGHT|L’utilisateur fait défiler vers le coin inférieur droit.|  
|SB_LINELEFT|L’utilisateur fait défiler vers la gauche d’une unité.|  
|SB_LINERIGHT|L’utilisateur fait défiler vers la droite d’une unité.|  
|SB_PAGELEFT|L’utilisateur fait défiler vers la gauche de la largeur de la fenêtre.|  
|SB_PAGERIGHT|L’utilisateur fait défiler à droite par la largeur de la fenêtre.|  
|SB_THUMBPOSITION|L’utilisateur a déplacé la case de défilement (curseur) et relâchez le bouton. Le mot de poids fort indique la position du curseur de défilement à la fin de l’opération de glissement.|  
|SB_THUMBTRACK|L’utilisateur fait glisser le curseur de défilement. Le message AFX_WM_ON_HSCROLL est envoyé à plusieurs reprises avec cette valeur jusqu'à ce que l’utilisateur relâche le bouton de la souris. Le mot de poids fort indique la position à laquelle la case de défilement a été déplacée.|  
  
> [!NOTE]
>  Le mot de poids fort de le *lParam* paramètre spécifie la position actuelle de la case de défilement, si le mot de poids faible est SB_THUMBPOSITION ou SB_THUMBTRACK ; sinon, ce mot n’est pas utilisé.  
  
 Le tableau suivant répertorie les valeurs d’indicateur pour le *lParam* paramètre du message AFX_WM_UPDATETOOLTIPS :  
  
|||  
|-|-|  
|Indicateur|Value|  
|AFX_TOOLTIP_TYPE_DEFAULT|0 x 0001|  
|AFX_TOOLTIP_TYPE_TOOLBAR|0 x 0002|  
|AFX_TOOLTIP_TYPE_TAB|0 x 0004|  
|AFX_TOOLTIP_TYPE_MINIFRAME|0x0008|  
|AFX_TOOLTIP_TYPE_DOCKBAR|0x0010|  
|AFX_TOOLTIP_TYPE_EDIT|0x0020|  
|AFX_TOOLTIP_TYPE_BUTTON|0 x 0040|  
|AFX_TOOLTIP_TYPE_TOOLBOX|0 x 0080|  
|AFX_TOOLTIP_TYPE_ALL|0xFFFF|  
  
## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
