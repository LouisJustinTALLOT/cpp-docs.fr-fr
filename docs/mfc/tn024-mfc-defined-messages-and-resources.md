---
description: 'En savoir plus sur : TN024 : messages et ressources MFC-Defined'
title: 'TN024 : messages et ressources définis par MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 7ead4d72588b9acae125cbe90be67d1e03230de8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215753"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024 : messages et ressources définis par MFC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit les formats des messages et des ressources Windows internes utilisés par MFC. Ces informations décrivent l’implémentation de l’infrastructure et vous aideront à déboguer votre application. Pour aventureux, même si toutes ces informations ne sont pas officiellement prises en charge, vous pouvez utiliser certaines de ces informations pour des implémentations avancées.

Cette note contient les détails de l’implémentation privée MFC. tout le contenu est susceptible d’être modifié à l’avenir. Les messages Windows privés MFC n’ont pas la même signification dans l’étendue d’une application, mais seront modifiés à l’avenir pour contenir des messages au niveau du système.

La plage des messages Windows privés et des types de ressources MFC se trouve dans la plage « système » réservée, définie par Microsoft Windows. Actuellement, tous les nombres des plages ne sont pas utilisés et, à l’avenir, de nouveaux nombres dans la plage peuvent être utilisés. Les nombres actuellement utilisés peuvent être modifiés.

Les messages Windows privés MFC se trouvent dans la plage 0x360->0x37F.

Les types de ressources privées MFC se trouvent dans la plage 0xF0->0xFF.

**Messages Windows privés MFC**

Ces messages Windows sont utilisés à la place des fonctions virtuelles C++ où un couplage relativement faible est requis entre les objets de fenêtre et où une fonction virtuelle C++ n’est pas appropriée.

Ces messages Windows privés et les structures de paramètres associées sont déclarés dans l’en-tête privé MFC’AFXPRIV. H'. Soyez averti que l’un de votre code qui comprend cet en-tête peut reposer sur un comportement non documenté et sera probablement rompu dans les futures versions de MFC.

Dans les rares cas où il est nécessaire de gérer l’un de ces messages, vous devez utiliser la macro de table des messages ON_MESSAGE et gérer le message au format LRESULT/WPARAM/LPARAM générique.

**WM_QUERYAFXWNDPROC**

Ce message est envoyé à une fenêtre en cours de création. Cela est envoyé très tôt dans le processus de création comme méthode permettant de déterminer si WndProc est **AfxWndProc. AfxWndProc** retourne 1.

| Paramètres et valeur de retour | Description |
|-|-|
|wParam|Non utilisé|
|lParam|Non utilisé|
|retourne|1 en cas de traitement par **AfxWndProc**|

**WM_SIZEPARENT**

Ce message est envoyé par une fenêtre frame à ses enfants immédiats pendant le redimensionnement ( `CFrameWnd::OnSize` appels `CFrameWnd::RecalcLayout` qui appellent `CWnd::RepositionBars` ) pour repositionner les barres de contrôle sur le côté du frame. La structure AFX_SIZEPARENTPARAMS contient le rectangle client actuellement disponible du parent et un HDWP (qui peut être NULL) avec lequel appeler `DeferWindowPos` pour réduire le redessin.

| Paramètres et valeur de retour | Description |
|-|-|
|wParam|Non utilisé|
|lParam|Adresse d’une structure AFX_SIZEPARENTPARAMS|
|retourne|Non utilisé (0)|

Si le message est ignoré, cela signifie que la fenêtre ne participe pas à la mise en page.

**WM_SETMESSAGESTRING**

Ce message est envoyé à une fenêtre frame pour lui demander de mettre à jour la ligne de message dans la barre d’État. Vous pouvez spécifier un ID de chaîne ou un LPCSTR (mais pas les deux).

| Paramètres et valeur de retour | Description |
|-|-|
|wParam|ID de chaîne (ou zéro)|
|lParam|LPCSTR pour la chaîne (ou NULL)|
|retourne|Non utilisé (0)|

**WM_IDLEUPDATECMDUI**

