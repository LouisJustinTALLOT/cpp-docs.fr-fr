---
title: 'TN024 : Messages définis par MFC et ressources | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a21ae615a3f4c644f6f0aa7c8f1306378a00ae5c
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957183"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024 : messages et ressources définis par MFC
> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.  
  
 Cette note décrit les messages internes de Windows et les formats de ressources utilisées par MFC. Ces informations explique l’implémentation de l’infrastructure et vous aide à déboguer votre application. Pour aventureux, même si toutes ces informations sont officiellement non pris en charge, vous pouvez utiliser certaines de ces informations pour les implémentations avancées.  
  
 Cette note contient les détails d’implémentation privée de MFC ; tout le contenu est susceptibles de changer dans le futur. Les messages Windows privés MFC ont une signification dans la portée d’une application uniquement, mais changeront dans le futur pour contenir les messages à l’échelle du système.  
  
 Les messages Windows privés de plage de MFC et les types de ressources sont dans la plage réservée « système » réserver par Microsoft Windows. Qui ne sont pas tous les nombres dans les plages sont utilisés et, à l’avenir, les nouveaux numéros de la plage peuvent être utilisés. Les numéros actuellement utilisées peuvent être modifiées.  
  
 Windows privés de MFC sont des messages dans la plage 0x360 -> 0x37F.  
  
 Ressource privée de MFC sont des types dans la plage 0xF0 -> 0xFF.  
  
 **Messages Windows MFC privé**  
  
 Ces messages Windows sont utilisés à la place des fonctions virtuelles C++ où relativement faible couplage est requis entre les objets de la fenêtre et où une fonction virtuelle C++ ne serait pas appropriée.  
  
 Ces messages Windows privés et les structures de paramètre associé sont déclarés dans l’en-tête privé MFC ' AFXPRIV. H'. Sachez que votre code qui inclut cet en-tête peut reposer sur comportement non documentée et seront probablement rompues dans les futures versions de MFC.  
  
 Dans le cas rare de devoir gérer un de ces messages, vous devez utiliser la macro de mappage de message ON_MESSAGE et gérer le message au format LRESULT/WPARAM/LPARAM générique.  
  
 **WM_QUERYAFXWNDPROC**  
  
 Ce message est envoyé à une fenêtre qui est en cours de création. Ceci est envoyé très tôt dans le processus de création en tant qu’une méthode permettant de déterminer si WndProc est **AfxWndProc. AfxWndProc** renvoie la valeur 1.  
  
|||  
|-|-|  
|wParam|Non utilisé|  
|lParam|Non utilisé|  
|retourne|1 si le traitement par **AfxWndProc**|  
  
 **WM_SIZEPARENT**  
  
 Ce message est envoyé par une fenêtre frame à ses enfants immédiats lors du redimensionnement (`CFrameWnd::OnSize` appelle `CFrameWnd::RecalcLayout` qui appelle `CWnd::RepositionBars`) pour repositionner les barres de contrôles autour du côté de l’image. La structure AFX_SIZEPARENTPARAMS contient le rectangle client disponible actuel du parent et un HDWP (qui peut être NULL) avec laquelle appeler `DeferWindowPos` afin de réduire la mise à jour.  
  
|||  
|-|-|  
|wParam|Non utilisé|  
|lParam|Adresse d’une structure AFX_SIZEPARENTPARAMS|  
|retourne|Non utilisé (0)|  
  
 Ignorer le message indique que la fenêtre ne font partie de la mise en page.  
  
 **WM_SETMESSAGESTRING**  
  
 Ce message est envoyé à une fenêtre frame pour lui demander de mettre à jour la ligne du message dans la barre d’état. Un ID de chaîne ou d’un LPCSTR peut être spécifié (mais pas les deux).  
  
