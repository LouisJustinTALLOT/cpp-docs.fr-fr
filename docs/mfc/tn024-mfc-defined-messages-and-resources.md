---
title: 'TN024 : Ressources et les Messages définis par MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.messages
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 029177821d37d5d26abe0b39ea1581e8a5ad602b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278130"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024 : Ressources et les Messages définis par MFC

> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit les messages Windows internes et les formats de ressources utilisées par MFC. Ces informations explique l’implémentation de l’infrastructure et vous aider dans le débogage de votre application. Pour aventureux, même si toutes ces informations sont officiellement pris en charge, vous pouvez utiliser certaines de ces informations pour les implémentations avancées.

Cette note contient des détails d’implémentation privés MFC ; tout le contenu est susceptibles de changer à l’avenir. Les messages Windows privés MFC ont une signification dans la portée d’une application uniquement, mais changeront à l’avenir pour qu’il contienne des messages de l’échelle du système.

Les messages Windows privés de plage de MFC et les types de ressources sont dans la plage réservée « système » gelées par Microsoft Windows. Actuellement pas tous les nombres dans les plages sont utilisés et, à l’avenir, les nouveaux numéros dans la plage peuvent être utilisés. Les numéros de cours d’utilisation peuvent être modifiées.

Windows privés de MFC sont des messages dans la plage 0x360 -> 0x37F.

Ressource privée MFC sont des types dans la plage 0xF0 -> 0xFF.

**Messages Windows privés MFC**

Ces messages de Windows sont utilisés à la place des fonctions virtuelles C++ où relativement couplage lâche est requis entre les objets de fenêtre et où une fonction virtuelle C++ ne serait pas appropriée.

Ces messages Windows privés et les structures de paramètre associé sont déclarés dans l’en-tête privé MFC ' AFXPRIV. H'. Être averti que votre code qui inclut cet en-tête peut reposer sur des comportement non documenté et seront probablement rompues dans les futures versions de MFC.

Dans le cas rare d’avoir à gérer l’un de ces messages, vous devez utiliser la macro de mappage de message ON_MESSAGE et gérer le message au format LRESULT/WPARAM/LPARAM générique.

**WM_QUERYAFXWNDPROC**

Ce message est envoyé à une fenêtre qui est en cours de création. Ceci est envoyé très tôt dans le processus de création en tant que méthode permettant de déterminer si WndProc est **AfxWndProc. AfxWndProc** retourne 1.

|||
|-|-|
|wParam|Non utilisé|
|lParam|Non utilisé|
|retourne|1 si traitée par **AfxWndProc**|

**WM_SIZEPARENT**

Ce message est envoyé par une fenêtre frame à ses enfants immédiats lors du redimensionnement (`CFrameWnd::OnSize` appels `CFrameWnd::RecalcLayout` qui appelle `CWnd::RepositionBars`) à repositionner les barres de contrôles autour du côté du frame. La structure AFX_SIZEPARENTPARAMS contient le rectangle client disponible actuel du parent et un HDWP (qui peut être NULL) avec laquelle appeler `DeferWindowPos` afin de réduire la mise à jour.

|||
|-|-|
|wParam|Non utilisé|
|lParam|Adresse d’une structure AFX_SIZEPARENTPARAMS|
|retourne|Pas utilisé (0)|

Ignore le message indique que la fenêtre ne participez à la disposition.

**WM_SETMESSAGESTRING**

Ce message est envoyé à une fenêtre frame pour lui demander de mettre à jour de la ligne de message dans la barre d’état. Un ID de chaîne ou un LPCSTR peut être spécifié (mais pas les deux).

|||
|-|-|
|wParam|Chaîne d’ID (ou zéro)|
|lParam|LPCSTR pour la chaîne (ou NULL)|
|retourne|Pas utilisé (0)|

**WM_IDLEUPDATECMDUI**