Ce message est envoyé dans un délai d’inactivité afin d’implémenter la mise à jour inactive des gestionnaires d’interface utilisateur Update-Command. Si la fenêtre (généralement une barre de contrôle) gère le message, elle crée un `CCmdUI` objet (ou un objet d’une classe dérivée) et appelle `CCmdUI::DoUpdate` pour chacun des « éléments » dans la fenêtre. Cela permet de vérifier un gestionnaire de ON_UPDATE_COMMAND_UI pour les objets dans la chaîne du gestionnaire de commandes.

| Paramètres et valeur de retour | Description |
|-|-|
|wParam|BOOL bDisableIfNoHandler|
|lParam|Non utilisé (0)|
|retourne|Non utilisé (0)|

*bDisableIfNoHandler* est différent de zéro pour désactiver l’objet d’interface utilisateur s’il n’existe ni ON_UPDATE_COMMAND_UI ni un gestionnaire de ON_COMMAND.

**WM_EXITHELPMODE**

Ce message est publié dans un pour `CFrameWnd` quitter le mode d’aide contextuelle. La réception de ce message met fin à la boucle modale démarrée par `CFrameWnd::OnContextHelp` .

| Paramètre et valeur de retour | Description |
|-|-|
|wParam|Non utilisé (0)|
|lParam|Non utilisé (0)|
|retourne|Non utilisé|

**WM_INITIALUPDATE**

Ce message est envoyé par le modèle de document à tous les descendants d’une fenêtre frame lorsqu’il est possible de procéder à la mise à jour initiale. Il correspond à un appel à `CView::OnInitialUpdate` mais peut être utilisé dans d’autres `CWnd` classes dérivées d’une autre mise à jour.

| Paramètres et valeur de retour | Description |
|-|-|
|wParam|Non utilisé (0)|
|lParam|Non utilisé (0)|
|retourne|Non utilisé (0)|

**WM_RECALCPARENT**

Ce message est envoyé par une vue à sa fenêtre parente (obtenue via `GetParent` ) pour forcer un recalcul de la disposition (généralement, le parent appellera `RecalcLayout` ). Cela est utilisé dans les applications serveur OLE où il est nécessaire que la taille de la trame augmente à mesure que la taille totale de la vue augmente.

Si la fenêtre parente traite ce message, elle doit retourner TRUE et remplir le rectangle transmis dans lParam avec la nouvelle taille de la zone cliente. Utilisé dans `CScrollView` pour gérer correctement les barres de défilement (placer ensuite sur l’extérieur de la fenêtre quand elles sont ajoutées) quand un objet serveur est activé sur place.

| Paramètres et valeur de retour | Description |
|-|-|
|wParam|Non utilisé (0)|
|lParam|LPRECT rectClient, peut être NULL|
|retourne|TRUE si le nouveau rectangle client est retourné ; sinon, FALSe.|

**WM_SIZECHILD**

Ce message est envoyé par `COleResizeBar` à sa fenêtre propriétaire (via `GetOwner` ) lorsque l’utilisateur redimensionne la barre de redimensionnement avec les poignées de redimensionnement. `COleIPFrameWnd` répond à ce message en tentant de repositionner la fenêtre frame à la demande de l’utilisateur.

Le nouveau rectangle, fourni dans les coordonnées clientes par rapport à la fenêtre frame qui contient la barre de redimensionnement, est pointé par lParam.

| Paramètres et valeur de retour | Description |
|-|-|
|wParam|Non utilisé (0)|
|lParam|LPRECT rectNew|
|retourne|Non utilisé (0)|

**WM_DISABLEMODAL**

Ce message est envoyé à toutes les fenêtres indépendantes détenues par une fenêtre frame en cours de désactivation. La fenêtre frame utilise le résultat pour déterminer s’il faut ou non désactiver la fenêtre indépendante.

Vous pouvez l’utiliser pour effectuer un traitement spécial dans votre fenêtre contextuelle lorsque le frame entre dans un État modal ou pour empêcher certaines fenêtres indépendantes d’être désactivées. Les info-bulles utilisent ce message pour se détruire quand la fenêtre frame passe dans un État modal, par exemple.

