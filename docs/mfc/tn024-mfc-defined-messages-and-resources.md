---
title: 'TN024 : messages et ressources définis par MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 24bcacd46b839babe9c9c89facb1cc56d18c0ee5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370350"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024 : messages et ressources définis par MFC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit les messages Windows internes et les formats de ressources utilisés par MFC. Ces informations expliquent la mise en œuvre du cadre et vous aideront à débogage de votre application. Pour les plus aventureux, même si toutes ces informations ne sont officiellement pas étayées, vous pouvez utiliser certaines de ces informations pour des implémentations avancées.

Cette note contient des détails de mise en œuvre privés MFC; tout le contenu est sujet à changement à l’avenir. Les messages Windows privés MFC ont un sens dans la portée d’une seule application, mais changeront à l’avenir pour contenir des messages à l’échelle du système.

La gamme de messages Windows privés MFC et les types de ressources se trouvent dans la gamme réservée « système » mise de côté par Microsoft Windows. Actuellement, tous les nombres dans les plages ne sont pas utilisés et, à l’avenir, de nouveaux numéros dans la gamme peuvent être utilisés. Les nombres actuellement utilisés peuvent être modifiés.

Les messages Windows privés MFC sont dans la gamme 0x360->0x37F.

Les types de ressources privées MFC sont de l’ordre de 0xF0->0xFF.

**Messages Windows privés MFC**

Ces messages Windows sont utilisés à la place des fonctions virtuelles de CMD où un accouplement relativement lâche est nécessaire entre les objets de fenêtre et où une fonction virtuelle CMD ne serait pas appropriée.

Ces messages Windows privés et les structures de paramètres associées sont déclarés dans l’en-tête privé MFC 'AFXPRIV. H'. Soyez averti que n’importe quel de vos codes qui inclut cet en-tête peut compter sur le comportement sans papiers et se brisera probablement dans les versions futures de MFC.

Dans le cas rare de la nécessité de gérer l’un de ces messages, vous devez utiliser la carte de ON_MESSAGE de message macro et gérer le message dans le format générique LRESULT/WPARAM/LPARAM.

**WM_QUERYAFXWNDPROC**

Ce message est envoyé à une fenêtre qui est en cours de création. Ceci est envoyé très tôt dans le processus de création comme une méthode pour déterminer si le WndProc est **AfxWndProc. AfxWndProc** revient 1.

|||
|-|-|
|wParam|Non utilisé|
|lParam|Non utilisé|
|retourne|1 si traité par **AfxWndProc**|

**WM_SIZEPARENT**

Ce message est envoyé par une fenêtre de cadre`CFrameWnd::OnSize` `CFrameWnd::RecalcLayout` à `CWnd::RepositionBars`ses enfants immédiats lors de la resizing ( appels qui appelle ) pour repositionner les barres de contrôle autour du côté du cadre. La structure AFX_SIZEPARENTPARAMS contient le rectangle de client actuel disponible du parent et un `DeferWindowPos` HDWP (qui peut être NULL) avec lequel appeler pour minimiser la repeindre.

|||
|-|-|
|wParam|Non utilisé|
|lParam|Adresse d’une structure AFX_SIZEPARENTPARAMS|
|retourne|Non utilisé (0)|

Ignorer le message indique que la fenêtre ne prend pas part à la mise en page.

**WM_SETMESSAGESTRING**

Ce message est envoyé à une fenêtre de cadre pour lui demander de mettre à jour la ligne de message dans la barre d’état. Un ID de chaîne ou un LPCSTR peut être spécifié (mais pas les deux).

|||
|-|-|
|wParam|Id de chaîne (ou zéro)|
|lParam|LPCSTR pour la chaîne (ou NULL)|
|retourne|Non utilisé (0)|

**WM_IDLEUPDATECMDUI**