|||  
|-|-|  
|wParam|Chaîne d’ID (ou zéro)|  
|lParam|LPCSTR pour la chaîne (ou NULL)|  
|retourne|Non utilisé (0)|  
  
 **WM_IDLEUPDATECMDUI**  
  
 Ce message est envoyé dans le temps d’inactivité pour implémenter la mise à jour de la durée d’inactivité de gestionnaires d’interface utilisateur de commande de mise à jour. Si la fenêtre (généralement une barre de contrôle) gère le message, il crée un `CCmdUI` objet (ou un objet d’une classe dérivée) et appelez `CCmdUI::DoUpdate` pour chacun des « éléments » dans la fenêtre. Il vérifie à son tour un gestionnaire ON_UPDATE_COMMAND_UI pour les objets dans la chaîne du Gestionnaire de commandes.  
  
|||  
|-|-|  
|wParam|BOOL bDisableIfNoHandler|  
|lParam|Non utilisé (0)|  
|retourne|Non utilisé (0)|  
  
 *bDisableIfNoHandler* est différente de zéro pour désactiver l’objet d’interface utilisateur, s’il existe un ON_UPDATE_COMMAND_UI, ni un gestionnaire ON_COMMAND.  
  
 **WM_EXITHELPMODE**  
  
 Ce message est publié dans une `CFrameWnd` mode à quitter sensibles au contexte d’aide. L’accusé de réception de ce message termine la boucle modale de démarré par `CFrameWnd::OnContextHelp`.  
  
|||  
|-|-|  
|wParam|Non utilisé (0)|  
|lParam|Non utilisé (0)|  
|retourne|Non utilisé|  
  
 **WM_INITIALUPDATE**  
  
 Ce message est envoyé à tous les descendants d’une fenêtre frame par le modèle de document lorsqu’il est possible de faire de leur mise à jour initiale. Il est mappé à un appel à `CView::OnInitialUpdate` mais peut être utilisé dans d’autres `CWnd`-dérivées des classes pour les autres Shot mise à jour.  
  
|||  
|-|-|  
|wParam|Non utilisé (0)|  
|lParam|Non utilisé (0)|  
|retourne|Non utilisé (0)|  
  
 **WM_RECALCPARENT**  
  
 Ce message est envoyé par une vue à sa fenêtre parente (obtenus via `GetParent`) pour forcer un recalcul de disposition (en règle générale, le parent appellera `RecalcLayout`). Il est utilisé dans les applications serveur OLE lorsqu’il est nécessaire pour le frame à croître à mesure qu’augmente de taille totale de la vue.  
  
 Si la fenêtre parente traite ce message, il doit retourner la valeur TRUE et remplir le rectangle passé dans lParam avec la nouvelle taille de la zone cliente. Cela est utilisé dans `CScrollView` pour traiter correctement les barres de défilement (place ensuite à l’extérieur de la fenêtre lorsqu’ils sont ajoutés) quand un objet serveur est activé sur place.  
  
|||  
|-|-|  
|wParam|Non utilisé (0)|  
|lParam|LPRECT rectClient, peut être NULL|  
|retourne|TRUE si un nouveau client rectangle renvoyé, FALSE dans le cas contraire|  
  
 **WM_SIZECHILD**  
  
 Ce message est envoyé par `COleResizeBar` à sa fenêtre propriétaire (via `GetOwner`) lorsque l’utilisateur redimensionne la barre de redimensionnement avec les poignées de redimensionnement. `COleIPFrameWnd` répond à ce message en tentant de repositionner la fenêtre frame que l’utilisateur a demandé.  
  
 Le nouveau rectangle, donné en coordonnées clientes par rapport à la fenêtre frame qui contient la barre de redimensionnement est pointé par lParam.  
  
|||  
|-|-|  
|wParam|Non utilisé (0)|  
|lParam|LPRECT rectNew|  
|retourne|Non utilisé (0)|  
  
 **WM_DISABLEMODAL**  
  
 Ce message est envoyé à toutes les fenêtres publicitaires appartenant à une fenêtre frame qui est en cours de désactivation. La fenêtre frame utilise le résultat pour déterminer ou non désactiver la fenêtre contextuelle.  
  
 Vous pouvez l’utiliser pour effectuer un traitement spécial dans votre fenêtre indépendante quand le frame entre dans un état modal ou conserver certaines fenêtres publicitaires à partir de la mise en route désactivé. Info-bulles utilisent ce message pour détruire eux-mêmes lorsque la fenêtre frame passe à l’état modal, par exemple.  
  