| Paramètres et valeur de retour | Description |
|-|-|
|wParam|Non utilisé (0)|
|lParam|Non utilisé (0)|
|retourne|Valeur différente de zéro pour **ne pas** désactiver la fenêtre, 0 indique que la fenêtre sera désactivée|

**WM_FLOATSTATUS**

Ce message est envoyé à toutes les fenêtres indépendantes détenues par une fenêtre frame lorsque le frame est activé ou désactivé par une autre fenêtre frame de niveau supérieur. Cela est utilisé par l’implémentation de MFS_SYNCACTIVE dans `CMiniFrameWnd` , pour maintenir la synchronisation de ces fenêtres indépendantes avec l’activation de la fenêtre frame de niveau supérieur.

| Paramètres | Description |
|-|-|
|wParam|L'une des valeurs suivantes :<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|Non utilisé (0)|

La valeur de retour doit être différente de zéro si FS_SYNCACTIVE est définie et que la fenêtre syncronizes son activation avec le frame parent. `CMiniFrameWnd` retourne une valeur différente de zéro lorsque le style est défini sur MFS_SYNCACTIVE.

Pour plus d’informations, consultez l’implémentation de `CMiniFrameWnd` .

## <a name="wm_activatetoplevel"></a>WM_ACTIVATETOPLEVEL

Ce message est envoyé à une fenêtre de niveau supérieur lorsqu’une fenêtre de son « groupe de niveau supérieur » est activée ou désactivée. Une fenêtre fait partie d’un groupe de niveau supérieur s’il s’agit d’une fenêtre de niveau supérieur (sans parent ou propriétaire) ou si elle appartient à une telle fenêtre. Ce message est similaire à l’utilisation de WM_ACTIVATEAPP, mais fonctionne dans les situations où les fenêtres appartenant à des processus différents sont mélangées dans une hiérarchie de fenêtre unique (courante dans les applications OLE).

## <a name="wm_commandhelp-wm_helphittest-wm_exithelpmode"></a>WM_COMMANDHELP, WM_HELPHITTEST WM_EXITHELPMODE

Ces messages sont utilisés dans l’implémentation de l’aide contextuelle. Pour plus d’informations, reportez-vous à la [note technique 28](../mfc/tn028-context-sensitive-help-support.md) .

## <a name="mfc-private-resource-formats"></a>Formats de ressources privées MFC

Actuellement, MFC définit deux formats de ressources privées : RT_TOOLBAR et RT_DLGINIT.

## <a name="rt_toolbar-resource-format"></a>Format de ressource RT_TOOLBAR

La barre d’outils par défaut fournie par AppWizard est basée sur une ressource personnalisée RT_TOOLBAR, qui a été introduite dans MFC 4,0. Vous pouvez modifier cette ressource à l’aide de l’éditeur de barres d’outils.

## <a name="rt_dlginit-resource-format"></a>Format de ressource RT_DLGINIT

Un format de ressource privée MFC est utilisé pour stocker des informations supplémentaires sur l’initialisation de la boîte de dialogue. Cela comprend les chaînes initiales stockées dans une zone de liste déroulante. Le format de cette ressource n’est pas conçu pour être modifié manuellement, mais il est géré par Visual C++.

Visual C++ et cette ressource de RT_DLGINIT ne sont pas requises pour utiliser les fonctionnalités associées de MFC, car il existe une alternative d’API à l’utilisation des informations de la ressource. L’utilisation de Visual C++ facilite grandement l’écriture, la maintenance et la traduction de votre application à long terme.

La structure de base d’une ressource de RT_DLGINIT se présente comme suit :

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

Une section répétée contient l’ID de contrôle auquel envoyer le message, le message # à envoyer (un message Windows normal) et une longueur variable de données. Le message Windows est envoyé sous la forme suivante :

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

Il s’agit d’un format très général, qui autorise tous les messages Windows et le contenu des données. L’éditeur de ressources de Visual C++ et MFC ne prennent en charge qu’un sous-ensemble limité de messages Windows : CB_ADDSTRING pour les choix de liste initiale pour les zones de liste déroulante (les données sont une chaîne de texte).

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