Ce message est envoyé dans le temps d’inactivité pour implémenter la mise à jour de la durée d’inactivité de gestionnaires de l’interface utilisateur de commande de mise à jour. Si la fenêtre (généralement une barre de contrôle) gère le message, il crée un `CCmdUI` objet (ou un objet d’une classe dérivée) et appelez `CCmdUI::DoUpdate` pour chacun des « éléments » dans la fenêtre. Ce processus vérifie à son tour un gestionnaire ON_UPDATE_COMMAND_UI pour les objets dans la chaîne de gestionnaire de commandes.

|||
|-|-|
|wParam|BOOL bDisableIfNoHandler|
|lParam|Pas utilisé (0)|
|retourne|Pas utilisé (0)|

*bDisableIfNoHandler* est différent de zéro pour désactiver l’objet d’interface utilisateur s’il n’est ni un ON_UPDATE_COMMAND_UI, ni un gestionnaire ON_COMMAND.

**WM_EXITHELPMODE**

Ce message est publié sur un `CFrameWnd` mode qui pour quitter sensible au contexte d’aide. L’accusé de réception de ce message termine la boucle modale de démarrage par `CFrameWnd::OnContextHelp`.

|||
|-|-|
|wParam|Pas utilisé (0)|
|lParam|Pas utilisé (0)|
|retourne|Non utilisé|

**WM_INITIALUPDATE**

Ce message est envoyé à tous les descendants d’une fenêtre frame par le modèle de document lorsqu’il est possible de faire leur mise à jour initiale. Il est mappé à un appel à `CView::OnInitialUpdate` mais peut être utilisé dans d’autres `CWnd`-classes autres la mise à jour One-Shot dérivées.

|||
|-|-|
|wParam|Pas utilisé (0)|
|lParam|Pas utilisé (0)|
|retourne|Pas utilisé (0)|

**WM_RECALCPARENT**

Ce message est envoyé par une vue à sa fenêtre parente (obtenu via `GetParent`) pour forcer un recalcul de disposition (en règle générale, le parent appellera `RecalcLayout`). Cela est utilisé dans les applications serveur OLE où il est nécessaire pour le frame de croître en taille au fur et à taille totale de la vue.

Si la fenêtre parente traite ce message, il doit retourner la valeur TRUE et remplir le rectangle passé dans lParam avec la nouvelle taille de la zone cliente. Cela est utilisé dans `CScrollView` à gérer correctement les barres de défilement (place ensuite à l’extérieur de la fenêtre lorsqu’ils sont ajoutés) quand un objet serveur est activé sur place.

|||
|-|-|
|wParam|Pas utilisé (0)|
|lParam|LPRECT rectClient, peut être NULL|
|retourne|TRUE si le nouveau client rectangle renvoyé, FALSE sinon|

**WM_SIZECHILD**

Ce message est envoyé par `COleResizeBar` à sa fenêtre propriétaire (via `GetOwner`) lorsque l’utilisateur redimensionne la barre de redimensionnement avec les poignées de redimensionnement. `COleIPFrameWnd` répond à ce message en essayant de repositionner la fenêtre frame que l’utilisateur a demandé.

Le nouveau rectangle, étant donné dans les coordonnées clientes par rapport à la fenêtre frame qui contient la barre de redimensionnement est pointé par le lParam.

|||
|-|-|
|wParam|Pas utilisé (0)|
|lParam|LPRECT rectNew|
|retourne|Pas utilisé (0)|

**WM_DISABLEMODAL**

Ce message est envoyé à toutes les fenêtres publicitaires appartenant à une fenêtre frame qui est en cours de désactivation. La fenêtre frame utilise le résultat pour déterminer s’il faut désactiver la fenêtre contextuelle.

Vous pouvez utiliser cela pour effectuer un traitement spécial dans votre fenêtre contextuelle lorsque le frame entre dans un état modal ou empêcher certaines fenêtres publicitaires de soit désactivé. Info-bulles utilisent ce message pour détruire eux-mêmes lorsque la fenêtre frame passe en état modal, par exemple.

