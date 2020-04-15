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
ms.openlocfilehash: b4ed86c11d3c5b5f1ce38e3146533109f3a6b00d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363599"
---
# <a name="afx-messages"></a>AFX (messages)

Ces messages sont utilisés dans MFC.

## <a name="messages"></a>Messages

Le tableau suivant répertorie les messages utilisés dans la bibliothèque MFC :

||||||
|-|-|-|-|-|
|Message|Description|[dans] *wParam (en)*|*lParam* (Tous les paramètres sont [dans] sauf indication contraire.)|Valeur de retour|
|AFX_WM_ACCGETOBJECT|Non utilisé.|Non utilisé.|Non applicable.|Non applicable.|
|AFX_WM_ACCGETSTATE|Utilisé pour le soutien à l’accessibilité. Envoyez ce `CMFCPopupMenu` message `CMFCRibbonPanelMenu` à l’état de l’élément actuel ou pour récupérer.|Index de l’élément, qui pourrait être un bouton de menu ou un séparateur.|Non utilisé.|L’état de l’élément. Il est de -1 si l’index est invalide, 0 si le bouton de menu n’a pas d’attributs spéciaux. Sinon, il s’agit d’une combinaison des drapeaux suivants:<br /><br /> TBBS_DISABLED — l’article est désactivé<br /><br /> TBBS_CHECKED — l’article est vérifié<br /><br /> TBBS_BUTTON — l’article est un pushbutton standard<br /><br /> TBBS_PRESSED — bouton est pressé<br /><br /> TBBS_INDETERMINATE — État indéfini<br /><br /> TBBS_SEPARATOR - plutôt qu’un bouton de menu, cet élément forme une séparation entre les autres éléments du menu|
|AFX_WM_CHANGE_ACTIVE_TAB|Le cadre envoie ce message au contrôle resizable de barre de contrôle. Traitez ce message pour `CMFCTabCtrl` recevoir des notifications d’objets lorsqu’un utilisateur change d’onglet actif.|L’index d’un onglet.|Non utilisé.|Nonzero.|
|AFX_WM_CHANGE_CURRENT_FOLDER|Le cadre envoie ce message `CMFCShellListCtrl` au parent de quand l’utilisateur a changé le dossier actuel.|Non utilisé.|Non utilisé.|Non utilisé.|
|AFX_WM_CHANGEVISUALMANAGER|Le cadre envoie ce message à toutes les fenêtres d’images lorsque l’utilisateur modifie l’actuel Visual Manager. En réponse à ce message, une fenêtre de cadre récalcule sa région et ajuste d’autres paramètres au besoin. Vous pouvez traiter le AFX_WM_CHANGEVISUALMANAGER message de votre demande si vous devez être informé de cet événement. Vous devez appeler le`OnChangeVisualManager`gestionnaire de la classe de base ( ) pour vous assurer que le traitement interne de cet événement par le cadre a lieu.|Non utilisé.|Non utilisé.|Non utilisé.|
|AFX_WM_CHANGING_ACTIVE_TAB|Envoyé au parent `CMFCTabCtrl` de l’objet.  Traitez ce message si vous `CMFCTabCtrl` souhaitez recevoir des notifications d’objets lorsqu’un utilisateur réinitialise un onglet.|L’index de l’onglet qui est activé.|Non utilisé.|Nonzero.|
|AFX_WM_CHECKEMPTYMINIFRAME|À usage interne uniquement.|Non applicable.|Non applicable.|Non applicable.|
|AFX_WM_CREATETOOLBAR|Envoyé `CMFCToolBarsListPropertyPage` à partir du moment où un utilisateur crée une nouvelle barre d’outils pendant le processus de personnalisation. Vous pouvez traiter ce message pour instantanér un objet dérivé de CMFCToolBar personnalisé. Si vous gérez ce message et créez votre propre barre d’outils, ometez l’appel au gestionnaire par défaut.|Non utilisé.|Un pointeur à une chaîne qui contient le nom de la barre d’outils.|Un pointeur à la barre d’outils nouvellement créée. NULL indique que la création de la barre d’outils a été annulée.|
|AFX_WM_CUSTOMIZEHELP|Envoyé à la fenêtre du cadre `CMFCToolbarCustomize Dialog` principal à partir de la feuille de propriété de personnalisation lorsque l’utilisateur appuie sur le bouton **Aide** ou la clé F1.|Spécifie la page active de la feuille de propriété de personnalisation.|Pointeur vers un objet `CMFCToolbarCustomize Dialog`.|Zéro.|
|AFX_WM_CUSTOMIZETOOLBAR|L’envoie `CMFCToolbarCustomize Dialog` ce message pour informer le cadre parent que l’utilisateur est la création d’une nouvelle barre d’outils.|VRAI lorsque la personnalisation est commencée, FALSE lorsque la personnalisation est terminée.|Non utilisé.|Zéro.|
|AFX_WM_DELETETOOLBAR|Envoyé à la fenêtre de cadre principale lorsque l’utilisateur est sur le point de supprimer une barre d’outils dans le mode de personnalisation.<br /><br /> Traitez ce message pour prendre des mesures supplémentaires lorsqu’un utilisateur supprime une barre d’outils en mode personnalisation. Vous devez également appeler`OnToolbarDelete`le gestionnaire par défaut ( ), qui supprime la barre d’outils. Le gestionnaire par défaut retourne une valeur qui indique s’il est possible de supprimer la barre d’outils.|Non utilisé.|Pointeur `CMFCToolBar` vers un objet à supprimer.|Nonzero si une barre d’outils ne peut pas être supprimée; sinon 0.|
|AFX_WM_GETDOCUMENTCOLORS|`CMFCColorMenuButton`envoie ce message à la fenêtre du cadre principal pour récupérer les couleurs du document.|Non utilisé.|[dans, dehors] Pointeur `CList<COLORREF, COLORREF>` vers un objet.|Zéro.|
|AFX_WM_GETDRAGBOUNDS|À usage interne uniquement.|Non applicable.|Non applicable.|Non applicable.|
|AFX_WM_HIGHLIGHT_RIBBON_LIST_ITEM|Envoyé à la fenêtre principale du cadre quand un utilisateur met en évidence un élément de liste de ruban.|Index de l’élément mis en évidence|Un pointeur à`CMFCBaseRibbonElement`|Non utilisé.|
|AFX_WM_ON_AFTER_SHELL_COMMAND|Envoyé à un `CMFCShellListCtrl` `CMFCShellTreeCtrl` parent ou contrôle quand un utilisateur finit d’exécuter une commande shell.|L’ID de la commande que l’utilisateur a exécuté|Non utilisé.|Si l’application traite ce message, il doit revenir à zéro.|
|AFX_WM_ON_BEFORE_SHOW_RIBBON_ITEM_MENU|Le cadre envoie ce message au parent du ruban avant qu’il n’affiche le menu pop-up. Vous pouvez traiter ce message et modifier les menus contextuels à tout moment.|Non utilisé.|Un pointeur à`CMFCBaseRibbonElement`|Non utilisé.|
|AFX_WM_ON_CANCELTABMOVE|À usage interne uniquement.|Non applicable.|Non applicable.||
|AFX_WM_ON_CHANGE_RIBBON_CATEGORY|Le cadre envoie ce message au cadre principal lorsque l’utilisateur modifie la catégorie de contrôle du ruban actif.|Non utilisé.|Un pointeur `CMFCRibbonBar` à la catégorie dont a changé la catégorie.|Non utilisé.|
|AFX_WM_ON_CLOSEPOPUPWINDOW|Le cadre envoie ce message pour `CMFCDesktopAlertWnd` informer le propriétaire que la fenêtre est sur le point d’être fermée.|Non utilisé.|Un pointeur à `CMFCDesktopAlertWnd` objecter.|Non utilisé.|
|AFX_WM_ON_DRAGCOMPLETE|À usage interne uniquement.|Non applicable.|Non applicable.|Non applicable.|
|AFX_WM_ON_GET_TAB_TOOLTIP|Envoyé à la fenêtre du cadre principal quand une fenêtre d’onglet est sur le point d’afficher une boîte à outils pour un onglet, si des outils personnalisés sont activés.|Non utilisé.|Un pointeur `CMFCTabToolTipInfo` vers une structure.|Non utilisé.|
|AFX_WM_ON_HSCROLL|Envoyé au contrôle de la barre de commande resizable. Traiter ce message pour `CMFCTabCtrl` recevoir des notifications d’objets lorsqu’un événement de défilement se produit dans la barre de défilement horizontal de widget tabbed.|Le mot de faible ordre spécifie une valeur de barre de défilement qui indique la demande de défilement de l’utilisateur.  Pour plus d'informations, consultez la table plus loin dans cette rubrique.|Non utilisé.|Nonzero.|
|AFX_WM_ON_MOVE_TAB|Envoyé au parent d’une fenêtre tabbed quand un utilisateur traîne un onglet à une nouvelle position.|L’indice à base nulle de l’onglet dans sa position d’origine.|[out] L’indice zéro de l’onglet dans sa nouvelle position.|Zéro.|
|AFX_WM_ON_MOVETABCOMPLETE|À usage interne uniquement.|Non applicable.|Non applicable.|Non applicable.|
|AFX_WM_ON_MOVETOTABGROUP|Envoyé à la fenêtre du cadre principal quand un utilisateur déplace une fenêtre d’enfant MDI d’un groupe tabbed à un autre.|Une poignée à la`CMFCTabCtrl`fenêtre tabbed ( ) à partir de laquelle la fenêtre de l’enfant MDI a été enlevée.|[out] Une poignée à la`CMFCTabCtrl`fenêtre tabbed ( ) à laquelle la fenêtre de l’enfant MDI a été insérée.|Ignoré.|
|AFX_WM_ON_PRESS_CLOSE_BUTTON|Envoyé à un `CDockablePane` parent de quand l’utilisateur clique sur le bouton **Close** sur la légende de la barre de contrôle.|Non utilisé.|Un pointeur à une vitre amarable sur laquelle l’utilisateur a cliqué sur le bouton **Close.**|VRAI si une vitre ne peut pas être fermée; autrement FALSE.|
|AFX_WM_ON_RENAME_TAB|Envoyé au parent de la fenêtre tabbed après que l’utilisateur a rebaptisé un onglet modifiable.|L’indice zéro de l’onglet renommé.|[out] Un pointeur à une chaîne qui contient le nouveau nom de l’onglet.|Nonzero si l’application traite ce message; le cadre supprimera `CMFCBaseTabCtrl::SetTabLabel`l’appel à .  Si zéro est `CMFCBaseTabCtrl::SetTabLabel` retourné, alors est appelé par le cadre.|
|AFX_WM_ON_RIBBON_CUSTOMIZE|Envoyé au cadre parent lorsque l’utilisateur commence la personnalisation. Traitez ce message si vous souhaitez afficher votre propre boîte de dialogue de personnalisation.|Non utilisé.|Un pointeur sur le contrôle du ruban à personnaliser.|Nonzero si l’application traite ce message et affiche sa propre boîte de dialogue de personnalisation. Si l’application renvoie zéro, le cadre affichera la boîte de dialogue de personnalisation intégrée.|
|AFX_WM_ON_TABGROUPMOUSEMOVE|À usage interne uniquement.|Non applicable.|Non applicable.|Non applicable.|
|AFX_WM_POSTSETPREVIEWFRAME|Envoyé pour informer le cadre principal que l’utilisateur a changé le mode aperçu d’impression|TRUE indique que le mode d’aperçu d’impression est défini. FALSE indique que le mode d’aperçu d’impression est désactivé.|Non utilisé.|Non utilisé.|
|AFX_WM_PROPERTY_CHANGED|Envoyé au propriétaire du contrôle`CMFCPropertyGridCtrl`du réseau de propriété ( ) lorsque l’utilisateur change la valeur de la propriété sélectionnée.|L’ID de contrôle de la liste des biens.|Un pointeur à`CMFCPropertyGridProperty`la propriété ( ) qui a changé.|Non utilisé.|
|AFX_WM_RESETCONTEXTMENU|Envoyé à la fenêtre du cadre principal lorsque l’utilisateur réinitialise le menu contextuelle lors de la personnalisation.|L’ID de ressource du menu contexte.|Un pointeur vers le `CMFCPopupMenu`menu contexte actuel, .|Non utilisé.|
|AFX_WM_RESETKEYBOARD|Le cadre envoie ce message à la fenêtre principale du cadre lorsque l’utilisateur réinitialise tous les accélérateurs de clavier lors de la personnalisation.|Non utilisé.|Non utilisé.|Non utilisé.|
|AFX_WM_RESETMENU|Le cadre envoie ce message au propriétaire du menu (une fenêtre de cadre) lorsque l’utilisateur réinitialise un menu d’image d’application lors de la personnalisation|L’ID de la ressource du menu.|Non utilisé.|Non utilisé.|
|AFX_WM_RESETPROMPT|Le cadre envoie ce message lorsque l’utilisateur réinitialise une barre d’outils à partir de la barre d’outils personnaliser la boîte de dialogue. Le gestionnaire par défaut affiche une boîte de message qui demande si l’utilisateur veut réinitialiser la barre d’outils.|Non utilisé.|Non utilisé.|Non utilisé.|
|AFX_WM_RESETTOOLBAR|Un `CMFCToolBar` objet envoie ce message lorsqu’une barre d’outils est restaurée à son état d’origine, c’est-à-dire chargée à partir des ressources. Traiter ce message pour réinsérer les boutons `CMFCToolbarButton`de barre d’outils dont les classes sont dérivées . Pour plus d’informations, consultez `CMFCToolbarComboBoxButton`.|L’id de ressource d’une barre d’outils dont l’état a été restauré.|Non utilisé.|Zéro.|
|AFX_WM_SHOWREGULARMENU|`CMFCToolbarMenuButton`l’objet envoie ce message à son propriétaire lorsque l’utilisateur clique sur un bouton de menu régulier. Traitez ce message chaque `CMFCToolbarMenuButton` fois que vous utilisez pour afficher un menu pop-up lorsque l’utilisateur clique sur un bouton.|L’ID de commande d’un bouton qui envoie le message.|Coordonnées d’écran du curseur. Le mot de faible ordre spécifie la x-coordonnées. Le mot de haute commande spécifie la y-coordinate.|Non utilisé.|
|AFX_WM_TOOLBARMENU|Envoyé à la fenêtre du cadre principal lorsque l’utilisateur libère le bouton droit d’une souris tandis que le pointeur de la souris est dans la zone client ou non-client d’une vitre.|Non utilisé.|Coordonnées d’écran du pointeur de la souris. Le mot de faible ordre spécifie la x-coordonnées. Le mot de haute commande spécifie la y-coordinate.|Zéro si l’application traite ce message; autrement, nonzero.|
|AFX_WM_UPDATETOOLTIPS|Envoyé à tous les propriétaires de bout à outils pour indiquer que leurs commandes de pointe à outils doivent être recréées.|Le type de contrôle qui devrait traiter ce message. Voir le tableau plus tard dans ce sujet pour une liste de valeurs possibles.|Non utilisé.|Non utilisé.|
|AFX_WM_WINDOW_HELP|`CMFCWindowsManagerDialog`envoie ce message à l’image parente lorsque l’utilisateur clique sur le bouton **Aide,** ou entre le mode d’aide en cliquant sur le bouton De légende **d’aide** ou la clé F1.|Non utilisé.|Un pointeur à `CMFCWindowsManagerDialog`l’exemple de .|Non utilisé.|