Ce message est envoyé en temps d’inactivité pour implémenter la mise à jour en temps d’inactivité des gestionnaires d’interface utilisateur de commande de mise à jour. Si la fenêtre (généralement une barre de contrôle) `CCmdUI` gère le message, elle crée `CCmdUI::DoUpdate` un objet (ou un objet d’une classe dérivée) et appelle pour chacun des « éléments » de la fenêtre. Cela permettra de vérifier à son tour un gestionnaire de ON_UPDATE_COMMAND_UI pour les objets de la chaîne de commande-gestionnaire.

|||
|-|-|
|wParam|BOOL bDisableIfNoHandler|
|lParam|Non utilisé (0)|
|retourne|Non utilisé (0)|

*bDisableIfNoHandler* n’est pas unzero pour désactiver l’objet d’interface utilisateur s’il n’y a ni ON_UPDATE_COMMAND_UI ni un gestionnaire de ON_COMMAND.

**WM_EXITHELPMODE**

Ce message est `CFrameWnd` affiché sur un mode d’aide sensible au contexte de sortie. La réception de ce message met fin `CFrameWnd::OnContextHelp`à la boucle modale commencée par .

|||
|-|-|
|wParam|Non utilisé (0)|
|lParam|Non utilisé (0)|
|retourne|Non utilisé|

**WM_INITIALUPDATE**

Ce message est envoyé par le modèle de document à tous les descendants d’une fenêtre de cadre lorsqu’il est sécuritaire pour eux de faire leur mise à jour initiale. Il est adapté `CView::OnInitialUpdate` à un appel, `CWnd`mais peut être utilisé dans d’autres classes dérivées pour d’autres mises à jour à un coup.

|||
|-|-|
|wParam|Non utilisé (0)|
|lParam|Non utilisé (0)|
|retourne|Non utilisé (0)|

**WM_RECALCPARENT**

Ce message est envoyé par une vue à `GetParent`sa fenêtre parente (obtenue via ) pour `RecalcLayout`forcer une recalcul de mise en page (généralement, le parent appellera ). Ceci est utilisé dans les applications de serveur OLE où il est nécessaire pour le cadre de croître en taille que la taille totale de la vue augmente.

Si la fenêtre parente traite ce message, il doit retourner VRAI et remplir le RECT passé en lParam avec la nouvelle taille de la zone client. Ceci est `CScrollView` utilisé pour manipuler correctement les barres de défilement (placez-les alors à l’extérieur de la fenêtre lorsqu’ils sont ajoutés) lorsqu’un objet serveur est activé en place.

|||
|-|-|
|wParam|Non utilisé (0)|
|lParam|LPRECT rectClient, peut être NULL|
|retourne|VRAI si le nouveau rectangle client est revenu, FALSE autrement|

**WM_SIZECHILD**

Ce message est `COleResizeBar` envoyé par la `GetOwner`fenêtre de son propriétaire (via ) lorsque l’utilisateur resize la barre de resize avec les poignées de resize. `COleIPFrameWnd`répond à ce message en essayant de repositionner la fenêtre de cadre comme l’utilisateur l’a demandé.

Le nouveau rectangle, indiqué dans les coordonnées des clients par rapport à la fenêtre de cadre qui contient la barre de resize, est pointé par lParam.

|||
|-|-|
|wParam|Non utilisé (0)|
|lParam|LPRECT rectNew|
|retourne|Non utilisé (0)|

**WM_DISABLEMODAL**

Ce message est envoyé à toutes les fenêtres pop-up appartenant à une fenêtre de cadre qui est désactivée. La fenêtre de cadre utilise le résultat pour déterminer s’il faut désactiver ou non la fenêtre pop-up.

Vous pouvez l’utiliser pour effectuer un traitement spécial dans votre fenêtre pop-up lorsque le cadre entre dans un état modal ou pour garder certaines fenêtres pop-up de devenir désactivé. Tooltips utiliser ce message pour se détruire lorsque la fenêtre de cadre va dans un état modal, par exemple.

|||
|-|-|
|wParam|Non utilisé (0)|
|lParam|Non utilisé (0)|
|retourne|Non-zéro pour **ne PAS** désactiver la fenêtre, 0 indique que la fenêtre sera désactivée|

**WM_FLOATSTATUS**