|||
|-|-|
|wParam|Pas utilisé (0)|
|lParam|Pas utilisé (0)|
|retourne|Valeur différente de zéro pour **pas** désactiver la fenêtre, de 0 indique que la fenêtre va être désactivée.|

**WM_FLOATSTATUS**

Ce message est envoyé à toutes les fenêtres publicitaires appartenant à une fenêtre frame lorsque le frame est soit activé ou désactivé par une autre fenêtre frame de niveau supérieur. Ceci est utilisé par l’implémentation de MFS_SYNCACTIVE dans `CMiniFrameWnd`, pour synchroniser l’activation de ces fenêtres publicitaires avec l’activation de la fenêtre frame de niveau supérieur.

|||
|-|-|
|wParam|Est une des valeurs suivantes :<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|Pas utilisé (0)|

La valeur de retour doit être différente de zéro si FS_SYNCACTIVE n’est définie et la fenêtre synchronise son activation avec le frame parent. `CMiniFrameWnd` retourne zéro lorsque le style est défini sur MFS_SYNCACTIVE.

Pour plus d’informations, consultez l’implémentation de `CMiniFrameWnd`.

## <a name="wmactivatetoplevel"></a>WM_ACTIVATETOPLEVEL

Ce message est envoyé à une fenêtre de niveau supérieur lorsqu’une fenêtre dans son « groupe de niveau supérieur » est activée ou désactivée. Une fenêtre fait partie d’un groupe de niveau supérieur s’il est une fenêtre de niveau supérieur (aucun parent ou le propriétaire), ou il appartient à une telle fenêtre. Ce message est similaire en cours d’utilisation à WM_ACTIVATEAPP, mais fonctionne dans les situations où windows appartenant à des processus différents sont combinés dans une hiérarchie unique de fenêtre (courante dans les applications OLE).

## <a name="wmcommandhelp-wmhelphittest-wmexithelpmode"></a>WM_COMMANDHELP, WM_HELPHITTEST, WM_EXITHELPMODE

Ces messages sont utilisés dans l’implémentation de l’aide contextuelle. Reportez-vous à [Note technique 28](../mfc/tn028-context-sensitive-help-support.md) pour plus d’informations.

## <a name="mfc-private-resource-formats"></a>Formats de ressources MFC privé

Actuellement, MFC définit deux formats de ressource privée : RT_TOOLBAR et RT_DLGINIT.

## <a name="rttoolbar-resource-format"></a>Format de la ressource RT_TOOLBAR

La barre d’outils par défaut fourni par AppWizard est basée sur une ressource personnalisée RT_TOOLBAR, qui a été introduite dans 4.0 de MFC. Vous pouvez modifier cette ressource à l’aide de l’éditeur de la barre d’outils.

## <a name="rtdlginit-resource-format"></a>Format de la ressource RT_DLGINIT

Un format de ressource privée MFC est utilisé pour stocker les informations d’initialisation de boîte de dialogue supplémentaires. Cela inclut les chaînes initiales stockées dans une zone de liste déroulante. Le format de cette ressource n’est pas conçu pour être modifié manuellement, mais est géré par Visual C++.

Visual C++ et cette ressource RT_DLGINIT ne sont pas requis pour utiliser les fonctionnalités de MFC dans la mesure où il existe alternative d’API à l’aide des informations dans la ressource. À l’aide de Visual C++ rend beaucoup plus facile à écrire, maintenir et traduire votre application sur le long terme.

La structure de base d’une ressource RT_DLGINIT est comme suit :

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

Une section répétée contient l’ID de contrôle pour envoyer le message, le Message # pour l’envoi (un message normal de Windows) et une longueur variable de données. Le message Windows est envoyé dans un formulaire :

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

Il s’agit d’un format très général, ce qui permet de n’importe quel les messages Windows et le contenu des données. L’éditeur de ressources Visual C++ et MFC prennent uniquement en charge un sous-ensemble limité de messages de Windows : CB_ADDSTRING pour les options de liste initiales pour les zones de liste déroulante (les données sont une chaîne de texte).

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