Le tableau suivant montre les valeurs pour le mot bas du paramètre *lParam* de la méthode AFX_WM_HSCROLL :

|||
|-|-|
|Value|Signification|
|SB_ENDSCROLL|L’utilisateur termine le parchemin.|
|SB_LEFT|L’utilisateur défile vers l’en haut à gauche.|
|SB_RIGHT|L’utilisateur défile vers le bas à droite.|
|SB_LINELEFT|L’utilisateur fait défiler la gauche d’une unité.|
|SB_LINERIGHT|L’utilisateur fait défiler à droite par une unité.|
|SB_PAGELEFT|L’utilisateur fait défiler la largeur de la fenêtre.|
|SB_PAGERIGHT|L’utilisateur défile à droite par la largeur de la fenêtre.|
|SB_THUMBPOSITION|L’utilisateur a traîné la boîte de défilement (pouce) et a libéré le bouton de la souris. Le mot de haute commande indique la position de la boîte de défilement à la fin de l’opération de traînée.|
|SB_THUMBTRACK|L’utilisateur fait glisser la case de défilement. Le message AFX_WM_ON_HSCROLL est envoyé à plusieurs reprises avec cette valeur jusqu’à ce que l’utilisateur libère le bouton de la souris. Le mot de haute commande indique la position à laquelle la boîte de défilement a été traîné.|

> [!NOTE]
> Le mot de haute commande du paramètre *lParam* spécifie la position actuelle de la boîte de défilement si le mot de bas ordre est SB_THUMBPOSITION ou SB_THUMBTRACK; sinon, ce mot n’est pas utilisé.

Le tableau suivant énumère les valeurs du drapeau pour le paramètre *lParam* du message AFX_WM_UPDATETOOLTIPS :

|||
|-|-|
|Indicateur|Value|
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