|||  
|-|-|  
|wParam|Non utilisé (0)|  
|lParam|Non utilisé (0)|  
|retourne|Non nul à **pas** désactiver la fenêtre, de 0 indique que la fenêtre va être désactivée.|  
  
 **WM_FLOATSTATUS**  
  
 Ce message est envoyé à toutes les fenêtres publicitaires appartenant à une fenêtre frame lorsque le frame est activé ou désactivé par une autre fenêtre frame de niveau supérieur. Ceci est utilisé par l’implémentation de MFS_SYNCACTIVE dans `CMiniFrameWnd`, l’activation de ces fenêtres publicitaires de synchroniser avec l’activation de la fenêtre frame de niveau supérieur.  
  
|||  
|-|-|  
|wParam|Est une des valeurs suivantes :<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|  
|lParam|Non utilisé (0)|  
  
 La valeur de retour doit être différent de zéro si FS_SYNCACTIVE n’est définie et la fenêtre synchronise son activation avec le frame parent. `CMiniFrameWnd` retourne zéro lorsque le style est défini sur MFS_SYNCACTIVE.  
  
 Pour plus d’informations, consultez l’implémentation de `CMiniFrameWnd`.  
  
## <a name="wmactivatetoplevel"></a>WM_ACTIVATETOPLEVEL  
 Ce message est envoyé à une fenêtre de niveau supérieur quand une fenêtre dans son « groupe de niveau supérieur » est activée ou désactivée. Une fenêtre fait partie d’un groupe de niveau supérieur s’il s’agit d’une fenêtre de niveau supérieur (aucun parent ou le propriétaire), ou il appartienne à une telle fenêtre. Ce message est semblable aux WM_ACTIVATEAPP, mais fonctionne dans les situations où windows appartenant à différents processus sont combinés dans une hiérarchie de la même fenêtre (courante dans les applications OLE).  
  
## <a name="wmcommandhelp-wmhelphittest-wmexithelpmode"></a>WM_COMMANDHELP, WM_HELPHITTEST, WM_EXITHELPMODE  
 Ces messages sont utilisés dans l’implémentation de l’aide contextuelle. Reportez-vous à [Technical Note 28](../mfc/tn028-context-sensitive-help-support.md) pour plus d’informations.  
  
## <a name="mfc-private-resource-formats"></a>Formats de ressources MFC privé  
 Actuellement, MFC définit deux formats de ressource privée : RT_TOOLBAR et RT_DLGINIT.  
  
## <a name="rttoolbar-resource-format"></a>Format de la ressource RT_TOOLBAR  
 La barre d’outils par défaut fourni par AppWizard est basée sur une ressource personnalisée RT_TOOLBAR, qui a été introduite dans MFC 4.0. Vous pouvez modifier cette ressource à l’aide de l’éditeur de la barre d’outils.  
  
## <a name="rtdlginit-resource-format"></a>Format de la ressource RT_DLGINIT  
 Un format de ressource privée MFC est utilisé pour stocker les informations d’initialisation supplémentaire de boîte de dialogue. Cela inclut les chaînes initiales stockées dans une zone de liste déroulante. Le format de cette ressource n’est pas conçu pour être modifié manuellement, mais est géré par Visual C++.  
  
 Visual C++ et cette ressource RT_DLGINIT ne sont pas obligés d’utiliser les fonctionnalités de MFC, car il existe également des API à l’aide des informations de la ressource. À l’aide de Visual C++ rend beaucoup plus facile à écrire, maintenir et convertir votre application à long terme.  
  
 La structure de base d’une ressource RT_DLGINIT est la suivante :  
  
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
  
 Une section répétée contient l’ID de contrôle pour envoyer le message, le Message # pour envoi (un message normal de Windows) et une longueur variable de données. Le message Windows est envoyé dans un formulaire :  
  
```  
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```  
  
 Il s’agit d’un format très général, ce qui permet de tous les messages Windows et le contenu des données. L’éditeur de ressources Visual C++ et MFC prennent uniquement en charge un sous-ensemble des messages Windows : CB_ADDSTRING pour les options de liste initiales pour les zones de liste déroulante (les données sont une chaîne de texte).  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