Ce message est envoyé à toutes les fenêtres pop-up appartenant à une fenêtre de cadre lorsque le cadre est activé ou désactivé par une autre fenêtre de cadre de haut niveau. Ceci est utilisé par la mise `CMiniFrameWnd`en œuvre de MFS_SYNCACTIVE en , pour maintenir l’activation de ces fenêtres pop-up en synchronisation avec l’activation de la fenêtre de cadre de niveau supérieur.

|||
|-|-|
|wParam|L'une des valeurs suivantes :<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|Non utilisé (0)|

La valeur de retour doit être non nulle si FS_SYNCACTIVE est réglée et la fenêtre syncronise son activation avec le cadre parent. `CMiniFrameWnd`retourne non-zéro lorsque le style est réglé sur MFS_SYNCACTIVE.

Pour plus d’informations, `CMiniFrameWnd`voir la mise en œuvre de .

## <a name="wm_activatetoplevel"></a>WM_ACTIVATETOPLEVEL

Ce message est envoyé à une fenêtre de haut niveau lorsqu’une fenêtre de son « groupe de haut niveau » est activée ou désactivée. Une fenêtre fait partie d’un groupe de haut niveau s’il s’agit d’une fenêtre de haut niveau (pas de parent ou de propriétaire), ou si elle appartient à une telle fenêtre. Ce message est similaire en usage pour WM_ACTIVATEAPP, mais fonctionne dans des situations où les fenêtres appartenant à différents processus sont mélangées dans une hiérarchie de fenêtre unique (commune dans les applications OLE).

## <a name="wm_commandhelp-wm_helphittest-wm_exithelpmode"></a>WM_COMMANDHELP, WM_HELPHITTEST, WM_EXITHELPMODE

Ces messages sont utilisés dans la mise en œuvre de l’aide sensible au contexte. Veuillez consulter [la note technique 28](../mfc/tn028-context-sensitive-help-support.md) pour plus d’informations.

## <a name="mfc-private-resource-formats"></a>Formats de ressources privées MFC

À l’heure actuelle, MFC définit deux formats de ressources privées : RT_TOOLBAR et RT_DLGINIT.

## <a name="rt_toolbar-resource-format"></a>Format de ressources RT_TOOLBAR

La barre d’outils par défaut fournie par AppWizard est basée sur une ressource personnalisée RT_TOOLBAR, qui a été introduite dans MFC 4.0. Vous pouvez modifier cette ressource à l’aide de l’éditeur Toolbar.

## <a name="rt_dlginit-resource-format"></a>Format de ressources RT_DLGINIT

Un format de ressources privées MFC est utilisé pour stocker des informations supplémentaires de initialisation de dialogue. Cela inclut les cordes initiales stockées dans une boîte combo. Le format de cette ressource n’est pas conçu pour être édité manuellement, mais est géré par Visual C.

Les ressources visuelles et de cette RT_DLGINIT ne sont pas tenues d’utiliser les caractéristiques connexes de MFC puisqu’il existe une alternative à l’utilisation de l’information contenue dans la ressource. L’utilisation de Visual CMD facilite beaucoup l’écriture, l’entretien et la traduction de votre application à long terme.

La structure de base d’une ressource RT_DLGINIT est la suivante :

```
+---------------+    \
| Control ID    |   UINT             |
+---------------+    |
| Message #     |   UINT             |
+---------------+    |
|length of data |   DWORD            |
+---------------+    |   Repeated
|   Data        |   Variable Length  |   for each control
|   ...         |   and Format       |   and message
+---------------+    /
|     0         |   BYTE
+---------------+
```

Une section répétée contient l’ID de contrôle pour envoyer le message à, le Message à envoyer (un message Windows normal) et une longueur variable de données. Le message Windows est envoyé sous une forme :

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

Il s’agit d’un format très général, permettant tous les messages Windows et le contenu de données. L’éditeur de ressources Visual CMD et MFC ne prennent en charge qu’un sous-ensemble limité de messages Windows : CB_ADDSTRING pour les choix de liste initiaux pour les boîtes combo (les données sont une chaîne de texte).

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
